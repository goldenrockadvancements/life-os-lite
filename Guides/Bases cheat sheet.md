---
type: guide
---
Every list, board and dashboard in this vault is a **Base**: Obsidian's built-in database. A base is a saved search over your notes' **properties** (the fields at the top of each note). Nothing is copied: change a note and every base updates.

> [!tip] The 30-second version
> - Open any file in `Bases/` to see all its views (tabs across the top).
> - Click a column header to sort. Use **Filter** to narrow, **Group** to group, **Properties** to add columns.
> - Changes you make in the toolbar are saved into the `.base` file, so they stick.

## Add a new item
1. Press `Ctrl/Cmd + N` for a new note, give it a title.
2. Type `/` and pick **Insert template** (or use the command palette: `Ctrl/Cmd + P` > "Templates: Insert template").
3. Pick the matching template. The note gets the right `type`, so it shows up in the right base.
4. Move it to its folder (drag it in the file list), or leave it anywhere: the bases find notes by `type`, not by folder.

Most bases also have a **New** button in their toolbar.

## Properties you'll see
| Kind | Example | Tip |
|---|---|---|
| Text | `status: Active` | Keep the spelling exact, since views match on it. |
| Number | `amount: 1200` | No currency signs or commas. |
| Date | `due: 2026-11-01` | Click the field for a date picker. |
| Link | `client: "[[Brightside Bakery]]"` | Type `[[` in the field to search your notes. |
| Checkbox | `paid: true` | Click to tick. |

## Change a view
- **Show another column:** Properties > tick it.
- **Filter a view:** Filter > add a rule such as `status is not Done`.
- **Edit by hand:** open the `.base` file in source mode (the `...` menu > *Source mode*). It's plain YAML. The official guide: https://help.obsidian.md/bases

## Formulas used here
Bases can compute columns. Examples from this vault:
```yaml
days_left: 'if(due, (date(due) - today()).days, "")'
weighted: 'if(value, value * probability / 100, 0)'
```
Dates subtract into a duration, so read `.days` from it before doing math.

## Embedding a view in a note
`![[Projects.base#Active]]` shows the **Active** view of the Projects base inside any note. The Home note is built this way.
