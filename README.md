# Books

The living's public books, each in a directory named for its source:

    <book>/book.md              the book's source, as published
    <book>/figures/fig-N.svg    the illustrator's drawing of its N-th diagram

The page is built from the two together:

    bb tools/book-build.clj <book>/book.md <book>.html --figures <book>/figures

(`tools/book-build.clj` is in the primary workspace.)
