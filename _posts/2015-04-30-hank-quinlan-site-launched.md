---
layout: post
title: "Let's build our own enum :)"
date: 2014-04-30
---
In this post I'm going to build the Rails enum type from scratch.

Why would you care to read a whole post of me implementing something that was already implemented by people more competent than me long ago? Well buckle your seat belt my friend because this ride is going to be fun, and educational: my solution for enum is much smaller and easier to understand and get your head around. So the outcome is (hopefully) a nice exercise that will make you practice your Rails  metaprogramming chops. Since some of the concepts were new to me I'll make it a point to be as specific and clear as possible, something I hope you will appreciate.

OK,  still here ? Let's get started!

First refresh your memory with [http://edgeapi.rubyonrails.org/classes/ActiveRecord/Enum.html](enums) if you need to. 
Just to recap: Enums are a way to represent a collection of string values without actually saving them in the database(Rails is smart enough to save an integer that holds the place in array of enum values and give you the string value instead), for example:

```ruby
class User < ActiveRecord::Base
  enum status: ['active', 'inactive', 'archived']
end

user.status
=>"active"
#Rails automagically returns the enum string value , in this case 'active', instead of the real database value which is 0
```
So despite the status field being an integer , Rails will give you the semantic word value (in this case - 'active'). This makes it nicer for you as an app developer because the code is clearer. You can do 

```ruby
user.active?
```
instead of having to do remember in your head that the active status is 0 

```ruby
#without enums we would need to do remember the integer values which aren't semantic and make for vague code
user.status == 0
```

Let's define what our enum module needs to implement:



