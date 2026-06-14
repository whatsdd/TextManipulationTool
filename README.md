# Text Manipulation Tool

> A powerful, zero-dependency text utility with 79 operations across 10 groups — runs entirely in your browser on any platform.
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

79 operations grouped into 10 categories, all accessible from a collapsible sidebar with a live search filter.

### Edit
| Button | What it does |
|--------|-------------|
| Insert | Prepend **X** and append **Y** to every non-empty line |
| Replace | Replace every **X** with **Y** (Ctrl/⌘-click evaluates **Y** as a JS expression) |
| Number Lines | Prefix each line with its line number (`1.`, `2.`, `3. …`) |
| Join Lines | Collapse all lines into one string joined by **X** |
| Split by X | Split each line into multiple lines at every **X** |
| Remove Lines with X | Delete every line that contains **X** |
| Keep Lines with X | Keep only lines that contain **X** |
| Duplicate Lines | Double every line (A → A, A) |
| Pad Lines | Left-pad every line to **X** chars wide using **Y** (default space) |

### Delete
| Button | What it does |
|--------|-------------|
| Before X | On each line, remove everything up to and including the first **X** |
| X … Y | On each line, remove the text between **X** and **Y** |
| After X | On each line, remove everything from the last **X** onwards |

### Order
| Button | What it does |
|--------|-------------|
| Sort | Sort lines A → Z. Ctrl/⌘-click sorts Z → A |
| Reverse | Reverse the order of all lines |
| Shuffle | Randomly shuffle line order (Fisher-Yates) |
| Flip Lines | Reverse characters within each line (`hello` → `olleh`) |

### Case
| Button | What it does |
|--------|-------------|
| Uppercase | Convert all text to UPPER CASE |
| Lowercase | Convert all text to lower case |
| Title Case | Capitalize the first letter of every word |
| Sentence Case | Capitalize the first letter of each sentence |
| camelCase | Convert to camelCase |
| PascalCase | Convert to PascalCase |
| snake_case | Convert to snake_case |
| kebab-case | Convert to kebab-case |
| CONSTANT_CASE | Convert to CONSTANT_CASE |
| dot.case | Convert to dot.case |
| Alternating | Alternate case character by character: `hElLo` |
| Inverse Case | Swap uppercase ↔ lowercase each letter |
| Slugify | Lowercase, remove accents, replace spaces/punctuation with `-` |

### Clean
| Button | What it does |
|--------|-------------|
| Unique | Remove duplicate lines, keeping the first occurrence |
| Remove Blanks | Delete all empty lines |
| Trim | Strip leading and trailing whitespace from each line |
| Extra Spaces | Collapse multiple consecutive spaces into one |
| Strip HTML | Remove all `<…>` tags, leaving plain text |
| List Sorter | Deduplicate + remove blanks, then interleave lines |
| Remove Accents | Normalize and strip accent marks (é → e) |
| Remove Punctuation | Strip all punctuation characters |
| Remove Numbers | Strip all digit characters |
| Remove Non-ASCII | Strip any character with codepoint > 127 |
| Dedupe Words | Remove duplicate words within each line |

### Encode
| Button | What it does |
|--------|-------------|
| Encode URL | URL-encode the entire text (`encodeURIComponent`) |
| Decode URL | URL-decode the entire text (`decodeURIComponent`) |
| Base64 Enc | Base64-encode the entire text |
| Base64 Dec | Base64-decode the entire text |
| HTML Enc | Encode HTML special characters (`&` → `&amp;`, `<` → `&lt;`, etc.) |
| HTML Dec | Decode HTML entities back to plain characters |
| ROT13 | Apply the ROT13 cipher |
| Hex Encode | Convert text to space-separated hex bytes |
| Hex Decode | Parse hex bytes back to text |
| Binary Encode | Convert text to space-separated 8-bit binary groups |
| Binary Decode | Parse binary groups back to text |
| Unicode Escape | Escape every character as `\uXXXX` |
| Unicode Unescape | Convert `\uXXXX` sequences back to characters |
| JSON Escape | Escape the string as a JSON string value |
| JSON Unescape | Unescape a JSON string value |
| Morse Encode | Convert text to Morse code (dots and dashes) |
| Morse Decode | Convert Morse code back to text |

### Hash
| Button | What it does |
|--------|-------------|
| MD5 | Compute MD5 hash (hand-rolled, pure JS) |
| SHA-1 | Compute SHA-1 hash (Web Crypto) |
| SHA-256 | Compute SHA-256 hash (Web Crypto) |
| SHA-512 | Compute SHA-512 hash (Web Crypto) |

### Data
| Button | What it does |
|--------|-------------|
| JSON Format | Pretty-print JSON (indent = **X**, default 2) |
| JSON Minify | Minify JSON to a single line |
| CSV → JSON | Parse CSV and output a JSON array of objects |
| JSON → CSV | Flatten a JSON array of objects to CSV |
| JSON → Table | Render a JSON array as a Markdown table |
| CSV → Table | Render CSV as a Markdown table |
| Extract Emails | Find all email addresses, one per line |
| Extract URLs | Find all `http/https` URLs, one per line |
| Extract Numbers | Find all numbers (integer and decimal), one per line |
| JWT Decode | Decode a JWT — pretty-print header and payload |

### Generate
| Button | What it does |
|--------|-------------|
| Lorem Ipsum | Generate **X** paragraphs of Lorem Ipsum (default 3) |
| UUID v4 | Generate **X** random UUID v4 values (default 1) |
| Random Numbers | Generate **X** random integers between 0 and **Y** |
| Number Sequence | Generate a sequence of numbers from **X** to **Y** |
| Timestamp | Insert the current Unix timestamp (seconds) |
| Date / Time | Insert the current ISO 8601 datetime |

### Nav
| Button | What it does |
|--------|-------------|
| Go to Line | Move the cursor to the line number in **X** |
| Select Line | Select the entire line at line number **X** |

---

## How to Use

**Option A — Online:** Visit [whatsdd.github.io/TextManipulationTool](https://whatsdd.github.io/TextManipulationTool/) in any browser. No install, no download.

**Option B — Offline:** Download `TextManipulationTool.html`, save it anywhere, and open it in your browser. Works with no internet connection.

Either way:
1. Paste your text into the large editing area on the right
2. Set **X** and **Y** in the footer bar as needed
3. Click a button in the sidebar — the result appears instantly

The sidebar has a **filter box** at the top — type to search across all 79 operations.

---

## The X and Y Fields

Almost every operation uses the **X** and **Y** input fields (in the footer bar) as parameters:

- **X** — the search string, delimiter, left boundary, or target line number
- **Y** — the replacement string, suffix, right boundary, or padding character

**Insert example:** X = `[`, Y = `]` → wraps every line so `hello` becomes `[hello]`

**Replace with Ctrl/⌘-click:** Set Y to a JavaScript expression. The variable `i` is the match index (zero-based). For example, Y = `` `[${i}] ` `` numbers each match sequentially.

---

## Keyboard Shortcuts

| Key | What it does |
|-----|-------------|
| `Ctrl/⌘` + `Z` | Undo |
| `Ctrl/⌘` + `Shift` + `Z` | Redo |
| `Ctrl/⌘` + `Y` | Redo (Windows alternative) |
| `Ctrl/⌘` + `F` | Open Find panel |
| `Ctrl/⌘` + `H` | Open Find & Replace panel |
| `Ctrl/⌘` + `S` | Save / download as text file |
| `Ctrl/⌘` + `Shift` + `C` | Copy all text to clipboard |
| `Escape` | Close Find panel |
| `Tab` (in editor) | Insert a real tab character |
| `Ctrl/⌘`-click **Sort** | Sort Z → A (reverse sort) |
| `Ctrl/⌘`-click **Replace** | Evaluate Y as a JS expression (dynamic replacement) |

---

## Tutorial

### The Basics

1. **Open** `TextManipulationTool.html` in your browser (or use the [live demo](https://whatsdd.github.io/TextManipulationTool/))
2. **Paste** your text into the large editing area on the right
3. **Set X and Y** in the footer bar — these are the parameters used by most operations
4. **Click a button** in the sidebar — the result appears instantly
5. **Undo** anything with `Ctrl/⌘+Z` — the tool keeps 100 history states

The live status bar shows **lines**, **characters**, **words**, and **selection size** as you type.

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

You have a list of names and want to wrap each in SQL single quotes: `'Alice'`, `'Bob'`, `'Carol'`

1. Paste: `Alice`, `Bob`, `Carol` (one per line)
2. Set **X** = `'` and **Y** = `'`
3. Click **Insert**

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

1. Set **X** = `, `
2. Click **Split by X** — each item becomes its own line

---

### Example 7 — Encode text for use in a URL

1. Paste your text (e.g., `hello world & more`)
2. Click **Encode URL** → `hello%20world%20%26%20more`
3. Click **Decode URL** to restore the original

---

### Example 8 — Hash a password or string

1. Paste the string
2. Click **SHA-256** (or MD5, SHA-1, SHA-512)
3. The hex digest replaces the text instantly

---

### Example 9 — Convert CSV to JSON

1. Paste your CSV (first row = headers)
2. Click **CSV → JSON**
3. Get a JSON array of objects

---

### Example 10 — Generate UUIDs

1. Set **X** = `10` (or any number)
2. Click **UUID v4** — generates 10 random UUID v4 values, one per line

---

### Example 11 — Sort and deduplicate a word list

1. Paste your words (one per line)
2. Click **Unique** → remove duplicates
3. Click **Sort** → sort A → Z
4. Hold `Ctrl/⌘` and click **Sort** → sort Z → A

---

### Dynamic Replace (Advanced)

Hold `Ctrl` (Windows/Linux) or `⌘` (Mac) and click **Replace** — the **Y** field is evaluated as a JavaScript expression. The variable `i` is the zero-based match index.

**Example:** Set X = `item`, Y = `` `item_${i+1}` `` then Ctrl/⌘-click Replace to number each match: `item_1`, `item_2`, `item_3` …

---

## What Changed in the Overhaul

The original Windows-only files used IE-only APIs and a flat horizontal toolbar. The tool has been completely modernised into a single cross-platform file:

| Old (original) | New |
|----------------|-----|
| Three separate files (HTA, Windows HTML, Mac HTML) | **One universal file** for all platforms |
| Flat horizontal toolbar (15 then 29 buttons) | **Collapsible sidebar** with live filter search |
| 15 → 29 operations | **79 operations** across 10 categories |
| No undo/redo | **Undo/Redo** (100 history states, Ctrl+Z/Shift+Z) |
| No dark mode | **Dark mode** with localStorage persistence |
| No find/replace panel | **Find & Replace panel** (Ctrl+F/H) with regex + case options |
| No file open/save | **Drag-drop open**, file picker, **Save/Download** button |
| No copy-all button | **Copy all** to clipboard |
| No hash functions | **MD5 + SHA-1/256/512** hash operations |
| No data tools | **CSV/JSON conversion**, table generators, JWT decode |
| No generators | **Lorem ipsum, UUID v4, random numbers**, sequences |
| No case variants | **13 case transforms** incl. camelCase, snake, kebab, slugify |
| No encode variants | **Hex, binary, Unicode escape, JSON escape, Morse** encode/decode |
| `document.selection.createRange()` | `setSelectionRange()` — standard |
| `event.srcElement` | `e.target` — standard |
| Global `event` object | Event parameter `e` passed explicitly |
| String-based event assignments | `addEventListener` |
| `escape()` / `unescape()` (deprecated) | `encodeURIComponent` / `decodeURIComponent` |
| `Array.prototype.unique` mutation | `Object.create(null)` filter — no prototype pollution |
| `document.write()` button generation | Static HTML with `data-action` attributes |
| Hard-coded `HEIGHT:600` | CSS Grid layout, fills viewport |
| `fixedsys` / `microsoft sans serif` | Cross-platform system font stack |
| No status bar | Lines · chars · words · selection count |
| X/Y in separate row | **X/Y moved to footer** — more editor space |

---

## Credits

**Original author:** [Rashid Saleem](https://github.com/whatsdd)

This tool was designed and built by Rashid Saleem for internal data mining and text assessment tasks. Rashid's creativity and engineering made this tool what it is. It was open-sourced by agreement so the wider community can use and extend it.

---

## Contributing

Bug reports, feature requests, and pull requests are welcome. Open an issue or submit a PR.
