---
name: analyze-components
description: Audit the components on a page, flag orphans, duplicates, and bad names, and fix what can be fixed in one pass. Use when the user asks for a component audit or a library cleanup.
---

# Component audit

Catalog every component on the page. Give each one a live preview in the audit frame.

Flag:

- Orphans that sit outside the library.
- Duplicates of a component that already exists.
- Names that break the file's pattern.

For an orphan, place a library copy and swap instances onto it. Leave a duplicate in place when swapping would change behavior, and say so.

Write the audit on the canvas: found, fixed, and still waiting on a person.
