---
layout: post
title: Ruby - private, protected and public
---

Programming Ruby (The pickaxe book) has the following definitions for public, protected and private methods.

> **Public methods** can be called by anyone - no access control is enforced. Methods are public by default (except for `initialize`, which is always private).

> **Protected methods** can be invoked only by objects of the defining class and its subclasses. Access is kept within the family.

> **Private methods** cannot be called with an explicit receiver - the receiver is always `self`. This means that private methods can be called only in the context of the current object; you can't invoke another object's private methods.


This stackoverflow [answer][1] gives a clear explanation on how private is different from protected.

The protected attribute is hidden from the outside world but if an instance of the class wants to compare itself with another instance of the class, it can access the protected attribute.
In the case of a private attribute, other instances of the same class will not have any access. Private methods are only accessible within that **instances** of the class.


In the context of Java, private is similar to the `protected` keyword as you can access the private method from within subclasses. 
This is because you do not need to have an explicit receiver to call the superclass method.

## The programmer is in charge

In the Eloquent Ruby book it states `The Ruby philosophy is that the programmer is in charge.`

So even though Ruby has the 3 levels of access control, you can gain access to any method by using the `send` method and passing it the symbol of the method you want to invoke.
It's up to the programmer whether they want to violate the access control.


[1]: http://stackoverflow.com/a/3534581/231513
