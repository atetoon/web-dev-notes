# CSS

## Stylesheet Types

| Type | How | Best Practice? |
| --- | --- | --- |
| Inline | `style` attribute on HTML tag | ❌ No |
| Internal | `<style>` inside `<head>` | ❌ No |
| External | `.css` file linked via `<link>` | ✅ Yes |

```html
<!-- Inline -->
<p style='color: red;'>Hello</p>

<!-- Internal -->
<head>
  <style>
    p { color: red; }
  </style>
</head>

<!-- External -->
<link href='./style.css' rel='stylesheet'>
```

## Selectors

```css
p { color: blue; }                        /* type */
.box { color: red; }                      /* class */
#main { color: green; }                   /* ID */
input[type="text"] { border: 1px; }       /* attribute */
* { margin: 0; padding: 0; }               /* universal — reset */
a:hover { color: red; }                    /* pseudo-class */
```

## Specificity

```
ID > Class > Type
```

```css
p { color: blue; }       /* weakest */
.text { color: green; }
#para { color: red; }    /* strongest — wins */
```

## Selector Combinations

```css
/* Chaining — div with class box only */
div.box { background: yellow; }

/* Descendant — p inside div only */
div p { color: purple; }

/* Multiple — same style to all */
h1, p, .box { font-family: Arial; }
```

## Classes vs IDs

```html
<!-- Classes — reusable -->
<div class="box"></div>
<div class="box"></div>  <!-- ✅ allowed -->

<!-- IDs — unique -->
<div id="main"></div>
<div id="main"></div>    <!-- ❌ wrong -->
```

Multiple classes on one element:

```html
<p class="red bold">Hello</p>
```

```css
.red { color: red; }
.bold { font-weight: bold; }
/* both apply */
```

## Text Styling

| Property | Purpose | Example |
| --- | --- | --- |
| `font-family` | Typeface | `font-family: Arial;` |
| `font-size` | Text size | `font-size: 20px;` |
| `font-weight` | Thickness | `font-weight: bold;` |
| `text-align` | Horizontal position | `text-align: center;` |
| `color` | Text color | `color: white;` |
| `background-color` | Color behind text | `background-color: black;` |
| `opacity` | Transparency (0–1) | `opacity: 0.5;` |
| `background-image` | Image behind element | `background-image: url("img.jpg");` |
| `!important` | Force override (avoid) | `color: red !important;` |

---
## Related
- [[02 - HTML]]
- [[12 - DOM]]
