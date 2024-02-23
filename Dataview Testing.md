---
tags: 
    - test
    - dataview
---
### Beginning thoughts
Let's first think about what Dataviews do.  The plugin indexes your notes and looks for metadata (not the full note text).  You can then use/combine/etc. this metadata to display tables/lists of notes that you can use in various ways.  The plugin does ==not== modify your notes.  Rather, it aggregates the metadata about the notes and let's you display that in curious ways.
#### How do we get metadata into our notes?
There's 3 ways:
1. Frontmatter
	This is the metadata as seen at the top of every file/note.  See above on this note for the 'tags' metadata I added.  Tags are a common [[Obsidian]] tool, but you're not limited to this.  Any key/value pair will work (even YAML lists, like the tags above).  For example, if I was taking notes about a book, I could put an 'author' key and a 'Stephen King' value in there.  That would allow me to query for all notes with an author key whose value is 'Stephen King'.  Several data formats will work, like strings in this example, but also numbers like `rating: 2` or even objects:
	```yaml
	person:
	    name: 'bob'
	    age: 21
	```
Then, in a dataview query you can use `person.age >= 18` to weed out the minors ;)

2. Inline
	You can add metadata inline using a 'Key:: Value' syntax anywhere in your note.


### Let's do a dataview!
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



### Adding Filters
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
