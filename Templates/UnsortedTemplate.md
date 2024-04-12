<%* let filetype = await tp.system.suggester(["Person", "Daily", "Computer"], ["Person", "Daily", "Computer"], false, "Which Template to use?") 
if (filetype === "Person") { _%>
<%_ tp.file.include("[[PeopleTemplate]]") _%> <% tp.file.move("/People/" + tp.file.title) _%>
<%* } else if (filetype === "Daily") { _%>
<%_ tp.file.include("[[DailyTemplate]]") _%> <% tp.file.move("/Daily/" + tp.file.title) _%>
<%* } else if (filetype === "Computer") { _%>
<%_ tp.file.include("[[ComputerTemplate]]") _%> <% tp.file.move("/Tech/" + tp.file.title) _%>
<%* } else { tp.file.cursor(1)} _%>