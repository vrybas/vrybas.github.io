---
layout: post
title: "Rails and Pipes"
date: 2014-04-04 07:06:42 +0700
comments: true
categories:
---



A **Controller/View** is just an Input/Output pipe.

A **Model** is just a Data Storage pipe.

Where's your application then?

<!-- more -->

**TL; DR**

[Ruby Midwest 2011 - Keynote: Architecture the Lost Years by Robert Martin][1]

{% youtube WpkDN78P884 %}

Your business logic got nothing to do with the WEB or database storage.
That's just a details. The core is in **Interactors** & **Entities**.

###### References:

- [Bob Martin - "Architecture. The Lost Years."][1]
- [Practicing Ruby Issue #4.11  - "Responsibility-centric vs.  data-centric design"][3]
- [Grouper - "Rails. The Missing Parts. Interactors."][2]
- [↑ & epic discussion on Hacker News][8] (mustread)
- [InfoQ - Domain Driven Design Quickly][9]
- [Focused Controller gem][6]
- [Decent Exposure gem][7]
- [Ruby Rogues Parley discussion][5]

[1]: http://www.confreaks.com/videos/759-rubymidwest2011-keynote-architecture-the-lost-years
[2]: http://eng.joingrouper.com/blog/2014/03/03/rails-the-missing-parts-interactors
[3]: https://practicingruby.com/articles/responsibility-centric-vs-data-centric-design
[4]: http://www.youtube.com/watch?v=4LMWsFbj6js
[5]: http://parley.rubyrogues.com/t/dhh-debating-controllers-abstracts-on-hn/1823/26
[6]: https://github.com/jonleighton/focused_controller
[7]: https://github.com/voxdolo/decent_exposure
[8]: https://news.ycombinator.com/item?id=7335211
[9]: http://www.amazon.com/Object-Oriented-Software-Engineering-Approach/dp/0201544350/
[10]: http://www.infoq.com/minibooks/domain-driven-design-quickly
