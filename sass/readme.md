# Vesper CSS

## Exponential ratio's

Vesper CSS is based around exponential ratio's. This means that the base value doubles every increment. For example: 

- `m-t-1` is a top margin of 5px
- `m-t-2` is a top margin of 10px
- `m-t-3` is a top margin of 20px
- `m-t-4` is a top margin of 40px

## Margin, Padding & Index (x,y,z)

The base value is set in variables.scss. This works with exponential ratio's. So if you set 5 in the variables it will become 5, 10, 20, 40 etc..

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

## Colours

### Background colours

`primary` primary background
`secondary` primary background
`black` black background
`white` white background
`dark` dark background (grey)
`light` light background (grey)

### Text colours

`text-primary` primary text colour
`text-secondary` primary text colour
`text-black` black text colour
`text-white` white text colour
`text-dark` dark text colour (grey)
`text-light` light text colour (grey)
`text-inherit` inherit a contrasting colour from the background colour when available

You can also force the link colour to a certain style:
`link-primary`, `link-secondary`, `link-black`, `link-white`, `link-dark`,`link-light`

## Text

`font-plain` the plain text (`p`, `input` etc..)
`font-header` the header font (also from `h1` to `h5`)

### Sizes

`text` is the base text of 16px (set in variables.scss)
`text-1` is one up: 18, (16 + 2) (h5)
`text-2` is two up: 20, (16 + 4) (h4)
`text-3` is two up: 24, (16 + 8) (h3)
`text-4` is two up: 32, (16 + 16) (h2)
`text-5` is two up: 48, (16 + 32) (h1)
`text-6` is two up: 80, (16 + 64) 

### Styles

`bold`, `regular`, `light`, `italic`, `underline`

## Grid

## Lists

## Components
