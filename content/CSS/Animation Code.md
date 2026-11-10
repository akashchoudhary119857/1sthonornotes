
# CSS Loaders — Beginner-Friendly Notes

This document contains simple HTML and CSS code for different loader animations.

## 1. Circular Spinner Loader

**Use case:** Page loading and API requests.

```
<!DOCTYPE html>
<html>
<head>
<style>
.loader {
  width: 60px;
  height: 60px;
  border: 6px solid #ddd;
  border-top: 6px solid royalblue;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
</style>
</head>
<body>
  <div class="loader"></div>
</body>
</html>
```

## 2. Two-Box Loader

**Use case:** Custom loading animations. The outer box rotates while the inner box counter-rotates to remain visually upright.

```
<!DOCTYPE html>
<html>
<head>
<style>
.outer {
  width: 70px;
  height: 70px;
  border: 5px solid royalblue;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: spin 2s linear infinite;
}

.inner {
  width: 25px;
  height: 25px;
  background: orange;
  animation: reverse-spin 2s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

@keyframes reverse-spin {
  to {
    transform: rotate(-360deg);
  }
}
</style>
</head>
<body>
  <div class="outer">
    <div class="inner"></div>
  </div>
</body>
</html>
```

## 3. Three Bouncing Dots

**Use case:** Chat applications and typing indicators.

```
<!DOCTYPE html>
<html>
<head>
<style>
.loader {
  display: flex;
  gap: 8px;
}

.dot {
  width: 15px;
  height: 15px;
  background: royalblue;
  border-radius: 50%;
  animation: bounce 0.6s infinite alternate;
}

.dot:nth-child(2) {
  animation-delay: 0.2s;
}

.dot:nth-child(3) {
  animation-delay: 0.4s;
}

@keyframes bounce {
  to {
    transform: translateY(-15px);
  }
}
</style>
</head>
<body>
  <div class="loader">
    <div class="dot"></div>
    <div class="dot"></div>
    <div class="dot"></div>
  </div>
</body>
</html>
```

## 4. Three Blinking Balls

**Use case:** Loading indicators where balls blink one after another.

```
<!DOCTYPE html>
<html>
<head>
<style>
.loader {
  display: flex;
  gap: 8px;
}

.dot {
  width: 15px;
  height: 15px;
  background: royalblue;
  border-radius: 50%;
  animation: blink 0.9s infinite;
}

.dot:nth-child(2) {
  animation-delay: 0.3s;
}

.dot:nth-child(3) {
  animation-delay: 0.6s;
}

@keyframes blink {
  0%, 100% {
    opacity: 0.2;
  }

  50% {
    opacity: 1;
  }
}
</style>
</head>
<body>
  <div class="loader">
    <div class="dot"></div>
    <div class="dot"></div>
    <div class="dot"></div>
  </div>
</body>
</html>
```

**How it works:**

- `opacity: 0.2` makes a ball dim.
    
- `opacity: 1` makes a ball fully visible.
    
- `animation-delay` creates the sequence.
    
- Change the animation duration to `1.5s` to slow down the blinking.
    

## 5. Bouncing Ball

**Use case:** Playful websites and game loading screens.

```
<!DOCTYPE html>
<html>
<head>
<style>
.ball {
  width: 35px;
  height: 35px;
  background: tomato;
  border-radius: 50%;
  animation: jump 0.7s ease-in-out infinite alternate;
}

@keyframes jump {
  from {
    transform: translateY(0);
  }

  to {
    transform: translateY(-50px);
  }
}
</style>
</head>
<body>
  <div class="ball"></div>
</body>
</html>
```

## 6. Bar Loader

**Use case:** Audio loading and data processing.

```
<!DOCTYPE html>
<html>
<head>
<style>
.loader {
  display: flex;
  gap: 5px;
  align-items: center;
  height: 60px;
}

.bar {
  width: 9px;
  height: 20px;
  background: mediumseagreen;
  animation: stretch 0.7s ease-in-out infinite alternate;
}

.bar:nth-child(2) {
  animation-delay: 0.15s;
}

.bar:nth-child(3) {
  animation-delay: 0.3s;
}

.bar:nth-child(4) {
  animation-delay: 0.45s;
}

@keyframes stretch {
  to {
    height: 55px;
  }
}
</style>
</head>
<body>
  <div class="loader">
    <div class="bar"></div>
    <div class="bar"></div>
    <div class="bar"></div>
    <div class="bar"></div>
  </div>
</body>
</html>
```

## 7. Progress Bar Loader

**Use case:** File uploads and indeterminate loading states.

```
<!DOCTYPE html>
<html>
<head>
<style>
.track {
  width: 250px;
  height: 10px;
  background: #ddd;
  border-radius: 10px;
  overflow: hidden;
}

.progress {
  width: 35%;
  height: 100%;
  background: royalblue;
  animation: loading 1.5s ease-in-out infinite;
}

@keyframes loading {
  from {
    transform: translateX(-100%);
  }

  to {
    transform: translateX(300%);
  }
}
</style>
</head>
<body>
  <div class="track">
    <div class="progress"></div>
  </div>
</body>
</html>
```

## 8. Pulse Loader

**Use case:** Waiting for a server response.

```
<!DOCTYPE html>
<html>
<head>
<style>
.pulse {
  width: 50px;
  height: 50px;
  background: #8e44ad;
  border-radius: 50%;
  animation: pulse 1s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% {
    transform: scale(0.7);
    opacity: 0.5;
  }

  50% {
    transform: scale(1.2);
    opacity: 1;
  }
}
</style>
</head>
<body>
  <div class="pulse"></div>
</body>
</html>
```

## 9. Rotating Square Loader

**Use case:** Minimalist website loading screens.

```
<!DOCTYPE html>
<html>
<head>
<style>
.square {
  width: 50px;
  height: 50px;
  background: orange;
  animation: rotate 1.5s ease-in-out infinite;
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }

  50% {
    transform: rotate(180deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
</style>
</head>
<body>
  <div class="square"></div>
</body>
</html>
```

## 10. Double-Ring Loader

**Use case:** Modern application loading screens.

```
<!DOCTYPE html>
<html>
<head>
<style>
.loader {
  width: 60px;
  height: 60px;
  border: 5px solid transparent;
  border-top-color: royalblue;
  border-bottom-color: royalblue;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
</style>
</head>
<body>
  <div class="loader"></div>
</body>
</html>
```

## 11. Orbit Loader

**Use case:** Creative portfolios and science-themed interfaces.

```
<!DOCTYPE html>
<html>
<head>
<style>
.orbit {
  width: 70px;
  height: 70px;
  border: 2px solid #bbb;
  border-radius: 50%;
  position: relative;
  animation: spin 1.5s linear infinite;
}

.planet {
  width: 15px;
  height: 15px;
  background: crimson;
  border-radius: 50%;
  position: absolute;
  top: -7px;
  left: 27px;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
</style>
</head>
<body>
  <div class="orbit">
    <div class="planet"></div>
  </div>
</body>
</html>
```

## 12. Skeleton Loader

**Use case:** Placeholder cards while content loads.

```
<!DOCTYPE html>
<html>
<head>
<style>
.card {
  width: 250px;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 10px;
}

.skeleton {
  height: 15px;
  margin: 12px 0;
  border-radius: 5px;
  background: linear-gradient(
    90deg,
    #eee 25%,
    #ddd 50%,
    #eee 75%
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
}

.image {
  height: 100px;
}

.short {
  width: 60%;
}

@keyframes shimmer {
  to {
    background-position: -200% 0;
  }
}
</style>
</head>
<body>
  <div class="card">
    <div class="skeleton image"></div>
    <div class="skeleton"></div>
    <div class="skeleton short"></div>
  </div>
</body>
</html>
```

## Quick Revision Table

|Loader|Main CSS concept|
|---|---|
|Circular spinner|`rotate()`|
|Two-box loader|Parent and child animations|
|Bouncing dots|`translateY()` and animation delays|
|Blinking balls|`opacity` and animation delays|
|Bouncing ball|`alternate`|
|Bar loader|Changing height|
|Progress bar|`translateX()`|
|Pulse loader|`scale()` and `opacity`|
|Rotating square|`rotate()`|
|Double-ring loader|Borders and `border-radius`|
|Orbit loader|Positioning and rotation|
|Skeleton loader|Gradient and `background-position`|

## Practice Tasks

1. Change the spinner color from blue to green.
    
2. Make the bouncing dots move faster.
    
3. Add two more dots to the blinking loader and arrange their delays.
    
4. Change the square loader into a rotating diamond.
    
5. Make the pulse loader use a square instead of a circle.
    
6. Create a loader with two rotating rings in opposite directions.
    
7. Create a skeleton card with an image placeholder, title, and three text lines.
    

**Important:** For a real website, display a loader while a task is running and hide it when the task finishes. Consider supporting `prefers-reduced-motion` for users who prefer less animation.