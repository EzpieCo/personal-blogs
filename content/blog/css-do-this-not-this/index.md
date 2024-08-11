---
title: CSS Do this Not This
date: 2024-04-20
description: useful CSS tricks to make you hate CSS even more
thumbnail: "./css_do_this_not_this.png"
---

CSS or Cascading Style Sheets introduced back in 1996 marked a turning point for making a website, look more like a website.

Now a days we have weird, cool, fun, classic and a lot of different styles of websites all thanks to CSS.

But the more you thank CSS the more you regret.

As a front-end developer I can assure you that if you hate react you probably hate CSS more because of it's no programming approach.

And to help you control your nerves before they pop out here are 6 CSS tricks that you would like and are my personal favourate.

## 1. Flexbox your problems

Here's an interview question I created.

> _"How does one center the div both vertically and horizontally?"_

Now before your panic alarm hits off here's the solution.

Ever head of `display: flex`? No? Well may god be with you on this one.

```css
.flexbox {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

All this does is it gives the element with the class flexbox, a **x** and **y** axis and then you can just with the help of `justify-centent: center` and `align-items: center` center the element both vertically and horizontally.

Congratulations you are now employable!

## 2. Grid columns and rows

Ever read a magazine? Or at least a newspaper?

If you did you might have **Not** wondered how on earth could you make that newspaper layout on a webpage.

Well, you're on a lucky day!

To make your webpage a newspaper page, you must understand how to use grids.

They are simple and easy once you understand how they work, they are just like Flexbox except they are nothing like Flexbox!

Here's some code and try not to panic on laying eyes on it.

```css
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 1rem;
}
```

and the html junk:

```html
<div class="grid">
  <p>CSS Is good</p>
  <p>CSS Is good</p>
  <p>CSS Is good</p>
  <p>CSS Is good</p>
  <p>CSS Is good</p>
  <p>CSS Is good</p>
  <p>CSS Is good</p>
  <p>CSS Is good</p>
  <p>CSS Is good</p>
</div>
```

And here's the result:


![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4zimkq0hxl4tvrc1fwj0.png)

And of course I'm just flexing on you with some unnecessary crap of CSS styling and acting as if I have a PhD on CSS.

## 3. Responsive aspect ratio

Now we it comes to responsive design there is no big pain then those UI designers who don't know how to code and make the entire design overly simple yet difficult to implement in CSS. And for the solution we devs tend to use the `@media` thing that I don't even know why we use?

But if you ask me I prefer to define an aspect ratio for my images and it always works!

```css
.aspect {
  aspect-ratio: 1/1;
}
```

and there you have it you mastered Responsive design in under 10 seconds!

## 4. Responsive design(actual)

OK yes that previous one only works well with images and videos many, but here's a better replacement for the `@media` thing.

there's this CSS feature called `clamp` which some how takes `@media` under it's control.

Take a div like this:

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wvcxetjcr76tkp4qzie6.png)

_Yes I'm flexing with my linguist skills_

But say you want to make sure that this div doesn't get smaller then 100px and doesn't get bigger then 500px. Well then clamp can be use full.

```css
.clamp-me {
  width: clamp(100px, 100%, 500px);
}
```

Here I have taken the middle value to be 100%, that means the width of the div will be same as the width of the parent element, that is 100% of it. Now if you resize the screen you will see the clamp property try's to fit the div to the parent element's width within 100px - 500px. Go head and change the value from 100% to anything and observe.

## 5. CSS... a programming language?

CSS is not a programming language because we cannot apply logic into our css code... or can we?

Ah no, but we have a little bit of programming stuff in css too. That is luckly variables!

Imagine having a primary color scheme as `#E8F6FF` can you imagine having to copy paste this all over your css code base? And imagine if that UI team decided to change it to something else!!!!

Here's where we get variables in to play... finally something useful!

```css
:root {
  --color-blue: #E8F6FF;
}

.blue-text {
  color: var(--color-blue);
}

.blue-background {
  background-color: var(--color-blue);
}
```

And a job well done, changes on there way and you don't have to copy paste your values 2 types but only once!

## 6. Typography trick 101

Ever wondered why reading text in a webpage sometime look's better, feel's better and imbarassing to you? Well here's the answer.

As per typography it's said that anything between 45 to 75 chars is good. And since we can do this with the help of our clamp trick too.

Take a div and put some text in it.


![Image](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pa248a5ssdfmcd8ytawi.png)

And yes reading this thing will be boring because it's over 75 chars per line. So let's add that little clamp with the ch unit rather then px

```css
.typo {
  width: clamp(45ch, 50%, 75ch);
}
```

And here's your homework, figure out why I set the middle value to 50% and why not 100%?

Hope you all found this post useful and now that you know 6 really cool CSS things which you propably didn't even knew exist, go ahead and create something and share it below in the comments.

In case I missed any CSS trick that you would like me to cover mention them right below this post... just below where there's a comment button, just right there... WHAT ARE YOU WAITING FOR!