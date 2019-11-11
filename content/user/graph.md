---
title: "Details: Annotation"
date: 2019-02-11T19:30:08+10:00
draft: false
weight: 5
summary: Starting with LEL graph feature
---

As previously mentioned LeL uses some annotations inside the markdown notes to create an other structured layer.
All of these annotations are explained here in detail.

### Nodes

![pic](/user/pic_node_single.png)

In order to create a node, both `@name` and `@entity` need to be set in the note:

````
```
@name example.com
@entity server
```

# Example.com
...information...
````

Beside the `server` value other different entities can be used out of the box:

```
database, node, globe, cserver, site, user, client, dc , win, server
relation, info
```

Additionally you can use your own icons via the `@icon <url>` annotation

```
@icon https://editor.l3l.lol/favicon.png
```

Similar to `@tags` you can specify multiple names for the node. But in constrast please keep them **unique**!
This is necessary to link nodes together.

### Relations

Linking nodes it very easy through the `@ref` annotation.

```
@name other.example.com
@entity server
@ref (this)->[connect to]->(example.com)
@ref (example.com)->[respond to ]->(this)
```

![pic](/user/pic_nodes.png)

The syntax for references can be seen here. The current node can be specified with the `this` keyword inside a reference.

```
@ref (subject)->[action]->(object)
```

Now image you compromised a system and collect different information: loot, logs what you did, infos about the system and creds. If everything is visually linked to the note then sooner or later the graph would explode ;)

Fortunately you can link information for one note, without creation one. AS can be seen in the next example the entity `info` indicates that the current document is only an information for a specific note, which can be connect in the short syntax `@ref <name>`.

```
@entity info
@ref other.example.com
@name other.example.com.mimikatz
```

Afterwards when the related note is selected the information bar on the right appear and displays all reference documents.

![pic](/user/pic_nodes_info.png)

If you click on the reference link the note opens.

**Note**: Better support for the graph will be added in v0.0.2

# Metatag details

#### @name

> Id parameter to reference the entity.

Names can be used to identify the entity. Multiple names can be set, which can be later referenced by other notes. Please chose unique names or use the complete notepath as the final ID.

```
@name <name>[, ?<names>]
@name example.com, 127.0.0.1, entrypoint-php-system, internal.hostname
@name recon-1
```

#### @ref

> Link between entities

Creates a connection between entities. The keyword `this` can be used, either as the sender, message or recipiant, based on its own @entity.

```
@ref (<node>)->[<action>]->(<node>)
@ref <node>

@ref (this)->[connects]->(other-node)
@ref (node-b)->[connect-to]->(this)
@ref (node-c)->[likes]->(node-d)

# only if @entity relation
@ref (node-a)->[this]->(node-b)

# only if @entity info
@ref parent-node
```

#### @tags

> Give your notes some context and group them

Tags can be used to group notes and give them context. It is helpful for later searches. Tags are separated by , can be have (almost) multiple depth layers.

```
@tags tag1
@tags tag2, tag3, tag4
@tags multi/path/tag/are, also/possible,
```

#### @todo

> Indicates the start of a todo list

connect a todo with a super topic and create todos seperated by newlines. Todos can be define as the todo.txt standard and can contain projects, tags and times and other information. Please see the todo section for additional details.

```
@todo topic-for-todo
task 1
task 2
task 3

@todo other-topic                                                       topic 1
```

#### @icon

> Lets you specify your own icon

Chose your own icons for your entities

```
@icon <url>
@icon http://example.com/icon/info.svg
```

#### @entity

> Specifiy which entity a note should be.

```
@entity <type>
types:

@entity info
# defines the relationship between nodes.
@entity relationship

```

**types**

```
database, node, globe, cserver, site, user, client, dc , win, server
```

#### @label

> Graph label for node

Label can be used to display the node in the graph. Labels can be used multiple times.

```
@label <display>
@label display-name
```
