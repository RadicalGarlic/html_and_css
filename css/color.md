# Color
Color values in CSS can be specified in multiple ways.
* Color name (one of 147). This isn't commonly used, aside from black and white.
```css
h1 {
    color: DarkCyan;
}
```
* RGB (values between [0,255])
```cs
h2 {
    color: rgb(100,100,90);
}
```
* RGB in hexadecimal. For values where all the letters are the same, the value can be abbreviated with just 3 of the characters (`#fff` is equivalent to `#ffffff`).
```css
h3 {
    color: #ee3e80;
}
```
CSS3 also introduces a new ways to specify colors ([described later](#CSS3-Features)).

## Foreground vs Background
Foreground color (usually color of the text) are specified with the `color` property.
```css
p {
    color: rgb(0,0,0);
}
```
Background color refers to the color of the implicit CSS box that surrounds each HTML element, behind any text. It is controlled with the `background-color` property and is transparent by default.
```css
p {
    background-color: #ee3e80;
}
```

## Hue, Saturation, and Brightness
Hue refers to the "color" of a color, if that makes any sense. It's the colloquial definition of what a color is.

Saturation refers to the amount of gray in a color. Lower saturation makes this look more muted.

Brightness refers to how much black is in a color. Lower brightness makes colors look more dark.

## Readability
Too low color contrast (different between colors), and text will be hard to discern from the background. Too high contrast though can make the screen tiring to look at after a while.

Medium contrast (off-black background with off-white text, for example) is usually best.

## CSS3 Features
### Opacity
CSS3 introduces the `opacity` property.
```css
p {
    background-color: rgb(0,0,0);
    /* 50% opacity */
    opacity: 0.5;
}
```
As you can imagine, this property controls the opacity of the element, making the other elements behind it more or less visible.

The values range from 0.0 (completely transparent) to 1.0 (completely opaque).

### RGBA
Opacity can also be specified as a part of RGBA.
```css
p {
    /* RGB (0,0,0) with 50% opacity */
    background-color: rgba(0,0,0,0.5);
}
```
The "A" in RGBA stands for "alpha", which refers to opacity in this context.

In case the browser doesn't support `rgba` for colors, you can supply a fallback color property that can be used instead.
```css
p {
    /* Fallback */
    background-color: rgb(100,100,100);
    /* rgba */
    background-color: rgba(100,100,100,0.2);
}
```
The `rgba` rule is just ignored for unsupported browsers, so the fallback rule will be used instead in that situation. If the browser does support `rgba`, the `rgba` rule will take precedence over the fallback rule only if it's specified after it (latter rules take precedence).

### HSL and HSLA
CSS3 introduces a way to specify colors using HSL (hue, saturation, and lightness).

Lightness is not the same as brightness. Zero lightness is pure black, 100% lightness is pure white, and 50% lightness is neutral. Lightness can add both white and black while brightness only conrols how much black is added. Lightness is sometimes referred to as "luminosity".
```css
p {
    /*
        First value is hue. Value ranges from [0,360].
        This single value covers the whole of RGB.

        Second value is saturation percentage.

        Third value is lightness percentage.
    */
    background-color: hsl(0,0%,78%);
}
```

There's also `hsla` which adds alpha similar to `rgba`. Here though, "alpha" refers to transparency. 100% alpha means completely transparent (non-opaque), and 0% alpha means completely non-transparent (opaque).
```css
p {
    background-color: hsla(0,0%,78%,50%);
}
```

Fallback colors can also be specified for `hsl` and `hsla`, similar to `rgba`.
```css
p.one {
    background-color: rgb(0,0,0);
    background-color: hsl(0,0%,78%);
}

p.two {
    background-color: rgb(0,0,0);
    background-color: hsla(0,0%,78%,50%);
}
```
