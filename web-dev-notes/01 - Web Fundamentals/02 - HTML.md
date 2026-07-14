# HTML

## Basic Tags

| Tag | Purpose |
| --- | --- |
| `<strong>` | Bold text |
| `<em>` | Italic text |
| `<h1>` to `<h6>` | Headings |
| `<div id="xyz">` | Division/container |
| `<p>` | Paragraph |
| `<br>` | Line break (single tag) |

## Lists

```html
<!-- Unordered List -->
<ul>
  <li>Item</li>
</ul>

<!-- Ordered List -->
<ol>
  <li>Item</li>
</ol>
```

## Images & Links

```html
<!-- Basic image -->
<img src="URL" />

<!-- Image with alt text -->
<img src="#" alt="A field of yellow sunflowers" />

<!-- Clickable image -->
<a href="#id"><img src="link" /></a>
```

## Key Rules

1. `<!DOCTYPE html>` must always be the first line
2. All HTML code goes inside `<html>`
3. Page info (title etc.) goes inside `<head>`
4. Page title set using `<title>` inside `<head>`
5. Title appears in the browser tab
6. `<a>` tags are used to link internal/external pages
7. Use `<a href="#id">` + `id` attribute to jump to sections
8. Whitespace makes code readable — doesn't affect browser rendering
9. Indentation shows parent-child relationships
10. Comments syntax: `<!-- comment -->`

---
## Related
- [[03 - CSS]]
- [[13 - Forms]]
- [[12 - DOM]]
