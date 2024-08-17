---
title: Top 3 Projects To Build To Learn a programming language
date: 2024-08-17
description: Learning a new programming language isn't easy, but with these 3 project ideas you can learn any programming language with ease.
thumbnail: "./index.png"
---

It's no joke, learning a new language can be a bit difficult... no not the human languages I meant the programming languages.

And to overcome this problem, I got the just perfect solution. That is learn by building something, and it works for everything! Rather it be frontend or backend, just build a simple project using the language and voila! You have it, you mastered the basics!

So here are some project ideas that helped me learn a new language with ease.

## Command line tool

Start it simple, start straight from the command line, or CLI for short.

Now I know just creating a simple calculator on the CLI can be boring, and believe it or not, I tried it and I couldn't learn a single thing.

But luckily, there's something better you can do, rather then creating a calculator, try creating a todo list instead!

It's no joke you will learn a lot from this. Such as:

- How to read and write to DB/CSV using the language
- How to print statements on the CLI in tabular form
- Best practices for safety

Yeah that might not be much, but the first and third are just S-tier stuff to learn, I mean, why won't anyone want to know best practices? And that too for safety! Also learning to read and write to file system is something you should know just for fun... well there are reasons better then this, such as, logs and audits, npm for instance to be exact.

Say you want to learn go, like I am currently(lambda's production version's backend will be written in it), try to create a simple CLI todo list, it should allow you to add, list all, delete and complete a todo.

To following commands should be there:

- `./task add "The Todo"`
- `./task list`
- `./task delete ID`
- `./task complete ID`

Here are some safety checks you should do:

- Check if arguments are passed for add, delete and complete.
- Check if DB exists, use CSV for the first time. In case it doesn't then create DB.csv and add the header data - `["ID", "Todo", "created", "completed"]`

These are just 2 checks you must do, but I recommend brainstorm some more checks for good sack.

## Rest API

OK, you leveled up big time now, now you want to be more job specific, let's say you want web dev are your core skill. Try to create restful APIs.

Now I won't go in depth about what restful means, but it just means that the server doesn't store any data about the user, and something like horizontal scaling, it helps build fast and reliable backends, in case one server crashes, there still are a dozen more to crash.

So all you have to do is create a simple calculator API.

Boring!

Yeah, wait for the painful part.

The real pain is, once again, safety. 

**NEVER TRUST YOUR USERS!**

Don't ask why, but your users just love crashing you services and products, they will do anything to find excuses to blame on you, so do your best to keep the service safe, and when I mean safe it means doing checks on what the user requests, and what the server response.

Get the joke? Request and response, it sure is webish...

So what is the thing? The thing is, you will need to check what data type the user gives you, what happens when it's a wrong data type, or what happens in case of a overly complicated 404 error?

From this you will learn the pain of web development:

- Best practices for **SAFETY**
- How to parse JSON data, work with JSON for simplicity and ease.
- How to handle errors

Here is the API design you should go for:

- POST add/ {a: int, b: int}
- POST subtract/ {a: int, b: int}
- POST divide/ {a: int, b: int}
- POST multiple/ {a: int, b: int}

Now I won't go much on details because that's something for you to figure out.

## HTTP request maker

Yeah, just more web dev huh? Well of course I am a web developer after all.

This is kind of simple if you use some package from the language package manager, but not for C... does C even have a package manager?

This is kind of like curl or wget, all you have to do is create a simple CLI tool that helps you send request to a provided URL, and display the response on the screen.

Here's what you need in this all:

```
$ butcherCleaver localhost:6969/add -d {a: 69, b: 69}
69 + 69 = 138
```

and for stuff like HTML content

```
$ butcherCleaver https://google.com
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>
```
_WOW_


Of course, you can go super san mode with this, do whatever you want, and display a warning if the site does not have https? Go for it.

And there you have it!

These are the Top 3 projects I create every time I want to learn a new language. Currently, I am learning go, why you ask? That's because once [lambda](https://github.com/ezpie1/lambda-official) hits 5K users, we are going official, straight into business, this means we would be using full AWS service, and since go is for speed and safety(debatable due to rust), it sounds like a great choice for a microservices architectures backend, so yeah these are the 3 projects I am creating and would like if you all give them a try too.