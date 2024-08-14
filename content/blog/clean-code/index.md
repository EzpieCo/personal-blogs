---
title: How To do clean code(real)
date: 2024-04-21
description: Learn to write clean code that isn't only clean in theory but also practically
thumbnail: "./index.png"
---

WARNING: All information in this post is nothing more than opinions, anything that you disagree with can be commented on, but keep in mind, that everything mentioned is just an opinion

You read the title you know what's coming and it's time to get toxic!

## What does Clean Code mean?

OK, first of all, what does it mean? What does Clean code even mean? Is it a practice? Is it a principle? Or is it something created out of thin air as always?

Well, that's debatable. To some, clean code is like their guidebook to coding in a team, while to some it's a way to make their code look more professional.

But the sad reality is, it just doesn't matter!

Many people focus on clean code as a way for them to make their code look more readable, but does readability matter? Who on earth is even going to read your code other than your co-workers who have worked on the codebase alongside you and know what each line of code is about, they know what function `ScreeenResolution()` does as much as you know, they know what you mean by, "Should we change the size to 4 by 3?" So why does it even matter to make your code readable?

It's not about readability it's about familiarity, that's why the new guy's code is always checked before accepting the PR, and the old guy's code is not even seen and accepted, because everyone knows that the old man has been working in the codebase for over 69 years.

But still, what is clean code?

Now I want you to know, that it's not a guidebook, but rather something that a team can understand and follow, it's the companies style guide that matters and not the common ideas that everyone accepts, because again, who is going to read your code other than your co-workers!

## How to really clean code

Now that we are clean with what clean code is, it's time to check out how to do it, because that's the main topic after all.

Now for this purpose I will take a simple example, it's a basic Fibonacci series:

```python
def F(n):
    r = [0, 1]

    while len(r) < n:
        r.append(r[-1] + r[-2])

    print(r[:n])

F(10)

```

Now to many, this makes sense... of course like after reading the code. Now keep in mind clean code is useful and not useful under certain conditions, and wait let me get there.

This code makes sense if you get used to it, that's getting familiar with the codebase, but at the same time, it's so utter garbage that even JavaScript looks better in front of this thing. This is where clean code would make sense, where you need not make your one function uses 10 - 15 helper function, but rather one self-explanatory function that doesn't require much hard work.

Let's try making this self-explanatory and one with 10 helper functions and compare which is better.

First of all, what's the problem here? The problem is those variable naming, all the variables are named using 1 char, and if you have ever written code with variables named using 1 char, you know how soon you will run out of names... 26 chars later.

So let's give it some clear names:

```python
def FibonacciSeriesGenerator(numberOfTerms):
  fibonacciSeries = [0, 1]

  while len(fibonacciSeries) < numberOfTerms:
    fibonacciSeries.append(fibonacciSeries[-1] + fibonacciSeries[-2])
  print(fibonacciSeries[:numberOfTerms])

FibonacciSeriesGenerator(69)
```

Now keep in mind, that I have used naming conventions that I use for [Lambda](https://github.com/ezpie1/lambda-official)... yeah you know I will advertise here, it's my post my well.

OK, just a short ad I promise. 

Are you tired of using Facebook? Or maybe X? Or Instagram? Or just tired of the fact that these companies focus only on the money and invade your privacy for more money? Then you, my petit une, you need to use Lambda! Lambda is an open-source privacy-based social media app that prioritizes your privacy and does not collect any personal data about you, all we take is your email ID, that too just for creating an account, and you are all done, fully private and secure(that's debatable). Also with open-source collaboration, all the features in the app are what you request, so yeah kill me by filling the issue tab with a lot of feature requests, but hey, I didn't create any issue template, so screw you!

OK, so where were we? Yeah, this example uses naming convection that I follow and recommend to be followed in the lambda codebase. So naming convection is pretty much something you and your team need to decide on.

And that's it! That's all clean code is, just use proper naming convection and make your code self-explanatory, that's all for today! Bye!

Yeah, no, no bye for you, there's more to it.

This isn't all in clean code, writing clean code also means a lot more, it can also mean that your code is maintainable, scaleable, and reusable (that's also debatable!)

Say we take that Fibonacci example:

```python
def FibonacciSeriesGenerator(numberOfTerms):
  fibonacciSeries = [0, 1]

  while len(fibonacciSeries) < numberOfTerms:
    fibonacciSeries.append(fibonacciSeries[-1] + fibonacciSeries[-2])
  print(fibonacciSeries[:numberOfTerms])

FibonacciSeriesGenerator(69)
```

If you see it still lacks something, it's not maintainable, you know why we have code testing as a tool? No, it's not for 100% code coverage, it's so that we can accept PRs that we don't want to read but still want to be sure that the code won't fail in production.

Now of course I made that part up, but still, imagine going through 10 files of code, each having 15 changes and you have no idea what you are seeing, how are you going to be sure that this won't cause you to die? You need to test it somehow, of course, you also will need to check and make sure that the test suits are not changed, then that's a real problem.

So how can we make something testable? Well, we can just write some tests and check it out, but that's too dumb to do for this example because everyone knows when you `print` something it doesn't get stored in a variable that you can assert. And yes the print statement is the problem in this part.

```python
def FibonacciSeriesGenerator(numberOfTerms):
  fibonacciSeries = [0, 1]

  while len(fibonacciSeries) < numberOfTerms:
    fibonacciSeries.append(fibonacciSeries[-1] + fibonacciSeries[-2])
  return fibonacciSeries[:numberOfTerms]

FibonacciSeriesGenerator(69)
```

Now that's something we can test. Now anything done to this code will be checked using the test suit, now of course, all one needs to do is not change anything in the file and just add malicious code, and if you get lucky some dumb idiot will accept the PR, and voila! You did it! You destroyed Googal!

Yeah, hopefully, that doesn't happen.

Now let's think about it, let's think about scalability, we have this code quite maintainable, it is self-explanatory, the function name clearly tells what the code is about, the naming conventions helps out a lot, and using return rather than print, we can now skip reading other people's code and keep accepting it if it passes all tests! But what about scalability?

Think about it, how can you make your code scalable? In fact, what makes code scale?

### Thinking of Scaling

What is scaling? Scaling is all about how well can a system handle requests, say you have a homemade server running, and it is capable of handling 10 requests/sec, now imagine you have to handle more than 10 requests/sec, say 11, even with just 1 more request your entire server will take decades to execute "hello world" on the user's screen, and now that's a crucifixion!

How can you make it handle more requests? One way would be to just have more servers and have a load balancer handle sending all requests to a server with less load and control the flow of it. But say you want to go cheap, you can, by using these tactics:

**Efficient Algorithm:** It matters, it matters quite a lot, having an algorithm that runs in under 10ms vs another algorithm executing in 20ms, is quite a big difference. It doesn't look much, but it is quite a difference. O(n) is better than O(n^2). What's O(n)? Well I got that covered [here](https://ezpieco.vercel.app/big-o-for-dummies/)

**Parallel code:** Imagine if you had to handle 10 people's orders at one time, how hard can it be right? It's better to spend some time on getting more waiters than just 1, the same can be said for code if you can make your code execute in parallel, that is if you can split your code and make it run in smaller chunks at the same time. It's sort of like concurrency.

Now there are a lot of other things you can do, but hey, it's tactics, not a strategy OK?

### Back to the show

OK now that we know what scalability is, what can we do to make the Fibonacci scalable? Well, nothing much can be done it took me a whole day figuring it out, we can use an efficient algo... data structure! You guessed it right! It's not the algorithm that's the problem it's the data structure, and yes data structures also matter ok? Take a hashmap for instance, it's fast, it's gold, it's blazing fast, it's gold and did I mention it's gold?

Wait hashmap for a Fibonacci series? How?

Well if that's your question, don't worry it was my question too, before I tried it, and guess what, it got faster, why? Well because you see, every time we generate a Fibonacci series we are following a certain rule, and no matter what number of terms you ask for the previous ones would be the same at all costs, it will always start from 0, 1, 1, 2... and so on, it can't change right? So why not just do some lookup at a hashmap and get all the numbers till the target term, if the target term is not reached, then do the maths and add those new Fibonacci numbers into the hashmap too! Simple isn't it? Just that it wasn't obvious, so yeah just test it out sometimes and here you have it, a Fibonacci series generator that uses hashmap.

```python
def FibonacciSeriesMapper(indexOfTerm, memo={0: 0, 1: 1}):
    if indexOfTerm not in memo:
        memo[indexOfTerm] = FibonacciSeriesMapper(indexOfTerm - 1, memo) + FibonacciSeriesMapper(indexOfTerm - 2, memo)
    return memo[indexOfTerm]

def FibonacciSeriesGenerator(numberOfTerms):
    return [FibonacciSeriesMapper(i) for i in range(numberOfTerms)]

print(generateFibonacciSeries(69))
```

Now here I am using 2 different functions that make sense to me, because it's easier to get hold of what's going on, plus I wasn't able to get it into 1 function, we have a mapper function that maps all the terms into a hashmap, yes a hashmap is a dictionary in python and all other lamguages call it what so ever, and we have the make generator function that generates the series. We have the hashmap named memo, of course, we could have named it `fibonacciSeriesMemorise` or `fibonacciSeries`, yes we could have also named `indexOfTerm` better, such as `fibonacciNumber` which would have made more sense to everyone, but this is more about familiarity, I am more familiar with those string then with those you all maybe with, but at the end, it matters on who will be working on the codebase, if it's an open-source project, just like [lambda](https://github.com/ezpie1/lambda-official), then it needs to have naming that everyone can understand rather then just a specific group of people, the developers.

So at the end we can have this fibonacci thing like so:

```python
def FibonacciSeriesMapper(fibonacciNumber, fibonacciSeries={0: 0, 1: 1}):
    if fibonacciNumber not in fibonacciSeries:
        fibonacciSeries[fibonacciNumber] = FibonacciSeriesMapper(indexOfTerm - 1, fibonacciSeries) + FibonacciSeriesMapper(fibonacciNumber - 2, fibonacciSeries)
    return fibonacciSeries[fibonacciNumber]

def FibonacciSeriesGenerator(numberOfTerms):
    return [FibonacciSeriesMapper(i) for i in range(numberOfTerms)]

print(generateFibonacciSeries(69))
```

And there you have it, a self-explanatory code that is scalable, maintainable, and testable.

Now keep in mind I didn't go with the limit per line rule, the 80 chars per line rule, so yeah it kind of exceeds that... yeah... that's also a problem.

Of course, this thing can be improved further... ah, who am I kidding, no it can't be OK. It's in it's best form. The best of the best form. And all this took me a whole week for some reason.

## The stupid clean code

Now let's take a look into the dumb stupid version of clean code, the version that tends to use 100s of functions just for print Hello World.

Let's take that fibonacci and make it an Apache hell.

I am not really that good at writing clean code, so I had to ask GPT to make some hectic version of the Fibonacci series in python and here it is, just a disclaimer, it's hectic indeed;

```python

def initialize_fib_series():
  return [0, 1]

def reached_desired_length(fib_series, numberOfTerms):
  return len(fib_series) >= numberOfTerms

def calculate_next_fib(fib_series):
  return fib_series[-1] + fib_series[-2]

def append_to_series(fib_series, next_fib):
  fib_series.append(next_fib)

def get_number_of_terms():
  return 69  # Adjust this to change the number of terms


def generate_fibonacci_series(numberOfTerms):
  fib_series = initialize_fib_series()
  
  while not reached_desired_length(fib_series, numberOfTerms):
    next_fib = calculate_next_fib(fib_series)
    append_to_series(fib_series, next_fib)
  
  return fib_series

def print_fib_series(fib_series):
  print(fib_series)

def main():
  number_of_terms = get_number_of_terms()
  fib_series = generate_fibonacci_series(number_of_terms)
  print_fib_series(fib_series)

main()
```

Of course, this makes sense, why won't it? Just that it's so much code and refactor, that it just looks unnecessary. And yes no one writes code like this, but it's only for demonstration purposes, don't try this at home, it's just too dangerous to do. Now keep in mind this is a possible edge case that can happen this is the kind of code that Uncle Bob, creator of clean code, says he wants code to look kind of like this, where each function is limited to 5 - 7 lines of code, can you imagine? Your entire function refactored into 100s of functions just for having each function with 6 lines of code?


Anyway that's all about clean code, of course, I haven't covered some other topics about clean code, stuff like dependency, singleton and other stuff, but hey, that's the SOLID principle that I still don't get it.

In case I haven't covered stuff that you wanted to be here, or maybe you want to get some more info, just comment below and I will explain that thing you asked and only that thing nothing more.