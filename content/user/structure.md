---
title: "Structure Layer"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 3
summary: Different Layer structure
---

The key element of LeL is to extract meta information from the notes and visualize them in a meaningful way.
This helps you to create multiple layers with ordinary plain text (markdown) files. These layers can be created via:

- File structure
- Tags
- Relations (graph)

#### File structure

The simplest structure is created by `files` inside the `notes/` structure. Similar to `Keepnote` you can freely choose your folder structure and depth.

![pic](/user/pic_nav.png)

Lel visualize the folder structures and lets you quickly search for the file you need - and with a click it opens in your favorite text editor.

For convience the navigation can be set to _sticky_ and stays on the left side or can be _pushed_ easily to the front.

**Note**: You can already see that some information is displayed in the `nav` menu (parsed names from the `@name` annotation - explained later).

#### Tags

Tags can be specified in any markdown file in the `notes/` folder with the following _annotation_:

```
# Any md-file
@tags kerberoast, ad/kerberoast
```

Multiple tags can be set with `,` as the delimiter. Each tag can have multiple levels separated through `/`.

Through the `Tags` view in the menubar you can easily search and group notes together, which contain the same tag.

![pic](/user/pic_tags.png)

**Note**: New view planned for v0.0.2

#### Relations / Graph

But the most crucial part and the main reason for **LeL** is the `graph` representation layer. You can easily create a reactive graph by including specifiy annotations inside your document. More details can be found at the [graph](/user/graph) section.

![pic](/user/pic_graph.png)

Each node is represented by **one document**. The minimal requirements to create such a node are:

```
@name example.com, 127.0.0.1
@entity server
```

Please keep in mind to choose **unique** names. Names can also be separated by `,`. Afterwards the names can be used to create relations between nodes via the `@ref` annotation.

```javascript
@name other.example.com
@entity server
@ref (this)->[connect to]->(example.com)
@ref (example.com)->[respond to]->(this)
```

**Note**: Planned for v0.0.2 is the notification, when a name is used more than once.
![pic](/user/pic_nodes.png)

More annotations details and other relations can be found in detailed [graph](/user/graph) section.
