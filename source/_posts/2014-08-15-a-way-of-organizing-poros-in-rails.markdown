---
layout: post
title: "A way of organizing POROs in Rails"
date: 2014-08-15 20:26:54 +0700
comments: true
categories:
---


## Service layer

So, now we came to a point where our app no longer fit to MVC and we
want to extract a service layer. By "Service Layer" I mean a collection
of Plain Old Ruby Objects, which hold pure business logic. What kind of
POROs it might be? Here's good [examples][1] by Bryan Helmkamp.

But, anyway, the question is - where do we put them?

We got several options here:

1. Dump everything to `lib/` dir
2. Call them non-ActiveRecord Models
3. Use Cases and Entities (DDD approach)
4. ???

Let's go through these options one after another.

### 1. `lib/`

If class/module is not Model, View or Controller, it suppose to go to
`lib/`, isn't it? Well, this approach got some disadvantages.

When you start to extract your business logic to POROs, on a big project
you're going to have a few dozen of them, maybe hundred(s). Pretty
soon you open your `lib/` - and it scares you. Even worse when it gets
explored by a new team member.

Another thing - it's pretty easy to loose track on what is used where
and for what reason. Especially in dynamic language like Ruby.

So, slowly but surely, `lib/` becomes "a big ball of mud".

## 2. non-ActiveRecord Models

It could be that everything what is not Controller, not AR Model itself
and not a Policy/Form/Service Object, and returns you some data
structure - is another Model, which doesn't inherit from
`ActiveRecord::Base`.

Well, that's better. Sort of. Part is in `lib/`, part is in `models/`. A
slightly less mess, but in two places now.

Besides, there's a problem each time to decide, whether this PORO is a
"model" or not. And it's even harder for others to guess, where to find
that class, when they explore your code.

## 3. Use Cases & Entities

The concept of Use Cases & Entities comes from DDD and from Bob Martin's
[talk][2] "Architecture: The Lost Years".  So, the core of your system
suppose be in UseCases(verbs e.g. *CreateUser*) and Entities(nouns e.g.
*User*).

But the problem with this - it takes you far away from "The Rails Way".
In one case I want to use my ActiveRecord model as Entitly, but in the
other case it should be a separate class with it's corresponding
Repository class. Sometimes, my Controller is pretty much the UseCase,
but sometimes I want to extract a few classes from it.

Decisions, decisions. It's all confusing. Besides, everyone in the team
need to share the exact same architectural concepts (which is solved by
Rails Way at first place). Pretty quick the codebase can become more
mess and hard to follow through, than it was before.

## 4. Namespaces FTW!

So, there's another approach, which is used by every single gem and
almost any other Ruby program - the namespaced classes and modules.

###### Disclaimer: As usual, code examples are highly synthetic and short to keep them easy to follow. Your "results may vary".

### Example with Controllers

Let's say you got a dashboard in your app.


```ruby
class DashboardController < ApplicationController
    def index
    end
end
```

And you want to show a list of users on this dashboard. But user list
should be paginated, sortable, and `current_user`-specific. Now, I think
it's a good idea to create a `UserList` class, which will handle all
this logic.

But where do I put this class? Is this a Service / Model / UseCase /
Entity / QueryObject? When using namespaces, the answer is - I don't
really care.

All I need to do is to create one more folder in `controllers/` with the
same name as controller.

```
controllers
├── dashboard_controller
│   └── user_list.rb
└── dashboard_controller.rb
```

and put my `UserList` class there

```
# app/controllers/dashboard_controller/user_list.rb

class DashboardController::UserList
  # codes codes codes
end
```

and then it can be used in `DashboardController` like this

```
class DashboardController < ApplicationController
  def index
    @users = UserList.new(current_user,
                          page: params[:page],
                          per_page: params[:per_page],
                          sort_by: params[:sort_by],
                          order_asc: params[:order_asc]).all
  end
end
```

Note that we don't even need to specify the namespace.

### Example with Models

Pretty much the same thing is with models. But with Models you'd
probably extract more Modules/Concerns than Classes.

```
class User < ActiveRecord::Base
  include Lockable
  include Settings

  def can_follow?(user)
    FollowingPolicy.new(self, user).can_follow?
  end
end
```

with files structure

```
models
├── user
│   └── following_policy.rb
│   └── lockable.rb
│   └── settings.rb
└── user.rb
```

and possible content

```
# app/models/user/lockable.rb
module User::Lockable
  def lock_access!
    update(locked_at: Time.now)
    UserMailer.account_locked_email(self).deliver
  end

  # ...
end

# app/models/user/settings.rb
module User::Settings
  extend ActiveSupport::Concern

  included do
    store_accessor :settings
  end

  # ...
end

# app/models/user/following_policy.rb
class User::FollowingPolicy
  attr_reader :current_user, :other_user, :account_verification

  def initialize(current_user, other_user)
    @current_user = current_user
    @other_user = other_user
    @account_verification = current_user.account_verification
  end

  # ...
end
```

As a result - your code is more logically organized. It would be
pretty easy to guess the locations of classes while exploring code. And
you'll never afraid to extract one more single responsibility class,
knowing that it is going to be small and "local" and won't conflict with
other's classes.

What goes to `lib/` then? API wrappers for one example. The
application-independent code, or code which doesn't belong to any model
or controller.





[1]: http://blog.codeclimate.com/blog/2012/10/17/7-ways-to-decompose-fat-activerecord-models/
[2]: http://vrybas.github.io/blog/2014/04/04/rails-and-pipes/
