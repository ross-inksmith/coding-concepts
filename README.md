# Coding Concepts

## Programming, in a nutshell
1. The best part about programming is that computers do exactly what they are told.
2. The worst part about programming is that computers do **exactly** what they are told.

So always remember: if the computer isn't doing what we want it to do, it's because it got the wrong instructions.

## First Instructions
Our micro:bit has a 5x5 grid of lights (called LEDs) that we can use to make basic pictures.
In the basic drawer there's a block called ``||show leds||`` that will let us control which lights are on and off.
``||basic.showIcon||`` does the same thing, but with premade patterns.
I'm going to use ``||basic.showIcon||`` and select the heart icon to make the micro:bit show a heart.
Click the lightbulb for more detail.


```blocks
basic.showIcon(IconNames.Heart);
```

Click on the "Basic" drawer, and then click and drag ``||basic.showIcon||`` inside of the ``||on start||`` block.
You can also find blocks by using the search box that's under the word **Toolbox**

## Pretty Pictures
Having our micro:bit just show one picture is cool, but it can do so much more.
We can make the heart look like its flashing by first showing an outline of a heart, and _then_ showing the heart icon.
``||basic.showIcon||`` doesn't have a heart outline premade for us, but we can use ``||basic.showLeds||`` to draw our own.

```blocks
basic.showLeds(`
    . # . # .
    # . # . #
    # . . . #
    . # . # .
    . . # . .
    `)
```

Drag the ``||basic.showLeds||`` block into the ``||on start||`` block, on top of the ``||basic.showIcon||`` block.
Next, click on the squares in the ``||basic.showIcon||`` block until it looks like a heart outline.

## Order Matters
Because each block in your program gets run one after another, the order of the blocks matters.
We can make it look like our heart is filling up by adding another step _between_ the heart outline and the full heart icon that's only part filled.
Or, we can make it look like it is emptying by changing the order of the blocks.
Try both!

```blocks
basic.showLeds(`
    . # . # .
    # . # . #
    # # , # #
    . # # # .
    . . # . .
    `)
```

Drag another ``||basic.showLeds||`` block between the outline block and the ``||basic.showIcon||`` block, then draw a partially filled heart.
You can also save yourself some time by right clicking on the heart outline block and clicking `Duplicate` to get a copy of the outline block, and then making that block into a partially filled heart.

## On Start vs Forever
When programming with blocks, we start out with ``||on start||`` and ``||basic.forever||`` blocks.
The ``||on start||`` and ``||basic.forever||`` blocks are special kinds of blocks because tell the micro:bit _when_ to run the blocks inside of them.
Like the name suggests, any block contained inside ``||on start||`` will happen exactly once at the very start of the program.
Anything contained in ``||basic.forever||`` will happen after ``||on start||``.
``||basic.forever||`` is different because each time it has gone through all the blocks inside of it, it will start again from its top block.

We've been putting all of our blocks in ``||on start||`` so far.
This makes our animation run once, each time the micro:bit starts.
If we want our  animation to keep looping, we can put it in the ``||basic.forever||`` block.
Let's make a simple heartbeat animation using the heart and small heart icons.

```blocks
basic.forever(() => {
    basic.showIcon(IconNames.SmallHeart);
    basic.showIcon(IconNames.Heart);
})
```

## Program Flow
Our animation now fills up a heart, and then starts beating forever.
We can see the three blocks it takes to show the heart filling animation, and then the two blocks it takes to show a heartbeat.
A total of 5 blocks.

However, we can also write this program with just 4 blocks if we remember that ``||basic.forever||`` is going to run right after ``||on start||``.
All I had to do was switch the order of the blocks in the forever block so that it would start with the heart icon, and remove the heart icon from the end of the filling animation.
There are often multiple ways to make the micro:bit do the same thing with different blocks.
So while we might feel clever for having used one less block, it might make our code more difficult to understand or change if we look at it later or give it to someone else.
Experimenting is the best way to learn!

```blocks
basic.showLeds(`
    . # . # .
    # . # . #
    # . . . #
    . # . # .
    . . # . .
    `)
basic.showLeds(`
    . # . # .
    # . # . #
    # # , # #
    . # # # .
    . . # . .
    `)
basic.forever(() => {
    basic.showIcon(IconNames.Heart);
    basic.showIcon(IconNames.SmallHeart);
})
```

