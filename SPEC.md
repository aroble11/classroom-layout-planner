# Classroom Layout Planner: spec for the shared version

Status: all six build steps were completed and published on 14 Nov 2026. The site is https://aroble11.github.io/classroom-layout-planner/

Where the built version differs from this spec:

- The walkway warning flags gaps from 1′ up to 2′. Pieces less than 1′ apart count as placed together and are not flagged.
- The four built-in starting layouts were removed in step 3, not step 4.
- A window that furniture can't go under gets a 1′ flagged strip in front of it. Door clear zones start 3′ deep.
- Uploading a file whose room or furniture sizes differ from the stored room creates a separate room marked "(uploaded)".
- The printed page and the look of the downloaded picture were not checked by the builder.
- 18 Nov 2026: the separate Room setup screen was removed. The room, its walls, boards, doors, windows and clear zones are all changed on the main screen. Clear zones are attached to a wall item and move with it. Fixtures can no longer be added. Student tables bring their chairs (one per 2½′ of width). `HANDOFF.md` has the details.

This spec describes the version of the planner that colleagues can use for their own classrooms. `HANDOFF.md` describes the current version, which is hard-coded to one room.

## 1. Goal

A free website where any teacher in the building can draw their room to scale, add their furniture, and try out layouts. It must stay simple enough for colleagues who are put off by busy screens.

## 2. Hosting and updates

- The planner is hosted on GitHub Pages from a public GitHub repository.
- Colleagues open one link. There is nothing to install and no account to create.
- When an update is pushed to the repository, colleagues get it the next time they refresh the page.
- The site address must not change once colleagues start using it, because saved work is tied to the address.
- Updates must never break saved work. The saved-data format carries a version number, and newer versions of the tool must keep opening older saves.

## 3. Where each person's work is kept

- Everything a colleague makes is stored in their own browser, on their own device. Nothing is sent to a server, and nobody can see or overwrite anyone else's work.
- Work in progress is saved automatically, so closing the tab does not lose it.
- Browser storage is lost if someone clears their browsing data or changes computers. The download file (section 9) is the backup.
- The "Save layout" button no longer uses claude.ai.

## 4. The two screens

| Screen | Used for | How often |
|---|---|---|
| **Arrange** | Adding, moving and rotating furniture; saving, downloading and printing layouts | Every time |
| **Room setup** | The room outline, wall features, fixed fixtures, clear zones and the furniture list | Usually once per room |

The tool opens on Arrange. Arrange shows only what is needed for arranging furniture.

A room picker at the top of the page switches between rooms.

## 5. Rooms

- A person can have several rooms. Each room has its own outline, features, furniture list and saved layouts.
- The first time someone opens the tool they see the default room: the original room from `HANDOFF.md`, with no furniture placed.
- Room actions: new room, rename, duplicate, delete (with a confirmation).

### Room outline

- The outline is drawn by clicking corners on the grid.
- Corners snap to 3″.
- All walls are at right angles. Diagonal walls are not supported.
- A wall's length can be typed in exactly, in feet and inches.
- New rooms can start from a plain rectangle (enter width and length) or from a copy of an existing room.
- **Flip room** mirrors the room left to right or front to back, along with its features and fixtures. This covers rooms on the opposite side of the hallway.

### Grid

- One grid square is 1′ × 1′, matching the floor tiles.
- Every fifth line is slightly darker, as it is today.

### Wall features

Placed along a wall in Room setup, each with a position and length:

- Whiteboard
- Window, with a setting for whether furniture can go underneath it
- Door
- Closet
- Projector screen (wall-mounted)
- Outlet
- Other, with a label the person types

### Fixed fixtures

Things that belong to the room and do not move: countertops, sinks, standalone projector screens, built-in cabinets and anything similar.

- Added in Room setup with a name and size.
- Locked on the Arrange screen, so they cannot be dragged by accident.
- Counted as obstacles by the checks and gap measurements.

### Clear zones

- Every door gets a keep-clear zone automatically.
- In Room setup a person can resize, move, delete or add clear zones.
- Furniture inside a clear zone is flagged in the checks.

## 6. Furniture

### Each room's furniture list

Each room has its own list. Every furniture type has:

- Name (student desk, teacher desk, bookshelf and so on)
- Shape: rectangle, round or kidney
- Size: width and depth, or diameter for round
- Color group: student table, chair or other (the current teal, gray and purple)
- How many the room has (optional; leave blank for no limit)
- Whether adding one also adds a chair

### Shapes

- Rectangle and round pieces are checked exactly.
- A kidney table is drawn as a kidney shape. The overlap and gap checks treat it as its surrounding rectangle, so those checks are slightly cautious around it.

### Desk and chair together

- Adding a desk type that is marked "comes with a chair" places the desk and its chair together, both selected, so they move as one at first.
- After that they are separate pieces. Each can be moved, rotated or deleted on its own.

### The starter furniture chart

- A table file in the repository, `furniture.csv`, holds the starter furniture list. Its main purpose is to give the site owner one easy place to add furniture types and adjust dimensions.
- It can be edited on the GitHub website. Adding a row adds a furniture type.
- Every new room starts with this list. The person then edits their own room's list freely.
- Changes to the chart affect **new rooms only**. Rooms that already exist keep their own lists.
- The first version of the chart contains:

| Name | Shape | Width | Depth | Color group | Comes with a chair |
|---|---|---|---|---|---|
| Student desk (single) | Rectangle | 2′ | 1′ 6″ | Student table | Yes |
| Chair | Rectangle | 1′ 7.5″ | 1′ 7.5″ | Chair | No |
| Teacher desk | Rectangle | 3′ 11″ | 2′ 6″ | Other | No |
| Bookshelf | Rectangle | 3′ | 1′ 3″ | Other | No |
| Storage unit | Rectangle | 4′ | 1′ 6″ | Other | No |

The single desk size is a placeholder to confirm. The other sizes are taken from the original room.

- The default room keeps its own list from `HANDOFF.md` (5′ × 2′ tables, COW cart and so on), because that furniture is specific to that room.

## 7. Arranging furniture

Kept from the current version:

- Drag with mouse or touch.
- Select several pieces by shift-click or by dragging a box across empty floor, then move them as a group.
- Rotate 90°, duplicate, delete, nudge with arrow keys, undo and redo.
- Snap to 3″.
- Gap measurements from the selected piece to the nearest piece or wall.
- The spare strip below the room for furniture that is not in use.
- Chair direction marker.
- Light and dark themes, and a layout that works at phone width.

New:

- **Alignment lines.** While a piece is dragged, a thin guide line appears when one of its edges or its center lines up with a nearby piece or a wall, and the piece snaps to that line.

## 8. Checks and counts

- Overlapping pieces.
- Pieces outside the room.
- Pieces inside a clear zone.
- **Walkway warning:** gaps under 2′ between pieces, or between a piece and a wall, where someone would need to walk.
- **Seat count:** the number of chairs in the room.
- **Inventory:** how many of each type are in the room against how many the room has, when a count was entered.

## 9. Saving, downloading and uploading

### Saved layouts

- Layouts are saved by name inside a room. Each can be opened, renamed or deleted.

### Download

- **Download** produces one PNG image of the current layout.
- The same file also holds, invisibly, the room, its furniture list and that one layout.
- One file holds one layout.

### Upload

- **Upload** takes a downloaded PNG and rebuilds the room and layout from it.
- If the file belongs to a room the person already has, the layout is added to that room. Otherwise a new room is created.
- A colleague can pass their file to someone else, who then gets the same room and layout.

### Limit to explain in the tool

The hidden data survives only when the file itself is kept: an email attachment, a USB stick, Google Drive. It is lost if the picture is screenshotted, pasted into a document, or sent through an app that recompresses images. When an uploaded image has no data in it, the tool says so in plain words.

### Print

- **Print** gives a clean one-page copy of the layout with the room name, layout name and seat count.

## 10. How to use page

- One short page, opened from a "How to use" link.
- Numbered steps in plain words. Text only, in a single column.
- Order: add furniture, move it, save, download, upload, print. Room setup comes last.

## 11. Privacy

- The repository and the site are public.
- The two layouts saved in the current version ("Experimental" and "Experimental 2") are removed from the public page and handed over as files to upload.
- No student names or other personal data are stored anywhere in the tool.

## 12. Left out of the first version

- Rotation at angles other than 90°.
- Diagonal walls.
- Metric units.
- Starting layouts generated automatically. The four built-in starting layouts in the current version are removed, because they only fit the original room.
- Sharing or syncing between people through the site itself. Sharing is done by passing a downloaded file.

## 13. Build order

Each step ends with a working tool that can be tried before the next step starts.

1. **Repository and site.** Put the current planner on GitHub Pages, with saving moved to the browser and the private layouts taken out.
2. **Download and upload.** The PNG file that reloads.
3. **Rooms.** Room picker, outline drawing, flip, wall features, fixtures and clear zones. The checks and gap measurements are rewritten to work for any right-angled room.
4. **Furniture.** Per-room furniture list, shapes, desk-with-chair, and the starter chart.
5. **Arranging extras.** Alignment lines, walkway warning, seat count, print.
6. **How to use page.**

## 14. Points to confirm

- **Single desk size.** 2′ × 1′ 6″ is a placeholder until a real desk is measured.
- **Chart format.** `furniture.csv` is proposed because GitHub shows it as a table. Sizes in the file would be written in inches (24 and 18 for the single desk) to avoid decimals. This is a suggestion, not something already agreed.
- **Walkway threshold.** 2′ comes from the "tight walkway" figure in `HANDOFF.md`. 3′ was the "comfortable" figure.
- **Original room measurements.** The door position and a 3.5″ mismatch on the back wall were never re-measured (see `HANDOFF.md`, section 3). The default room carries those over.
- **PNG data method.** Storing data inside a PNG is a standard technique, but it has not yet been tested in this tool across browsers. Step 2 will confirm it.
