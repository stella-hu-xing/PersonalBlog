---
title: AngularJS Study Notes 2
subtitle: Modules and Directives
date: 2017-07-19 13:38:45
tags: AngularJS
---

## Modules
An AngularJS module defines an application.

The module is a container for the different parts of an application.

The module is a container for the application controllers.

Controllers always belong to a module.

e.g. create a module and add one controller to it
```

<div ng-app="myApp" ng-controller="myCtrl">
{{ firstName + " " + lastName }}
</div>

<script>
//declare the myApp above
var app = angular.module("myApp", []);

app.controller("myCtrl", function($scope) {
    $scope.firstName = "John";
    $scope.lastName = "Doe";
});

</script>
```

## Functions local to module
Global functions should be avoided in JavaScript. They can easily be overwritten or destroyed by other scripts.

AngularJS modules reduces this problem, by keeping all functions local to the module.

## Load the library
It is recommended that you load the AngularJS library either in the <head> or at the start of the <body>.
This is because calls to angular.module can only be compiled after the library has been loaded.

## Directives
AngularJS lets you extend HTML with new attributes called Directives.

AngularJS has a set of built-in directives which offers functionality to your applications.

AngularJS also lets you define your own directives.