---
title: "Let's build Privatus in public: Day 2"
date: 2024-09-30
description: Building privatus in public. This is day 2 - day 6 report. Implementing the design for the homepage in code, along side other functionality.
thumbnail: "./index.png"
---

And we are back! Day 2!

Welcome back everyone to day 2. Today we have very little to do.

To put it into perspective here's what I have in plan:

- update design

that's it, update the design, I will not add the media sharing feature because that means S3 bucket and that's a lot of data to store which I think supabase can't handle.

So let's get into it!

## Quick back note
For those who don't know what's going on here, hey I am EzpieCo and I am on a mission to create the perfect social media platform you want, something that is open-sourced, privacy based, well-being focused, and really for the users by the users.

In simple terms privatus is the open-source privacy based social media platform that will be open for user opinions. I know it sounds crazy but hey, what's the worst that can happen?

As for features the actual platform will have:

- media sharing
- blogging
- microblogging
- human mods
- premium feature

and a lot more, because it will be the all in one platform, why have 4 when you can have 1 for everything? The swiss army knife for the average social media user.

If you want more details check the [github readme](https://github.com/ezpie1/lambda-official)


## Back to the story

So to begin I decided with a simple layout like this

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/uusmn2jvdxebesf87wka.png)
_Rookie style_

it's basic, but a good start in my opinion, start with a mess and clean as you go, just what works fine for me.

Firstly I will fix the sidebar because that's what I want to fix as of now.

As you can see in this figma image we have to... Do a lot

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/go2nf0mg6wkj0uuywstf.png)

Now I will be honest I got a bit of track... that's the reason why this is posted on day 4 and not day 6! Well technically I also did other stuff but wait.

So here's a simple problem I had, what about the state? The options, feed and popular, are in the sidebar and not in the same component as the post displaying component, so how would I share the state? Well for this I came up with this stupid contraption, I created a different component that will be the parent of the 2 components, this component can be called `HomePageRenderer` of course no rendering just state sharing, the child component - the sidebar, shares the state of the 2 options with the parent - the homePage, the parent component then passes that info down the other child - PostDisplay, then the display component uses that info to display the posts.

Here's some artwork to explain

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bzjf7j9mkvd1vdus56ki.png)
_WOW!_

I know I should have just used the main component but you can't have states in a server component... makes total sense of course, its scaleable!

So here's the output of wasting a whole day

https://github.com/user-attachments/assets/c9201823-867b-42b9-87c1-2d8a902eb23b
_Don't worry it's just a github link_

And yeah! It works!

Time to fix the design again...

And here's the final product

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/922bkwxnsvxzg9b4uwa6.png)
_No political statement, I don't support party in Your nation_

As you can see I have added the feed and the nice little following section too. Now here's something really annoying I did which caused this day 2 post get converted into a day 6 post... I got stuck at the following section. I wasn't able to loop through the following array because it was an async function that was returning a promise and stuff stuff you know what I am talking about?

And finally this brought me to an end to this part of privatus, that being said hopefully I won't take days fixing the next task.

day 7 - Update to blog view.
