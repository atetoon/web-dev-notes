# HTML Forms

## Form Structure

```html
<form action="/submit" method="POST">
</form>
```

| Attribute | Purpose |
| --- | --- |
| `action` | Where form data goes |
| `method` | How data is sent (`GET` / `POST`) |

## Label + Input

```html
<label for="username">Username</label>
<input id="username" name="username" type="text">
```

Rule: `for === id`. Clicking the label focuses the input.

## id vs name vs value

```html
<input id="username" name="username" value="Captain">
```

| Attribute | Purpose |
| --- | --- |
| `id` | Locator (CSS, JS, Label) |
| `name` | Key sent to server |
| `value` | Actual data |

Form submits: `username=Captain`

## Input Types

### Text

```html
<input type="text">
```
Used for: Username, Name, City

### Password

```html
<input type="password">
```
Displays: `********`

### Number

```html
<input type="number" min="1" max="10" step="1">
```

| Attribute | Purpose |
| --- | --- |
| `min` | Smallest value |
| `max` | Largest value |
| `step` | Increment amount |

### Range (Slider)

```html
<input type="range" min="0" max="100" step="1">
```
Used for: Volume, Brightness, Ratings

### Checkbox

```html
<input type="checkbox" name="topping" value="cheese">
```
✅ Multiple selections allowed

### Radio Button

```html
<input type="radio" name="gender" value="male">
```
✅ One selection only — same `name` = same group.

### Dropdown

```html
<select name="food">
  <option value="pizza">Pizza</option>
  <option value="burger">Burger</option>
</select>
```
Server receives: `food=pizza`

### Datalist

```html
<input list="cities">
<datalist id="cities">
  <option value="Tokyo">
  <option value="Paris">
</datalist>
```

| Select | Datalist |
| --- | --- |
| Must choose option | Can choose or type own value |
| No search | Search available |

### Textarea

```html
<textarea id="comment" name="comment" rows="5" cols="30">
Write here...
</textarea>
```
Used for: Comments, Reviews, Feedback, Blog Posts

### Submit Button

```html
<input type="submit" value="Send">
```

## Validation

### Required

```html
<input required>
```

### Min / Max

```html
<input type="number" min="1" max="10">
```

### Minlength / Maxlength

```html
<input minlength="3" maxlength="15">
```

### Pattern (Regex)

```html
<input pattern="[0-9]{6}">
```

Common patterns:

```html
pattern="[0-9]{6}"       <!-- 6 digit PIN -->
pattern="[0-9]{5}"       <!-- 5 digit ZIP -->
pattern="[0-9]{14,16}"   <!-- Credit Card -->
pattern="[a-zA-Z]+"      <!-- Letters Only -->
```

### Validation Order

```
required → min/max → minlength/maxlength → pattern → Submit ✅
```

## Quick Reference

```
<form>      → Form container
<label>     → Describes input
for = id    → Connects label and input
id          → Locator
name        → Sent to server
value       → Actual data
Checkbox    → Many choices
Radio       → One choice
Select      → Dropdown
Datalist    → Searchable dropdown
Textarea    → Multiline input
Submit      → Sends form
required    → Cannot be empty
pattern     → Regex validation
```

---
## Related
- [[12 - DOM]]
- [[../01 - Web Fundamentals/02 - HTML]]
