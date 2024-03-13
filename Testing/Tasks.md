---
tags:
    - test
---


## Some considerations
This community plugin comes with some built-in goodness.  There's a Modal that you can use to create tasks in a special way, with lots of options.  You can either toggle it with the Command Palette `Tasks: Create or Edit` or with the hotkey combo I created for this purpose `Ctrl + Shift + t`
Why not try it in the section below?
I opted _not_ to use a global identifier with the tasks.  I'm told in the documentation that this will make the Tasks Plugin track all items in all files that utilize the default checkbox workflow as tasks.  If I _had_ used one, you'd need to create tasks to be tracked by this plugin by utilizing that special global identifier.

### Below is a list of tasks.  We're going to try to use the tasks plugin to do fun stuff

- [x] Get busy with the stuff  [completion:: 2024-03-13]
- [x] Walk the dog  [due:: 2024-03-05]  [completion:: 2024-03-13]
- [x] Try the veal, and the hotkey shortcut  [completion:: 2024-03-13]
- [x] Use the Dataview Format  [priority:: high]  [due:: 2024-03-11]  [completion:: 2024-03-13]
- [x] On restart and after a setting change, now there's create dates automatically added.  But I'm not seeing it happen  [completion:: 2024-03-13]
- [x] Looks like you have to use the modal to add an automatic Created Date  [created:: 2024-03-04]  [completion:: 2024-03-13]
- [x] #purchase Buy some chickens with poison interlaced with the meat  [due:: 2024-03-10]  [completion:: 2024-03-13]



> [!info] 
> See how the tasks above look normal?  They display fancy icons and emojis when used in a task view, as below



## Queries
### Here is a tasks query that retrieves all tasks tracked by the plugin. 
As you can see, the ones we created up above show up in the list below.  This query also shows some links (emojis) you can use to modify the tasks, as well as a link to the page where the task was created (directly pointing to the actual task)

```tasks
```



### Here's a query wrapped in a collapsed callout
>[!check]- Due Today
>```tasks
>due today
>not done


### Query with dates or ranges of dates
Oh my, this is fancy
>[!check]- With a single date
>```tasks
>starts before 2024-03-09
>due on or before today

>[!check]- Another example
>```tasks
>due on or after today

>[!check]- Check out this range, baby
>```tasks
>happens this week

### Text Filters?
>[!check]- Filtering by header text
>This query block searches for tasks that are contained within a section that has a header with the text 'Daily TODO' (the default for my daily notes)
>```tasks
>heading includes Daily TODO

>[!check]- Heading Text filter
>```tasks
>heading does not include Daily TODO

>[!check]- How about tagged searching?
>In this one, there are two filters (one for a due date after today and another for specific tags)
>Notice that there is an implied 'AND' separating these tasks (not explicit)
>You can use any of the major boolean operators 'NOT', 'AND', 'OR', 'AND NOT', 'OR NOT' and 'XOR' if you wanna, but you have to wrap each condition in parens (:)
>
>```tasks
>tags include #purchase 

```

### Date filters?
>[!check]- No Due Dates
>```tasks
>no due date

>[!check]- Done date?
>``` tasks
>has done date
>```



