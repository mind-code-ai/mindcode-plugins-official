---
name: create-color
description: Map every fill, stroke, and shadow on a component to a design token. Use when the user asks for a color spec, token coverage, or hard-coded colors.
---

# Color tokens

Walk the selection, including each variant and state. For every visible fill, stroke, and shadow:

- Bind it to an existing token or style when one matches.
- Flag it when the color is hard-coded.

Stacked fills and gradients get their own lines. List each fill in stacking order. List each gradient stop with its position, color, and bound variable.

Write the spec beside the component so someone can rebuild the treatment without opening every layer.
