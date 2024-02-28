---
tags: 
    - test
    - dataview
sampleNumber: 3
sampleBoolean: true
---
## Beginning thoughts
### What even is it?
Let's first think about what Dataviews do.  The plugin indexes your notes and looks for metadata (not the full note text).  You can then use/combine/etc. this metadata to display tables/lists of notes that you can use in various ways.  The plugin does ==not== modify your notes.  Rather, it aggregates the metadata about the notes and let's you display that in curious ways.

### How do we get metadata into our notes?
There's 3 ways:
#### Frontmatter
This is the metadata as seen at the top of every file/note.  See above on this note for the 'tags' metadata I added.  Tags are a common [[Obsidian]] tool, but you're not limited to this.  Any key/value pair will work (even YAML lists, like the tags above).  For example, if I was taking notes about a book, I could put an 'author' key and a 'Stephen King' value in there.  That would allow me to query for all notes with an author key whose value is 'Stephen King'.  Several data formats will work, like strings in this example, but also numbers like `rating: 2` or even objects:
	```yaml
	person:
	    name: 'bob'
	    age: 21
	```
Then, in a Dataview query you can use `WHERE person.age >= 18` to weed out the minors ;)

#### Inline
You can add metadata inline using a 'Key:: Value' syntax anywhere in your note.
On an individual line with no content before it you can do it like so:
```yaml
Basic Field:: Some random Value
**Bold Field**:: Noice!
```
Every bit of data after the double colon '::' is the value of the key until the next line break.  Notice how we used spaces in the 'Key' parts above?  This is technically translated by Dataview into a sanitized version of the key.  (in this case, 'basic-field' and 'bold-field')

If you want to embed metadata directly in a sentence, or put multiple bits on the same line, use the bracket syntax:
```yaml
I give this movie [rating:: 2 snaps in 'z' formation]!  it was [mood:: aight]
```

#### Implicit
##### Files
Out of the box, Dataview comes with several metadata bits that are automatically indexed for various things.  Notably, files have a [Huge List](https://blacksmithgu.github.io/obsidian-dataview/annotation/metadata-pages/)of things that you can query without any manual input by you.  Some are file.cday (when the file was created) file.folder (duh)

##### Lists/Tasks
There are also some [implicit metadata bits](https://blacksmithgu.github.io/obsidian-dataview/annotation/metadata-tasks/) added to lists of items or tasks.  You can also explicitly add metadata using the Inline method mentioned above (with brackets/double colons)



## Let's do a dataview!
 > [!info]- Check out the code block below:
 > 
>```` 
>```dataview
>LIST
>``` 
>````
>In this block, we started off by using Dataview Query Language (DQL) to create a code block that searches metadata on our notes.  This one opens a code block with triple backticks immediately followed by the word 'dataview'.  Then on the next line, we create our query.  In this case we're only using 'LIST' to have dataview retrieve all filenames of all files (with no 'WHERE' clause in effect).  This list will grow dynamically as the number of notes we create increases.  Snazzy!  See the results of the above Dataview Query below:
>```dataview
>LIST
>```



### Filters
You can further filter the results from a Dataview Query by including a 'FROM' and 'WHERE' clause.
These things work a lot like SQL as in the view below:

````
```dataview
LIST
FROM #dataview 
```
````

This query will pull all notes that are tagged with '#dataview' (That's like a 'FROM' in SQL.  As of this writing, only this current note fits the query)
See the results in the view below
```dataview
LIST
FROM #dataview 
```
Try sprinkling an 'AND' or an 'OR' in there like so:
```dataview
LIST
FROM #template or #dataview 
```

You can even use 'WHERE' statements to further filter, though, I'm not demonstrating it here because I'm in the early stages of testing this shiz out...


### Tables
You aren't limited to 'Lists' like in the examples above.  You can also create tables of data like in the example below:
```dataview
TABLE file.cday AS CreateDate, file.tasks.text as Tasks
FROM #daily
```


You can even sort the results that show in the table by adding a `sort` statement
```dataview
table file.ctime
sort file.ctime
```

---

### Task views
You can create a task view that will display checkboxes (tasks) and their metadata.  See the list below.  It retrieves all Tasks from notes tagged '#daily' that are incomplete:

```dataview
TASK
FROM #daily 
WHERE !completed
```

And now a list of completed tasks (from any note, with any tag):
```dataview
TASK
WHERE completed
```


And finally one that grabs only tasks with a 'type' value of 'purchase'
```dataview
TASK
WHERE type = purchase
```

---
On the one below, we're finding any notes that have unfinished tasks in them.  If you want to get more complex, we're going to have to do some fancy function calling.  (We'll get back to that)
```dataview
LIST
WHERE any(file.tasks, (t) => !t.completed)
```


## Query Language
### Dataview query language (DQL)
Obvs, looking at the above examples, you can create a block query using the code block format (triple backticks) and adding the 'dataview'  type, like so:
````
```dataview
<here is some query stuff>
```
````

### Inline query
You can also just run a query inline in a sentence using a single-backtick and the 'Inline Query' prefix you specified in the options for this plugin (in my case it's as below)
```
`dv:`
```

This inline format lets you do some `dv: date(today)` fancy things (you can see them if you move your cursor over the date section in this sentence)

These inline queries only display one value (not a list or table).  They act on one thing.  If you use the `this` keyword, you can access metadata about the current file.  See below:
````
`dv: this.file.name`
````
Renders this note's filename: `dv: this.file.name`

```
`dv: this.file.mtime`
```
Will render this note's last Modify Time: `dv: this.file.mtime`

```
`dv: this.sampleNumber`
```
Will render the value of the Frontmatter Key 'sampleNumber': `dv: this.sampleNumber`

It's also possible to call out other notes by using the link to them `[[Obsidian]]` and appending the dot notation to it, as below, to see the create date of the Obsidian file:
```
The [[Obsidian]] note was created on: `dv: [[Obsidian]].file.cday`
That was like `dv: [[Obsidian]].file.cday - date(today)` ago!
```
The [[Obsidian]] note was created on: `dv: [[Obsidian]].file.cday`
That was like `dv: [[Obsidian]].file.cday - date(today)` ago!

**Now that's fancy!**

### Block Dataview JS
There's a JavaScript API you can use too.  It let's you do some fancy shiz also, like some arbitrary and complex logic for queries and views.
You can pull this off by making a block of code and giving it the 'dataviewjs' type as below:
````
```dataviewjs
let pages = dv.pages("#daily");
for (let p of pages) {
	dv.header(3, p.file.link)	
}
```
````
```dataviewjs
let pages = dv.pages("#daily");
for (let p of pages) {
	dv.header(5, p.file.link)	
}
```

### Inline Dataview JS
Besides doing it in a block as above, you can also inline that stuff with the default JS Inline Prefix, ```
```
`$=`
```

This allows you to harness the full capabilities of the DataviewJS API inline to do shiz like the following:
```
`$= dv.current().file.mtime`
```
Which renders out to be: `$= dv.current().file.mtime`
