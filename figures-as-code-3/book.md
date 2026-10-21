<!-- to-the-living:start -->
Presentation.{ «Figures as code, 3rd edition» }

# Figures as code, 3rd edition

### Proposal 1: psyche-context › vision/book.md

  A proposal that touches a code component shows the code it changes or adds.

+ The illustrator draws every figure itself, as an SVG, which is text; no layout program draws one.

Ruling: land, amend, or reject.

### Proposal 2: psyche-context › vision/book.md

  A proposal that touches a code component shows the code it changes or adds.

+ A published book is kept in the public books repository, in a directory named for it: its source as book.md, and beside it figures/fig-N.svg, the drawing of its N-th diagram counted from the top. The page is built from that directory alone; a book missing a figure is not built.

```
+---------------------------+
| book source               |
+---------------------------+
     |                |
     | is copied      | sends each
     | as book.md     | diagram to
     |                v
     |        +---------------+
     |        | illustrator   |
     |        +---------------+
     |                |
     |                | draws
     |                | fig-N.svg
     v                v
+------------------------------------------------+
| public books repository                        |
| +-------------------+ +----------------------+ |
| | book.md           | | figures/fig-N.svg    | |
| +-------------------+ +----------------------+ |
+------------------------------------------------+
                        |
                        | is read by
                        v
+------------------------------------------------+
| builder                                        |
+------------------------------------------------+
                        |
                        | builds
                        v
+------------------------------------------------+
| book page                                      |
+------------------------------------------------+
```

Ruling: land, amend, or reject.

### Proposal 3: primary › subagents/book.md

  it for the figure as one inline SVG. The illustrator role composes
  vision-book's figure grammar; the brief carries the sketch and nothing
- more. Pass each returned SVG to the builder with `--figures`. A figure
- the builder refuses goes back to the illustrator with the builder's
- one-line error. If the illustrator role is unavailable, report the
+ more. Copy the source to `<book>/book.md` in the Books repository, save
+ the N-th returned SVG there as `<book>/figures/fig-N.svg`, and build
+ with `--figures <book>/figures`. A figure the builder refuses goes back
+ to the illustrator with the builder's one-line error. Commit and push
+ the Books repository when the page is published. If the illustrator
+ role is unavailable, report the
  blocker rather than drawing the figure here.

Ruling: land, amend, or reject.
<!-- to-the-living:end -->
