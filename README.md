# Classroom Layout Planner

A to-scale, drag-and-drop floor plan for arranging classroom furniture.

Open it here: https://aroble11.github.io/classroom-layout-planner/

- The planner is the single file `index.html`. It has no build step.
- Rooms and layouts are saved in each person's own browser. Nothing is sent to a server.
- `SPEC.md` describes the version being built for sharing with colleagues.

## The starter furniture chart

`furniture.csv` is a starter list of furniture. Edit it to add furniture or change a size.

**Not used at the moment.** It used to be the furniture list for each new room. Since November 2026 a new layout copies the furniture list of the layout it was made from, so nothing reads this file. It is kept in case it is wanted again.

| Column | What to put in it |
|---|---|
| `name` | The name shown in the planner, for example `Student desk (single)` |
| `shape` | `rectangle`, `round` or `kidney` |
| `width_in` | Width in inches. For a round piece, the distance across. |
| `depth_in` | Depth in inches. Ignored for round pieces. |
| `color` | `table` (teal), `chair` (gray) or `other` (purple) |
| `with_chair` | How many chairs adding one brings, as a number. Leave it as `yes` or `no` for student tables (color `table`) to get one chair per 2½ feet of width. For other furniture, `yes` means one chair. |

To edit it on GitHub:

1. Open `furniture.csv` in the repository and click the pencil icon.
2. Add a line or change a number. Keep the commas, one line per piece of furniture.
3. Click **Commit changes**.

The site picks up the change within about ten minutes.

Each layout keeps its own furniture list, which people change with the **Edit** button above a selected piece.

If a name contains a comma, put the name in double quotes.
