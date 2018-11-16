---
layout: post
title:      "Principles of Object Oriented Programming"
date:       2018-11-16 19:57:34 +0000
permalink:  principles_of_object_oriented_programming
---


## Encapsulation
Encapsulation is binding the data and behaviors together in a single unit. The data is not accessed directly but accessed through the exposed functions. We create private methods to prevent other classes from accessing it. 

```
class Car
  att_accessor :name, :color, :model_year
	
  def initialize(name, color, model_year)
    @name = name
    @color = color 
    @model_year = model_year
  end
	
  def info
    "The car's name is #{@name} with color of #{@color} and model year of #{@model_year}"
  end
end
```

## Abstraction
It lets you focus on what the object does instead of how it does it. It means working with something we know how to use without knowing how it works internally. For example, we don’t need to know the inner workings of a car. We know that to make the car move, we put it in drive, press on the gas pedal on the right and use the steering wheel. 

## Inheritance
Inheritance helps in organizing classes into a hierarchy and enabling these classes to inherit attributes and behavior from classes above in the hierarchy. It describes an “is a” relationship. For example, a canary is a bird. You create a child class by deriving from another parent class. The child class reuses all methods of the parent class and can implement its own. This helps in reducing duplication of code.

```
class Vehicle
  def drive
    "Driving"
  end
end

class Car < Vehicle
end

mack = Car.new
mack.drive   // "Driving"
```

## Polymorphism
It allows us to define more than one way to do something. It redefines the way something works by either changing how it’s done or by changing the parts. You can override methods in derived classes, in order to change their original behavior inherited from the base class. 

```
class Animal
  def make_sound
    "Sound"
  end
end

class Dog < Animal
  def make_sound
	  "Woof"
	end
end

class Cat < Animal
  def make_sound
	  "Meow"
	end
end

dusty = Animal.new
dusty.make_sound   // "Sound"

perry = Dog.new
perry.make_sound   // "Woof"

coco = Cat.new
coco.make_sound   // "Meow"
```


