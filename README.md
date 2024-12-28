# CSS Space Toggle Hack
Getting to grips with the CSS Space Toggle Hack...

It feels like this trick / hack _ought_ to be incredibly useful, but, so far, I can't see any way to deploy it which is more straightforward than not deploying it.

For example, here's the **CSS Space Toggle** toggling no fewer than 8 properties, including the `content` property of an `::after` pseudo-element:

## HTML
```html
<div class="square" tabindex="0"></div>
```

## CSS
```css
.square {
  --squareFocusToggle: /**/;
}  

.square:focus {
  --squareFocusToggle: initial;
}

.square {
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

.square {
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
  transition: all 1.8s ease-out;
  background-clip: padding-box;
  box-sizing: border-box;
  cursor: pointer;
}

.square::after {
  content: var(--contentBlur, var(--contentFocus));
  position: absolute;
  inset: 0;
  display: grid;
  place-content: center;
}
```
