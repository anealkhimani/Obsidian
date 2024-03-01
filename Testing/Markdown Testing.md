# Heading 1
## Heading 2
etc.

_italics can be achieved with an underscore surrounding the text_
*A single asterisk will do it too* ^54d81d

__bold is done with double undercore or double asterisk__
~~Double Tilde strikes through~~

==Double Equal Signs will highlight==

### Lists
Unordered lists use hyphen and space (or asterisk or plus sign)
- Something
- something else
- more
+ list item
+ more list items
* list item
* another

Ordered lists begin with numbers and periods followed by a space
1. Find Sarah Connor
2. Find John Conner
3. Get to the Choppa

And checklists?  use `Ctrl + l`
- [ ] good
- [ ] better
- [ ] best [type::purchase]


### Links
`[[ ]]` double brackets creates a link to another note in your vault.  You can suffix the note name with a space, `|` pipe character, space and type an alias to change the text value of the link like the one below:
[[Dataview Testing | something here]]

Headers in the same page
You can link to an individual _heading_ section in a file by suffixing your link with a hash and then selecting the actual heading text.  It get's all breadcrummy if you look at the reading view.
[[Markdown Testing#Links]] 
Yes, you can alias these too with a pipe like we did in the first example.
Here's the same link aliased in a super appropriate way:
[[Markdown Testing#Links|Doobers make my taco pop]]

Blocks in the same page
If you're really fancy, you can link to an individual _block_ of text in a file with the caret character `^` like so:
[[Markdown Testing#^54d81d]]
Let's try to alias that shiz
[[Obsidian#^ddc44b|Obsidian Stuff]]
