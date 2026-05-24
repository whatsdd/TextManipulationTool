# Text Manipulation Tool

> A powerful, zero-dependency text utility with 29 operations across 7 groups — runs entirely in your browser on any platform.
> No installation. No internet. No server. Just open and use.

Originally built by **[Rashid Saleem](https://github.com/whatsdd)** for internal data mining and text assessment work, and open-sourced so everyone can use and contribute.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Open%20Tool-0071e3?style=flat-square)](https://whatsdd.github.io/TextManipulationTool/)

---

![Tool Preview](https://raw.githubusercontent.com/whatsdd/TextManipulationTool/master/tool.PNG)

---

## Table of Contents

- [Download & Open](#download--open)
- [Features](#features)
- [How to Use](#how-to-use)
- [The X and Y Fields](#the-x-and-y-fields)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Tutorial](#tutorial)
- [What Changed in the Overhaul](#what-changed-in-the-overhaul)
- [Credits](#credits)

---

## Download & Open

| | How |
|---|---|
| 🌐 **Use online (no download)** | [whatsdd.github.io/TextManipulationTool](https://whatsdd.github.io/TextManipulationTool/) — open in any browser, nothing to install |
| 💾 **Download for offline use** | [`TextManipulationTool.html`](TextManipulationTool.html) — save the file, open it locally, works with no internet |

Works on Windows, macOS, and Linux. No dependencies, no build step, no server.

---

## Features

29 operations grouped into 7 categories. Every operation works instantly on the text in the editor — no clipboard required.

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

## How to Use

**Option A — Online:** Visit [whatsdd.github.io/TextManipulationTool](https://whatsdd.github.io/TextManipulationTool/) in any browser. No install, no download.

**Option B — Offline:** Download `TextManipulationTool.html`, save it anywhere, and open it in your browser. Works with no internet connection.

Either way:
1. Paste your text into the large editing area
2. Set **X** and **Y** as needed
3. Click a button — result appears instantly

---

## The X and Y Fields

Almost every operation uses the **X** and **Y** input fields as parameters:

- **X** — the search string, delimiter, or (for Go to Line) the target line number
- **Y** — the replacement, the appended string, or the right delimiter

**Insert example:** X = `[`, Y = `]` → wraps every line so `hello` becomes `[hello]`

**Replace with Ctrl/⌘:** Set Y to a JavaScript expression. The variable `i` is the match index (zero-based). For example, Y = `` `[${i}] ` `` numbers each match sequentially.

---

## Keyboard Shortcuts

| Key | Where | What it does |
|-----|-------|-------------|
| `Tab` | Textarea | Inserts a real tab character (does not lose focus) |
| `Ctrl`+click / `⌘`+click | **Sort** button | Sort Z → A (reverse sort) |
| `Ctrl`+click / `⌘`+click | **Replace** button | Evaluate Y as a JS expression (dynamic replacement) |

---

## Tutorial

### The Basics

1. **Open** `TextManipulationTool.html` in your browser
2. **Paste** your text into the large editing area
3. **Set X and Y** — the two input fields at the top are the parameters used by most operations
4. **Click a button** — the result appears instantly in the editor

The live status bar at the bottom shows **lines**, **characters**, and **words** as you type.

---

### Example 1 — Clean up a messy list

You have a list copied from a website with extra spaces, blank lines, and duplicates:

```
  Apple  
  Banana

  Apple
    Cherry  
```

Steps:
1. Paste the text into the editor
2. Click **Trim** → removes leading/trailing spaces from every line
3. Click **Remove Blanks** → deletes the empty lines
4. Click **Unique** → removes the duplicate "Apple"

Result: `Apple`, `Banana`, `Cherry` — one per line, clean.

---

### Example 2 — Add a prefix and suffix to every line

You have a list of names and want to wrap each one in SQL single quotes: `'Alice'`, `'Bob'`, `'Carol'`

Steps:
1. Paste: `Alice`, `Bob`, `Carol` (one per line)
2. Set **X** = `'` and **Y** = `'`
3. Click **Insert**

Result: each line is wrapped with the X prefix and Y suffix.

---

### Example 3 — Replace text across a block

You copied a config file and need to change every `localhost` to `production.server.com`:

1. Paste the config text
2. Set **X** = `localhost`, **Y** = `production.server.com`
3. Click **Replace**

---

### Example 4 — Number a list

You have 10 lines and want them numbered `1.`, `2.`, `3. …`:

1. Paste the lines
2. Click **Number Lines**

To remove the numbers later: set **X** = `. ` and click **Delete → Before X**.

---

### Example 5 — Extract data between two delimiters

You have lines like `name: "Alice" age: 25` and want just the names:

1. Set **X** = `"` and **Y** = `"`
2. Click **Delete → Before X** to remove everything up to and including the first quote
3. Click **Delete → After X** to remove everything from the last quote onwards

---

### Example 6 — Convert a comma-separated string to lines

Input: `apple, banana, cherry, date`

1. Set **X** = `, ` and **Y** = (leave empty)
2. Click **Replace** — each comma+space becomes a newline, splitting onto separate lines

---

### Example 7 — Encode text for use in a URL

1. Paste your text (e.g., `hello world & more`)
2. Click **Encode URL** → `hello%20world%20%26%20more`
3. Click **Decode URL** to restore the original

---

### Example 8 — Sort and deduplicate a word list

1. Paste your words (one per line)
2. Click **Unique** → remove duplicates
3. Click **Sort** → sort A → Z
4. Hold Ctrl/⌘ and click **Sort** → sort Z → A

---

### Dynamic Replace (Advanced)

Hold `Ctrl` (Windows/Linux) or `⌘` (Mac) and click **Replace** — the **Y** field is evaluated as a JavaScript expression. The variable `i` is the zero-based match index.

**Example:** Set X = `item`, Y = `` `item_${i+1}` `` then Ctrl/⌘-click Replace to number each match: `item_1`, `item_2`, `item_3` …

---

## What Changed in the Overhaul

The original Windows-only files used several IE-only and deprecated APIs. The tool has been modernised and consolidated into a single cross-platform file:

| Old (original) | New |
|----------------|-----|
| Three separate files (HTA, Windows HTML, Mac HTML) | **One universal file** for all platforms |
| `document.selection.createRange()` | `setSelectionRange()` — standard |
| `event.srcElement` | `e.target` — standard |
| Global `event` object in functions | Event parameter `e` passed explicitly |
| String-based mouse event assignments | `addEventListener` |
| `escape()` / `unescape()` (deprecated) | `encodeURIComponent` / `decodeURIComponent` |
| `Array.prototype.unique` mutation | `Object.create(null)` filter — no prototype pollution |
| Three buttons all labeled "delete" | **Before X**, **X … Y**, **After X** |
| `document.write()` button generation | Static HTML with `data-action` attributes |
| Hard-coded `HEIGHT:600` | Flexbox layout, fills viewport dynamically |
| `fixedsys` / `microsoft sans serif` | Cross-platform system font stack |
| No status bar | Live line count + character count + word count |
| No URL encode/decode | Encode URL + Decode URL buttons |
| No Go to Line button | Go to Line in toolbar |
| No button tooltips | `title` attribute on every button |
| No button grouping | Grouped toolbar (Edit, Delete, Order, Case, Clean, Encode, Nav) |
| 15 operations | 29 operations |

---

## Credits

**Original author:** [Rashid Saleem](https://github.com/whatsdd)

This tool was designed and built by Rashid Saleem for internal data mining and text assessment tasks. Rashid's creativity and engineering made this tool what it is. It was open-sourced by agreement so the wider community can use and extend it.

---

## Contributing

Bug reports, feature requests, and pull requests are welcome. Open an issue or submit a PR.
