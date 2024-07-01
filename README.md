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

# Shared Layout Animations

- `layoutId` with the same value will cause framer motion to trigger optical illusion that it's a single element animating.
- For example, underline under tabs.
- Same `layoutId` will animate the same optical "element" throughout the app, even if different components.
- You may find weird quirks with the animation, such as intial styles you want applied that flicker for a split second. To solve this, you can use `animate` and set initial animation to false. But this isn't recommended because we don't need to animate the "core" styles we initially want applied, so use `initial` as object and set your styles there.
- If you're using positioning, it's important to understand that by natural, the stacking context happens in the order of the DOM if no zIndex is set. So you may see unexpected behavior if you don't account for this when using position.

# Layout Groups

- layoutId used to animate different pieces of items between different containers.
- No need to set layout prop if layoutId is set
- layoutId can not be null, considered falsy value
- use a unique value for layoutId
- Make sure to count each layoutId in a way where they're globally unique but also ranked in their own order
- For example, in container 1 you may have a list of items, but if they move to container 2, they should be in the same order
- So the ones moving from container 1 should still be in their order
- One example is to keep track of the order in container 1, and then start from the length of the end of container 1
- layoutId and key must both be unique, key can't be index while layoutId is unique
