---
layout: post
title: "Rails and Pipes (DDD notes)"
date: 2014-04-04 07:06:42 +0700
comments: true
categories:
---

Very interesting talk on Rails apps architecture by Uncle Bob.

[Ruby Midwest 2011 - Keynote: Architecture the Lost Years by Robert Martin][1]

{% youtube WpkDN78P884 %}

Here's the short summary:

"The MVC is not your applcation architecture.  It's just a tiny part of
it. The real Application should have it's own architecture(built in with
the best OOP practices and patterns), and interact with your
I/O(controllers) and data storage(models) via limited API.

The real Application should be in **Interactors** & **Entities**(or
similar structure). It should be in the **Service Layer**.

**Controller** => **Interactor** => **Entity** => **Model**

Controller shouldn't speak to the Model directly. And Model shouldn't
speak to other Models. And all the dependencies should go only one way,
but not the other."

Well, this totally ruins the Rails Way, and not really applicable
directly. But that's a good start and occasion to think about
architecture, code organizing etc. Here's some materials on the topic I
found useful and pleasant to read:

- [Practicing Ruby Issue #4.11  - "Responsibility-centric vs.  data-centric design"][3]
- [Grouper - "Rails. The Missing Parts. Interactors."][2]
- [↑ & epic discussion on Hacker News][8]
- [InfoQ - Domain Driven Design Quickly][9]
- [Jared Carrol - Does My Rails App Need a Service Layer?][11]
- [Wikipedia - Data, Context and Interaction(DCI)][12]
- [Focused Controller gem][6]
- [Decent Exposure gem][7]
- [Ruby Rogues Parley discussion][5]

[2]: http://eng.joingrouper.com/blog/2014/03/03/rails-the-missing-parts-interactors
[3]: https://practicingruby.com/articles/responsibility-centric-vs-data-centric-design
[4]: http://www.youtube.com/watch?v=4LMWsFbj6js
[5]: http://parley.rubyrogues.com/t/dhh-debating-controllers-abstracts-on-hn/1823/26
[6]: https://github.com/jonleighton/focused_controller
[7]: https://github.com/voxdolo/decent_exposure
[8]: https://news.ycombinator.com/item?id=7335211
[9]: http://www.amazon.com/Object-Oriented-Software-Engineering-Approach/dp/0201544350/
[10]: http://www.infoq.com/minibooks/domain-driven-design-quickly
[11]: http://blog.carbonfive.com/2012/01/10/does-my-rails-app-need-a-service-layer/
[12]: http://en.wikipedia.org/wiki/Data,_context_and_interaction
