# Lua-ANSI

* [List of CGA Codes](list-of-cga-codes.md)

## Common Style for All Commands
Each command has some arguments, and a `handle` argument at the end. This could be a file,
or more commonly `io.stdout`. If a handle exists, then it writes the code to the handle. Else, it simply
returns the value of the code.

## Colors and Styles
##### Loaded in `ansi.color`
* `setColor(layer, color, handle)` - Sets the color of the specified layer.
  * Colors include: `black`, `red`, `green`, `yellow`, `blue`, `magenta`, `cyan`, `white`, and `reset`.
  * Layers include `layers.fg` for the text color and `layers.bg`for the background color.
* `setTrueColor(layer, red, green, blue, handle)` - Sets a 256-color color for the specified layer. Not supported on all platforms.
* `setCGA(cga_code, handle)` - Modifies the text with one of [these CGA codes](list-of-cga-codes.md)
* `reset(handle)` - alias for `setCGA(cga.reset, handle)`

## Cursor and Terminal Manipulation
##### Loaded in `ansi.term`
* Erase Modes - Each of these should be self-explanatory, and are used in conjunction with `eraseLine` and `eraseScreen`.
  * `erase.cursorToStart`
  * `erase.cursorToEnd`
  * `erase.all`

* `moveUp(lines, handle)` - Moves the cursor up `lines` lines.
* `moveDown(lines, handle)` - Moves the cursor down `lines` lines.
* `moveBack(cols, handle)` - Moves the cursor left `cols` columns.
* `moveFwd(cols, handle)` - Moves the cursor right `cols` columns.
* `setCursor(line, col, handle)` - Sets the cursor to `line, col`.  `1, 1` is the top-left corner of the terminal.
* `eraseLine(mode, handle)` - Erases the line depending on the mode.
* `eraseScreen(mode, handle)` - Erases the screen depending on the mode.
* `saveCursor(handle)` - Saves the position of the cursor.
* `restoreCursor(handle)` - Restores the cursor at the saved position.
* `clearScreen(handle)` - alias for `eraseScreen(erase.all, handle)`.
