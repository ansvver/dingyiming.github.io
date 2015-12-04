---
layout: post
title: laravel初学CRUD记录
category: 技术
tags: laravel
keywords: laravel,CRUD
description: laravelCRUD记录
---

```
//获取数据库名称，检测数据库是否连接成功
Route::get('/dbname', function(){
   $name = DB::connection()->getDatabaseName();
   echo $name;
});

//增 Insert
Route::get('db/insert', function(){
   $data = array('what\'s your name?','myname is Tom!');
   $posts = DB::insert('insert into demo1(title,body) values(?,?)',$data);
   dd($posts);
});

//查 Select id
Route::get('db/select/id',function(){
    $data = array(1);
    $posts = DB::select('SELECT * FROM demo1 WHERE id = ?',$data);
    dd($posts);
}

);

//查 Select all 返回结果数组
Route::get('db/select/all',function(){
    $posts = DB::select('SELECT * FROM demo1');
    dd($posts);
});

//改 update 返回 0或1
Route::get('db/update',function(){
    $data = array('更新下',2);
    $posts = DB::update('UPDATE demo1 set body = ? WHERE id = ?',$data);
    dd($posts);
});

//删 ,返回0或1 
Route::get('db/delete',function(){
    $data = array(3);
    $posts = DB::delete('DELETE FROM demo1 WHERE id = ?',$data);
    dd($posts);
});

```