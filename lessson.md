# HTML/CSS 3 - Media Queries and Animations

## Objectives

### Media Queries

- Student can describe why media queries are used
- Student can use media queries to build a responsive app
- Student can use `min-width` when creating a breakpoint
- Student can use `max-width` when creating a breakpoint
- Student can specify multiple parameters for breakpoint using `and` with min-width and max-width

### Animations

- Student can specify the rules of an animation using `@keyframes`
- Student can use `from` and `to` to specify specific styles to change with `@keyframes`
- Student can use percentages to specify specific styles to change with `@keyframes`
- Student can use `animation-name` on class to specify animation to be used
- Student can use `animation-duration` on class to specify animation's duration
- Student can use `animation-iteration-count` on class to specify how many times animation will run
- Student can use `transition` shorthand property to smoothly transition style changes
- Student can specify which css class properties `transition` will be applied to.
- Student can use `refs` to trigger animations in react

## Resources

- [Lecture Video](https://vimeo.com/250309874/99dcf8b1ba)
- [Mobile First Design](https://mayvendev.com/blog/mobilefirst)
- [Refs and the DOM](https://reactjs.org/docs/refs-and-the-dom.html)

---

## Lesson

- [Space Jam](https://www.spacejam.com/archive/spacejam/movie/jam.htm) website

  - show what it looks like in desktop view.
  - Then inspect the page and show them what it would be like to browse that website with an iPhone X. Spoiler alert...it's terrible.

- Then I show them https://tinkerwatches.com/ in the desktop view.
  - Show off the animations and clean design,
  - Show what it looks like in mobile view. I point out how some of the animations were removed, but it still has a clean design and great feel for mobile.

### Prevalence of mobile browsing

- Trend: more people are consuming web content on a mobile device.
- There are now more cell phones than people.
- More people have cell phones than have toilets.
- Estimated 5.28 billion mobile broadband subscriptions
- Approx. 2.5 billion people check facebook on their phones every month
  - [source](https://qz.com/1608103/there-are-now-more-cellphones-than-people-in-the-world/)
- The point is that if we develop only for desktop we are ignoring a huge potential customer base.

#### Two ways to build an app

1. Mobile First
2. Desktop First

Desktop First:

- developing desktop view and working down to mobile views.
- This way tends to lead to a feature rich dektop view which may be hard to scale down to mobile views.
- May try to cram features from desktop view to mobile views to keep same features and feel.
- Can lead to a mobile view that feels like an afterthought rather than a well thought out app.

Mobile First:

- Dev mobile first
- build in the most critical and needed features
  - take into account device capabilities
- Build up to desktop view
  - add in more/better features as device is more powerful/has better capabilities.
- Starting with mobile tends to lead to views/features that are well designed for all platforms/views.

> Let the students know that whether the dev mobile first or not, it's possible to create a great app for all platforms, BUT the trend is mobile first.

#### Responsive Design

Responsive design --> building an app that optimizes its UI based on the device being used.

To help us build responsive design, we will use media queries.

- Create a simple nav bar with students
- Then add override the background-color. Example:

```
.nav {
    height: 55px;
    width: 100%;
    background-color: some color
}

.nav {
    background-color: some other color
}

```

- What color will show up?
  - Why
- What if we only wanted the nav bar to change color for mobile users?

## Media Queries

```
@media (parameter) {
    // styles to be applied
}

```

- The two main media features that I show them are min-width and max-width.

  - > min-width: if the screen is AT LEAST this big

  - > max-width: if the screen is AT LEAST this small

- Change the css to the following:

```
.nav {
    height: 55px;
    width: 100%;
    background-color: some color
}

@media (min-width: 375px) {
    .nav {
        background-color: some other color
    }
}

```

- Media queries at the bottom of our css, last thing to be applied
- Explain how the new background color only gets applied now if the width of the device is 375px or less. Show them in the browser.
- At this point I show them another example and explain how you can change the styles in any way.
- Ask the students to create a breakpoint with min-width and apply any new styles.

Max width:

- Show an example of using max width to change the size of a square.
- Example:

```
.square {
    width: 300px;
    height: 300px;
    color: some color;
}
@media (max-width: 500px) {
    .square {
        width: 100px;
        height: 100px;
    }
}
```

- Give the students a few mins to create a breakpoint using max-width

AND

- Show the students how to use `and`
- Example:

```
@media (min-width: 300px) and (max-width: 500px) {
    // super cool styles
}
```

Build a responsive nav bar with the students

- I like to clone this simple nav bar with the students: https://blackrockdigital.github.io/startbootstrap-blog-post/
  - I just find a simple hamburger icon in an image search

FLIP FLEX DIRECTION

#### Animations

Discuss with the students what an animation is. Talk about the benefit of animations - when they are done right.

Show then examples of some well done animations.

- http://www.theglyph.studio/#home
- Point out the more complex animations AND the very simple animations on the page.
  - an animation does not have to be some big, grand action on your app. They can also be very simple and subtle.

You can also go very wrong/overboard with you animations

- https://www.lingscars.com/

There are many ways to incorporate animations into an app, from using CSS animations to more complex JS libraries.

##### CSS Animations w/ @keyframes

Using CSS animations, we have a simple way to animate HTML elements.

I usually start with something really basic, like making a square spin.

- Make sure to discuss from/to, and using specific percentages:

Example

CSS

```
.square {
    width: 100px;
    height: 100px;
    background-color: red;
    animation-name: spin;
    animation-duration: 4s;
    animation-iteration-count: infinite;
}
```

using from/to

```
@keyframes spin {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(1080deg);
    }
}
```

using percentage

```
@keyframes spin {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(1080deg);
    }
}
```

Using CSS animations, your styles with _smoothly_ transition from starting point to end (based on the duration of the animation)

Show them how to trigger the same animation, but on a click event (in a react component).

Animation-fill-mode:

- Allows us to specify the ending css property values

Examples of what can be done with css animations: https://webdesign.tutsplus.com/articles/15-inspiring-examples-of-css-animation-on-codepen--cms-23937

**If there is time**, create a beating heart animation. Simple examples can be google searched (found some simple examples on codepen)

Have the students spend some time creating their own animations. Give them some simple ideas.

- Inform them of animation libraries, what they are, why people use them, convenient, etc.

#### Transitions (for simple animations)

Sometimes you want to simply animate something (making it bigger/smaller, move it from one point to another, etc). This is where the transition property is helpful.

Transitions do not handle the starting or ending values for css properties. Transitions don't even change css properties, they just define how the change occurs (example: how long the animation takes).

Transitions cannot loop like animations can.

Transitions must be triggered to run (click, hover, etc)

Show students how to use the transition property and why it is useful.

I like to build a realistic example of what they may do with the transition property. I build a side menu that slides out when a hamburger menu is clicked on. Or:

- A menu that slides down from under the nav bar
- a button/image that gets slightly larger when cursor hovers over
- etc.

If you have extra time at the end, have some animation/transition examples for the students to pick from that you can build together.

- Another option is to introduce them to the react-motion lib
  - Telling them what it is and why they may want to use it
  - Show them examples
  - Show them where tutorials are: https://github.com/DevMountain/dm-tutorials

#### Animating in React

- Show students how to use Refs to trigger animations in React.
- Highlight that they shouldn't be using `document.[method]` to interact with the DOM.
- Go into refs and show them how they are a wrapper over the `document` methods
  - What refs are
  - Why we need them
  - How to declare a ref
    - It can be beneficial to show the older syntaxs they might see as well, but definitely show the current syntax
  - `console.dir` a ref so they can see that it operates like the `document` methods
  - Show some logic to start and stop an animation, etc.
