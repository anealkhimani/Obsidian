# Heading 1
## Heading 2
etc. ^191944

_italics can be achieved with an underscore surrounding the text_
*A single asterisk will do it too* ^54d81d

__bold is done with double undercore or double asterisk__
~~Double Tilde strikes through~~

==Double Equal Signs will highlight==

### Lists
Unordered lists use hyphen and space (or asterisk or plus sign)[^1]
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


Linking externally.
We've done this before, but a single bracket surrounding the link text and follow that with parens, surrounding the link URL like so:
[The Googs](https://google.com)
You can tell this is external visually by the little icon to the right that points outward to an external link.


Now you can embed a link directly into a note by prefixing the bracket stuff with an exclamation point like so:

![[Markdown Testing#^191944]]

Note that here I embedded a section in the current note, and it provides some styling and a little link icon to allow you to connect directly to the linked note (which would be helpful if the embedded bit was from another note altogether.)

### Footnotes
You can create a link to a footnote thusly:
`[^1]`

By doing so, you can later create the destination of the link thusly:
`[^1]: <some stuff>`

Imma try to footnote above.  Look for the fancy bracket-number bidness to see it work.
==Keep in mind, footnotes are only viewable in _reading mode_==





[^1]: This is the referenced footnote