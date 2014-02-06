---
layout: post
title: "Learning Ruby Singletons"
date: 2014-02-02 19:32:35 -0800
comments: true
categories: 
---

The application of the singleton class is really interesting, it is considered an in between class 
( the singleton class sits between an object and its object class!). This means that you can create instances of an object, and if you wanted to change something about one specific object you can alter that without changing anything in the class method it looks like this
________________________________________________
    instance_object = Object.new
    instance_object.name == "Hello"
    
    def instance_object.name
             return "Goodbye"
    end 
this should override hello and return goodbye for only this instance of the Object class.