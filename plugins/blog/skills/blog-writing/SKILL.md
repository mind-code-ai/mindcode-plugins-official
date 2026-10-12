---
name: blog-writing
description: Write, review, or tighten an engineering blog post. Use when the user asks for a blog post, a launch note, a postmortem, a tutorial, or a pass on a draft that should read like a developer wrote it.
---

# Blog writing

Write the post a senior engineer would send to their team. Be specific, direct, and willing to say what failed.

## Open

The first sentences state the problem or the conclusion. Skip the company history and the announcement warm-up.

## Shape

Answer the reader's questions in this order:

1. What problem does this solve?
2. How does it work, at the level of the system, not the buttons?
3. What did you decide against, and why?
4. How does the reader try it?

A deep engineering post also says what was tried and abandoned, and what still does not work.

## On the page

One idea per paragraph. Start a new paragraph when the point turns.

Headings carry information. "Background" and "Conclusion" do not. A heading should say the claim.

If a system has more than two parts, include a diagram with the real names.

A performance claim includes the number. Code in the post has to run, with the imports and the config it needs. Comments say why.

## Leave out

Cut these on sight:

- Excited to announce, best-in-class, seamless, empower, leverage, unlock, robust, streamline.
- "In this post we will explore."
- Filler: that being said, it's worth noting, at the end of the day.
- A slogan standing in for the explanation.
- A stack of one-line fragments where a sentence would do.
- A personal opening, a flat middle, and a sign-off that only asks the reader to try the product.

## Close

End with a concrete next step: the docs, the source, or how to try the change. Tie it back to the opening. Do not recap the post, and do not close on a slogan.

## Before you call it done

- The title makes a specific claim.
- A developer could share it.
- Technical claims match the system.
- A changelog entry would have been enough, and this post still earns the extra length.
- The byline is a person, when the post is published under a name.
