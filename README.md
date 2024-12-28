# CSS Space Toggle Hack
_Getting to grips with the CSS Space Toggle Hack..._

**Working Example:** https://rouninmedia.github.io/css-space-toggle-hack/

_________

I first came across the **CSS Space Toggle Hack** halfway through 2021 and, while I could follow the syntax, I could barely get my head around it.

I've come back to it recently, now that I'm learning about the forthcoming `if()` function in CSS and it's much clearer to me how it all works.

_Hint: although it's called the **Space Toggle**, the `initial` value of the custom property is **as important** as the `whitespace` value.

It _feels_ like this trick / hack ought to be incredibly useful.

But, so far, (neither in May 2021 nor now in late December 2024) I cannot see any way to deploy it which works better than _not_ deploying it.

For example, here's the **CSS Space Toggle** toggling no fewer than _8 properties_ simultaneously - including the `content` property of an `::after` pseudo-element:

## HTML
```html
<div class="square1" tabindex="0"></div>
```

## CSS
```css
.square1 {
  --squareFocusToggle: /**/;
}  

.square1:focus {
  --squareFocusToggle: initial;
}

.square1 {
  --backgroundColorBlur: var(--squareFocusToggle) rgb(255, 127, 0);
  --backgroundColorFocus: rgb(255, 0, 0);
  
  --colorBlur: var(--squareFocusToggle) rgb(255, 255, 255);
  --colorFocus: rgb(255, 255, 0);
  
  --fontSizeBlur: var(--squareFocusToggle) 14px;
  --fontSizeFocus: 18px;
  
  --textStrokeBlur: var(--squareFocusToggle) 2px rgba(0, 0, 0, 0.5);
  --textStrokeFocus: 4px rgba(0, 0, 0, 0.5);
  
  --textTransformBlur: var(--squareFocusToggle) uppercase;
  --textTransformFocus: capitalize;
  
  --contentBlur: var(--squareFocusToggle) 'Click me';
  --contentFocus: 'Click outside me';
  
  --borderBlur: var(--squareFocusToggle) 9px solid rgb(255, 0, 0);
  --borderFocus: 3px solid rgb(0, 127, 0);
  
  --borderRadiusBlur: var(--squareFocusToggle) 0%;
  --borderRadiusFocus: 50%;
}

.square1 {
  position: relative;
  width: 100px;
  height: 100px;
  line-height: 1.5;
  font-family: sans-serif;
  font-size: var(--fontSizeBlur, var(--fontSizeFocus));
  font-weight: 700;
  text-align: center;
  text-transform: var(--textTransformBlur, var(--textTransformFocus));
  color: var(--colorBlur, var(--colorFocus));
  -webkit-text-stroke: var(--textStrokeBlur, var(--textStrokeFocus));
  paint-order: stroke fill;
  background-color: var(--backgroundColorBlur, var(--backgroundColorFocus));
  border: var(--borderBlur, var(--borderFocus));
  border-radius: var(--borderRadiusBlur, var(--borderRadiusFocus));
  transition: all 1.2s ease-out;
  background-clip: padding-box;
  box-sizing: border-box;
  cursor: pointer;
}

.square1::after {
  content: var(--contentBlur, var(--contentFocus));
  position: absolute;
  inset: 0;
  display: grid;
  place-content: center;
}
```

It works and it's very clever. But, also, it feels excessively complex, next to more conventional CSS, which does exactly the same thing:

## HTML
```html
<div class="square1" tabindex="0"></div>
```

## CSS
```css
.square2 {
  position: relative;
  display: inline-block;
  width: 100px;
  height: 100px;
  margin-right: 12px;
  line-height: 1.5;
  font-family: sans-serif;
  font-size: 14px;
  font-weight: 700;
  text-align: center;
  text-transform: uppercase;
  color: rgb(255, 255, 255);
  -webkit-text-stroke: 2px rgba(0, 0, 0, 0.5);
  paint-order: stroke fill;
  background-color: rgb(255, 127, 0);
  border: 9px solid rgb(255, 0, 0);
  border-radius: 0%; 
  transition: all 1.2s ease-out;
  background-clip: padding-box;
  box-sizing: border-box;
  cursor: pointer;
}

.square2::after {
  content: 'Click me';
  position: absolute;
  inset: 0;
  display: grid;
  place-content: center;
}

.square2:focus {
  color: rgb(255, 255, 0);
  font-size: 18px;
  text-transform: capitalize;
  -webkit-text-stroke: 4px rgba(0, 0, 0, 0.5);
  background-color: rgb(255, 0, 0);
  border: 3px solid rgb(0, 127, 0);
  border-radius: 50%;
}

.square2:focus::after {
  content: 'Click outside me';
}
```
_________

## Current Thoughts

It feels like the second example (using conventional CSS) is both:

 1. Shorter
 2. Easier to read and understand

________

On that basis I'd be really keen to see an example of the **CSS Space Toggle Hack** which enables an effect which would be harder to understand / much more verbose / impossible to write using conventional CSS.

________

## Further Reading:

- <a href="https://css-tricks.com/the-css-custom-property-toggle-trick/" target="_blank">https://css-tricks.com/the-css-custom-property-toggle-trick/</a>
- <a href="https://github.com/propjockey/css-sweeper#css-is-a-programming-language-thanks-to-the-space-toggle-trick" target="_blank">https://github.com/propjockey/css-sweeper#css-is-a-programming-language-thanks-to-the-space-toggle-trick</a>
- <a href="https://lea.verou.me/blog/2020/10/the-var-space-hack-to-toggle-multiple-values-with-one-custom-property/" target="_blank">https://lea.verou.me/blog/2020/10/the-var-space-hack-to-toggle-multiple-values-with-one-custom-property/</a>
