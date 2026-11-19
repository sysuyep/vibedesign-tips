Prompt

Review the choice controls in my product (switches, checkboxes, radio buttons, segmented controls, selects and dropdown menus) and decide for each one whether it is the right control. Diagnose first; change only what I approve, in my own code and components, without new dependencies.

1. Read the product
Find every place a person picks something, turns something on or off, or runs an action from a list. For each, note what it sets or does, how many options it has, how many can be picked, and whether it takes effect at once or on Save.

2. How to choose
a. Switch or checkbox: when it takes effect.
- Switch: takes effect the moment it is flipped (settings that save on their own, no Save button).
- Checkbox: one answer in a form, applied on Submit or Save.
- One thing on or off is one switch, never two radios (On / Off). If both sides have names of their own (Light / Dark), it is a choice of one: see (c).

b. Select or dropdown menu: a value or an action.
- Select: holds a value; after a pick the field shows it, and the picked option has a tick in the list.
- Dropdown menu: holds actions (Export, Duplicate, Delete). A pick runs it, the button keeps its name, and the result shows elsewhere. Menus go in page headers, toolbars and row ends, not among form fields. A split button pairs a main action with a menu of related ones (Send, with Send later and Save as draft beside it).
- Tabs switch to other content and set nothing; a segmented control sets a value or the view of the same content.

c. One of several: by the number of options.
- 2 to 5 short options: a segmented control.
- 2 to 5 that each need a line: radio buttons, stacked under the label.
- 6 or more, or labels that change or grow (names, dates, items people add): a select, so the layout never shifts.
- Hundreds (time zones, countries, people): a select with search, and a clear message when nothing matches.

d. Radio or checkbox: how many can be picked.
- Radio: exactly one, all options in view, as in a survey question. It can't be cleared once picked, so add a "none" option (Not sure yet) when that is a fair answer.
- Checkbox: any number, none included.
- Inside a select: a tick for one value, never radio circles; a checkbox before each option for several, with the picks shown as chips in the field.

3. Report before changing
Give me a table, one row per control: where, what it sets or does, the control now, the control it should be (or "right as it is"), why in one line, and anything else that changes (a Save button, a "none" option, an action moved out of a form). Flag every change in behaviour, ask about cases that could go either way, and wait for me to choose.

4. Change what I approve
Use my components, or the platform's own controls when I have none. Keep the values people already saved. Check that switches act at once and checkboxes on submit, selects show their value, menu buttons keep their name, and everything works by keyboard and screen reader.
