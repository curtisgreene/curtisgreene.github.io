---
layout: post
title:  "Why Do We Use Symbols for Keys"
date:   2017-03-23 12:20:49 -0400
categories: hashes keys symbols strings
---


Hashes are a common and powerful data structure in Ruby. Like Objects in Javascript, hashes contain pairs of associative data, known as Key-Value Pairs. These pairs have two parts; (unsurprisingly) keys and values. The easy analogy is a dictionary: Keys are like the words and Values are like the definitions.

As you are learning more about hashes in Ruby, you’ll see that keys are most commonly set to SYMBOLS, an interesting type of data in Ruby. Values can be any type of data, be it a string, an integer, and float, but why are keys usually presented as SYMBOLS. What is a symbol anyway? Why do I care? But why male models?

SYMBOLS are like strings except in one very important way — they cannot be changed.
In Ruby, strings can be mutated in many, many different ways — that is one of the things we love about Ruby!

{% highlight ruby %}
2.3.0 :005 > "This is a cool string!".reverse
 => "!gnirts looc a si sihT"
2.3.0 :006 > "This is a cool string!".upcase
 => "THIS IS A COOL STRING!"
2.3.0 :007 > "This is a cool string!".downcase
 => "this is a cool string!"
 {% endhighlight %}

Because strings are implicitly mutable, Ruby knows that every string in your source code needs it’s own object id; essentially being a unique entity. So if you are mentioning strings that look the same throughout your program (like when you are operating on a hash) each one of those has its own object id.

{% highlight ruby %}
2.3.0 :001 > "name".class
=> String
2.3.0 :002 > "name".object_id
=> 70229489515160
2.3.0 :003 > "name".object_id
=> 70229489367560
2.3.0 :004 > "name".object_id
=> 70229489299120
2.3.0 :005 >
{% endhighlight %}

Symbols, however, cannot be mutated at all. Because symbols are immutable, they only need to be saved in a single place in memory and given a single object id. For this reason, symbols are ‘lighter’ than strings.

{% highlight ruby %}
2.3.0 :001 > :some_symbol.class
 => Symbol
2.3.0 :002 > :some_symbol.object_id
 => 1156828
2.3.0 :003 > :some_symbol.object_id
 => 1156828
2.3.0 :004 > :some_symbol.object_id
 => 1156828
{% endhighlight %}

Once you declare a symbol, in this context as a Key in a hash, you cannot change it. You can change the value it references through hash operations, but you can’t change the symbol. This results in slightly faster programs.


That may feel sort of limiting, but when you are operating inside of a massive hash, this becomes  a strength. By having your keys be immutable, you don’t have to worry about what will happen if your keys change names — if just won’t happen. Remember that hashes can be nested, so things can get complicated fast. Eliminating chances for errors is a huge help.

Similarly, we sometimes use hashes as the arguments for methods, in order to better understand what values we are passing in. If we had the ability to change the names of those hashes (particularly when we have attribute writer methods floating around in classes), we could easily get ourselves in a tough spot.


Using symbols as keys makes this process much easier for both programmers and their machines.
