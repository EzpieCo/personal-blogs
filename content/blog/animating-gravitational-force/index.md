---
title: Animating Gravitational Force
date: 2025-02-18
description: Using motion canvas to animate how a simple 2 body system works
thumbnail: "./index.png"
---

So here's the plan, I want to animate a simple 2 body system in which one body will pull the other using newton's gravitational law.

What's that? Well I guess you never paid attention to physics class. But hey! Who said I can't teach a little physics?

The gravitational law is... yeah no physics class it will take forever. But basically it's just one simple statement -

> Everything in the universe attracts each other... but not programmers they only attract bugs

Now I made the last part up but you get the point? Everything, you, me, Sun, Earth, Moon, Your Boss(mostly repel but you know?) attracts everything around it using this formula -

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/23snoqhlyj7ute3lace2.png)

Where _F_ is the force between the 2 object, _r_ is the distance between them and m<sub>1</sub> and m<sub>2</sub> are the masses of the 2 object.

Now to keep things simple I'm not going to add too much complexity to this because this is already very complex to think about. So let's get started.

To animate this, I'm using [motion canvas](https://motioncanvas.io/), it's a very cool TS(yes) based npm package that allows you to animate using code, kind of like remotion except that... it was the first one I came across ok? I just came across remotion so not my problem!

Now in this 2 body system I firstly need... 2 bodies!

Which I have added using this line of code

```ts
const planetA = createRef<Circle>();
const planetB = createRef<Circle>();

scene.add(
  <>
    <Circle
      ref={planetA}
      width={100}
      height={100}
      fill={'red'}
    />
    <Circle
      ref={planetB}
      width={100}
      height={100}
      fill={'blue'}
    />
  </>
)
```

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ry672mggtu8am1uf942m.png)

But wait, where is the red circle? Well it's still there, just that it's underneath the blue one

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tvx4ch8n45c6ohoik4c7.png)
_same position of both the circles_

Since we didn't define the position for the 2 circles the default position has been applied to both the circles. Now in order to apply a position to the objects motion canvas gives us 2 options. 1 is to use the `position` attribute and the second is to use the individual `x` and `y` positions. For the purpose of keeping things simple(because I don't want to do maths) I'll use only one axis and that would be the `x` axis. This would make the code change into this

```ts
const planetA = createRef<Circle>();
const planetB = createRef<Circle>();

const planetAPos = createSignal(-800);
const planetBPos = createSignal(800);

scene.add(
  <>
    <Circle
      ref={planetA}
      width={100}
      height={100}
      fill={'red'}
     x={planetAPos}
    />

    <Circle
      ref={planetB}
      width={100}
      height={100}
      fill={'blue'}
     x={planetBPos}
    />
  </>
)
```

Due to this brand new position, the red circle is now visible

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ygs9fuid0v58xi39vrp9.png)
_yeah!_

Now the next thing that comes is applying physics! Time to make me hate myself!

Firstly we need to define the mass of the 2 planets, for simplicity, I'm going with 10 units for both the planets as of now. We of course need a gravitational constant which for now I'll take as 1 unit for now. Next is the distance.

For calculating the distance we just have to subtract the position of planetA from planetB, because the position of planetA is `-800`(x axis) and for planetB it is `800`, if we subtract one from another the distance between the 2 will be `-1600`, which to me is a bit strange so we'll take the magnitude of the value by applying an abs to it. This means our code would look like this

```ts
const massOfPlanetA = 10;
const massOfPlanetB = 10;
const gravitationalConstant = 1;

let distanceBetweenPlanets = createSignal(Math.abs(planetAPos() - planetBPos()));

scene.add(
  <Latex
    tex={() => `distance = ${distanceBetweenPlanets().toFixed(2)}km`}
    fill={'white'}
  />
)
```

As you can see I'm also displaying the values on the scene because motion canvas doesn't gives the option of `console.log()`... maybe it's a skill issue by my side but never mind.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lkqxjpbh47lfsb2h6bdz.png)

And just like our calculation the distance between the 2 planets is `1600km`, now I'm using km for the sake of using it, but it doesn't really has any effect at the output, it's still going to be just a number and nothing more.

Next is the gravitational force. Sounds simple right?(that's how you know it wasn't) All you need to do is apply the formula and job done! NO! It wasn't easy for some stupid reason which I don't know! But I finally managed to do it.

The end code is like this

```ts
let force = createSignal((gravitationalConstant * massOfPlanetA * massOfPlanetB) / Math.pow(distanceBetweenPlanets(), 2))

scene.add(
  <Latex
    tex={() => `force = ${force()}N`}
    fill={'white'}
    y={80}
  />
)
```

Now as you can see, all we are doing is multiplying the gravitational constant by the masses of the planets and then dividing the result by the squared distance.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k73iihznpgan3l5m02uc.png)

As you can see the force is very low, and it makes sense, because the mass of the 2 planets is really small compared to their distance, if you do the maths the mass of the 2 planets multiplied is only 100kg, but the squared distance is 2,560,000km<sup>2</sup>, and the gravitational constant is just 1 so it doesn't really do anything. For now, it doesn't really matters because I'll adjust the masses later so that it has some visible effects.

Next in line is calculating the acceleration, now here's the thing, I can do some really complicated maths and calculate the updated force and acceleration as the planets get closer, or I can totally screw all that and go for a safer, faster, and easier approach of just calculate the acceleration and don't dynamically update it...

Yeah option 2 is what I did here.

To calculate the acceleration we can just use the second law of motion that states `F = ma` where _m_ is mass, _a_ is acceleration(our target) and _F_ is the force between the 2 planets we have already calculated(the computer but you know?).

```ts
let accOfB = createSignal(force() / massOfPlanetB)

scene.add(
  <Latex
    tex={() => `Acceleration = ${accOfB()}m/s^2`}
    fill={'white'}
    y={160}
  />
)
```

**NOTE:** So I want to quickly go over this, because I'm using motion canvas, `force` is a function and not a variable, if you check the documentation of motion canvas, you'll see that this is more precisely a signal, which is just values which change and can be used to update the animation as per the change in value.

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/e7yl4lazkguzt0gh13wk.png)

And of course, the acceleration is also very low. Now let's calculate the velocity of the planetB, for this I'm just going to simple use the simple formula `v = u + at` where `u = 0`, here for the value of _t_ I'm going to use 1/60, that's because I'm rendering this animation at 60FPS, so this means 1 second is equal to 60 frames, and since I want to change the position of the planet by it's velocity each frame, I'll use 1/60 as the time here. I could use 1 second as the time but I found out that 1/60 is a better option.

```ts
let velocityOfB = createSignal(accOfB() * 1 / 60);

scene.add(
  <Latex
    tex={() => `V = ${velocityOfB()}m/s`}
    fill={'white'}
    y={240}
  />
)
```

This is the final value that we need, the only value by which we can move the planetB close to planetA. So let's do this!

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/83l7i4uliz4ll9yv53ww.png)

To really show some movement I'll be using a for loop which will move the planetB 10 frames, each frame lasting 0.1 seconds, this means in total it would take 1 sec to move from it's initial position to it's new position.

Now because the velocity is just soo low there is literally no movement and it would be useless for me to render this. So for the sake of this article, I went ahead and updated the values of the gravitational constant, and the masses of the 2 planet which are as follows

```ts
const massOfPlanetA = 10e18;
const massOfPlanetB = 10;
const gravitationalConstant = 6.67e-11;
```

As you can see I didn't change the mass of planetB because these values gave just good enough movements and I don't really want to mess with it, if it works, don't touch it!

![description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dmxmuu0wpdjfbvrgw0m5.png)

And yeah the velocity also changed to a value I'm happy with. And here's the final render. Enjoy!

<iframe width="914" height="514" src="https://www.youtube.com/embed/THuwYB-wS-o" title="Gravitational Force animated" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


Well that was boring...
