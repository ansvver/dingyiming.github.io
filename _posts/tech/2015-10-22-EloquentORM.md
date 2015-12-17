---
layout: post
title: EloquentORM的CURD
category: 技术
tags: laravel
keywords: laravel
description:laravel的EloquentORM的CURD
---

> 学一下,只记有用的关键点，其他用到时候查，不可急于大而全
> http://laravelacademy.org/post/138.html
> http://laravelacademy.org/post/966.html

## 获取输入的值

```
 $input = $req->all();
 $input['intro'] = mb_substr($req->get('content'), 0, 64);
  //$input['published_at'] = Carbon::now();
  $article = Article::create($input);
```

## Model模型类

* 命令生成

```
php artisan make:model Article
```

* 表名为 `Articles`（复数）,模型类名为 `Article`（单数）
* 指定模型对应表

```
protected $table = 'my_flights';
```

* 指定主键名

```
protected $primaryKey = 'u_id';
```

* 不自动管理 created_at和updated_at

```
public $timestamps = false;
```

* 序列化时间格式

```
 protected $dateFormat = 'U';
```

* 可被批量复制的字段需要设置

```
protected $fillable = ['name'];
```

* 不能被批量复制的字段设置

```
 protected $guarded = ['price'];
```

## Eloquent查询

* 所有值

```
$articles = App\Article::all();
return view('article.index',compact('articles'));
```

* 添加约束

```
$articles = App\Article::where('id', 1)
               ->orderBy('id', 'desc')
               ->take(10)
               ->get();
```

* 分组块

```
Article::chunk(10, function () {}
```

* 条件查找

```
Article::find(1);
```

* 根据条件查找第一条记录

```
Article::where('title', 1)->first();
```

* 查找失败,抛异常

```
Article::findOrFail(1);
Article::where('id', '>', 10)->firstOrFail(); //有则得到第一个结果，不然抛异常
```

* 其他

```
->count(); //总数
->max();//最大
-> sum();
```

## Eloquent 插入

* 单个保存

```
$article = Article::find(1);
$article->title = 'New title';
$article->save();
```

* `firstOrCreate `
* `firstOrNew `
* 批量赋值

```
 $input = $req->all();
 $article = Article::create($input);
//获取全部请求参数存储，需要设置fillable
```

## 删除

* 查找删除

```
$article = Article::find(1);
$article->delete();
```

* 软删除

## 更新

```
Article::where('id', 1)
          ->where('title', 'new title')
          ->update(['content' => 'xxx']);
```