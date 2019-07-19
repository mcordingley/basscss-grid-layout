# BassCSS Grid Layout

BassCSS provides a great base from which to build a set of utility-first styles.
Unfortunately, it was built before CSS Grid became widely supported and so ships
with a grid system that is float-based. While that works, CSS Grid is more
powerful and flexible, all without requiring negative margins to compensate for
the gutters.

This module is built to complement BassCSS by mimicking its naming conventions
and using the same CSS variables. As a result, it should slot smoothly in place
next to BassCSS. As it is also fully self-contained, it can be used independently
of BassCSS.

The styles contained within are composable, immutable utilities that are
designed to each do one thing, do it well, and to be extended by user-defined
styles in each project's stylesheets. As such, do not feel limited to the styles
that are provided. 

## Defining a Grid

To start out with, define your grid container by adding the `grid` class to it.
The immediate children of this element will be arranged into a grid.
Unfortunately, your grid won't be very grid-like until you define some columns.

## Setting Columns

CSS Grid provides several powerful ways to define a grid to be exactly what your
project needs. The possibilities are too varied to be encoded into a utility
module like this, but the basic notion of a regular columnar grid translates well
into utility styles and should cover most needs.

To set the number of columns within a grid container, add one of the `grid-col-X`
classes to your grid container, where `X` is the desired number of columns.
There are classes for 2, 3, 4, 6, 8, 9, 12, and 16 column layouts.

Of course, you're always free to define your own classes to set columns as well.

### Responsive Columns

Column sizes are also responsive with the `sm-`, `md-`, and `lg-` prefixes, which
come into effect at the same break points as for BassCSS. This includes an
additional prefix of `xl-` for extra large screens at two size increments (12em)
above `lg-`. 

### Spanning Columns

It's common to need some grid items to span multiple columns. For this, add
one of the `grid-col-span-X` classes to the element that needs to span multiple
columns. As with the column definitions, these classes are responsive with the
same set of prefixes.

### Getting into the Gutter

Without further classes, your grid will contain no space between grid items.
We'll want to let the items have some space, so there are utilities to add some
space between your rows and your columns. `col-gap-X` will set spaces between
columns, while `row-gap-X` will set spaces between rows. `gap-X` will set both
at once. `X` follows the same sizes as BassCSS spaces, so `gap-2` will add as
much space between grid items as `mb2` would add beneath an element.

## Grid Item Alignment

By default, grid items are stretched to fill their respective slots in the grid.
There are several classes available to fine-tune this. Some can be set on the
grid container to affect all items, while others go onto individual grid items
for more targeted adjustments.

### On the Grid Container

For vertical alignment, use `align-items-center`, `align-items-end`, and
`align-items-start` to align items to the center, bottom, or top of their grid
areas. `align-items-stretch` is also available to return to the default of
stretching  them.

Horizontal alignment uses the `justify-items-center`, `justify-items-end`,
`justify-items-start`, and `justify-items-stretch` classes.

Both vertical and horizontal can be set at the same time by `items-center`,
`items-end`, `items-start`, and `items-stretch`.

### On Individual Grid Items

The classes for individual adjustments mirror those that go directly on the
grid container.

`align-self-center`, `align-self-end`, `align-self-start`,
and `align-self-stretch` set the vertical alignment of individual items.

`justify-self-center`, `justify-self-end`, `justify-self-start`,
and `justify-self-stretch` set the horizontal alignment of individual items.

`self-center`, `self-end`, `self-start`, and `self-stretch` will set both at once.

## Automatic Placement of New Grid Items

Grid items that don't have specific places on a grid defined will be automatically
placed horizontally after the last grid item. This behavior can be changed by
setting one of the `grid-auto-flow-X` classes onto the grid container.

`grid-auto-flow-column` will cause new items to be placed vertically until the grid
runs out of rows before moving on to the next column. `grid-auto-flow-column-dense`
does the same, but will go back and fill in holes in the grid layout as it is able.

`grid-auto-flow-row` explicitly sets what is otherwise the default behavior of
filling in a row before moving to the next while, while `grid-auto-flow-row-dense`
will attempt to fill in earlier holes in the grid.