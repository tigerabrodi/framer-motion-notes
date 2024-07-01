# Motion tag

`motion.div` would be a motion tag.

Whatever you place after `motion.` is the HTML tag that will end up in the DOM. Even if you put any jibberish in there.

# Spring Physics

Spring physics make animations feel real. As if you're moving a real object. If you think of a ball rolling on the floor, it doesn't move with the same pace towards the end before stopping.

Stiffness: Refers to the tension released when the animation happens.

Dampening: Refers to the universal trait that slows down the motion aka dampens the motion.

Springs are nice when it comes to motion.

# Syntax

```jsx
<motion.div
  initial={false}
  className="yellow ball"
  transition={{
    type: "spring",
    stiffness: 300,
    damping: 20,
  }}
  animate={{
    y: isEnabled ? 60 : 0,
  }}
/>
```

- `initial` whether to start the animation right away or not.
- `spring` as type for spring animation.
- `stiffness` to control the tension of the spring.
- `damping` to control the dampening of the spring.
- `animate` to control the motion of the spring.

You want to make sure your animations have spring motions to make them feel real.

Don't hesistate to play around with damping and stiffness to get the best result.

# Layout animations

If needing to animate the layout e.g. size or positioning, you can set `layout` to true.

- Both parent and all children need layout animation set to true.
- Children need it too, to avoid animating in the wrong way.
- Parent and children need the same transition values to look in sync.
- Parent needs to make sure the positioning of children is ok so that during layout animation they don't look jarring.
