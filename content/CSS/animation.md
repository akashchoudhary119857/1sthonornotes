short hand property used for animation-name, animation-timing-function, animation iteration /direction count

```css
@keyframes changecolor {
  from { background-color: red; }
  to { background-color: yellow; }
}

.animated-element {
  animation-name: changecolor;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: 1s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-fill-mode: forwards;
}
```
