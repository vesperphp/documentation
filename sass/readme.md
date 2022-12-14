# Vesper CSS

## Breakpoints

The breakpoints are set in the variables file and has four values. More values can be added later. The idea is that we work from mobile up to desktop since most web applications are most useful if they work perfectly on mobile devices.
- The breakpoint name.
- The set viewport width.
- The corresponding wrapper width.
- The scaling ratio of margins and font sizes.


## Exponential ratio's

Vesper CSS is based around exponential ratio's. This means that the base value doubles every increment. For example: 

- `m-t-1` is a top margin of 5px
- `m-t-2` is a top margin of 10px
- `m-t-3` is a top margin of 20px
- `m-t-4` is a top margin of 40px

## Margin, Padding & Index (x,y,z)

The base value is set in variables.scss. This works with exponential ratio's. So if you set 5 in the variables it will become 5, 10, 20, 40 etc..

### Margin

- `m-0` to `m-9` is a margin on all sides.
- `m-y-0` to `m-y-9` is a margin on the y-axis (vertical).
- `m-x-0` to `m-x-9` is a margin on the x-axis (horizontal).

- `m-l-0` to `m-l-9` is a margin on the left side.
- `m-r-0` to `m-r-9` is a margin on the right side.
- `m-t-0` to `m-t-9` is a margin on the top side.
- `m-b-0` to `m-b-9` is a margin on the bottom.

### Padding

- `p-0` to `p-9` is a padding on all sides.
- `p-y-0` to `p-y-9` is a padding on the y-axis (vertical).
- `p-x-0` to `p-x-9` is a padding on the x-axis (horizontal).

- `p-l-0` to `p-l-9` is a padding on the left side.
- `p-r-0` to `p-r-9` is a padding on the right side.
- `p-t-0` to `p-t-9` is a padding on the top side.
- `p-b-0` to `p-b-9` is a padding on the bottom.

### Index & Position

- `sticky`, `relative`, `absolute` & `fixed` are classes you can use to change objects on a positional level.
- `pos-l-0` to `pos-l-9` is a padding on the left side.
- `pos-r-0` to `pos-r-9` is a padding on the right side.
- `pos-t-0` to `pos-t-9` is a padding on the top side.
- `pos-b-0` to `pos-b-9` is a padding on the bottom.
- `pos-t-auto` sets the value to auto. This works for all the other sides as well.
- `z-0` to `z-9` are z-index values from 0 to 90.
- `zm-0` to `zm-9` are z-index values from  -0 to 90.

### Useful helpers

`m-auto` is the same as `margin: auto 0;` and centers your block.

## Colours

### Background colours

- `primary` primary background
- `secondary` primary background
- `black` black background
- `white` white background
- `dark` dark background (grey)
- `light` light background (grey)
- `danger` background (red)
- `warning` background (yellow)
- `success` background (green)
- `info` background (blue)

There are also light and dark versions of every colour. You can access those by using `primary-l` or `primary-d`. This will of course work with every preset colour.

### Text colours

- `text-primary` primary text colour
- `text-secondary` primary text colour
- `text-black` black text colour
- `text-white` white text colour
- `text-dark` dark text colour (grey)
- `text-light` light text colour (grey)

You can also force the link colour to a certain style:
- `link-primary`, `link-secondary`, `link-black`, `link-white`, `link-dark`,`link-light`

## Text


### Sizes

- `<p>` is the base text of 16px (set in variables.scss)
- `text-1` is one up: 18, (16 + 2) (h5)
- `text-2` is two up: 20, (16 + 4) (h4)
- `text-3` is two up: 24, (16 + 8) (h3)
- `text-4` is two up: 32, (16 + 16) (h2)
- `text-5` is two up: 48, (16 + 32) (h1)
- `text-6` is two up: 80, (16 + 64) 

### Styles

- `bold`, `regular`, `light`, `italic`, `underline`

## Grid

## Lists

## Components

### Buttons

`button` is the most basic form of a button. It has some set values you can modify by adding classes. A html `<button>` tag has some preset properties but it can also be used on `<a href="#" class="button">My button</a>`
- `icon-info` adds an info icon and aligns the text to the left. Other icons are at this moment: `mail`, `user`..

### Flash messages

Use `flash-warning` or other classes on a div to style the flash messages that appear on top of the page after a change. The colour names/ type names correspond with the available colours. So `flash-primary` is also usable for instance. You can also use icons by adding `icon-info` to the classlist. Other icons are at this moment: `mail`, `user`..

```
<div class="flash-warning icon-danger">
    <p>My danger message</p>
</div>
```
