---
name: ui-state-expander
description: Expand a screen, component, or flow into the states engineering has to build. Use when the user asks for empty, loading, error, disabled, or edge states.
---

# UI states

Start from the happy path. Add a frame for each of these, and skip one only when it cannot occur:

- Loading
- Empty
- Error
- Disabled
- Partial data
- The edge case that breaks the layout, such as a long name or a missing image

On each frame write the trigger, the copy, the transition, and what has to be implemented. Lay the states in one row.
