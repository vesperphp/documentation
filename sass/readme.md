# Vesper CSS

## Exponential ratio's

Vesper CSS is based around exponential ratio's. This means that the base value doubles every increment. For example: 

- `m-t-1` is a top margin of 5px
- `m-t-2` is a top margin of 10px
- `m-t-3` is a top margin of 20px
- `m-t-4` is a top margin of 40px

## Margin, Padding & Index (x,y,z)

The base (1 = 5px) value is set in variables.scss.

### Margin

- `m-1` to `m-9` is a margin on all sides.
- `m-y-1` to `m-y-9` is a margin on the y-axis (vertical).
- `m-x-1` to `m-x-9` is a margin on the x-axis (horizontal).

- `m-l-1` to `m-l-9` is a margin on the left side.
- `m-r-1` to `m-r-9` is a margin on the right side.
- `m-t-1` to `m-t-9` is a margin on the top side.
- `m-b-1` to `m-b-9` is a margin on the bottom.

### Padding

- `p-1` to `p-9` is a padding on all sides.
- `p-y-1` to `p-y-9` is a padding on the y-axis (vertical).
- `p-x-1` to `p-x-9` is a padding on the x-axis (horizontal).

- `p-l-1` to `p-l-9` is a padding on the left side.
- `p-r-1` to `p-r-9` is a padding on the right side.
- `p-t-1` to `p-t-9` is a padding on the top side.
- `p-b-1` to `p-b-9` is a padding on the bottom.

### Index

- `z-0` to `z-9` are z-index values from 0 to 90.
- `zm-0` to `zm-9` are z-index values from  -0 to 90.

### Useful helpers

`m-auto` is the same as `margin: auto 0;` and centers your block.
