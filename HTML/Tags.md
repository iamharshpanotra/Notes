### **What are HTML Tags?**

**HTML (HyperText Markup Language)** uses **tags** to structure and display content on a web page.

### **Structure of a Tag**
Most HTML tags come in pairs:

```html
<tagname>Content</tagname>
```

- The **opening tag**: `<tagname>`
- The **closing tag**: `</tagname>`
- The **content**: Text or other elements between the tags

Example:
```html
<p>This is a paragraph.</p>
```

### **Types of Tags**

1. **Container Tags (with opening and closing)**
   - These wrap content.
   - Example:
     ```html
     <h1>Hello</h1>
     <div>Some content</div>
     ```

2. **Empty or Self-closing Tags (no content inside)**
   - These don't have a closing tag.
   - Example:
     ```html
     <br>  <!-- Line break -->
     <img src="image.jpg" alt="Image"> <!-- Image tag -->
     ```

---

### **Common HTML Tags**

| Tag | Purpose |
|-----|--------|
| `<html>` | Root of an HTML document |
| `<head>` | Contains meta info, styles, links |
| `<title>` | Title of the page (shows in tab) |
| `<body>` | Main content of the page |
| `<h1>` to `<h6>` | Headings (largest to smallest) |
| `<p>` | Paragraph |
| `<a>` | Hyperlink |
| `<img>` | Image |
| `<div>` | Division/container |
| `<span>` | Inline container |
| `<ul>` / `<ol>` | Unordered / Ordered lists |
| `<li>` | List item |
| `<table>` | Table |
| `<tr>` | Table row |
| `<td>` | Table cell |
| `<form>` | Form for input |
| `<input>` | Input field |
| `<button>` | Button |

---

### **Attributes in Tags**
Tags can have **attributes** to add more information.

Example:
```html
<a href="https://example.com" target="_blank">Visit Example</a>
```
- `href` is the URL to go to
- `target="_blank"` opens the link in a new tab

---