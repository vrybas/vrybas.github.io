---
layout: post
title: "How Do I Pomodoro"
date: 2014-03-24 07:38:21 +0700
comments: true
categories:
---

I'm a big fan of **Pomodoro** time management technique, created by
Francesco
Cirillo in the 80's. In this post I'll describe what it is, how I use it
(tools and their tweaks), and how it helps me to get through my day.

<!-- more -->

## Interruptions

Interruptions are horrible. They are your productivity's worst enemy.
Jason Fried gave excellent [talk][1] on that. In fact, the most important
measurement of quality of your working environment (and working style) is how
much uninterrupted time you can have per day.

{% youtube 5XD2kNopsUs %}

There are external interruptions. A dozen of devices ring one after another.
Notifications pop up on the screen. People come talk to us.  It's hard to get
away even for 10 minutes.

And there's also interruptions of our own. We become "tired" and "feel like
we deserve a break". We open up twitter and who knows if we come back
for next 30 minutes. Or some idea just hits us in the middle of the working
day, and we can't help but think it over and over again, while, at the same
time, trying to stay focused on current task.

The thing is, we can't just shut off all notifications and don't talk to
anybody. At least not for a long time. We are team workers, and have to
interact. And we can't work without breaks all day long, but we want to
control them, so a little trip to Facebook don't become a time-wasting
disaster. We don't want our brilliant ideas to get lost, but we want to work
on them on priority.

## Pomodoro is here to help

So there's a Pomodoro Technique ([pdf][2]). In short, it offers you to work
for a fixed amount of time, and then have a fixed short break.

You set a timer to 25 minutes(canonical), and, during that time, you shut off
all your notifications. Nothing and no one can interrupt you, even your
lazy-self. You're don't let yourself to think of any extraneous thoughts. If
something pops up to your mind, you write it down somewhere (if it's worth it)
to come back to it later.

After timer rings, you immediately stop what you're doing, checking your email
and other messages, you go get that co-worker who had a question. And, more
importantly, you're having a scheduled break for 5 minutes or so. It's a good
time to stand up, walk outside, get some water and fresh air, [limber up][3],
give your brain, eyes and whole body some rest.

[![](http://f.cl.ly/items/0h1M0D2T3T2n1W1e0h2A/Screen%20Shot%202014-03-24%20at%2011.01.21%20PM.png)][3]

This is just the right balance between work and rest. It gives ability
to be interrupted and communicate only when you're available and when you don't mind.
It also makes you more self-disciplined in general, as well as it's a good will-power
exercise.

## But how 'bout my Flow?

Yes, [Flow][4]. The thing with Flow is hard to get in and so easy to get
out. Some of Pomodoro newbies complain that this forced break is a
Flow-killer. But I don't think it is. Well, Pomodoro helps you to get into the
Flow at the first place. And, again, you don't want to get lost for several
hours for the team, draining all of your brain & body power, leaving yourself
completely exhausted. Pomodoro helps to stay productive all day
(days/weeks/months), not just a few Flow hours.

Yes, it is hard to go for a break when you're in a middle of something. But it
teaches you to respect your time and "protect Pomodoro at all cost", so you
can do more. Also, when it's couple of minutes left on the timer, you should
start writing down what you're doing now, and what you're going to do next
(which is a good thing to do anyway). So, for me, that's never been a problem
to get back to the same point after a break.

But every workflow is different, and every mind is different. For example in
ability to stay focused on a task for a long period of time. So, I can suggest
to just try it out for a few days and see if it works for you.

## Start it slow

A quick tip for Pomodoro beginners - start it slow. Maybe you would want
to start with 10 minutes of high quality Pomodoro. Or even 5 minutes. And
increase length over time. Because successful short Pomodoros are better than
few [#procastodoros][16].

[![](http://f.cl.ly/items/2L2Z2j2s243l3G1W0A2v/Screen%20Shot%202014-03-24%20at%2010.54.38%20PM.png)][16]

## There's an app for that

In fact, that can be enough to use a kitchen timer (the one they're
[offering][5] on the site) with just pen & paper. I know a bunch of developers
who use pen & notebooks as a primary GTD tool and it works for them. And if it
works for you - that's fine. But there sure some apps. I'll describe my
favorites. Each one works best in certain circumstances.

#### [Tomato.es (Web)][10]

The best way to try Pomodoro out. You don't have to install anything. Just
open new tab with this application, sign in with Github or Twitter
(optionally), hit Space bar and see the timer going. It'll ring when Pomodoro
is over and send Chrome's desktop notification. And there's a nice daily,
weekly, monthly stats and even Leaderboards.  After all, it's
[opensource](https://github.com/potomak/tomatoes), so you can suggest (or
better develop) some new features.

#### [Teamodoro.com (Web)][11]

This one is for team synchronization. You can't stop and start Pomodoros,
they're just starting automatically and counter is the same for everybody. And
nice and simple fullscreen view to put on external monitor/device.

#### [Wind-up Timer (iOS)][6]

Swipe to set a timer to desired time. It ticks in the background. It rings in
the end. Nice design. It is always in your pocket or desk. Well, mostly. I was
happy with it at first. But there's no way to disable iOS notifications and
keep the screen unlocked. So you basically set a timer and enable airplane
mode or lock the screen. Still useful sometimes.

#### [Pomodoro.app (OSX)][13]

![](http://f.cl.ly/items/2w34273X191m1W1r1B2i/Screenshot_6_30_13_9_15_PM-2.png)

The most advanced OSX Pomodoro I've seen. You can configure everything.
Pomodoro length, break length, automatic restarts, sounds, Growl
notifications, Twitter integration, Calendar intergration and, finally,
execute applescripts on Pomodoro start/end/reset/interrupt/resume. And this
opens endless possibilities, like disabling all possible notifications on your
Mac & Devices when Pomodoro starts, and automatically re-enable them when
Pomodoro ends. And, for instance, send message to Campfire. Check out my
set of [pomodoro-scripts][12].

The app is [opensource][13], you can compile it with XCode. Or download
precompiled version [here][14].

#### [BreakTime (OSX)][8]

This is not exactly a Pomodoro. It's just locks your screen after specified
amount of time, so you are forced to take a break. Sometimes I use it
standalone, or accompanied with other tools. Can execute applescripts.

#### [Thyme (console)][9]

And, finally, the terminal solution. Which have nice progressbar, Tmux
integration, and can also execute applescripts (via [osascript][15]) or any
other terminal commands.

That's it. Be productive, respect your time, and happy Pomodoring!

###### References:

- [Jason Fried - Why work doesn't happen at work][1]
- [The Pomodoro Technique by Francesco Cirillo][2]
- [Bathroom Break Yoga - infographic][3]
- [Flow - Wikipedia][4]
- [The Pomodoro Technique official timer][5]
- [Tomato.es][10]
- [Teamodoro.com][11]
- [Wind-up Timer][6]
- [Pomodoro.app][13]
- [Pomodoro Scripts][12]
- [BreakTime][8]
- [Thyme][9]

[1]: http://www.ted.com/talks/jason_fried_why_work_doesn_t_happen_at_work.html
[2]: http://www.pomodorotechnique.com/download/pdf/ThePomodoroTechnique_v1-3.pdf
[3]: http://infographicsmania.com/wp-content/uploads/2012/09/Bathroom-Break-Yoga-infographic.jpg
[4]: http://en.wikipedia.org/wiki/Flow_(psychology)
[5]: http://pomodorotechnique.com/timer/
[6]: https://itunes.apple.com/us/app/wind-up-timer/id325610693?mt=8
[8]: https://itunes.apple.com/us/app/breaktime/id427475982?mt=12
[9]: http://thymerb.com/
[10]: http://tomato.es/
[11]: http://teamodoro.com/
[12]: https://github.com/vrybas/pomodoro-scripts
[13]: https://github.com/ugol/pomodoro
[14]: http://cl.ly/3Q3H333y2132
[15]: https://github.com/vrybas/dotfiles/blob/4b0f29c0dd688f8bb78eec5d66f6c657a4bf9bb1/thyme/thymerc.symlink#L4
[16]: https://twitter.com/kubem/status/350390764515233792
