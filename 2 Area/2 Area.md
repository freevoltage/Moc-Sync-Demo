---
up: "[[Home]]"
aliases:
  - Areas MOC
---
```base
filters:
  and:
    - file.inFolder(this.file.folder)
    - file.name.endsWith("MOC")
    - note.up == this.file
formulas:
  Backlinks: file.backlinks.length
views:
  - type: table
    name: MOCs in this folder
    order:
      - file.name
      - formula.backlinks

```
