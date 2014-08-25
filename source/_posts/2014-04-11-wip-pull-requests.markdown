---
layout: post
title: "Work-In-Progress Pull Requests"
date: 2014-04-11 08:19:56 +0700
comments: true
categories:
---

There've been a lot of criticism([1],[2],[3]) on Github Pull Requests
lately.

The summary is pretty much in this([4]) Hacker News comment:

> ...GitHub is missing this kind of environment(IRC, Mailing List), so
> it's almost inevitable that first contact between maintainers and
> potential contributors usually comes in the form of a pull request.

... and there's no code review and discussion is done BEFORE a pull
request, which is the main reason so many PRs are not accepted.

While it's definitely true, it don't have to be this way.

There's a common mental model the Pull Request is something finished.
The ready-to-ship kind of thing.

Well, not always.

In our team, we send Pull Requests as soon as there's one commit in a
new branch. Or even empty commit.

`git commit -m "initial commit: User can verify their account" --allow-empty`

Contributor starts with some basic ideas, small patches,
failing tests. And then the PR grows collaboratively. Somebody
contributes with comment. Somebody does commit. Sometimes commits are
reverted and replaced with better solutions. It's like an asynchronous
pair programming with unlimited collaborators. The value is tremendous.

And PR got merged only when no one have better ideas. Ideally all team
members, who are interested in keeping codebase clean and to have a
collective code ownership(everyone, right?), should look through PR and
leave :thumbsup: in comments. One thumb is required, others are
optional(if you're in a hurry with shipment, which you souldn't).

Although this kind of Work-In-Progress PRs are possible only in
repositories in which everyone has commit access to, I'd suggest to try
this approach when sending PR from a fork. The early-on feedback is
still very much valuable.

##### References:

- [@antirez - Pull requests are not conversations][1]
- [↑ & discussion on Hacker News][5]
- [@torvalds - "I don't do github pull requests..."][2]
- [@madsheep - Ups and Downs of Pull Request Flow][3]
- [NEOVim pull-requests][6]

![neovim-prs][7]



[1]: http://oldblog.antirez.com/post/pull-requests-are-not-conversations.html
[2]: https://github.com/torvalds/linux/pull/17#issuecomment-5654674
[3]: https://netguru.co/blog/posts/ups-and-downs-of-pull-request-flow-part-1
[4]: https://news.ycombinator.com/item?id=2183287
[5]: https://news.ycombinator.com/item?id=2182873
[6]: https://github.com/neovim/neovim/pulls
[7]: http://cl.ly/image/1Q2r1J0L2b35/Screen%20Shot%202014-08-25%20at%202.40.17%20PM.png
