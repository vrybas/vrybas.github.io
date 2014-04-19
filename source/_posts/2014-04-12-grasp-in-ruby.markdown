---
layout: post
title: "GRASP in Ruby(on Rails)"
date: 2014-04-12 14:51:59 +0700
comments: true
categories:
---

## What is GRASP?

**GRASP([1])** stands for General Responsibility Assignment Software
Patterns and Principles.

## Why it's important?

Responsibilities Assignment is one of the most important skills in OOP.

The two major problems of relatively large codebases - code is messy and
code is coupled. Usually it's messy because it's coupled. And often
times the cause is wrong responsibilities assignment.

So, GRASP helps to effectively distribute responsibilities between
objects.

These patterns and principles are:

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

_Controller is an object within the system which handles incoming
parameters and delegate work to others._

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

_Creator is an object, which creates other objects._

If the one class instance have enough data to create other class
instance (or form other class instance) - it should proceed with
creation.

That's how you extract responsibilities. By gathering together a related
data chunks with methods, required for its processing in a separate
class, which instance can be used in current context.

`$RAILS_ROOT/lib` is your friend at this time. But if this folder grows
tremendously, it's a clear sign you need a Service Layer([2]).

## High Cohension

_The responsibilities of a given element should be strongly related and
highly focused._

But Rails models usually look like a bunch of unrelated methods, just
happening to use the data from one database table. So, "Fat Models"
strongly violate this principle. Good news there's plenty of
ways([3],[4]) to decompose them.

Speaking of modules and "Concerns", it is actually cheating([5]),
because you're not taking responsibility away, you're hiding it. But it
still useful in some cases, and might be a first step on gathering and
extracting related pieces of functionality.

## Indirection

_The Indirection pattern supports low coupling (and reuse potential)
between two elements by assigning the responsibility of mediation
between them to an intermediate object._

MVC shows a good example of Indirection. Views don't know anything about
the Models(or shouldn't anyway), because there's a Controller between
them.

But in a complex system that's not enough. Ar Controller should not know
about the Models either, talking to them through Contexts, or UseCases,
or Interactors. And Controller action clearly shouldn't be using several
models at once.

## Information Expert

_Responsibility should be placed in a class with the most information
required to fulfill it's data._

While this is a good general approach, it better not to be in conflict
with **High Cohension** and not to produce God-classes(aka Fat Models).

## Low Coupling

Principles of Low Coupling:

* _Lower dependencies between classes_
* _Changes in one class should not impact other classes_
* _Higher Reuse Potential_

In Rails coupling often comes with chain(>2) of before_filters,
ActiveRecord callbacks and stuff like `accept_nested_attributes_for`.

To reduce a number of these harmful entities, you can use Creator class
and it's variations. Need to synchronize a creation of two or more
models during single HTTP request? Use an Interactor or UseCase in your
controller and make the process as clear as possible. Ideally, your
models should not know about each other more than they are
related via `has_many/belongs_to` associations.

## Polymorphism & Protected Variations

_According to Polymorphism, responsibility of defining the variation of
behaviors based on type is assigned to the types for which this
variation happens._

_The Protected Variations pattern protects elements from the variations
on other elements (objects, systems, subsystems) by wrapping the focus
of instability with an interface and using polymorphism to create
various implementations of this interface._

Sandi Metz excellent quote([6]):

> No object in your system should have to know the class of any other
> object in order to know how to behave.  Everything is a Duck.  Tell
> the Duck WHAT and the Duck should know HOW.


## Pure Fabrication

_A Pure Fabrication is a class that does not represent a concept in the
problem domain, specially made up to achieve low coupling, high
cohesion, and the reuse potential thereof derived (when a solution
presented by the Information Expert pattern does not). This kind of
class is called "Service" in Domain-driven design._

##### References:

- [Wikipedia - General Responsibility Assignment Software Patterns][1]
- [Rails and Pipes(DDD notes)][2]
- [Code Climate Blog - 7 Patterns to Refactor Fat ActiveRecord Models][3]
- [DHH - Put chubby models on a diet with concerns][4]
- [Ryan Bates - My issues with Modules][5]
- [Sandi Metz - Ruby Case Statements and 'kind_of?'][6]

[1]: http://en.wikipedia.org/wiki/GRASP_(object-oriented_design)
[2]: http://vrybas.github.io/blog/2014/04/04/rails-and-pipes/
[3]: http://blog.codeclimate.com/blog/2012/10/17/7-ways-to-decompose-fat-activerecord-models/
[4]: http://signalvnoise.com/posts/3372-put-chubby-models-on-a-diet-with-concerns
[5]: https://gist.github.com/ryanb/4172391
[6]: http://www.sandimetz.com/blog/2009/06/12/ruby-case-statements-and-kind-of/
