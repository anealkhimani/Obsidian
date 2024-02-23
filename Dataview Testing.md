---
tags: 
    - test
    - dataview
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
Out of the box, Dataview comes with several metadata bits that are automatically indexed for various things.  Notably, files have a [Huge List](https://blacksmithgu.github.io/obsidian-dataview/annotation/metadata-pages/)of things that you can query without any manual input by you.  Some are file.cday (when the file was created) file.folder (duh)


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
