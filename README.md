# Speed Read

A single-page reader that shows text a few words at a time at a set pace. It is styled after a small e-ink panel: one ruled display, a status line of settings, and a segmented progress bar.

It has two reading views and three ways to get text in:

- **Speed Read** flashes one group of words at a time in a fixed spot.
- **Focal Read** shows the passage as a block and moves a highlight through it.
- Text can be pasted, or pulled from a chosen section of a **PDF** or **EPUB**.

Everything runs in the browser. No text or file is uploaded anywhere.

## Quick start

1. Open the page. A short sample passage is already loaded.
2. Press **Start** (bottom left of the panel), or press Space.
3. To read your own text, paste it into the box under the panel, give it a title, and press **Load text**.

## How it works

### Reading loop

The text is split into words on whitespace, and blank lines are remembered as paragraph breaks. Words are then grouped into "flashes" according to the Mode setting.

Each flash stays on screen for:

```
words in the flash × (60,000 ÷ WPM) milliseconds  +  any Cut pause
```

The timer corrects for drift, so a long session stays on pace even if individual frames run late.

### The panel, row by row

| Row | What it shows |
|---|---|
| 1 | View tabs (Speed Read, Focal Read) and the title of the text |
| 2 | Settings. Click any one to cycle through its options. Word count on the right |
| 3 | The reading area, between two measuring rules with triangle markers |
| 4 | Rate, Page, Remaining |
| 5 | Progress bar and percentage |
| 6 | Reading indicator, and Fwd / Back / Center / Full page |

### Stats

- **Rate** is words per minute, 50 to 1500, changed in steps of 25.
- **Page** is an estimate from the Words per page field (default 300). For text taken from a PDF it shows the real PDF page instead.
- **Remaining** is words left divided by the rate. It does not include Cut pauses, so it runs slightly short when Cut is on.
- **Progress** is the share of words read. Click anywhere on the bar to jump there.

## Settings

Shown in both views:

| Setting | What it does | Options |
|---|---|---|
| Mode | Words per flash | 1W, 2W, 3W, 4W |
| Align | Speed Read: anchors the word to the left, centre or right marker. Focal Read: aligns the text block | L, C, R |
| LUT | Paper tone, named after panel temperature | 0C cool, 20C neutral, 40C warm |
| Cut | Ends a flash at punctuation and holds there. Sentence ends get the full time; commas, semicolons, colons and dashes get half | Off, Auto 60ms, 120ms, 240ms |
| SPI | Refresh speed. Slower settings blank the word for the last part of each flash | 40MHz none, 20MHz 15%, 10MHz 30% |

Shown in Focal Read only:

| Setting | What it does | Options |
|---|---|---|
| Lines | Height of the reading area, in lines of text | 3L, 5L, 9L, 15L |
| Zoom | Text size | 75%, 100%, 125%, 150%, 200% |
| Track | Place moves the highlight down the text and flips the view when it runs off. Center keeps the highlighted line in the middle | Place, Center |

## Controls

| Action | Mouse or touch | Key |
|---|---|---|
| Start, pause, resume | Reading indicator, the reading area, or Center | Space |
| Jump 25 words | Fwd +25, Back -25 | Right, Left |
| Change rate by 25 WPM | − 25, + 25 under the rate | Down, Up |
| Jump to a point in the text | Click the progress bar | |
| Jump to a word (Focal Read, while paused) | Click the word | |
| Full page | Full page | F to toggle, Esc to leave |

The Reading indicator shows the current state: Start, Reading, Paused or Finished. Pressing it after Finished starts again from the top.

Reading pauses by itself when the browser tab is hidden. While reading, the page asks the browser to keep the screen awake where that is supported.

## Reading views

### Speed Read

One flash at a time, set large between the two rules. If a flash is too wide for the panel, it is shrunk to fit.

### Focal Read

The passage is shown as a block with the current flash highlighted. Rate, Mode, Cut, SPI, skipping and the progress bar all work the same way.

- The text fills the height of the reading area. Lines sets that height in the normal view; in full page the text fills all the spare space.
- The triangle markers on the rules follow the highlighted word.
- The block has its own scrollbar for looking ahead or back.
- For texts over 6,000 words, only about 4,000 words around the current position are in the block at once. The scrollbar covers that window. Use the progress bar to move further.

### Full page

Expands the panel to fill the browser window. Works with both views.

## Text sources

The tabs under the panel choose where text comes from. In every case the text lands in the text box, where it can be edited before pressing **Load text** again.

### Text

Paste or type, set a title, press **Load text**.

### PDF

1. Open the **PDF** tab and choose a file. Only the outline and page count are read at this point.
2. If the PDF has an outline, its chapters and sub-sections are listed with their start pages. Click one to extract and load just that section.
3. Otherwise, or as well, set a **From / To** page range and press **Extract pages**.

Details:

- A section runs until the next outline entry at the same or a higher level.
- Where the outline records a position on the page, the text is trimmed there, so a chapter that starts mid-page does not include the end of the previous one. This applies to unrotated pages; otherwise whole pages are used.
- One extraction is limited to 200 pages.
- Words hyphenated across a line break are rejoined.

### EPUB

Works the same way as PDF, with two differences:

- EPUBs have no fixed pages, so sections and ranges are counted in **parts**. A part is one file inside the book, usually a chapter.
- One extraction is limited to 50 parts.

Sections come from the book's table of contents and are trimmed at the exact heading when the table of contents points to one. Opening a book reads only the table of contents; images and stylesheets are never unpacked.

PDF and EPUB files are held separately, so switching tabs keeps each one open.

## What is remembered

Saved in the browser's local storage, on that device only:

- the loaded text and its title
- reading position
- all settings, the rate, and words per page
- which view and which source tab were open

PDF and EPUB files themselves are not saved. After a reload the extracted text is still there, but the file has to be chosen again to pick another section.

## Feature list

**Reading**
- Two views: single-flash Speed Read and highlighted-block Focal Read
- 1 to 4 words per flash
- Rate from 50 to 1500 WPM in steps of 25
- Automatic pauses at punctuation, with three lengths
- Optional blank between flashes
- Drift-corrected timing
- Auto-pause when the tab is hidden; screen kept awake while reading

**Navigation**
- Start, pause and resume from the indicator, the reading area, or the keyboard
- Skip forward and back 25 words
- Click-to-seek progress bar
- Click a word to jump to it in Focal Read
- Full-page mode

**Display**
- Left, centre or right alignment
- Three paper tones
- Light and dark themes, following the system setting
- Focal Read line count, zoom and tracking mode
- Measuring rules with markers that track the current word
- Live rate, page, time remaining and percentage
- Works at phone width

**Text sources**
- Pasted text, with paragraph breaks kept
- PDF by outline section or page range, with real page numbers
- EPUB by table-of-contents section or part range
- Extraction limited to the chosen section, never the whole file
- Extracted text is editable before loading

**Other**
- Position, text and settings restored on the next visit
- All processing in the browser

## Limitations

- **Scanned PDFs** have no selectable text and are reported as needing OCR.
- **Password-protected PDFs** cannot be opened.
- **Copy-protected EPUBs** are untested and are expected to fail or produce unreadable text.
- **Multi-column PDF pages**: the mid-page trim assumes a single column, so a section starting or ending partway down a multi-column page can be cut in the wrong place.
- **Hyphenation**: rejoining words split across lines will occasionally merge a genuine hyphenated compound.
- **Headers, footers and page numbers** in PDFs are extracted along with the body text.
- **PDF and EPUB need a connection** the first time each is used, to fetch the reader library.

## Technical notes

- One file, `speed-read.html`, containing all markup, styles and script. No build step and no server-side code.
- Libraries are loaded only when first needed:
  - [PDF.js](https://mozilla.github.io/pdf.js/) 3.11.174, from cdnjs
  - [epub.js](https://github.com/futurepress/epub.js/) 0.3.93, from jsDelivr
  - [JSZip](https://stuk.github.io/jszip/) 3.10.1, from cdnjs (required by epub.js)
- Fonts come from Google Fonts: Literata for reading text, Barlow Semi Condensed for labels, Barlow Condensed for figures. System fallbacks are declared for each.
- The file was written for a host that supplies the outer page wrapper. To serve it on its own, add `<!doctype html>`, `<meta charset="utf-8">` and `<meta name="viewport" content="width=device-width, initial-scale=1">` at the top.
- Saved state lives under the local storage key `speedread.v1`.
