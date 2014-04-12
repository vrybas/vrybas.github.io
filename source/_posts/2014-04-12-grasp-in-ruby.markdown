---
layout: post
title: "GRASP in Ruby"
date: 2014-04-12 14:51:59 +0700
comments: true
categories:
---

## What is GRASP?

**GRASP** stands for General Responsibility Assignment Software
Patterns.

## Why it's important?

It turns out that Responsibilities Assignment is one of the most
important skills in OOP.

The two major problems of relatively large codebases - code is messy and
code is coupled. Usually it's messy because it's coupled. And often
times the cause is wrong responsibilities assignment.

So, GRASP is a set of patterns, which helps to distribute
responsibilities between objects.

These patterns are:

* Controller
* Creator
* High Cohension
* Indirection
* Information Expert
* Low Coupling
* Polymorphism
* Protected Variations
* Pure Fabricaton

## Controller

Controller is an object within the system which handles incoming
parameters and delegate work to others

That's what "C" in "MVC" for. In Rails we have our Controllers, which
handle incoming requests. But, according to GRASP, they should meet a
few requirements:

* The controller should delegate the work that needs to be done to other
  objects
* It only coordinates or controls the activity
* It should not do much work itself

So, in other words, the controller should be skinny. Maybe so skinny it
can only process incoming parameters and render results. All other work
should be delegated if possible.

## Creator

Creator is an object, which creates other objects.

If the one class instance have enough data to create other class
instance (or form other class instance) - it should proceed with
creation.

That's how you extract things. By gathering together a related data
chunks with methods, required for its processing in a separate class.

`$RAILS_ROOT/lib` is your friend at this time. But if this folder grows
tremendously, it's a clear sign you need a [Service Layer][2].

## High Cohension

The responsibilities of a given element should be strongly related and
highly focused.

But Rails models usually looks like a bunch of unrelated methods, just
happening to use the data from one database table.

## Indirection

Like Controller between Model and View

## Information Expert

Responsibility should be in a class, which have most of required data
(sometimes not true)

## Low Coupling

* Lower dependencies between classes
* Changes in one class does not impact other classes
* Higher Reuse Potential

## Polymorphism

## Protected Variations

Interface + polymorphism

## Pure Fabrication

A Service class, which does not have it's own logic. And specially made
up to achieve low coupling e.t.c.

##### References:

- [Wikipedia - General Responsibility Assignment Software Patterns][1]
- [Rails and Pipes(DDD notes)][2]

[1]: http://en.wikipedia.org/wiki/GRASP_(object-oriented_design)
[2]: http://vrybas.github.io/blog/2014/04/04/rails-and-pipes/
