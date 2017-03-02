---
layout: post
title: "Directives: Angular JS"
date: "2017-02-02 03:00:10 +0100"
blog: true
author: kofi
image: /assets/images/Blog/angularjs.jpeg
tag:
  - tech
  - angularjs
  - javascript
  - directives
  - code
comments: true
description: A brief overview of directives in Google's Angular JS and its use with the help of a simple example
permalink: /blog/:categories/:title/
categories: Tech
---


Directives are if not the most relevant component of Angular JS, a very essential one. It affords the ability to basically extend HTML and makes code more readable.

![Angular JS](/assets/images/Blog/googleangularjs.jpg)
Directives are also reusable hence creating a more cleaner, easy to debug and easier to test codebase. Consider the code below:

{% highlight js %}

cars.directive('cars', function() {
    return{
       restrict: 'E',
       scope:{
       	info: '='
       },
       templateUrl: 'js/directives/cars.html'
      };
});
{% endhighlight %}


Directives basically tell the browser that a new element has been added.

Restrict signals how a particular element is to be used in the browser
Restrictions can be set to <br>

* E (as in this case) matches only element name
* A - matches only element name
* C - matches only class name
* M - matches only comment

Scope signals that information will be passed into this directive through the attribute.
Hence  info: '='  tells the directive to scan through the <cars> element for  an attribute called info.  The syntax is identical to calling a class to an html element e.g. <h1 class=”someclass”><h1>. In this case, it will be
{% highlight html %}
<cars info=”bmw”>
{% endhighlight %}

Scope:{} means is set to empty


The templateUrl is then used to specify the html file used to display the date. Typical html
{% highlight html %}
<h2 class="make">{{ info.make }}</h2>
<p class="manufacturer"> {{ info.manufacturer }}</p>
<p class="price"> {{ info.price | currency }}</p
{% endhighlight %}


Assuming the scopes have been defined in the MainController eg.




{% highlight js %}
cars.controller('MainController', ['$scope', function($scope) {
  $scope.bmw = {
    icon: 'img/bmw.jpg',
    make: 'BMW',
    Manufacturer: 'BMW Company.',
    price: 20,000
  };

  $scope.audi = {
    icon: 'img/audi.jpg',
    make: 'Audi',
    Manufacturerr: 'Audi Motors',
    price: 30,000
  };

  $scope.volkswagen = {
    icon: 'img/volkswagen.jpg',
    make: 'Volkswagen',
    Manufacturer: 'Volkswagen Motors.',
    price: 40,000
  };
}]);
{% endhighlight %}


Then data will be called and displayed in the format as defined in cars.html
