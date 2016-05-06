# Remember who you're talking to

I have a confession to make, and I'm sure this will come as a surprise to many of you, but ....

I'm in love with Ruby.

Ruby's great. It lets me express my thoughts in a very succinct way.

```ruby
def factorial(n)
  return 1 if n <= 1
  n * factorial(n - 1)
end

factorial(5) #=> 120
```

```ruby
def factorial(n)
  return 1 if n <= 1
  fact = 1
  2.upto(n) do |i|
    fact *= i
  end
  fact
end

factorial(5) #=> 120
```

```ruby
def factorial(n)
  n.downto(1).reduce(1, :*)
end

factorial(5) #=> 120
```

It also lets me do really stupid things...

```ruby
class Fixnum
  def !
    self.downto(1).reduce(1, :*)
  end
end

!5 #=> 120
```

And yes, I know that `!5` is a subfactorial, but, ya know, work with me.

Anyway, the point is, I love being able to do crazy things like this (and often do, as a way to learn and try new things). That said, as we've all heard

(insert picture of spiderman here)

"With great power ..."

All joking aside, being able to write code like this (maybe not the last one) is _crucial_ to our success. Building upon abstractions lets us think at higher levels and create ever newer and more exciting products. I mean, if I had to think about the way bits are sent over the wire to produce a page in a browser every time I wrote a website, I'd **never** get anything done.

Writing Ruby (and other high-level languages) lets you interact with the computer in ever more _human_ terms. The problem with this mindset is that, at the end of the day, **you're talking to a computer**, and computers are infinitely more logical than you'll ever dream of being. They'll do exactly what you tell them to, and Ruby, for all its perks can hide what you're actually telling the computer to do. I want to stress again, this is _usually_ a good thing.

**Let's back all the way up**

I first wanna talk briefly about abstractions. Abstractions are a way for us to think about something metaphorically - or talk about one thing in terms of another. When we talk about a button on a screen, it's not really a button, it's an _abstraction_ of a physical concept that renders a set of pixels on a screen and, when clicked, it (probably) does something - _like a real button_. Abstractions work best when they emulate the real world. When an abstraction breaks down, we often call them "leaky". The rest of this talk is going to quickly move upward through _layers of abstraction_ in the computing world. These layers build upon each other and, eventually, produce working software.

First principles - at it's **core** (there's a joke there), a computer is nothing more than a fancy calculator. When we talk about a computer, we're talking about a piece of machinery that does computations (see, computers). Additionally, computers (at least the ones we normally use) are **logical** machines and think in absolutes - truth and falsehood, on and off, zero ... and one. You can model an amazing amount of data in zeros and ones, and our computers do - from numbers, to words, to pictures, everything that we see on our computers, eventually, is modeled in _bits_: zeros and ones. If you want proof that you can do this, just look at Morse **code**.

Given that many _bits_ together can carry information, we can use these bits to provide instructions to the computer. For example,
we might define a series of bits like this:

```
110011
```

to mean "store this Word document to my hard drive with the name 'super-important.docx'". This is an abstract that we often call a "convention". A "convention" is merely a mutually agreed upon abstraction. Other conventions might be "the number 97 means the lowercase letter 'a'" or "if a file starts with the number 8950, it's a valid PNG". By everyone agreeing upon something like this, we can begin to move up the ladder. A more realistic example of an instruction is something like "store 938 in slot 29 on my hard drive" or "multiply the last two numbers I told you to remember" or "go get the number in slot 29 on my hard drive". Your computer has a rather small set of these instructions that it knows how to do (that "instruction set" is much bigger than it used to be).

**Get instruction set of the original 8pin chip**

The problem with conventions like this is that it's **really hard** for humans to remember. Imagine if you had to give instructions to someone verbally while constantly worrying about the spelling (awful, right?). So we came up with a concept to _abstract away_ the hardness. That concept was _assembly_. Assembly is a very light abstraction on top of the instructions we give the computer.

If we were trying to say, "store the number 3 in slot 99". In bits, we might write:
```
1110111111001000
```

But the abstraction of "assembly" looks like:

```
set 99, 3
```

A program to multiply two numbers in assembly might go something like this:

```
set 98, 3
set 99, 4
mult 98, 99, 100 # multiply slots 98 and 99, and store in 100
```

But we're not all trying to built calculators.

So, to create code that writes text, we might use conventions that turn letters into numbers (and therefore words into sets of numbers) and pictures into numbers and sounds into numbers, and, and, and ...

But managing everything as numbers is taxing on the human brain. I don't know about you, but I can barely remember five phone numbers, much less that in ASCII "eighty-four" is a "capital T". So we came up with another abstraction - a "high-level" programming language - FORTRAN.

... Then Java (talk about JVM and cross compilation) - a harrowing tale of competing conventions.

Finally we come back to Ruby, implemented on a VM ... etc.
