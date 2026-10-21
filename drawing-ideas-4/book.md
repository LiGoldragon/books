<!-- to-the-living:start -->
Presentation.{ «Drawing ideas, 4th edition» }

# Drawing ideas, 4th edition

## field-context › role/illustrator-faithfulness.md

Receive one ASCII sketch and its book title. Return exactly one SVG and nothing else, drawing the sketch by the figure grammar in vision-book. The book title is context, not permission to add a diagram title. If the sketch has no relation to draw, return the sketch instead of drawing it. If the sketch is ambiguous, report that refusal instead of inventing content.

### Proposal 1: psyche-context › vision/book.md

  ## Pictures
  
- A figure shows one thing, where the idea has a shape, and its colours and marks mean the same in every book.
+ A figure shows one thing, where the idea has a shape, and its colours and marks mean the same in every book: what its sketch marks + is drawn green with its plus, what it marks - is drawn red with its minus, and all else is drawn without colour and without dashes.

```
+--------------------------------------------+
| the sketch                                 |
| +----------+ +----------+ +-------------+  |
| | + a line | | - a line | | a line      |  |
| +----------+ +----------+ +-------------+  |
+--------------------------------------------+
      |            |              |
      | is drawn   | is drawn     | is drawn
      | green      | red          | plain
      v            v              v
+--------------------------------------------+
| the figure                                 |
+--------------------------------------------+
```

### Proposal 2: psyche-context › vision/book.md

  A figure shows how a thing moves, one question per figure, readable in seconds. Its grammar: a box is a thing or a collection; an arrow is a one-way relation carrying a verb, so that box, verb, box reads as a sentence; nearness and enclosure are kinship; top to bottom is order; colour carries a role or is absent. A list in boxes, a tally, or a sentence in a rectangle is not a figure. A diagram in a book's source is ASCII in that grammar, drawn so a phone shows it; a sketch without arrows is rewritten before it is sent. The published book never shows the ASCII, but a figure drawn from it by a Tertiary or Quaternary subflow that is given the grammar with the sketch, keeps every box, label and arrow, and adds nothing the source does not say; a figure that lost an arrow is returned. A sizable book carries several figures.
  
+ In the sketch, an arrow points to the end where its head is, v, ^, < or >; the words beside its shaft are its verb; a box drawn inside another is enclosed by it.

### Proposal 3: field-context › role/illustrator-svg.md

- Draw a portrait figure whose every label reads on a phone, on light and dark surfaces. SVG must be self-contained: no script, foreignObject, external references or event handlers. Keep every arrow of the sketch an arrow; write only the sketch's own words, in <text>, and put no <title>, <desc> or aria-label words the sketch does not carry. Return markup only. The calling book author places the artifact. Do not create illustration files in Primary.
+ Draw a portrait figure whose every label reads on a phone, on light and dark surfaces. SVG must be self-contained: no script, foreignObject, external references or event handlers. Write the sketch's words in <text>, and none in <title>, <desc> or aria-label. Return markup only. The calling book author places the artifact. Do not create illustration files in Primary.
<!-- to-the-living:end -->
