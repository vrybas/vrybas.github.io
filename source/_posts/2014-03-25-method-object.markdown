---
layout: post
title: "Refactoring Patterns: Method Object"
date: 2014-03-25 07:06:42 +0700
comments: true
categories:
---

There are few ways to decompose a large class, which has too many
responsibilities. The one is to extract a module(mixin/concern).
Another is to extract a Method Object(or Service Object).

<!-- more -->

**TL; DR**

1. Take a huge method and copy-paste it to it's own class.
2. Pass all dependencies as parameters
3. Replace body of original method with Method Object call.


#### Before:

```ruby
def matches_conditions_hash?(subject, conditions = @conditions)
  if conditions.empty?
    true
  else
    if model_adapter(subject).override_conditions_hash_matching? subject, conditions
      model_adapter(subject).matches_conditions_hash? subject, conditions
    else
      conditions.all? do |name, value|
        if model_adapter(subject).override_condition_matching? subject, name, value
          model_adapter(subject).matches_condition? subject, name, value
        else
          attribute = subject.send(name)
          if value.kind_of?(Hash)
            if attribute.kind_of?(Array) || (defined?(ActiveRecord) && attribute.kind_of?(ActiveRecord::Relation))
              attribute.any? { |element| matches_conditions_hash? element, value }
            else
              !attribute.nil? && matches_conditions_hash?(attribute, value)
            end
          elsif !value.is_a?(String) && value.kind_of?(Enumerable)
            value.include? attribute
          else
            attribute == value
          end
        end
      end
    end
  end
end
```

#### After:

```ruby
def matches_conditions_hash?(subject, conditions = @conditions)
  IsMatchesConditionsHash.(model_adapter, subject, conditions)
end
```

```ruby
class IsMatchesConditionsHash < Struct.new(:model_adapter, :subject, :conditions)

  def self.call(*args)
    new(*args).call
  end

  def initialize(model_adapter, subject, conditions)
    self.model_adapter  = model_adapter
    self.subject    = subject
    self.conditions = conditions
  end

# ======== actual logic
  def call
    return true if conditions.empty?

    if model_adapter.override_conditions_hash_matching?(subject, conditions)
      return model_adapter.matches_conditions_hash?(subject, conditions)
    end

    conditions.all? do |name, value|
      if model_adapter.override_condition_matching?(subject, name, value)
        return model_adapter.matches_condition?(subject, name, value)
      end

      condition_match?(subject.send(name), value)
    end
  end
# ========

  private

  def condition_match?(attribute, value)
    case value
    when Hash       then match_hash_value(attribute, value)
    when Enumerable then (!value.is_a?(String) && value.include?(attribute))
    else attribute == value
    end
  end

  def match_hash_value(attribute, value)
    if attribute.kind_of?(Array) || (defined?(ActiveRecord) && attribute.kind_of?(ActiveRecord::Relation))
      attribute.any? { |element| self.class.(model_adapter, element, value) }
    else
      !attribute.nil? && self.class.(model_adapter, attribute, value)
    end
  end
end
```

We can go deeper of course. Shave the yak completely. But that's a good
start.

Actually, in this case, the implementation was moved back to the
original class with a few private methods extracted. But nice thing
about Method Object - it helps to understand all the dependencies this
beast have, so you can deal with it.

###### References:

- [Ryan Bates - My issues with Modules][1]
- [RailsCasts Pro - Service Objects][3]
- [Wikipedia - Composition over Inheritance][2]
- [SourceMaking - Replace Method with Method Object][4]

[1]: https://gist.github.com/ryanb/4172391
[2]: http://en.wikipedia.org/wiki/Composition_over_inheritance
[3]: http://railscasts.com/episodes/398-service-objects
[4]: http://sourcemaking.com/refactoring/replace-method-with-method-object
