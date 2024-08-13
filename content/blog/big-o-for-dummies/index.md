---
title: Big O notation For dummies
date: 2024-06-29
description: Big O notation made easy for dummies with gifs
thumbnail: "./index.png"
---

When it comes to programming there is one thing we all dev suck at... well mostly the new devs. And that's big O notation. So here's what Big O is and why it matters.

## ❓What is Big O notation❓
Imagine this(and imagine only), you are at a buffet where you can eat all you want without any payment(see why you only have to imagine it?) eyeing those sweet sugary diabetes-giving chocolate stuff. Now say you want to know how quickly can you scoop up all that diabetes on your plate without taking much time. That's what Big O notation is all about! No not chocolate, how quickly can you do one thing?

Of course, this was just an imagination

![really](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/te2uj84p2oi4os44w8g1.gif)

and in programming, it's not us doing the thing, it's the computers that do our dirty work! So Big O notations tell us how fast an algorithm works.

## 📊 Types of Big O notation 📊

There are different types of Big O notation, but I won't call them types more like stages.

### O(1) - The myth: Constant Time ⏱️

Now say you have to pick something up from a toolbox and you have 2 tools(not a handyman are?) you wouldn't take much time, say you have 15 tools in the toolbox, but still no time taken. You take the same amount of time in both cases because all you have to do is pick it up! 

AND IF YOU CAN'T EVEN DO THAT WELL THAT'S A SKILL ISSUE!

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sur34hk4dmgs133lri5x.png)

This is called constant Time of O(1), how do you say it? That's another skill issue.

There are different ways of saying, Big O of 1, O of 1, order of 1, and bluh bluh bluh bluh and I hate all that, so I call it... constant time... yeah don't even ask.

In code, it would look kind of like this:
```js
const firstElement = randomStupidArray[0];
```

Exactly like picking a hammer from a toolbox, this code also is trying to look for a hammer(element) in a toolbox(array).

And that's just how simple O(1) run time complexity is. Simply, it's fast and it's just another myth that we believe because we all write code in O(n) run time complexity.

### O(n) - The one we all do: Linear time 📈

Now O(1) sounds really nice, it's the dream you have for your code, but sadly we devs are just too optimistic and write code only in our dreams in O(1), meanwhile, our real codebase looks like it takes more time than a tortoise.

That's O(n), it's that useless yet seen everywhere organism that just doesn't make sense, like those humans outside your house(but, really do you think you are a robot?).

Imagine, and again just imagine, that you have to cut 10 ropes, each one by one, that takes you say 1s each, that would be 10s in total. Now say you have to cut 100 ropes, taking the same 1s each how much time will you take now? No! You are wrong! Unless you are right. It would take 100s in total.

And there you have it that's O(n) rum time complexity!

Of course, we also need the code example for the wewbies!
```js
// real life code
if (let i = 0; i < arr.length; i++) {
  console.log(i);
}
```

And this will take exactly... O(n) time! Why? Because it takes a certain time to console log `i`, and now it has to console `i` `n` number of times. Thus it takes O(N) to execute.

### O(n^2) - The killer: Quadratic Time 🔳

Once again let's imagine and only imagine!

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3odrzy08kgxll01782fr.png)

Imagine you have to make pairs of socks, and there are exactly 10 pairs in a jumbled-up pile of socks. For each sock, you will need to search through the pile, and for each pair, you will need to do this 2 times. So, now say you take 1s to find 1 sock(fast for a robot), that means to find 1 pair you will take 2s, which gives us a total time of 20s to sort out all the pairs. And it grows exponentially.

Mathematically (Prepare to die) it means that we are doing `n X n`, or more simply we are just doing the same operation 2 times and over `n` number of times again for the other elements as well... yeah you know I am talking about nested list.

```js
for (let i = 0; i < arr.length; i++) {
  for (let j = 0; j < arr.length; i++) {
    console.log(i * j)
  }
}
```

Yeah I have no idea why but this code makes sense. We have a for loop that has another for loop, and both are doing the same thing, thus it's twice the thing and has exponential growth in run time. Professional isn't it?

## O(log(n)) - The Hero: Logarithmic Time 📉

Let's take a book... never heard of it? Are you even real?

Say I want to open page 69... cause why not.

One way is to go over each page one by one and see if it's page 69. but sadly this method takes a bunch of time... or run time if you may.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nvdkr9txqyk17ha5ve80.png)

And yes it's slow even for some god sack reason 10ms is also slow!

And in case you tried to get what run time complexity it is... well comment below that your homework!

Now to make this fast there is one way we can do this.

Now think about it, it's really simple. All the pages are in sorted order right? They all are sorted, page 4 comes after page 3 and page 69 comes after page 68. So that means if we pick a page randomly and check if it's greater then or lesser then the target page, we can ignore all other pages before or after that page and repeat the process till we reach page 69!

In fact it has it's own name, it's called the binary search algorithm. All it does is it takes the middle item of the array, checks if it is greater or smaller then the target, if it is greater then it ignores all the other items in the array after that item, it again picks the middle item of this new array and repeats the process of dividing and checking if the middle item is the target or not. And there you have it! You can find page 69 faster in O(log(n)) run time complexity!

Yeah in code it's like this:

```js
function binarySearch(arr, x) {    
  let low = 0;
  let high = arr.length - 1;
  let mid;

  while (high >= low) {
    mid = low + Math.floor((high - low) / 2);
 
    if (arr[mid] == x)
      return mid;
 
    if (arr[mid] > x)
      high = mid - 1;
            
    else 
      low = mid + 1;
  }
  // in case the item does not exist... edge case!
  return -1;
}
```

And there you have it! This code runs in O(log(n)), so it is fast but keep in mind, it only works if the array is sorted, if not... well then sort it first, and don't you use the default sorting method!

And there you have it! That's all about Big O!

Now keep in mind there is more to Big O than just this. Creating an efficient algorithm takes a lot of thinking, which I guess `nil` of you do, well even I don't! But it is quite a fun thing if you ask me. Big O is useful as it can help you reduce your AWS bill from $1.000000001B to $1B, now of course that's not how it works but you git it right?

For a proper example, say your company has an AWS EC2 server running 24 hours a day, and the only piece of code you wrote is a sorting algorithm that takes 69ms to sort an array of 10 items, now that's a skill issue if I have seen any, not only will the latency go up, your AWS bill will go O(n^2)! and now that's a crucifixion!

To fix this issue you can just make your algorithm a bit more faster, and voila! Your algorithm now runs 10x faster and your bill is now more payable! Finally, now you can pay your AWS bills without robbing your neighbors!

If you think you have what it takes to solve a problem, try solving this one in O(n)!

_Given an array of `n` numbers that contains between 1 and n+1, find duplicates in that array in O(n) run time complexity. Assume that there is only 1 duplicate number but it can repeat multiple times, find that number_

And of course the array: `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 1, 12, 13, 14, 15]`

And if you did solved it... good. You did a good job, because I sure love making other people do my work!


