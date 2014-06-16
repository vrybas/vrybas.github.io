---
layout: post
title: "TDD resources"
date: 2014-04-30 23:34:04 +0700
comments: true
categories:
---

## Design:

### J.B. Rainsberger - [Integrated Tests Are A Scam][1]
> - They don't put pressure to the design
> - You can't possibly test all cases
> - Introduce "Collaboration" tests
> - Introduce "Contract" tests

### Chris Parsons - [Your Tests Are Lying To You][2]
> - Some tests are saying they're Unit, but they're actually Integration
> - Good design is easy to test - Corey Haines
> - Mockist vs Classist
> - Mocks are isolated, fast & tell you about design flaws

### Sandi Metz - [The Design of Tests][6]
> - Messages to self - rarely tested
> - Incoming messages - assert on result
> - Outgoing messages - test for calling
> - Outgoing queries - don't test!
> - Outgoing commands - expectations on mocks

## Mocks:

### Martin Fowler - [Mocks Aren't Stubs][3]
> - Mockist & behavior design VS Classist & STATE

### Corey Haines - [Yay! Mocks!][4]
> - Mocks lead to better design that easy to change
> - OO design is about interactions & roles
> - Delegate the "How"
> - Don't let mocks depend on other mocks

### Gregory Moeck - [Why You Don't Get Mock Objects][5]
> - Mocks assert on messages
> - Stub returns value
> - Mock Roles, not concrete objects.

### Gary Bernhardt - [Test Isolation Is About Avoiding Mocks][7]
> - Nested stubs are telling something about the design
> - Good TDDers don't write nested mocks
> - We write huge functions because there's no pressure of testing them
>   isolated.
> - Isolated tests are microscope of object interactions
> - Don't let your tests make code less readable
> - Don't isolate "Collaborator" classes

### Piotr Solnica - [Mocking and Ruby][8]
> - Mock only what you own
    If you don't own it, you don't have control on it's evolution
> - Don't mock just for speed
> - Be aware that mocks introduce maintenance costs
> - Keep mocks simple
> - Mock rarely

## Is TDD Dead?

### series: [Part 1 - 5][9]

[1]: http://vimeo.com/80533536
[2]: http://www.confreaks.com/videos/697-rubyconf2011-your-tests-are-lying-to-you
[3]: http://martinfowler.com/articles/mocksArentStubs.html
[4]: http://www.confreaks.com/videos/1237-aloharuby2012-yay-mocks
[5]: http://www.confreaks.com/videos/659-rubyconf2011-why-you-don-t-get-mock-objects
[6]: http://www.youtube.com/watch?v=qT5iriwidRg
[7]: https://www.destroyallsoftware.com/blog/2014/test-isolation-is-about-avoiding-mocks
[8]: http://solnic.eu/2014/05/22/mocking-and-ruby.html
[9]: http://martinfowler.com/articles/is-tdd-dead/




