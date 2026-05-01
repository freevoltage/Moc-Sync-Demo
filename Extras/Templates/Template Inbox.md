---
up: "[[0 Inbox MOC]]"
tags: 
Links: 
created: <% tp.date.now("YYYY-MM-DD") %>
aliases: 
Topic:
---
# [[<% tp.file.title %>]]

<% tp.file.cursor() %>

## Resources
- 


---
## Outgoing Links
```dataview
list
from outgoing([[]])
where file.name != this.file.name
```

## Linked Mentions
```dataview
table file.link as "Backlinks"
from ""
where contains(file.outlinks, this.file.link) and file.name != this.file.name
```

