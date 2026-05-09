# Text Manipulation Tool

> A lightweight, zero-dependency text utility that runs entirely in your browser or as a native Windows desktop app.
> No installation. No internet. Just open and use.

Originally built by **[Rashid Saleem](https://github.com/whatsdd)** for internal data mining and text assessment work, and open-sourced so everyone can use and contribute.

---

![Tool Preview](https://raw.githubusercontent.com/whatsdd/TextManipulationTool/master/tool.PNG)

---

## Download & Open

| File | Platform | How to open |
|------|----------|-------------|
| [`CODE.HTA`](CODE.HTA) | **Windows — Desktop App** | Double-click. Opens as a native borderless window via the Windows HTA runtime. No browser needed. |
| [`CODE.html`](CODE.html) | **Windows — Browser** | Open in Microsoft Edge, Chrome, or Firefox on Windows. |
| [`TextManipulationTool_Mac.html`](TextManipulationTool_Mac.html) | **macOS / Linux / Any modern browser** | Open in Safari, Chrome, Firefox, or any modern browser. |

All three files are single standalone HTML files — no dependencies, no build step, no server.

---

## Features

| Group | Button | What it does |
|-------|--------|-------------|
| **Edit** | Insert | Prepend **X** and append **Y** to every non-empty line |
| | Replace | Replace every **X** with **Y** across the full text. Ctrl/⌘-click evaluates **Y** as a live JS expression |
| | Number Lines | Prefix each line with its line number (`1. 2. 3. …`) |
| | Join Lines | Collapse all lines into one string joined by **X** |
| **Delete** | Before X | On each line, remove everything up to and including the first **X** |
| | X … Y | On each line, remove text between **X** and **Y** |
| | After X | On each line, remove everything from the last **X** onwards |
| **Order** | Sort | Sort lines A → Z. Ctrl/⌘-click sorts Z → A |
| | Reverse | Reverse the order of all lines |
| | Shuffle | Randomly shuffle line order (Fisher-Yates) |
| | Flip Lines | Reverse the characters within each line (`hello` → `olleh`) |
| **Case** | Uppercase | Convert all text to UPPER CASE |
| | Lowercase | Convert all text to lower case |
| | Title Case | Capitalize the first letter of every word |
| | Sentence Case | Capitalize the first letter of each sentence |
| **Clean** | Unique | Remove duplicate lines, keeping the first occurrence |
| | Remove Blanks | Delete all empty lines |
| | Trim | Strip leading and trailing whitespace from each line |
| | Extra Spaces | Collapse multiple consecutive spaces into one |
| | Strip HTML | Remove all `<…>` tags, leaving plain text |
| | List Sorter | Deduplicate + remove blanks, then interleave lines |
| **Encode** | Encode URL | URL-encode the entire text (`encodeURIComponent`) |
| | Decode URL | URL-decode the entire text (`decodeURIComponent`) |
| | Base64 Enc | Base64-encode the entire text (`btoa`) |
| | Base64 Dec | Base64-decode the entire text (`atob`) |
| | HTML Enc | Encode HTML special characters (`&` → `&amp;`, `<` → `&lt;`, etc.) |
| | HTML Dec | Decode HTML entities back to plain characters |
| | ROT13 | Apply the ROT13 cipher — rotate each letter by 13 positions |
| **Nav** | Go to Line | Move the cursor to the line number in the **X** field |

---

## The X and Y Fields

Almost every operation uses the **X** and **Y** input fields as parameters:

- **X** — the search string, delimiter, or (for Go to Line) the target line number
- **Y** — the replacement, the appended string, or the right delimiter

**Insert example:** X = `[`, Y = `]` → wraps every line so `hello` becomes `[hello]`

**Replace with Ctrl/⌘:** Set Y to a JavaScript expression. The variable `i` is the match index. For example, Y = `` `[${i}] ` `` numbers each match sequentially.

---

## How to Use

### Windows — Desktop App (`CODE.HTA`)

1. Clone or download the repository
2. Double-click `CODE.HTA`
3. Windows opens it as a native HTA window (no browser chrome, no address bar)
4. Paste your text, set X and Y, click any button

> Requires the Windows HTA runtime, which ships with all versions of Windows (XP through 11). Will not open on macOS or Linux.

### Windows — Browser (`CODE.html`)

1. Clone or download the repository
2. Open `CODE.html` in **Edge**, **Chrome**, or **Firefox**
3. Same usage as above

### macOS / Linux / Any modern browser

1. Clone or download the repository
2. Open `TextManipulationTool_Mac.html` in your browser
3. Same usage as above

---

## Platform Comparison

| | `CODE.HTA` | `CODE.html` | `TextManipulationTool_Mac.html` |
|---|---|---|---|
| **Platform** | Windows desktop (HTA) | Windows browsers | macOS / Linux / any browser |
| **Runtime** | IE11 / Trident engine | Edge, Chrome, Firefox | Safari, Chrome, Firefox |
| **Modifier key** | Ctrl | Ctrl | ⌘ Cmd or Ctrl |
| **Monospace font** | Consolas, Courier New | Consolas, Courier New | SF Mono, Menlo, Monaco |
| **UI font** | Segoe UI | Segoe UI | -apple-system, Helvetica Neue |
| **`gap` CSS** | Via margins (IE11) | Standard `gap` | Standard `gap` |
| **`closest()` API** | DOM-walk polyfill (IE11) | Native | Native |
| **Line endings** | Reads CRLF/CR/LF, writes LF | Reads CRLF/CR/LF, writes LF | Reads CRLF/CR/LF, writes LF |

---

## What Changed in the Overhaul

The original Windows files used several IE-only and deprecated APIs. All three files have been modernised to share the same feature set and code quality:

| Old (original) | New (overhauled) |
|----------------|-----------------|
| `document.selection.createRange()` | `setSelectionRange()` — standard |
| `event.srcElement` | `e.target` — standard |
| Global `event` object in functions | Event parameter `e` passed explicitly |
| String-based mouse event assignments | `addEventListener` |
| `escape()` / `unescape()` (deprecated) | `encodeURIComponent` / `decodeURIComponent` |
| `Array.prototype.unique` mutation | `Object.create(null)` filter — no prototype pollution |
| Three buttons all labeled "delete" | **Before X**, **X … Y**, **After X** |
| `document.write()` button generation | Static HTML with `data-action` attributes |
| Hard-coded `HEIGHT:600` | Flexbox layout, fills viewport dynamically |
| `fixedsys` / `microsoft sans serif` | System font stacks per platform |
| No status bar | Live line count + character count |
| No URL encode/decode | Encode URL + Decode URL buttons |
| No Go to Line button | Go to Line in toolbar |
| No button tooltips | `title` attribute on every button |
| No button grouping | Grouped toolbar (Edit, Delete, Order, Case, Clean, Encode, Nav) |

---

## Credits

**Original author:** [Rashid Saleem](https://github.com/whatsdd)

This tool was designed and built by Rashid Saleem for internal data mining and text assessment tasks. Rashid's creativity and engineering made this tool what it is. It was open-sourced by agreement so the wider community can use and extend it.

---

## Contributing

Bug reports, feature requests, and pull requests are welcome. Open an issue or submit a PR.
