# BUGS

This are Bugs which I encountered during usage of the plugin

## Bug 1: Notes are moved even if they are a Folder Note them selfs.
```
davidwitulla@MacBook-Pro-5 1 Projects % tree .
.
├── 1 Projects.md
├── Project A
│   └── Project A.md
└── Project B
    └── Project B.md
```
with Project A contains:
# Project A.md
---
up: "[[1 Projects]]"
tags: []
Links: []
aliases: []
topic:
---

! THIS NOTE SHOULD NOT BE MOVED


After the execution of the "MOC Sync: Sync all Notes to MOC Folders Command"
```
davidwitulla@MacBook-Pro-5 1 Projects % tree .
.
├── 1 Projects.md
├── Project A
├── Project A.md
├── Project B
└── Project B.md
```

### The same problem occured here:

.
├── 2 Area.md
├── Money MOC
│   ├── Money MOC.md
│   └── Money Topic Note.md
└── Personal MOC
    ├── Another Personal Note.md
    ├── Personal MOC.md
    └── Test Nested.md

which was moved to

davidwitulla@MacBook-Pro-5 2 Area % tree .
.
├── 2 Area.md
├── Money MOC
│   └── Money Topic Note.md
├── Money MOC.md
├── Personal MOC
│   ├── Another Personal Note.md
│   └── Test Nested.md
└── Personal MOC.md

Because "Money MOC.md" and "Personal MOC.md" contain "2 Areas" in their up link. They should not be moved.


Solution:
- A Note should never be moved if its name is identical to its directory name

## Bug 2: Template Notes are moved
```
davidwitulla@MacBook-Pro-5 Extras % pwd
/Users/davidwitulla/Documents/moc-sync-dev/Extras
davidwitulla@MacBook-Pro-5 Extras % tree .
.
├── Bases
│   ├── MOC Base.base
│   └── RecentlyModified.base
└── Templates
    └── Template Inbox.md

3 directories, 3 files
```

The Template Inbox Note contains:
```
---
up: "[[0 Inbox MOC]]"
tags: 
Links: 
created: <% tp.date.now("YYYY-MM-DD") %>
aliases: 
Topic:
---
```

Even tho it should never be moved

Solution:
Add a filter which the user can change in the settings, which directories should be excluded from the move command. Defaults to "Templates". It is also possible to explicitly disable auto-sync for all notes with "Templates" in the name. A Regex is possible. 