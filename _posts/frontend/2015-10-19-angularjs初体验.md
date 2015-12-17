---
layout: post
title: angularjs初体验
category: 前端工程
tags: 前端工程
keywords: 前端工程
description: angularjs初体验
---

> 很棒的学习网站 ： https://www.codecademy.com/

## Awesome! You built an AngularJS app. How does it work?

* In app.js, we created a new `module` named MyApp. A module contains the different components of an AngularJS app.

* Then, in` index.html `we added `<body ng-app="myApp">`. The `ng-app `is called a directive. It tells AngularJS that the MyApp module will live within the <body> element, termed the application's scope. In other words, we used the ng-app directive to define the application scope.

* In `MainController.js ` we created a new `controller` named MainController. `A controller manages the app's data`. Here we `use the property title to store a string`, and` attach it to $scope`.

* Then, in` index.html`, we added `<div class="main" ng-controller="MainController">`. Like ng-app, ng-controller is a directive that defines the controller scope. This means that properties attached to` $scope` in` MainController` become available to use within `<div class="main">`.

* Inside `<div class="main">` we accessed $scope.title using` {{ title }}`. This is called an expression. Expressions are used to display values on the page.

* The value of title showed up when we viewed the app in the browser.

## Modules 

```
// app.js
var app = angular.module("myApp",[]);
```

## 视图

```
// index.html
····
  <body ng-app="myApp">
  ···
  <div class="main" ng-controller="MainController">
···
```

## 控制器

```
// MainController.js
app.controller('MainController',['$scope',function($scope){
    $scope.title ='Hello Angularjs';
}]);

```

So far this is our typical workflow when making an AngularJS app:

1. Create a module, and use ng-app in the view to define the application scope.
2. Create a controller, and use ng-controller in the view to define the controller scope.
3. Add data to $scope in the controller so they can be displayed with expressions in the view.


Let's do a quick review:

* A module contains the different components of an AngularJS app
* A controller manages the app's data
* An expression displays values on the page
* A filter formats the value of an expression



MainController

```
// MainController
    $scope.products = [ 
  { 
    name: 'The Book of Trees', 
    price: 19, 
    pubdate: new Date('2014', '03', '08'), 
    cover: 'img/the-book-of-trees.jpg' 
  }, 
  { 
    name: 'Program or be Programmed', 
    price: 8, 
    pubdate: new Date('2013', '08', '01'), 
    cover: 'img/program-or-be-programmed.jpg' 
  } 
];
 
```