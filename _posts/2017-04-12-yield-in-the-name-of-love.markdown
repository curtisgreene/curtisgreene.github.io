---
layout: post
title:  "Yield in the Name of Love"
date:   2017-04-12 08:16:01 -0600
categories: ruby blocks yield
---


Ruby is a friendly language. The syntax and library of keywords make for a readable and accessible programmatic language. Such was Matsumoto's goal. That being said, there are plenty of ways that Ruby can get confusing or run counter to what you might be expecting. One specific keyword that I found initial confusing was `yield`. After learning the basics of Ruby, `yield` looked different than anything I had seen before (or so I thought).

To understand was `yield` does and how it is implemented, lets first take one step back to talk about **blocks**.

### Blocks ###

Must simply put, a block is code that does between a `do` and an `end`. This pair of words should seem really familiar. We see them encapsulating code in loops regularly. Blocks can be presented in two forms; multi-line and in-line.

* Multi-line blocks appear between `do` and `end`
* In-line blocks appear between curly braces; `{` and`}`

Let's take a look at a super simple example:

```ruby
[1, 2, 3].each do |n|
  puts "Number #{n}"
end
```

OR

```ruby
[1, 2, 3].each {|n| puts "Number #{n}"}
```

I'm not going to break down how an `each` loop works or explain the `n` as a `block parameter`, but it's important to know that blocks are common in Ruby. Blocks are chunks of code. No biggie.

### Yield ###

So now let's talk about `yield` -- the elephant in the room. Yield can be confusing because of how it gets called and how it interacts with parameters. Let first take a peek at a super simple example of `yield`.

```ruby
def simple_example
  puts "this is the top"
  yield
  puts "this is the bottom"
end

simple_example do
  puts "this is the yield"
end
```
And when this code gets run, it will return:
```
this is the top
this is the yield
this is the bottom
=> nil
```
Let's examine how we are calling the simple method I defined, `#simple_example`. The method gets called **with a block**. I think this is what catches people off guard about `yield`. You can call a method with a block attached to it. That is exactly what `yield` is waiting to see. Think about it as a parameter to the method -- just some additional code that we are including.

`yield` lets us _inject_ code into a method. This allows you to tweak how the method operates without having to rewrite the entire thing.  

If the method doesn't have a `yield` inside of it, that additional code (in the block) will get skipped.

 If you have a `yield` in your method, it will be listening for that method to be called with a block. When `#simple_example` is being executed line by line and gets to the `yield`, it will look for the block and execute that code. After the block we added to the method call is executed, we jump back into the method and execute what remains.

 If your method has a `yield` in it, but you call that method without including a block, your program will break. Specifically, it will break when it gets to the `yield`. It will successfully execute everything before it, but it wont know what to do with that lonely `yield`.

 ```ruby
 LocalJumpError: no block given (yield)
 ```

 [You can subvert this being using the predefined `#block_given?` method.](https://ruby-doc.org/core-2.1.1/Kernel.html#method-i-block_given-3F)

To complicate things a little `yield` can also take parameters. Let's look at another genius example:

```ruby
def genius_example
  yield("Ruby", 22)
end

genius_example do |language, age|
  puts "#{language} is #{age} years old."
end
```
and this will give us:

```
Ruby is 22 years old.
=> nil
```

Lastly, check out the return value. `yield` will returns the last evaluated expression from the block -- in this case `nil`. In other words, it will return what the block returns.

Hopefully this gives us a basic understanding of how `yield` functions in the simplest terms. It only gets more complicated from here, but understanding how `yield` works at a very basic level can help you not be so thrown off when you see it a more complicated context.
