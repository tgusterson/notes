# Markdown Cheatsheet

---

## Headings

```
# H1
## H2
### H3
#### H4
```

---

## Text Formatting

```
**bold**
*italic*
~~strikethrough~~
`inline code`
```

Renders as: **bold**, *italic*, ~~strikethrough~~, `inline code`

---

## Lists

```markdown
- unordered
- list
  - nested (2 spaces)

1. ordered
2. list
   1. nested (3 spaces)
```

---

## Links & Images

```markdown
[link text](https://example.com)
[link with title](https://example.com "hover title")

![alt text](image.png)
![alt text](image.png "title")
```

---

## Code

Inline: `` `code` ``

Fenced block (specify language for syntax highlighting):

````
```javascript
const x = 1;
```
````

---

## Blockquotes

```markdown
> This is a quote.
>
> Multiple paragraphs.
>> Nested quote.
```

---

## Tables

```markdown
| Column A | Column B | Column C |
|----------|----------|----------|
| cell     | cell     | cell     |
| cell     | cell     | cell     |

# Alignment
| Left     | Center   | Right    |
|:---------|:--------:|---------:|
| text     | text     | text     |
```

---

## Horizontal Rule

```markdown
---
```

---

## Task Lists (GitHub Flavored)

```markdown
- [x] Done
- [ ] Not done
```

---

## Escaping

Prefix special characters with `\` to render them literally:

```
\* \_ \` \# \[ \] \| \~
```
