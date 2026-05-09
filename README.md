# Text Manipulation Tool

A lightweight, zero-dependency text manipulation utility that runs entirely in your browser (or as a Windows desktop app). No installation, no server, no internet required — just open the file and start working.

Originally created by **[Rashid Saleem](https://github.com/whatsdd)** for internal data mining and text assessment tasks, and open-sourced so everyone can use and contribute.

---

![Tool Preview](https://raw.githubusercontent.com/whatsdd/TextManipulationTool/master/tool.PNG)

---

## Versions

| File | Platform | How to open |
|------|----------|-------------|
| `CODE.HTA` | **Windows** | Double-click — runs as a native desktop app via Windows HTA runtime (Internet Explorer engine). No browser needed. |
| `CODE.html` | **Windows (browser)** | Open in Internet Explorer or legacy Edge. |
| `TextManipulationTool_Mac.html` | **macOS / Linux / Any modern browser** | Open in Safari, Chrome, Firefox, or any modern browser. Works on Mac, Linux, and Windows with a modern browser. |

---

## Features

| Operation | Description |
|-----------|-------------|
| **Insert** | Prepend the value of **X** and append the value of **Y** to every non-empty line |
| **Replace** | Replace every occurrence of **X** with **Y** across the entire text. ⌘/Ctrl+click evaluates **Y** as a JavaScript expression for dynamic replacements |
| **Delete Before X** | On each line, remove everything up to and including the first occurrence of **X** |
| **Delete X … Y** | On each line, delete the text found between **X** and **Y** |
| **Delete After X** | On each line, remove everything from the last occurrence of **X** onwards |
| **Sort** | Sort lines alphabetically A → Z. ⌘/Ctrl+click sorts Z → A |
| **Reverse** | Reverse the order of all lines |
| **Uppercase** | Convert all text to UPPER CASE |
| **Lowercase** | Convert all text to lower case |
| **Unique** | Remove duplicate lines, keeping the first occurrence |
| **Remove Blanks** | Delete all empty lines |
| **List Sorter** | Deduplicate + remove blanks, then interleave lines (useful for balanced list merging) |
| **Encode URL** | URL-encode the entire text using `encodeURIComponent` |
| **Decode URL** | URL-decode the entire text using `decodeURIComponent` |
| **Go to Line** | Jump the cursor to the line number specified in the **X** field |

---

## How to Use

### macOS / Linux / Modern browser (recommended)

1. Download or clone this repository.
2. Open **`TextManipulationTool_Mac.html`** in Safari, Chrome, Firefox, or any modern browser.
3. Paste your text into the large text area.
4. Set **X** and **Y** values in the input fields at the top (these are the search/replace targets used by many operations).
5. Click any button to apply that operation instantly.

### Windows (native desktop app)

1. Download or clone this repository.
2. Double-click **`CODE.HTA`**.
3. Windows will open it as a native HTA (HTML Application) — a borderless desktop window, no browser chrome.
4. Use exactly the same way as above.

> **Note:** The HTA version requires the Windows HTA runtime (built into all versions of Windows). It will not work on macOS or Linux.

---

## X and Y Fields

Most operations use the **X** and **Y** input fields as parameters:

- **X** — the search string, delimiter, or line number (for Go to Line)
- **Y** — the replacement string or the value to insert

For the **Insert** operation, X is prepended and Y is appended to each line.  
For **Replace** with ⌘/Ctrl held, Y is evaluated as JavaScript — for example, Y = `` `[${i}]` `` would insert a counter at each match.

---

## Differences: Mac vs Windows version

| | Windows HTA (`CODE.HTA`) | Mac HTML (`TextManipulationTool_Mac.html`) |
|---|---|---|
| Runtime | Windows HTA / Internet Explorer engine | Any modern browser |
| Line endings | `\r\n` (CRLF) | `\n` (LF), reads both |
| Modifier key | Ctrl | ⌘ Cmd or Ctrl |
| Encoding functions | `escape()` / `unescape()` (deprecated) | `encodeURIComponent()` / `decodeURIComponent()` |
| Fonts | `Fixedsys`, `Microsoft Sans Serif` | `SF Mono`, `Menlo`, `Monaco`, `monospace` |
| Button labels | Three buttons all labeled "delete" | Labelled "Before X", "X … Y", "After X" |
| Status bar | None | Live line count and character count |
| Tab key in textarea | Uses IE `createRange` API | Uses standard `setSelectionRange` API |

---

## Credits

**Original author:** [Rashid Saleem](https://github.com/whatsdd)

This tool was built by Rashid Saleem for internal data mining and text assessment workflows. It was open-sourced by agreement so that the wider community can use and extend it.

Contributions, bug reports, and feature requests are welcome — feel free to open an issue or pull request.

---

## License

Open source. See repository for details.
