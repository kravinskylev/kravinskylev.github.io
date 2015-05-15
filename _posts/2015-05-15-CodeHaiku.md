---
layout: post
title: CodeHaiku
published: true
---

<h2>announcing a new project: CodeHaiku</h2>
Two of my favorite things in this world are coding and poetry. And what better way to combine them in my favorite language (Ruby) than by paying homage to Japan, the country ruby was created in! With that in mind, I'm excited to introduce CodeHaiku.

<h2>what is CodeHaiku?</h2>
CodeHaiku is an ongoing project where I will post elegant coding solutions in the format of a haiku. Combining <a href="http://en.wikipedia.org/wiki/Code_golf">code golf</a>, <a href="http://en.wikipedia.org/wiki/Haiku">Japanese Haiku</a>, and just a little bit of humor, CodeHaiku aims to be a pleasant pick me up. This is a way for me to sharpen my skills on traditional technical interview problems while having fun, exploring new mediums, and hopefully, bringing a smile to some of your faces.

<h2>madam, I'm adam</h2>
I'm starting off this project with a fairly easy problem. The idea is to take in a string and check to see if the string is a <a href="http://en.wikipedia.org/wiki/Palindrome">palindrome</a> - if it is the same backwards and forwards. This is not a particularly difficult problem, but the length of the solution (and the fact that it involves more word-play) makes it perfect for CodeHaiku. Here's the ruby code:

``` ruby
string.reverse == string ?
print "palindrome" :
print "not palindrome"
```

And here's the Haiku:

<div class="message">
<div class="haiku">
<span class=haiku-header>String</span><br>
If reversed equals <br>
string, then print palindrome, else <br>
print not palindrome. <br>
</div>
</div>

<h2> cool! now what?</h2>
I'd like to add a new CodeHaiku on a semi-regular basis. Next week I will try to write <a href="http://rosettacode.org/wiki/FizzBuzz">FizzBuzz</a> as a CodeHaiku. If you enjoyed this, <a href="/contact">drop me a line</a>. And if you'd like to submit a CodeHaiku, please let me know! I'd love to have other people contribute to this fun little project.
