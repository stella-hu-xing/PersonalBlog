---
title: AngularJS Basic Concepts
date: 2017-07-18 14:54:13
tags: AngularJS
---

## JS Framework
AngularJS is a JavaScript framework. It is a library written in JavaScript.

AngularJS is distributed as a JavaScript file, and can be added to a web page with a script tag:

```
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
```

## Important Concepts
AngularJS extends HTML with __ng-directives__.

The __ng-app__ directive defines an AngularJS application.

The __ng-model__ directive binds the value of HTML controls (input, select, textarea) to application data.

The __ng-bind__ directive binds application data to the HTML view.

```
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
<body>

<div ng-app="">
  <p>Name: <input type="text" ng-model="name"></p>
  <p ng-bind="name"></p>
</div>

</body>
</html>
```
The __ng-init__ directive initializes AngularJS application variables.
```
<div ng-app="" ng-init="firstName='John'">

<p>The name is <span ng-bind="firstName"></span></p>
<p>The name is also as {{firstName}}</p>
</div>
```

## Expressions
AngularJS expressions are written inside double braces: {{ expression }}.
AngularJS expressions bind AngularJS data to HTML the same way as the __ng-bind__ directive.

## Applications
AngularJS __modules__ define AngularJS applications.

AngularJS __controllers__ control AngularJS applications.

The __ng-app__ directive defines the application, the __ng-controller__ directive defines the controller.

```
<div ng-app="myApp" ng-controller="myCtrl">

First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{firstName + " " + lastName}}

</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.firstName= "John";
    $scope.lastName= "Doe";
});
</script>
```

