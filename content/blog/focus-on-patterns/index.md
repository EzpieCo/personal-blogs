---
title: Why Focus on learning patterns
date: 2024-08-27
description: Trying to learn a new programming language is hard, but if you just learn patterns rather then the technology itself, it becomes more easier because everything just boils down to those patterns.
thumbnail: "./index.png"
---

When you start programming, there are many things you need to know, which is why programming is like being a doctor. No matter how many degrees you have, we all have non that's for sure, at the end, you still have to learn something or the other, because tech can't stop evolving, what is this a simulation about evolution?

But to keep things in place and not get overwhelmed, there's a solution.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/niyfm7z3qldw2n4918dy.png)

Just like my little buddy here said, focus on patterns, but why?

You might be thinking, "Hey that guy from ezpie! I know react, why can't I just live with that?"

Well you are an id...e

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/gu0qju2ebd1qeb62yo0g.png)

Well let me give you some good reasons.

Here are 4 terms:

- Dynamic type
- Static type
- Weakly type
- Strongly type

Can you tell what are these 4 weird things?

Well in case you didn't knew what they meant, let me explain.

Ever heard of JavaScript?

That programming language that brings happiness... to the devil of programming? Yeah that one for whom `"this str" + 69` is legit code and output should be `this str69`.

Now, here's the question:

_Is JavaScript a strongly typed or weakly typed language?_

And the answer is weakly typed. Of course, because firstly it should be impossible to concatenate a string and an int. Even if it can be you should do it explicitly rather than the interpreter doing it by itself.

This makes JavaScript a very... Unsafe language, this means that you can just do whatever you want, it won't give a runtime error so this means the code works no matter what. And this is why someone like me, would recommend using TypeScript even though I criticize it because it's a VSCode extension.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sbbcjv1xz3v36n9qwny3.png)

To be exact, try to not think of JS as a language, but rather as dynamically typed and weakly typed, why? This will help you understand that when you write code, your co-worker can change the value of `PI` to string literal and JS will execute it even if it's not supposed to, and now you will be blamed and will need to debug the entire codebase because it's all your fault.

So what am I saying?

I'm saying that don't learn something in tech by learning something specific, rather learn the patterns and you will be able to see a more high level view of the technology itself and once you get hold of the high level stuff you can move to learning more specific stuff.

Let's take another example, let's take web for instance, of course I am a web dev.

Take it like this, web development is all about 2 things, storing data, and displaying data... well that's the whole focus of software engineering but let's not talk about that.

You have to do 2 things, store data, display data, how are you going to do that? You will need a way to communicate between your display and the place where the data is stored right? This is exactly what I am trying to say. Don't learn react just because it's everywhere, learn the high level overview so that you can understand the underline technology better.

Yeah, but how do you make one display communicate with the database? Well you use an API right? So can you draw a layout of this communication?

It would be like this:

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6mrsgxp6grf8jwtrcryh.png)

As a cherry on top, I overly complicated the entire thing, but on a high level, it's just a frontend device communicating to a server/service on any corner of the world.

So if you think about it, it all just boils down to patterns, all you have to do is, learn the patterns.

Take design patterns for instance, why do you think they work? Well when I mean work I mean work for C++, that's because these design patterns help in breaking down stuff into simple and easy to implement code. The idea of breaking down large problems isn't new, everything follows a certain pattern, take the notification thing you always get everytime their's something funny going on in social media, you always get a notification in your phone saying what happened.

How do you think this works? Well it's just the pub/sub pattern, basically what this is, it's a way to say, you subscribed to "this", and every time "this" makes a public change, you will receive notifications about it, or in simple words, every time "this" hits a publish, "this" also hits a function that sends a notification to all those who subscribed to "this".

And now you know what pub/sub is, you can even implement it in any language you want!

Try to do this using Python for instance.

Here's how it looks:

```python
class Publisher:
  def __init__(self):
    self.members = [] // add a method for this named sub()

  def notify(self):
    for member in self.members:
      // notify members
```

This is kind of a really simple example, but you get the overview, you just need to know the pattern, and that's why focusing on patterns is more important then focusing on the technology.

Once you get the pattern, learning a new language becomes more easy, I have an article on... well [2 articles](https://ezpieco.vercel.app/how-to-learn-programming/) to be exact, on this topic, but I believe this one has to be the best on of the 3.

Take this for instance, you want to learn JavaScript

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1m4bmh2ezu449trdavkg.png)

You shouldn't try to learn how react or angular or even JQuery, start simple start easy, and learn to implement some patterns that you learned, such as pub/sub or even the builder pattern, these will help you in understand how dumb your life choices are... well how the language functions rather than learning the syntax, this helps in a lot of ways, you are basically improving your DSA skills with this, yes there's almost no data being stored in most cases but hey, you can always store data when you're a programmer... pub/sub in case you forgot.


Now I can go on and on about why learn patterns and not the language specific stuff, but that would make this too long of a post, so in case you want more, here are some good resources:

- Refactoring Guru: https://refactoring.guru/design-patterns
- Neetcode's design pattern video: https://www.youtube.com/watch?v=dQw4w9WgXcQ
- Another neetcode: https://www.youtube.com/watch?v=tAuRQs_d9F8
- Everyone's favorite fireship: https://www.youtube.com/watch?v=tv-_1er1mWI

## This post is brought to you by

Hi everyone, as you may know, I am the sole creator of lambda, it's a social media app that is privacy centric, open-source and non-targeted advertisement based. Currently, lambda is a prototype, it's an idea of how we can make social media a profitable market, but also remove the insane privacy concerns most traditional platforms have, privatus, the production version, will be made to focus on these such concerns, it would be privacy centric, human moderation to prevent censorship, and non-targeted advertisements to further reduce privacy concerns. Privatus can be launched only if the prototype gets >5K signups, this means that it's really important for me to let you click this [link](https://lambda-official.vercel.app/signup). If you like you may give the prototype's GitHub repo a star right over [here](https://github.com/ezpie1/lambda-official)