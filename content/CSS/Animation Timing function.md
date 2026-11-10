# CSS Animation Timing Functions

## 1. What is an Animation Timing Function?

The `animation-timing-function` property defines how the speed of a CSS animation changes over its duration.

It controls whether an animation moves at a constant speed, starts slowly, speeds up, or slows down.

**Syntax:**

```
animation-timing-function: value;
```

You can also use it inside the `animation` shorthand property.

```
animation: spin 1s linear infinite;
```

## 2. Types of Animation Timing Functions

### 1. `linear`

- The animation moves at a constant speed.
    
- It does not accelerate or decelerate.
    

```
.box {
  animation: move 2s linear infinite;
}
```

### 2. `ease`

- This is the default timing function.
    
- The animation starts slowly, speeds up in the middle, and slows down at the end.
    

```
.box {
  animation: move 2s ease infinite;
}
```

### 3. `ease-in`

- The animation starts slowly and gradually speeds up.
    
- Useful when an element should appear to accelerate.
    

```
.box {
  animation: move 2s ease-in infinite;
}
```

### 4. `ease-out`

- The animation starts quickly and gradually slows down.
    
- Useful when an element should come to a smooth stop.
    

```
.box {
  animation: move 2s ease-out infinite;
}
```

### 5. `ease-in-out`

- The animation starts slowly, speeds up in the middle, and slows down at the end.
    
- Creates a smooth animation.
    

```
.box {
  animation: move 2s ease-in-out infinite;
}
```

### 6. `step-start`

- The animation jumps immediately to the final state at the start of the timing interval.
    
- It does not transition smoothly between states.
    

```
.box {
  animation: move 2s step-start infinite;
}
```

### 7. `step-end`

- The animation stays at the initial state until the end of the timing interval, then jumps to the final state.
    

```
.box {
  animation: move 2s step-end infinite;
}
```

### 8. `steps(n)`

- Divides the animation into a specified number of discrete steps.
    
- Useful for frame-by-frame animations and sprite animations.
    

```
.box {
  animation: move 2s steps(4) infinite;
}
```

Here, `steps(4)` divides the animation into four discrete steps.

### 9. `cubic-bezier()`

- Allows you to create a custom animation speed curve.
    
- It accepts four numerical parameters.
    

```
.box {
  animation: move 2s cubic-bezier(0.42, 0, 0.58, 1) infinite;
}
```

## 3. Comparison Table

|Timing Function|Role|
|---|---|
|`linear`|Constant speed|
|`ease`|Slow start, faster middle, slow finish|
|`ease-in`|Slow start, then accelerates|
|`ease-out`|Fast start, then decelerates|
|`ease-in-out`|Slow start and finish|
|`step-start`|Jumps to the final state immediately|
|`step-end`|Jumps to the final state at the end|
|`steps(n)`|Moves in discrete steps|
|`cubic-bezier()`|Creates a custom speed curve|

## 4. Complete Working Example

```
<!DOCTYPE html>
<html>
<head>
<style>
.box {
  width: 60px;
  height: 60px;
  background: royalblue;
  margin: 15px 0;
  animation: move 3s ease-in-out infinite alternate;
}

@keyframes move {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(250px);
  }
}
</style>
</head>
<body>

<div class="box"></div>

</body>
</html>
```

### Explanation

- `move`: Name of the animation.
    
- `3s`: Animation duration is three seconds per cycle.
    
- `ease-in-out`: Starts and finishes slowly.
    
- `infinite`: Repeats continuously.
    
- `alternate`: Reverses direction on every other cycle.
    
- `@keyframes`: Defines the animation's starting and ending states.
    

## 5. Difference Between `infinite` and `alternate`

These values serve different purposes.

### `infinite`

Controls the number of repetitions.

```
animation: move 2s linear infinite;
```

The animation repeats continuously.

### `alternate`

Controls the direction of successive animation cycles.

```
animation: move 2s linear infinite alternate;
```

The element moves forward, then backward, and continues alternating.

**Important:** `infinite` and `alternate` are not timing functions. They are animation iteration-count and direction values, respectively.

## 6. Quick Revision

- `linear` = Same speed.
    
- `ease` = Smooth default speed variation.
    
- `ease-in` = Starts slowly.
    
- `ease-out` = Finishes slowly.
    
- `ease-in-out` = Starts and finishes slowly.
    
- `steps(n)` = Moves in jumps.
    
- `cubic-bezier()` = Custom speed curve.
    
- `infinite` = Repeats forever.
    
- `alternate` = Reverses direction on alternate cycles.
    

**Remember:** The timing function controls the animation's speed progression, while the duration controls how long each cycle takes.