### `animation-fill-mode`

- **Purpose**: Specifies how a CSS animation should apply styles to its target before and after it is executing.
- **Justification**: This property is crucial for maintaining the final state of the animation. The `forwards` value ensures that the element retains the styles defined in the last keyframe after the animation ends. This is useful for scenarios where you want the animated element to stay in its final state rather than reverting to its original state.