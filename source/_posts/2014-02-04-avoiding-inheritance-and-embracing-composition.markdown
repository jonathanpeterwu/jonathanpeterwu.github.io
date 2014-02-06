---
layout: post
title: "Avoiding Inheritance and Embracing Composition"
date: 2014-02-04 23:26:21 -0800
comments: true
categories: 
---
### A look at the dark forces of inheritance and the guiding light of composition

I am currently taking a nine week bootcamp intensive called devbootcamp  in San Francisco learning web development with a rapid accelerated learning curve, looking at how learning mindset and motivation can affect growth.

![Inheritance Dark fores][1]

    "In object oriented programming, Inheritance is the evil forest. Experienced programmers know to avoid this evil because they know that deep inside the Dark Forest Inheritance is the Evil Queen Meta-Programming." -Zed Shaw

####Keywords to know:

**Implicit Inheritance**
In object-oriented programming (OOP), implicit inheritance is when an object or class is based on another object or class, using the same implementation
**Explicit Inheritance**
In object-oriented programming (OOP), explicit inheritance is when a user directly alters inheritance to have a class inherit attributes from a class not implicitly related.
**Composition**
Is the act of composing and relating two different object classes together so that they are interlinked, a containing object is responsible for both the creation and destruction of its interlinked object

### Composition with class Car and Type
```ruby
class Car
    attr_reader :wheels, :engine
    def structure
      @wheels = 4
      @engine = "diesel"
      puts "#{@wheels} wheels, and a #{@engine} engine"
    end
end

class Type
    attr_reader :type, :color, :car
    def initialize(*args)
        @car = Car.new()
        @type = args[0]
        @color = args[1]
        puts "Your #{color} #{type} car has"
        puts car.structure
    end

end

ferrari = Type.new("ferrari", "red")
```

####**_What is going on here?_** 
When creating a Car Class one can ascribe attributes to all car types, some of the standards might be their number of wheels, and whether they have an engine or not. When we create a Type class that wants to reference Car Class, the assumption is to create inheritance between the two class like below:
### Explaining Explicit Inheritance 
```ruby
 class Car
    #redacted
end
    
class Type < Car # this would inherent the attributes of Car class
    #redacted
end
```

####**_Why does this even matter?_**
That's a great question to explore... Now in the simple case of what we're doing in this example,inheritance is not a big deal. It is very clear that a class Car's attributes are to be inherited and embodied by class Type. Unfortunately when creating larger, long-lasting code. Inheritance becomes a tricky game to play if you do not consider the incorrect assumptions of what inheritance passes. This is because inheritance, passes along to class Type the blueprint or framework of the class Car. Unfortunately passing the blueprint of class Car is not the same as passing in data about an instance of the class Car such as ferrari = Car.new("red"). In this case ferrari's data of color red will not be inherited by class Type 

### The Darkness of Inheritance
```ruby
    class Car
        def initialize(engine_type)
            @engine = engine type
        end
    end
    
    class Type < Car
        # code redacted
        def print
            print @engine
        end
    end
    
    #Drivercode
    diesel_car = Car.new(diesel)
    vw = Type.new
    # this will not return a vw car instance type with diesel, this is because inheritance does not pass in the instance data of class Car 
```


####**_Wrapping Up_**
A good rule of thumb is to be wary of the use and application of inheritance as a way to pass in structure to another class if the use is not very clear and defined. Instead take a look at using composition to create relationships between different classes that are related. Remember

>Always test what your code is doing, try it out in IRB or use the Ruby Debugger gem to see what you "think" is actually going on 

##**Extras**

####Do some more reading
[inheritance vs composition](http://ruby.learncodethehardway.org/book/ex44.html)
[wikipedia: composition over inheritance](http://en.wikipedia.org/wiki/Composition_over_inheritance)


  [1]: http://prodigalthought.files.wordpress.com/2011/04/dark-forest-night-image.jpg

