---
title: "Let's build Privatus in public: Day 7"
date: 2024-10-12
description: Building privatus in public. This is day 7 - day 11 report. Implementing the design for the blog view, and profile view in code, along side other functionality.
thumbnail: "./index.png"
---

So we are back!

Firstly here's a little detail about what's going on

I am EzpieCo, and I am trying to create a better social media platform, one without targeted ads, no privacy concerns, one which is open-source, and isn't full of trust issues like every other platform on earth. Thanks a lot, Mark Zuckerberg(and Elon maybe)

Privatus is just a privacy-based open-sourced social media app that I am planning to create, as of now I am not sure if this is worth my time, and because of this I am making this prototype, that's why the codebase is supabase and nextjs, just a simple garbage site that shows you what you can expect from the real product, MVP? Well, you may call it if you want. My mission is to get 5K signups before the end of this month. If I do get it I will go full into it. As of now(11 Oct 24), the prototype has got up to 80 signups, which means I need 4,920 more to get false confidence! So do sign up by clicking this [link](https://lambda-official.vercel.app/signup). So mind the site is poorly made because it's a prototype so the latency is high, like 2 secs at most for 4G.

If you want to show more support please share this with others, the sooner we get to 5K signups the sooner I would make this into an official work.

Now back into our regular show.

As of now this is what we have for the homepage.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dgllio227flnllamvp60.png)

We have a simple sidebar with a following list, and I have 2 test users for testing the feed feature and that list. As you can see it works perfectly.

Now we get into the work done in the blog view

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wc5vl9z7vofbdlt584h7.png)

So I did some changes and here's how it looked.

Now I went on to fix the profile viewer.

The design I went with is simple. The sidebar exist... of course, the user's info is now in the center rather then the side of the page. And the blogs are shown beneath the user's info.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6txz9qovmhizkm2i0e7q.png)

Now let's do a quick side by side comparison:

homepage:

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/58942rjs9at9dzw4t8yy.png)
_nice editing huh?_

blog view:

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7x11j253rueo4xn9w6q4.png)

profile view:

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/joofw4675zox9yvaqnzq.png)

And from this we can conclude that I have done a makeup of the entire site once again! Look it's not easy getting users to signup ok?

Once again please signup for the prototype. [click me](https://lambda-official.vercel.app/signup)
