---
tags:
  - obsidian
  - testing
---


1. This is an ordered list
2. It auto adds the number for each subsequent line
3. ==Note:== Use double equal signs to highlight <- like we did on the first word in this sentence
*Double-Enter will exit out of the auto-numbering of ordered lists*

### Images are fun!
![Aneal|120](https://anealkhimani.com/assets/img/avatar2.jpg)

### Can we make a checklist?  WE CAN!
- [ ] Aneal is special
- [ ] Aneal is the best
- [x] I wake up, piss excellence


### Errbody to the TABLE!
| **First** | **Last** | Rank   |
| --------- | -------- | ------ |
| Bob       | Jones    | Master |
| Susan     | Jenkins  | Padwan |
| Mary      | Smith    | Master |
| Another   | Name     | Knight |




Let's link to our daily note from a few days ago! [[2024-02-09]]
This is silly, but I guess it means something.

```dataview
TABLE file.cday AS "Created", file.tags AS "Tags"
FROM "Daily"
```

The above block is created because of a Dataview

### Callouts
This could be handy if you use it
>[!question]- What the hell is one?
>This is a block quote.  The first line has an open bracket with an exclamation point and the word 'question' followed by a closing bracket and a minus sign.  This creates a callout that's foldable (and defaults to folded with a minus sign, unfolded with a plus sign).  There are several callout 'types'.  Question is one of them.  I think this adds to styling


### Links and shiz
You can link internally to another file (note) by using double square brackets.
For example, this like [[Obsidian]] points to the note titled Obsidian.md

If you want the link text to be different than the title of the file (like Obsidian above) just follow the link text in the square brackets with a | and the new 'alias' like this [[Obsidian | some other link]]

You can even link to individual header sections within files by suffixing w/ a hash and the name of the block like [[README#Errbody to the TABLE! | this one]] which links to the table section above in this note...  Crafty!


