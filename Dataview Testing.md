---
tags: 
    - test
    - dataview
---

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
