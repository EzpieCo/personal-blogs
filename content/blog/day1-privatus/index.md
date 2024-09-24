---
title: "Let's build Privatus in public: Day 1"
date: 2024-09-24
description: Building privatus in public. This is day 1 report. Completed the redesign in figma and now implementing it in code, along side other functionality.
thumbnail: "./index.png"
---

Hey It's me! EzpieCo.

I got back into work with Lambda and have decided to do build in public to show you all what I am doing currently with Lambda. But firstly some quick info about lambda.

## What is Lambda?
Lambda is an open-source privacy based social media alternative. It's like decentralized platforms except it provides you an alternative to Instagram and facebook, not twitter or X or call it what ever you want. Lambda is currently a prototype version for gaining traction, if this prototype get's 5K signups before October end I will take it as an accomplishment and go full time into lambda, basically making it an official startup(sweet). The actual version of lambda will have the following features:

- Media sharing. This is your images and videos
- Human moderators
- Premium features

For more information please checkout the [github repo of the prototype](https://github.com/ezpie1/lambda-official). Please be noted this is a prototype and doesn't have all the features you want.

To show support just signup for the prototype, help me reach 5K signups for lambda and how knows maybe we could do something big.

**NOTE:** Quick note, from now on lambda will be named privatus as lambda is already used in many places.

## Back to the story

Now that you know what this is all about let me show you what I have lined up.

Now I already had redesigned the prototype and here's how it looks in figma


![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/b3fyeg5k04ajuo7edxid.png)

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x422mh5pg70hjfove0d6.png)

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6771a5z8mqnk10gz9alm.png)

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/goi4pmx7sfxcdrinvd6b.png)

Is this an absolute ripoff of Instagram? 

Well so is Snapchat.

Now, I did a little fixing on the figma design and came up with this.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/m9x8wnwmdm6wgnlapknp.png)

As you can see it looks good enough.

Now the my next target is to get some validation, because people trying to signup do one thing, they add white spaces to their username, use already taken username... basically now I have to add validation in the signup form.

For this I did one simple thing, I created a function that would take the 
provided username and check for white space, if username is already taken or even worst, if username is even provided, yes some people tried that also.

And here's what I have:

```typescript
"use client";

import { createClientComponentClient } from "@supabase/auth-helpers-nextjs";

const supabase = createClientComponentClient<Database>();

export async function ValidateUsername(username: string) {

  if (/\s/.test(username)) {
    alert("Invalid username. Try again")
    return false;
  }

  if (username == "") {
    alert("Please give provide")
    return false;
  }
  
  const { data } = await supabase
  .from("profiles")
  .select("username")
  .eq("username", username)
  .single();

  if (data?.username == username) {
    alert("Username taken")
    return false;
  }

  return true;
}

export async function ValidateEmail(email: string) {
  const { data } = await supabase
  .from("profiles")
  .select("email")
  .eq("email", email)
  .single();

  if (data?.email == email) {
    alert("Email already taken")
    return false;
  }
}
```

Now I know this looks ugly, but yeah, no buddy cares, it's just a prototype and I am the only one working on it, I like it the way it is. Also I have bad habits OK? Skill issues and bad habits don't go hand in hand.

Now as I tested this contraption of mine, it seems to work. Now if you were an average software engineer like the most of you all, you would write a test suit for this right? Right? NO! But I wouldn't! And you can't make me! Seriously I don't want to write any test suit in jest it's a real pain to run an entire backend in your laptop, it's slow and painful, and now I don't want to put GBs of space just for running a jest test suit that checks if my validator that I manually tested works or not, plus no one else is working on it, so why should I care?

And with this the authentication process is finally done and this brings us to the end of the day.

For tomorrow the homepage will be redesigned.

Till then Happy hacking!

Once again if you like the idea of having a privacy centric open-source social media app that is also democratic in ways that it literally has a voting system in which user's can give opinions on what all the platform should have, go ahead and signup for the [prototype](https://lambda-official.vercel.app) and help it reach 5K signups before the end of October, we are only 4,929 signups away!(yeah we have 71 signups in 3 months)