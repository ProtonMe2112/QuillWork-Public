# QuillWork — User Manual

*Version: Beta (pre-release). This manual is kept up to date alongside the app and is what QuillWork's own **Help** shows (top bar > Help, or **Ctrl+K** then "User manual"). [Appendix A](#appendix-a-complete-function-reference) at the end lists every function, what it does and exactly how to reach it.*

QuillWork is a locally-run novel writing aid. It runs entirely on your own machine, talks to an AI model you control (LM Studio or Ollama), and keeps a structured "bible" of your novel's characters, world, and plot so the AI stays consistent with your story as it grows — even across books.

Nothing you write ever leaves your computer unless you choose to connect a cloud model.

---

## Contents

1. [Quick Start — Starting a New Manuscript](#1-quick-start--starting-a-new-manuscript)
2. [Quick Start — Importing an Existing Manuscript](#2-quick-start--importing-an-existing-manuscript) — includes [Importing from other tools](#21-importing-from-other-tools) ([Aeon Timeline](#211-aeon-timeline), [Obsidian](#212-obsidian), [Scrivener](#213-scrivener), [Scanned/photographed pages](#214-scanned-or-photographed-pages-ocr), [Word and ODT sync](#215-word-and-odt-sync))
3. [The QuillWork Window](#3-the-quillwork-window)
4. [Connecting an AI Model](#4-connecting-an-ai-model)
5. [Writing](#5-writing) — includes [Scenes](#57-scenes) (splitting a chapter, dialogue attribution)
6. [The Novel Bible](#6-the-novel-bible) — includes [Character voice, Dialogue fingerprint & Observed voice](#61-characters), [Possible duplicate characters](#61-characters), [Worldbuilding consistency checker](#67-worldbuilding), [Narrator beliefs](#68-narrator-beliefs), [Knowledge tracker](#69-knowledge-tracker), [Foreshadowing (Chekhov's Gun)](#610-foreshadowing-chekhovs-gun), [Facts & constants](#611-facts--constants), the [Research Workspace](#612-research-workspace), [Bible updates](#613-bible-updates), and [Author notes](#614-author-notes)
7. [Series — Sharing a World Across Multiple Books](#7-series--sharing-a-world-across-multiple-books)
8. [AI Writing Tools](#8-ai-writing-tools) — includes [Synopsis generator](#88-synopsis-generator), [Query letter](#89-query-letter), [Chat](#810-chat), [Pacing](#811-pacing), and [Story Analyst](#812-story-analyst) (events and causality, the health report, What if…, and the Patterns tab)
9. [Search Index — Working with Very Long Novels](#9-search-index--working-with-very-long-novels)
10. [Projects — Saving, Loading, Switching Novels](#10-projects--saving-loading-switching-novels)
11. [Exporting Your Novel](#11-exporting-your-novel) — includes [Book setup: front & back matter](#111-book-setup--front-and-back-matter) and [Manuscript format for submission](#114-manuscript-format--traditional-submission)
12. [Audiobook Narration](#12-audiobook-narration) — includes [Per-character voices](#123-per-character-voices)
13. [Saving, Autosave, and Closing QuillWork](#13-saving-autosave-and-closing-quillwork)
14. [Troubleshooting](#14-troubleshooting)
15. [Beta Testing, Feedback & Licensing](#15-beta-testing-feedback--licensing) — includes [Sending a beta report](#151-sending-a-beta-report), [Activating a license key](#152-activating-a-license-key), [Updating QuillWork](#153-updating-quillwork) and [Diagnostic capture](#154-diagnostic-capture)
16. [Reference — Anti-AI Prose Rules](#16-reference--anti-ai-prose-rules)
17. [Appendix A. Complete Function Reference](#appendix-a-complete-function-reference)

---

## 1. Quick Start — Starting a New Manuscript

**First launch:** the very first time you open QuillWork, a short **setup wizard** walks you through connecting your AI model and creating your first project — the steps below, guided. Its second step also offers **Quick AI setup**, which can choose and download an AI model for you (see [Section 4](#quick-ai-setup-optional)). You can reopen it any time from the command palette (**Ctrl+K → "Getting started"**). The installer, or QuillWork itself the first time it starts, also asks one question that only you can answer: whether to keep the Story Analyst up to date as you write, which uses your model in the background (see [Keeping it up to date as you write](#812-story-analyst)). If you'd rather set things up yourself, the manual steps are:

1. **Launch QuillWork.** Double-click `QuillWork.vbs` (silent, recommended) or `Start QuillWork.bat` (shows a console window — useful if something goes wrong). Your browser opens automatically to `http://localhost:5000`.
2. **Start LM Studio or Ollama** and load a model, if you haven't already (see [Section 4](#4-connecting-an-ai-model)).
3. Click **Projects** in the top bar → **New project**. Give it a title and genre (genre is optional and just informs the AI's tone — it doesn't restrict anything). If your genre matches one QuillWork recognizes (Fantasy, Science Fiction, Mystery/Thriller, Romance, Horror, Historical, Literary, Young Adult), World & style starts with a short list of genre-relevant prompts already in world-building notes, edit or delete them freely, they're just a starting scaffold, never fake content.
4. Click **World & style** in the sidebar and fill in whatever you already know: synopsis, author style notes (POV, tense, voice), world-building notes. You don't need to fill in everything — the bible grows as you write.
5. Click **New chapter** in the sidebar. This creates Chapter 1 and opens it in the editor.
6. Start writing directly, or use **Scene beat** at the bottom of the screen to have the AI draft a passage from a brief description (see [Section 8](#8-ai-writing-tools)).
7. As you introduce characters and locations, add them via **Characters** and **Locations** in the sidebar so the AI has them as reference for consistency in everything it writes afterward.

That's the whole loop: write (or generate a draft), the bible informs every AI call, QuillWork autosaves as you go.

---

## 2. Quick Start — Importing an Existing Manuscript

If you already have a manuscript written outside QuillWork, QuillWork can ingest the whole thing and build the bible automatically.

**Not sure which import you need?** Click **Bring in your writing** at the top of the sidebar (or press **Ctrl+K** and type "Bring in"; the first-run guide and the link at the top of the Import manuscript panel open the same window). It asks **What are you bringing?** and shows one line for each choice saying what it will and will not bring:

| You have | It takes you to | It brings | It does not bring |
|---|---|---|---|
| A Word or ODT document | Word/ODT sync ([2.1.5](#215-word-and-odt-sync)) | Your chapters, found from Heading 1 styles or clear markers such as "Chapter 1", and a Bible built from them | Any change to your file, which QuillWork only reads. Chapter detection is not guaranteed when the document has no clear headings |
| A text or Markdown file, pasted text, or photographed pages | Import manuscript (below) | The whole manuscript split into chapters, with a full Bible; photographed pages are read by OCR first and you check the text | Word or ODT files: use the Word or ODT choice for those |
| A Scrivener project | Scrivener ([2.1.3](#213-scrivener)) | A new project with every chapter of your Draft, and characters, places and plot threads read from your notes and research | Documents marked Exclude from Compile, unless you untick the box that skips them |
| An Obsidian vault of notes | Obsidian ([2.1.2](#212-obsidian)) | Characters, locations, relationships and plot threads found in your notes, added to the book you have open | Chapters: it brings notes, not chapters |
| An Aeon Timeline file | Aeon Timeline ([2.1.1](#211-aeon-timeline)) | Characters, locations, relationships and timeline events, added to the book you have open | Which chapter each event belongs to: you assign those afterwards |
| Nothing yet | The New project window | A blank book to write in from the first sentence | |

Nothing is imported from the chooser itself; you confirm in the importer it opens. It closes only with its own **Close** button, so a stray click never dismisses it.

The rest of this section describes the plain text import in detail.

1. Click **Projects → New project** first (or start from a blank project) — Import works on the current project.
2. Click **Import manuscript** in the sidebar (or choose **A text or Markdown file** in the chooser above).
3. Either:
   - **Drag and drop** a `.txt` or `.md` file onto the drop zone, or click it to browse, **or**
   - **Paste the full manuscript text** directly into the text box.
4. Give it a **Novel title** and click **Start import**.
5. QuillWork runs through several stages automatically, shown live as they complete:
   - **Chapter splitting** — uses the chapters your manuscript states for itself: any line that says "Chapter", or the same word in another language (Capítulo, Chapitre, Kapitel), followed by a number, whether written as 12, XII or "twelve", with or without a title after it and with or without Markdown or bold marks. A heading such as "Day 2" or "Part II" straight above a chapter stays with the chapter that follows it, and anything before the first chapter stays with chapter 1, so no text is dropped. The titles you gave your chapters are kept. Only a manuscript with no such lines falls back to looser markers (`***`, headings) and, as a last resort, an AI guess at natural breaks
   - **Per-chapter summarising** and **title suggestion**
   - **Character extraction**, deduplicated across chapters
   - **Location extraction**
   - **Worldbuilding extraction** — magic systems, factions, religions, languages, if the text establishes any
   - **Relationship mapping** between extracted characters
   - **Facts & constants**: quantitative details (ages, heights, prices, dates, distances) mined into [Facts & constants](#611-facts--constants), merged by name
   - **Plot thread identification**
   - **Synopsis generation**
   - **Search index build** — every chapter is embedded for semantic search (see [Section 9](#9-search-index--working-with-very-long-novels)), so the imported novel is immediately usable with the AI tools on very long manuscripts
6. When it finishes, the full bible is populated and every chapter is in the sidebar, ready to continue writing.

**Notes:**
- Import can take a while for a long novel — it's making many AI calls. Leave the tab open until it reports "Import complete!" Locations, worldbuilding, relationships, facts & constants and plot threads are five separate calls over the same text by default; **Combine locations, worldbuilding, relationships, facts and plot threads into one call when importing a manuscript** in Settings → AI model & connection reads them in one call instead, which is faster but asks more of your model at once. It is off by default, and the setting shows a note on whether your configured model's size on disk, and whether it fits your detected video memory, make that a reasonable trade to try — worth comparing a chapter's results both ways before trusting it for a whole import, since a model asked for five things at once can thin out one of them: a real comparison on a 14B model found it kept characters, locations and relationships intact but returned two plot threads where five separate calls found four.
- **Cancel import** stops it at any point and asks whether to keep what was found so far or discard it and restore the automatic snapshot taken just before the import began.
- The AI-extracted bible is a **starting point**, not gospel — review Characters/Locations/Relationships/Plot threads afterward and correct anything it got wrong or missed. This matters because every AI writing call afterward trusts the bible as fact.
- If you only have a single chapter to add to an *existing* QuillWork project (rather than a whole manuscript), use **Add written chapter** instead (see [Section 8.7](#87-add-written-chapter)) — it's the same idea but scoped to one chapter and merges into your existing bible rather than replacing it.

### 2.1 Importing from other tools

Bridges from other writing/plotting tools live under **Import from other tools** in the sidebar's Story section — click it to expand the submenu and pick a tool.

#### 2.1.1 Aeon Timeline

If you've been plotting in [Aeon Timeline](https://www.aeontimeline.com/), you don't have to re-type your characters, locations, or events by hand — **Aeon Timeline** in the submenu offers two ways in: your project's own `.aeon` file directly (no export needed), or a CSV export. The panel has a toggle at the top to switch between them.

**Native `.aeon` file (recommended):**

1. Open **Aeon Timeline** and, on the **Native .aeon file** tab, click to browse for your project's own `.aeon` file (the file itself, not a folder) — this opens your normal Windows file picker.
2. QuillWork scans it and shows how many characters, locations, relationships, and timeline events it found, plus how much other project content (clues, story notes, anything that doesn't fit those categories) there is to scan for extra detail. Nothing is imported yet at this point.
3. Click **Import into this book**. Because the native file has its own reliable type system — every item in an Aeon project knows whether it's a person, a location, or something else — characters, locations, and **real relationships** (using whatever relationship types you defined in Aeon, like "Participant" or "Witness", not just a generic description) are all extracted directly, no manual column mapping needed. Anything that doesn't fit those categories still feeds the same character/location/relationship/plot-thread extraction the manuscript importer uses. Everything is **merged into the book you currently have open** — nothing is replaced, and nothing creates a new project.
4. Both older and newer Aeon Timeline project file versions are supported.

**CSV export (if you'd rather not point at the project file directly):**

1. In Aeon Timeline, export **one CSV per type** you want to bring in — Characters, Locations, or Timeline Events (File → Export → CSV/TSV). Aeon lets you choose your own column names, so there's no fixed template to match.
2. On the **CSV export** tab, click to browse for the CSV.
3. QuillWork guesses **what the file contains** (Characters / Locations / Timeline events — a Start Date-like column is treated as a strong signal for events) and **which column maps to which field**, then shows you a preview of the first few rows plus a dropdown for every field so you can correct any guess before anything is saved. Nothing is written to your bible until you click **Import**.
4. Click **Import**. Characters and locations are matched by name against what's already in your bible, so re-importing the same file twice won't create duplicates. The CSV path has no relationships category — use the native file if you want those brought in too.

**About timeline events specifically:** Aeon's events use real calendar dates, but QuillWork's timeline is chapter/story-day based (see [Section 6.5](#65-timeline)) — there's no way to know which of *your* chapters an event belongs to, on either import path, so **chapter is never assigned automatically**; you'll want to open events afterward and assign chapters (and tag characters/plot threads) once you know where each one falls in your book. **Day** is handled differently between the two paths, though: the native `.aeon` file carries a real timestamp per event, so QuillWork computes a genuine relative day number for each one — day 1 is your import's earliest event, day 2 is one day later, and so on — instead of leaving every event on an identical "unknown day" (which, with a large import, used to collapse the whole Visual Timeline into one indistinguishable column). The CSV path doesn't have a reliable per-row timestamp to work from, so CSV-imported events still land with **no day assigned** (shown as "Ch.? · Day ?"); either way, the original date, summary, participants, and location from Aeon are always preserved in the event's own text.

#### 2.1.2 Obsidian

If your characters, locations, and plot notes live in an [Obsidian](https://obsidian.md/) vault, **Obsidian** in the submenu extracts them straight from your notes — the same extraction the manuscript importer uses, applied to your vault instead of a manuscript.

1. Open **Obsidian** and click to browse for your vault's top-level folder — this opens your normal Windows folder picker. QuillWork scans it and shows how many notes it found and roughly how much work it'll be — nothing is imported yet at this point.
2. Click **Import**. QuillWork reads every `.md` note in the vault (skipping Obsidian's own `.obsidian` and `.trash` folders, and anything else tucked in a dot-folder), and extracts characters, locations, relationships, and plot threads from the combined text, the same four passes manuscript import uses.
3. Everything found is **merged into the book you currently have open** — nothing is replaced, and nothing creates a new project. Review the results the normal way, in the Characters/Locations/Relationships/Plot threads panels.

**What gets cleaned up automatically before extraction:** YAML frontmatter is read for a note title (if you use one) and then stripped out; fenced code blocks (including Dataview query blocks) are removed entirely rather than fed to the AI as if they were prose. `.canvas` files aren't read — only `.md` notes. `[[wikilinks]]` are marked **bold** and `![[embeds]]` *italic* rather than read as plain text — a linked mention is more likely to be a real character or location than incidental text, so keeping it visually distinct helps both you and the extraction itself.

Since a vault can hold far more notes than a novel has chapters, take the note count QuillWork shows you seriously before starting — more notes means more AI calls and a longer wait, the same tradeoff as importing a very long manuscript.

#### 2.1.3 Scrivener

If your novel is written in [Scrivener](https://www.literatureandlatte.com/scrivener/), **Scrivener** in the submenu reads the project directly — unlike the Aeon and Obsidian bridges above, this builds a **brand-new QuillWork project**, the same way pasting a whole manuscript does, because a Scrivener Draft already *is* your manuscript, chapters and all.

1. Open **Scrivener** and click to browse for your project's **`.scriv` folder** (the folder itself, not a file inside it) — this opens your normal Windows folder picker.
2. QuillWork scans the project and shows how many chapters it found, the total word count, whether it found any research/notes content, and how many documents are marked **Exclude from Compile** in Scrivener (drafts, cut scenes, notes to self — if you have any, a checkbox appears letting you skip them, checked by default). Nothing is imported yet at this point.
3. Click **Import as new project**. Each top-level item in your Draft becomes one chapter — if it's a folder containing multiple scenes, they're stitched together in order; if it's a single document, that's the chapter as-is. Chapter titles from Scrivener are kept as-is (QuillWork only suggests a title itself if a chapter genuinely has none). If a document has no written prose yet, its synopsis card is used as a stand-in so outline-stage content isn't silently dropped. Everything else in the project — a Research folder, or any other folder you keep alongside the Draft (Characters, Places, Front Matter, whatever you've called it) — isn't turned into chapters, but does feed the same character/location/relationship/plot-thread extraction the rest of the manuscript gets, along with every document's own notes and any comments or footnotes you've attached to it via the inspector panel. Scrivener's own Trash folder is never read. Both the newer and older on-disk Scrivener project layouts are supported.
4. When it finishes, you're switched straight into the new project, same as any other import.

Footnotes, Word-style comments, and Scrivener's own inline footnotes and coloured Inline Annotations are all stripped out of your prose entirely before extraction — none of them are meant to be part of your finished manuscript, so none of them get fed to the AI as if they were.

**Linking your project for auto-sync.** Lower down in the same **Scrivener** panel, **Choose folder…** lets you point at your `.scriv` project's real folder on disk instead of uploading it — click **Link & import as new project** and QuillWork remembers that location so you never have to re-select it:

1. **Sync now** re-reads the linked project on demand and merges in only what's changed. Chapters are matched to their existing counterpart by **title** (not position, since reordering or inserting a chapter would shift that) — unchanged chapters are skipped entirely, so a sync only spends AI time on what's actually different. A chapter that's disappeared from Scrivener is never deleted automatically here either — it's flagged so you can remove it yourself if that's really what happened. A chapter you have edited in QuillWork since the last sync is never overwritten by an older copy from Scrivener: if only you changed it, your edit stays; if it changed in both places, QuillWork leaves your version exactly as it is and the sync message names the chapters it left alone.
2. QuillWork also checks the linked project **automatically in the background every 30 seconds**, so a chapter you save in Scrivener shows up in QuillWork on its own — no click needed, the same "notices on save" experience whether QuillWork is in the foreground or not.
3. **Unlink** stops the auto-sync. Anything already brought in stays in your project; nothing is removed.

#### 2.1.4 Scanned or photographed pages (OCR)

If your only copy of a manuscript is on paper — a scanned notebook, printed drafts, photos taken on your phone — **Choose page images…** in the main **Import manuscript** panel recognizes the text from one or more images and drops it straight into the paste box below, ready to review and correct before you import normally.

1. Select one or more page images (JPG, PNG, etc.) — multiple pages in one go are stitched together in the order you selected them, separated by a `--- page break ---` marker so you can see where one photo ended and the next began.
2. **Read through the result before importing.** OCR is never perfect — skewed photos, unusual fonts, or handwriting will introduce errors that a spellchecker won't necessarily catch, since a wrong-but-real word doesn't look "wrong." Fix anything that reads oddly, then click **Start import** as normal.
3. If a page comes back blank, QuillWork tells you so — try a clearer, better-lit, more level photo of that page.

**Windows:** the QuillWork installer sets this up for you automatically — it bundles Tesseract and configures it during setup if it doesn't find one already on your machine (an existing install is always left alone and used instead). There's nothing to install separately; OCR import just works out of the box.

**Linux:** the installer offers to install Tesseract via `apt` during setup if it isn't already present (on Debian/Ubuntu-based distros); on other distros it prints the right command for your package manager instead. Either way, install it, then set its path in **Settings → OCR import** if it isn't on your system PATH (click **Check** there to confirm QuillWork can reach it).

#### 2.1.5 Word and ODT sync

**Word/ODT sync**, in the same submenu, links a `.docx` (Word) or `.odt` (OpenDocument, from LibreOffice and others) file to your project and keeps it in sync, the same idea as Scrivener auto-sync above but for a single document, and read-only in both directions: QuillWork reads the file, never writes to it. Both formats work the same way; for an `.odt`, level-1 headings are the chapter breaks.

> **⚠ Read this before you link a file — chapter detection here is not guaranteed to be accurate.**
>
> A `.docx` or `.odt` has no built-in chapter structure the way a Scrivener project does. QuillWork looks for **Heading 1**-styled paragraphs first; if your document doesn't have at least two of those, it falls back to the same patterns manuscript paste-import already looks for ("Chapter 1", numbered markers, `***` scene breaks) — and if none of *those* are present either, an AI guess at natural breaks, which may not land on your actual chapter boundaries. If your manuscript doesn't consistently use headings or a clear marker convention, this feature may split it in ways you don't expect.
>
> Sync also matches chapters to your project by **title**. If you rename a chapter's heading in Word, the next sync is likely to create a new chapter rather than update the existing one — it won't know they're the same chapter.
>
> **You don't have to use this feature to bring a Word manuscript into QuillWork.** Copy-pasting into **Import manuscript**, or pasting a written chapter into **Add written chapter**, works exactly as well and doesn't depend on any of the above — you'd just be doing the sync step yourself instead of QuillWork doing it automatically.
>
> The app shows this same warning, unskippable, the first time you open this panel — this isn't just manual fine print.

If you've read that and still want it:

1. Open **Word/ODT sync** in the **Import from other tools** submenu.
2. Click **I understand, choose a file…** and pick your `.docx` or `.odt` in the native file dialog that opens.
3. Click **Link & sync**. QuillWork reads the file, matches what it finds to your project's existing chapters by title, and merges in whatever's new or changed — exactly like a Scrivener sync, including never deleting a chapter automatically if it's gone missing from the document (you'll just see it flagged). The same protection applies to your own edits: a chapter you have changed in QuillWork since the last sync is not replaced by an older copy from the document, and if it changed in both places QuillWork keeps your version and tells you which chapters it left alone.
4. From then on, **Sync now** re-reads the file on demand, and QuillWork also checks it automatically in the background (every 30 seconds) the same way it does for a linked Scrivener project — save the document in Word and the change shows up in QuillWork on its own, no click needed.
5. **Unlink** stops the syncing. Anything already brought in stays in your project; nothing is removed.

---

## 3. The QuillWork Window

QuillWork's interface has four regions:

| Region | Contents |
|---|---|
| **Top bar** | Project name, save status, **Autosave** switch, the theme button, a **Ctrl K** command-palette button, **Save**, **Export**, **Projects**, **Beta report**, **Settings**, **Help** (opens this manual inside QuillWork), and the **Close** button that shuts the server down cleanly |
| **Left sidebar** | Story tools (Import, Embed manuscript, Version history, Cloud backup) and the chapter list stay always visible; **Bible**, **AI Tools**, and **Submission** are collapsible sections — click a section header to expand or collapse it. (An **Audio** section appears only if you turn on audiobook narration in Settings.) A **Stop AI** button and a live AI-connection status sit at the bottom; click the status to open Settings. |
| **Main editor** | The chapter you're currently writing, in a distraction-light writing surface. A small **Research** tab sits at the top centre; pull it down to open the [Research Workspace](#612-research-workspace) |
| **Bottom bar** | Formatting tools (new paragraph, headings, table, embed image, source view, bold, italic, underline, strikethrough, colour), quick actions (Check, Refine, Mark as claim), a free-text append box, the Scene beat and Chat panels (which expand upward when opened), and the **Auto-analyse** switch that turns background analysis on or off |

Clicking any sidebar item other than a chapter opens a slide-out panel from the right. Only one panel is open at a time; press **Esc** or click **✕** to close it. **Esc** closes the frontmost thing first (an open edit window), then the panel underneath on the next press. Clicking outside a panel never closes it, on purpose, so a window that needs an answer can't be lost by accident. A **back arrow** at the top left of a panel means it was opened from inside another one, and takes you back.

The **Bible**, **AI Tools**, **Submission**, and **Audio** sections collapse by default to keep the sidebar short — click the section name to expand it. This is purely a display state and doesn't affect anything else; expand whichever sections you use most.

Hover over any button, control, or checkbox for a moment and a tooltip explains what it does — this covers the whole interface, so if you're ever unsure what something does, hovering is the fastest way to find out.

**Command palette (Ctrl+K).** Press **Ctrl+K** (or click the **Ctrl K** button in the top bar) to open a searchable list of every action, panel, and chapter. Start typing to filter, use **↑ ↓** to move, **Enter** to open, **Esc** to close — the fastest way to jump anywhere without hunting through the sidebar.

**Themes.** The sun/moon button in the top bar cycles between three themes — **Light** (warm paper), **Sepia** (dimmer and softer, easier on the eyes for long sessions), and **Dark** (warm near-black). Your choice is remembered between sessions. You can also set a specific theme from the command palette (search "theme").

**Interface language.** Settings has a Language section for the interface itself, separate from your novel's own language (World & style, section 6.6), which is what the AI writes in, not what QuillWork's own buttons, menus, tooltips and help text are shown in. QuillWork's own interface is available in English (UK and US), French, German and Spanish: choose one, confirm the **Change language?** window, and the page reloads in that language. About thirty languages are listed; for one without a translation yet, QuillWork keeps showing English and remembers your choice, then switches over on its own when that translation ships. This manual is always shown in English.

**Stop AI.** The button at the bottom of the sidebar force-stops any AI generation running right now, in any panel — even a scene beat, chat reply, or import you don't have open in front of you. It greys out when nothing's actually running and only turns active (red) while a real model call is in flight, so it's safe to ignore most of the time rather than something that looks like it needs attention. Clicking it asks you to confirm, then reports what it stopped: running AI calls, a multi-step import or scan that will stop at its next checkpoint (usually within seconds), or that nothing was running. It also stops the background Bible extraction described in [Section 4](#auto-extract-bible-info-as-you-write).

**Every function in one table.** [Appendix A](#appendix-a-complete-function-reference) lists everything QuillWork does, what each function does and exactly how to reach it, including every keyboard shortcut.

---

## 4. Connecting an AI Model

QuillWork doesn't include a model — it talks to a model you're already running locally via **LM Studio** or **Ollama**, using their OpenAI-compatible APIs. It never sends your text anywhere else unless you explicitly configure a cloud provider (not available in this beta).

### Quick AI setup (optional)

If you would rather not choose models yourself, **Settings > Quick AI setup** (the first section under License) can choose and download them for you. It is entirely optional, and **Skip, I'll set this up myself** hides it at any point. The first-run wizard links to it too: in step 2, "Connect your AI model", choose **Let QuillWork set this up for me**.

1. Click **Install Ollama**. This opens Ollama's official download page in your browser and switches QuillWork to the Ollama backend. QuillWork does not install, bundle or redistribute Ollama itself: install it as you would any program, and QuillWork checks every few seconds until it answers ("Ollama detected and running.").
2. QuillWork reads your graphics-card memory and system RAM and tells you what it will download: "Based on your hardware (tier), QuillWork will download: model". The tiers run from no dedicated graphics card up to 36 GB+ of VRAM, and each has its own writing model, vision model and, where there is spare headroom, a fast model.
3. Choose your options. **Include mature/uncensored writing support** is off by default; when on, an uncensored writing model is chosen instead of a standard one. **Also set up a vision model, for describing research images** is on by default. **Also set up a fast model, for quicker routine tasks** appears on tiers that have room for one.
4. Click **Set up now**. The models download through Ollama itself, with a progress bar, and QuillWork fills in each of your Model, Fast model and Vision model settings as soon as that model has arrived. A model Ollama already has is not downloaded again, and QuillWork says so.
5. **Cancel download** appears beside the button while it runs. Cancelling stops Ollama at once and keeps what it had already fetched, so **Set up now** carries on from where it stopped, not from the start.

**If something goes wrong, QuillWork says what happened and what to do, and never reports a download as finished unless Ollama confirmed it.** Your settings are never pointed at a model that did not arrive. Each of these leaves everything as it was, and pressing **Set up now** again is always the way forward:

| What happened | What you see | What to do |
|---|---|---|
| The disk fills up | Ollama ran out of disk space while downloading | Free space on the drive where Ollama keeps its models, then press **Set up now**. What was fetched is kept. |
| The connection drops, or Ollama stops or restarts | The download was interrupted, or the connection to Ollama was lost | Check the connection or that Ollama is running, then press **Set up now**. It carries on from where it stopped. |
| Ollama goes silent for ten minutes | Ollama stopped sending progress, so QuillWork stopped waiting | Check Ollama and the connection, then press **Set up now**. |
| The model has been renamed or removed from Ollama's library | Ollama's library has no model called "name"; nothing was downloaded | Choose a model yourself in Settings, or try again later. |
| The computer running Ollama cannot reach Ollama's library | It could not reach Ollama's model library (ollama.com) | Check that computer is online, then press **Set up now**. |
| You press **Cancel download** | Download cancelled; what was fetched is kept | Press **Set up now** to carry on. |
| Ollama is not running, or refuses the request | QuillWork could not reach Ollama, or Ollama refused the request | Start Ollama, or check its address and API key in Settings. |
| A download is already running (in another window, or before you reloaded the page) | A model download is already running | Wait, or press **Cancel download**. QuillWork runs one at a time. |

If the page loses contact with QuillWork while a download runs, it says so, and nothing is lost: press **Set up now** again. If you start the same download from two copies of QuillWork, Ollama joins them into one and installs the model once.
Two things worth knowing. Automatic setup needs the Ollama backend; with LM Studio you choose and load models yourself, as described below. And QuillWork never hosts or proxies a model file: every download comes from Ollama's own library, through your own Ollama. The recommendations live in a small data file that can be updated without a new release, so the picks can change as better models appear.

### Setting it up

1. Install and open [LM Studio](https://lmstudio.ai/) or [Ollama](https://ollama.com/), and load a model suited to your writing (long-context, uncensored-if-needed creative-writing models work best — see the [hardware guide below](#choosing-an-uncensoredcreative-writing-model-for-your-hardware), or let [Quick AI setup](#quick-ai-setup-optional) choose for you).
2. Open **Settings** (**Settings** in the top bar, or click the connection status at the bottom of the sidebar) and go to **AI model & connection**. Choose **LM Studio** or **Ollama**. Every field here has plain-language help beneath it — you can usually leave the address and API key at their defaults.
3. The **Endpoint URL** defaults to the right value for each (`http://localhost:1234/v1` for LM Studio, `http://localhost:11434/v1` for Ollama) — only change this if you're running the backend on a different machine or port.
4. If your backend requires an API key (LM Studio 0.4.0+ supports optional token auth), enter it in the **API key** field.
5. Click **Test**. The dot next to "LM Studio"/"Ollama" turns:
   - 🟢 **Green** — connected, model(s) available
   - 🟡 **Amber** — QuillWork reached the backend but no model is currently loaded (common with LM Studio's just-in-time loading — load a model and click Test again, or just proceed — it may load automatically on first use)
   - 🔴 **Red** — can't reach the backend at all; check LM Studio/Ollama is running and the endpoint URL is correct

   Underneath the dot, a plain-language diagnosis box explains exactly what it checked and what to do next — not just "reachable or not," but whether the *specific model* selected below is actually available and loaded right now. This catches the case a green dot alone can miss: the dot only ever proves QuillWork can list LM Studio/Ollama's models, not that the one chosen in Settings is real, loaded, or the one you meant.
6. Pick your model from the dropdown that populates after a successful Test. Not sure which model to run? Click **"See the hardware-based model guide"** right below the dropdown to jump straight to [the section below](#choosing-an-uncensoredcreative-writing-model-for-your-hardware) matched to your VRAM/RAM.

> **Ollama users, one thing to double-check:** if you've also pulled an embedding model (e.g. `nomic-embed-text`, used for the search index) alongside your writing models, it will appear in this same dropdown with no visual distinction from a real chat model — Ollama doesn't expose the information QuillWork would need to tell them apart automatically. LM Studio does filter these out, but Ollama's model listing has no equivalent. If Chat or Scene beat suddenly stops responding, check Settings and confirm the **Model** field is actually pointed at a chat/instruct model, not an embedding one.

> **A green dot means the connection works — it doesn't mean every request will fit.** The Test button only ever sends a tiny request (asking for the model list), so it can't tell you whether a *real* generation — your full bible, retrieved manuscript context, and the passage itself — will actually fit in your model's loaded context window. A model with a small context and a detailed bible can go from "connected, model loaded, everything green" straight to a request that's too large, with nothing in between to warn you. QuillWork checks this separately, immediately before every generation, and tells you plainly if a request won't fit rather than leaving you waiting on it — see [Troubleshooting](#14-troubleshooting) and [Models with a larger context window](#models-with-a-larger-context-window) if you see that message.

### Connecting across machines, WSL, or Docker

The defaults above (`localhost:1234` / `localhost:11434`) only work when QuillWork and your LM Studio/Ollama backend are the same machine talking to itself. Running them apart takes a bit more setup on both sides:

- **Backend on a different physical machine on your network:** in the **Endpoint URL** field, replace `localhost` with that machine's LAN IP (e.g. `http://192.168.1.50:1234/v1`). You'll also need to tell LM Studio/Ollama to actually listen for connections from other machines, not just itself — LM Studio: Settings → Developer → allow connections from the local network; Ollama: set `OLLAMA_HOST=0.0.0.0` before starting it. Check your firewall isn't blocking the port either.
- **Backend running inside WSL, QuillWork running on Windows (or vice versa):** WSL2's networking means `localhost` doesn't always mean the same thing on both sides. From Windows reaching into WSL, try the WSL instance's actual IP (`wsl hostname -I` from a Windows terminal) instead of `localhost`. From WSL reaching out to a Windows-side LM Studio/Ollama, the same logic in reverse — WSL2 typically resolves `localhost` back to Windows automatically for outbound connections, so that direction usually works with no change.
- **Backend running in a Docker container:** point the Endpoint URL at whatever the container publishes on the host (e.g. `-p 1234:1234` means `http://localhost:1234/v1` from the host still works). If QuillWork itself is *also* containerized and needs to reach a backend on the host machine, use `host.docker.internal` in place of `localhost` in the Endpoint URL (Docker Desktop on Windows/Mac supports this out of the box; on Linux you may need `--add-host=host.docker.internal:host-gateway` when starting the container).

Whatever the setup, the same **Test** button and diagnosis box above apply — a cross-machine connection that's actually working looks identical to a local one once it's green.

### Optional: a second "fast" model for analytical work

Below the main model dropdown is a **Fast model** selector. This is optional, and defaults to *"same as main"* — leave it there and QuillWork uses one model for everything.

If you set it, QuillWork uses that model for **analytical, low-creativity tasks** — chapter summaries, continuity checks, the Un-AI scanner, the extraction steps during Import, and **Chat** — while your **main model handles all the creative writing** (Scene beat, Refine, Plot ideas, A → B bridge). Because both models run locally, there's **no per-call cost to running two at once** — you can pair a large, slow model for prose with a small, fast one for the routine checks, and the fast tasks stop tying up your big model. (Whether both can be loaded simultaneously depends on your VRAM and how LM Studio/Ollama manages loading.)

**Story Analyst: what the Fast model reads.** Under the Fast model selector, two tick boxes say which Story Analyst steps go to the Fast model. **Events** is on by default: listing what happens in a scene is work a small model does nearly as well as a large one and far faster. **Who knows what, and how events cause each other** is off by default, because small models are much less reliable at it: on the same scene an 8B model gave the same events as a 24B model in about a tenth of the time, but the number of who-knows-what rows swung from 1 to 13 between runs and a 4B model gave no usable links at all. Tick it if your Fast model is a strong one. It only saves time if the Fast model has room of its own: a computer that can hold both models in memory at once, one that swaps models as they are asked for, or a Fast model on another computer. On one graphics card that cannot hold both, keeping both loaded makes each slower (on a 12 GB card, analysing one 500-word scene took about 1.3 times as long with both models loaded, 742 seconds against 567, as with the main model alone), so in that case leave the Fast model on "same as main". Everything that judges, meaning what a scene means, the questions it raises and answers, what job it does and the check of whether each quote shows what a result says, always uses your main model. With no separate Fast model nothing changes and one model does everything. When the two are different models, the analysis reads every scene with the Fast model first and then judges every scene with the main one, so a computer that can hold only one model at a time swaps once, not once per scene.

**Run a scene's passes together instead of one after another.** Also under Settings → AI model & connection: each scene is normally read several times over during analysis, once for its events, once for who knows what, and so on, one after another. Turning this on asks for five of them (scene facts, events, who-knows-what, questions and scene function; two more, mapping causality and checking each quote, always follow after, since they need those five already written) at once instead. It is off by default and shows a note built from your configured model's size and whether it fits your detected video memory: this is faster when your model fits entirely on your graphics card, and slower when it does not, because the card becomes the one thing every request is waiting on. A real comparison on a model that fits found it took about a third less time on the same scene; it is your choice, and QuillWork does not switch it on for you.

**Fast model on a different server.** Under the Fast model selector, switch on **Run the Fast model on a different server** if the Fast model lives in another program or on another computer, for example your main model in LM Studio on this machine and a small model in Ollama on another one. Choose the program, enter that server's address and, only if it asks for one, its API key, then click **Test**. QuillWork lists the models on that server so you can pick the Fast model, and sends routine jobs there while your writing still goes to the main server. Each server has its own key, and the main server's key is never sent to the other one. Your text goes to whichever address you enter, so use only a server you trust. The memory bars under Your hardware count only this computer, so a Fast model on another machine is left out of them. Switching the option off returns everything to the main server.

Model choice matters a lot for prose quality — this is a local generation tool, so the model you load *is* the writer. QuillWork's prompt engineering (see [Section 16](#16-reference--anti-ai-prose-rules)) pushes any model toward more human prose, but a stronger base model will always sound better. [Choosing a model: what it changes in QuillWork](#choosing-a-model-what-it-changes-in-quillwork) explains what the model decides in each part of the app and where it can run.

### Your hardware, and whether the models will fit

Under the Model dropdown, **Your hardware** shows your graphics card, its VRAM and your system RAM. RAM is read from your computer. VRAM is read from NVIDIA's own tools, so it is detected automatically only on NVIDIA cards; if yours isn't detected, a **GB VRAM** box appears so you can enter it yourself. Once a main model is chosen, two bars show **GPU VRAM** and **System RAM** as used over total gigabytes: your main model fills VRAM first, a separate fast model takes what is left, and anything that doesn't fit spills into the RAM bar (the legend marks Main model and Fast model). The bars update as you change either dropdown, work even when your AI backend is offline, and are guidance only: they never stop you choosing a model.

### Optional: a vision model

Next to Fast model is **Vision model** (default "none configured"). Pick a model that can see images if you want the [Research Workspace](#612-research-workspace) to describe what you upload (look for "VL" or "vision" in the name). With LM Studio, QuillWork can swap your writing model out for the vision model while it describes an image, then swap back, so the two never need to fit in memory together. With Ollama the vision model is used directly.

### Max tokens (advanced)

Under the model settings, **Writing model default** and **Fast model default** set how long a single reply may be. Leave both blank and QuillWork uses its own tuned limit for each feature. Raise them only if a reasoning model returns empty results: its "thinking" uses up the budget before it writes the actual answer. The Story Analyst sizes its own limit to the scene it is reading, and asks again with more room if a reply is still cut off, unless you have set a limit here, in which case it tells you the reply was cut off and leaves your limit alone. A step that goes to your main model because you have a Fast model set uses the Writing model default, and the message names that box. Each has an **Unlimited (let the server decide)** tick that sends no limit at all, so LM Studio's or Ollama's own setting applies.

### Auto-extract Bible info as you write

**Auto-extract Bible info as I write** (Settings > AI model & connection) is on by default. While you write, once a chapter has grown by roughly 150 words, and at most once every three minutes per chapter, QuillWork quietly runs its character, location, relationship, fact and plot-thread extraction in the background. Brand-new entries are added outright; anything that would change an existing character or location goes to [Bible updates](#613-bible-updates) for you to review. It uses extra AI calls while you write, so turn it off if you would rather trigger extraction yourself with **Re-scan bible** in the chapter header.

### Three more Settings switches

- **Keep the Story Analyst up to date as I write** (off until you choose): analyses chapters whose text has changed, in the background, when you have paused and are not using the model. The installer asks whether you want it, and so does QuillWork the first time it starts if you skipped that or updated from a version that did not have it. It is the same switch as **Auto-analyse** beside Scene beat at the bottom of the screen. See [Keeping it up to date as you write](#812-story-analyst). It is many model calls, so turn it off if you would rather run the analysis yourself.
- **Check continuity when I approve a Scene beat draft** (off by default): after you approve a generated passage, QuillWork runs a continuity check on just that passage in the background and shows the result in a small card that never blocks you. It uses the model straight after you approve, which is why it is off unless you ask for it.
- **Count dialogue I reworked from AI drafts in voice fingerprints** (off by default): a character's voice fingerprint measures only the dialogue you wrote yourself, so QuillWork's own output can never quietly become their recorded voice. Turn this on to also count lines you started from an AI draft and then edited. Lines you approved without changing are never counted.

### Choosing a model: what it changes in QuillWork

QuillWork doesn't include a model. It uses whichever one you connect, and that choice decides how good most of what you see is. The same manuscript put through a small model and a large one gives visibly different prose, different summaries and a different Story Analyst. Nothing is broken when that happens. It is the model, so it is worth choosing on purpose.

#### What the model decides

| Part of QuillWork | What the model decides | What a weak model tends to do |
|---|---|---|
| Scene beat, Refine, Plot ideas, A to B bridge | The prose itself: voice, variety, how closely it follows your bible and your style | Generic wording, repeated phrases, forgotten details from the bible, drifting away from your voice |
| Chat, chapter summaries, continuity checks | Whether what it tells you about your own book is accurate | Missing a real problem, or reporting one that isn't there |
| Import and Bible extraction | Which characters, places and facts it finds, and how it links them | Missed entries, duplicates, wrong relationships (you review these before they change anything) |
| Story Analyst | How well each scene is read into events, who knows what, how events cause each other, and the questions a scene raises | Fewer events, invented links, and "could not be read" messages when the model cannot give a properly structured answer |
| Research Workspace images | How well an uploaded image is described | Vague or wrong descriptions (only the vision model matters here) |

Writing and reading are different jobs. A model can write pleasant prose and still read a scene badly, and the other way round. That is why QuillWork lets you set a separate [Fast model](#optional-a-second-fast-model-for-analytical-work) for routine reading.

#### Size, quantisation and what they cost you

- **Size (the "B" number).** More parameters generally means better understanding, better prose and fewer mistakes, and more memory. In our own testing on one scene, an 8B model listed the events of a scene about as well as a 24B model in a fraction of the time, but it was unreliable at who knows what and at how events cause each other, and a 4B model produced no usable links at all. That is one scene, so take it as a pointer, not a rule: the more a task needs judgment, the more a bigger model helps.
- **Quantisation (`Q8_0`, `Q4_K_M` and so on).** This is compression. The [table of suffixes](#understanding-the-model-suffixes) below explains each one. As a rule of thumb, a larger model at `Q4_K_M` usually beats a smaller model at `Q8_0`, and very low settings (`Q3` and below) are where careful, structured work such as the Story Analyst starts to suffer first. Use the lowest setting only to squeeze a model in that would not otherwise fit.
- **Instruct or chat versions.** Choose a model labelled "Instruct" or "Chat". A raw base model does not follow QuillWork's instructions reliably.
- **Uncensored or standard.** A standard "safety-tuned" model may refuse or soften mature or violent scenes, and may also decline to analyse them, which leaves gaps in what the Story Analyst reads. If your book has that material, use an uncensored or abliterated model (see the [hardware guide](#choosing-an-uncensoredcreative-writing-model-for-your-hardware)).

#### Reasoning ("thinking") models

Some models write out a stretch of reasoning before they answer. They can be good at judgment work, but they are slower, and the reasoning uses up part of the length limit before the answer begins. If one returns empty or cut-off replies, raise **Max tokens** ([see above](#max-tokens-advanced)). For creative writing, a plain non-reasoning model is often faster and no worse, so it is worth trying both on the same scene before you commit.

#### Context window

The context window is how much the model can hold at once: your bible, the surrounding manuscript and the passage. A small window is the usual reason QuillWork says a request will not fit. See [Models with a larger context window](#models-with-a-larger-context-window).

#### Vision models

A vision model is only used to describe images in the Research Workspace. It plays no part in your writing or in the Story Analyst, so it does not need to be big, and the quality of your prose does not depend on it. See [Optional: a vision model](#optional-a-vision-model).

#### Where the model runs: this computer, your network, or the internet

| | On this computer | On another computer you own | A hosted service on the internet (planned, not yet supported) |
|---|---|---|---|
| **Privacy** | Your text never leaves your machine | Your text stays on your own network | Your text is sent to the company running the service |
| **Speed** | As fast as your graphics card allows | As fast as that computer allows, so a stronger machine can serve a weaker one | Usually the fastest, and the largest models are available |
| **Cost** | Free after the download | Free after the download | Usually charged by use |
| **Rules on content** | Yours (choose an uncensored model if you need one) | Yours | The provider's, which can be strict about mature material |

**Privacy and speed pull in opposite directions.** If you are working on unpublished, contracted or sensitive writing, keep the model on your own computer or your own network. If speed matters more to you than privacy, or your machine cannot run a model good enough for the job, the way to get both speed and privacy is a stronger computer of your own on your network. It is your decision, and QuillWork does not stop you.

- **On this computer:** the default, and fully supported.
- **Another computer on your network:** enter that computer's address in **Endpoint URL**. See [Connecting across machines, WSL, or Docker](#connecting-across-machines-wsl-or-docker). You can also put only the Fast model there. This is supported.
- **A hosted service on the internet:** this is on the roadmap as an optional, off-by-default choice with a plain warning about what leaves your computer, and it is not built yet. Today QuillWork supports LM Studio and Ollama and has been tested only with those. The Endpoint URL and API key fields are open, so a service that offers an OpenAI-compatible interface may work if you enter its address and key by hand, but QuillWork has not tested it, does not warn you when you do it, and cannot promise it will work. If you try it anyway, you are choosing speed over privacy, and the points below apply to you.

If you point QuillWork at a hosted service by hand, know these things:

- **Everything QuillWork sends goes to that address.** That includes chapter text, your bible, and the passage. It is not limited to the paragraph you are working on.
- **Read the provider's terms on keeping your text and on training.** Terms for a service's programming interface are often different from those of its chat website, and they change.
- **A whole-novel analysis is a lot of requests.** The Story Analyst makes several calls for every scene. On a service that charges by use, check the price and any rate limits before you run it on a full manuscript.
- **The provider's content rules apply.** A hosted model may refuse scenes a local uncensored model would write.
- **A key is a password.** Anyone with it can spend your money. Do not share a project or settings file that contains one.

#### Guardrails: getting reliable results

1. **Start from the recommendation for your hardware,** or let [Quick AI setup](#quick-ai-setup-optional) choose. Change one thing at a time (the model, or its quantisation, or the context length), so you know what made the difference.
2. **Try a chapter you know well before you run a whole book.** Read a few results against the text. Ten minutes here saves an evening.
3. **Don't judge a model on one run.** Results vary from run to run, small models most of all. If a result matters, run it twice.
4. **Watch the amber marks and the Evidence check.** They exist because models sometimes claim more than the quoted words show. A few are normal. If a large share of one kind of result is flagged, that is your sign to try a stronger model for that job, not to trust it more.
5. **Switching models does not redo the work already done.** The Story Analyst keeps what it has read and skips any scene whose text has not changed, even if you have changed model since. To have the new model read everything again, use **Re-analyse everything** ([More run options](#812-story-analyst)). Otherwise different chapters of the same book will have been read by different models.
6. **A stronger model still gives readings, not facts.** Analyst results are AI-judged. The quote tells you where the model looked. It does not prove the model was right.
7. **Save your best model for prose.** Give routine and mechanical jobs to the Fast model, and only if it has memory of its own (see [the Fast model section](#optional-a-second-fast-model-for-analytical-work) for when this saves time and when it does not).
8. **If one job fails again and again, suspect the model.** Repeated "could not be read" errors usually mean the model is too small, too compressed, or a reasoning model running out of length. Try a larger or less compressed one, or raise Max tokens.

### Choosing an uncensored/creative-writing model for your hardware

Fiction — especially anything mature or explicit — needs an *uncensored* or *abliterated* model; a standard "safety-tuned" model will refuse or soften scenes regardless of how you prompt it. The right model also depends on how much VRAM (GPU memory) and system RAM you have. The tables below cover three common setups; find the one closest to yours.

#### 12 GB VRAM / 16 GB RAM

**High tier — fits fully in VRAM, fast:**
- `Qwen 2.5 14B Uncensored` (`Q5_K_M`) — the sweet spot for 12 GB VRAM; smart roleplay, handles 32k context, fits entirely in GPU memory.
- `Llama 3.1 / 3.3 8B Uncensored` (`Q8_0` or `FP16`) — maximum precision, very fast, up to 64k+ context without exceeding your VRAM.
- `Mistral 7B` / `Nemo 12B Abliterated` (`Q8_0`) — descriptive, high prose quality, snappy generation.

**Mid tier — partial CPU offload to your 16 GB RAM, still decent speed:**
- `Qwen 2.5 32B Uncensored` / `Gemma 2 27B Abliterated` (`Q4_K_M`) — splits ~10–15 layers into VRAM, the rest into RAM; around 5–10 tokens/sec.
- `Dolphin 2.9.2 Mixtral 8x7B` (`Q4_K_M`) — Mixture-of-Experts, only runs two 7B "experts" at a time, leans on your 16 GB RAM for storage while staying reasonably fast.

More RAM than that widens this tier rather than unlocking a new one: the same 27B–32B-class models just get more headroom to raise quantisation or context length, and a 70B-class model starts becoming viable with 64 GB+ system RAM to offload into.

#### 16 GB VRAM / 32 GB RAM

**High tier — fits fully in VRAM:**
- `Qwen 2.5 14B Uncensored` (`Q8_0`) — the gold standard for this setup; maximum precision with room to spare for a large context window.
- `Mistral Nemo 12B` / `Starling-LM 11B Uncensored` (`Q8_0`) — excellent prose variety and creative flow.
- `Llama 3.1 / 3.3 8B Uncensored` (`FP16` or `Q8_0`) — blazing fast, virtually unlimited context (up to 64k+).

**Mid tier — fits tightly, needs a low context limit:**
- `Gemma 2 27B Abliterated` (`IQ4_XS` or `Q3_K_M`) — exceptional depth and logic, but keep context under 8k tokens to avoid crashing.
- `Qwen 2.5 32B Uncensored` (`Q3_K_L` / `IQ4_XS`) — very articulate, but tightly VRAM-constrained.

**Partial CPU offload — relies on your 32 GB RAM:**
- `Dolphin 2.9.2 Mixtral 8x7B` (`Q4_K_M`) — its MoE design keeps this running decently despite the offload.
- `Command R 35B Abliterated` (`Q3_K_M`) — highly creative roleplay, split across both memory pools, 5–15 tokens/sec.

#### 24 GB VRAM / 64 GB RAM

**High tier — fits fully in VRAM:**
- `Qwen 3.6 27B` / `Qwen3 32B Uncensored` (`Q4_K_M` / `IQ4_XS`) — top-tier generalist for roleplay, handles long context gracefully.
- `Gemma 4 26B` / `Gemma 3 27B` (Abliterated/Uncensored `Q4_K_M`) — exceptional depth and nuance, right at the 24 GB ceiling.
- `Dolphin 2.9.2 Mixtral 8x7B` (`Q5_K_M`) — reliable, heavily-trained MoE model, runs very fast on 24 GB.
- `Command R+` (Abliterated/Uncensored `IQ2_XXS` or `IQ3_XS`) — unmatched multi-turn coherence if you can fit it.

**Mid tier — blazing fast, small VRAM footprint:**
- `Dolphin Qwen 3 14B` / `Qwen3 14B Uncensored` (`Q8_0`) — flawless prose at near-maximum precision.
- `Llama 3.1 / 3.3 8B Uncensored` / `Llama-3-8B-Lexi-Roleplay` (`Q8_0`) — the gold standard for light roleplay, maximum speed, room for huge context.
- `Mistral Small 3` / `Starling-LM-7B` (Uncensored/Abliterated `Q8_0`) — snappy, deep vocabulary, fully maximizes 8-bit precision.

**Deep CPU offload — smartest, but slow:**
- `Llama 3.3 70B Uncensored` (`Q4_K_M`) — smartest logic available, but spills from 24 GB VRAM into 64 GB system RAM, dropping to single-digit tokens/sec.

#### Understanding the model suffixes

| Suffix | What it means | Impact |
|---|---|---|
| `7B`, `14B`, `70B` | Model size (billions of parameters) | Bigger = smarter and better prose, but exponentially more VRAM. |
| `FP16` / `BF16` | Uncompressed, original 16-bit precision | Highest quality, largest file size. Rule of thumb: parameters (B) × 2 ≈ required VRAM in GB. |
| `Q8_0` | 8-bit quantisation | Compressed to half the original size, near-perfect quality retention. |
| `Q4_K_M` | 4-bit quantisation (medium) | The community standard — slashes VRAM by 70%+ with only minor quality loss. Best balance of speed and smarts. |
| `Q3_K_M` / `IQ4_XS` | 3-bit or extreme compression | Noticeable quality drop; only used to force a large model into limited VRAM. |

**K-quant vs IQ:** `K` (K-quant) is the standard llama.cpp compression method — it groups weights into blocks, keeping the important data accurate and compressing the rest. `_S`/`_M`/`_L` (small/medium/large) are size variants within the same bit-rate — `_M` is usually the sweet spot. `IQ` (Importance Matrix Quantisation) is a newer method that uses a "cheat sheet" during compression to protect the model's most vital logic paths, which is what lets very small quantisations (`IQ2`–`IQ4`) still perform well; `_XS` (extra small) is the tightest of these, aimed at squeezing under strict VRAM limits like 8 or 12 GB.

**FP vs BF:** `FP16` is the standard 16-bit floating-point format used to train most models. `BF16` (Bfloat16, from Google Brain) packs the same dynamic range as 32-bit industrial formats into 16 bits — most modern models (Llama 3, Qwen 2.5, etc.) are natively trained in `BF16` because it handles complex logic better than plain `FP16`.

#### Will a model fit in your VRAM?

```
Required VRAM (GB) ≈ (parameters in billions × quantisation bits ÷ 8) + 4 GB (context & OS overhead)
```

Example: a 14B model at 4-bit (`Q4_K_M`) needs roughly `(14 × 0.5) + 4 = 11 GB` — comfortable on a 12 GB card.

#### Offloading to system RAM

When a model doesn't fit in VRAM, LM Studio/Ollama split its layers between your GPU and system RAM:

| Strategy | VRAM | RAM | Speed |
|---|---|---|---|
| Full VRAM | 100% of layers | 0% | Blazing (30–90+ tokens/sec) — real-time. |
| Partial CPU offload | 40–70% of layers | 30–60% | Usable (5–15 tokens/sec) — like a fast-typing text message. |
| Deep CPU offload | Under 20% of layers | Over 80% | Sluggish (1–4 tokens/sec) — slow, best for long-form generation you can walk away from. |

#### Cheat sheet

When shopping for a model file on Hugging Face:
- **`Q4_K_M`** = 4-bit, K-quant, medium size — your safest default pick.
- **`IQ4_XS`** = 4-bit, importance-matrix quantised, extra small — best if you're right on the edge of running out of VRAM.

#### Models with a larger context window

If Scene beat, Refine, or another AI tool refuses a request with a message about not having enough room in your model's context window, that's not a bug — QuillWork checks this *before* it starts generating, so you're not left waiting for a passage that would just get cut off partway through anyway (see [Section 14](#14-troubleshooting)). Your bible, retrieved manuscript context, and the passage itself all have to fit together in one window, and a detailed bible on a novel with a lot of characters can genuinely eat most of a small one.

You have two ways to fix it: shorten the request (a smaller target length in Scene beat, or a leaner bible), or load a model with more headroom to begin with. The models below are a solid, verified starting point — all with a native context window of 128K tokens or more, several of them at sizes that already fit the same VRAM tiers covered above. VRAM figures use the same formula as [above](#will-a-model-fit-in-your-vram): `(parameters × bits ÷ 8) + 4 GB`.

| Model | Context | VRAM (`Q4_K_M`) | VRAM (`Q8_0`) | Notes | Download |
|---|---|---|---|---|---|
| Llama 3.1 8B Instruct (abliterated) | 128K | ~8 GB | ~12 GB | Fast, fits almost anywhere — the safest first stop if a small-context model is turning you away. | [Hugging Face](https://huggingface.co/mlabonne/Meta-Llama-3.1-8B-Instruct-abliterated-GGUF) |
| Command R7B (abliterated) | 128K | ~7.5 GB | ~11 GB | Built for long, coherent multi-turn context — a good fit for chat-heavy sessions as well as long scenes. | [Hugging Face](https://huggingface.co/bartowski/c4ai-command-r7b-12-2024-abliterated-GGUF) |
| Mistral Nemo 12B (abliterated) | 128K | ~10 GB | ~16 GB | Strong prose variety at a moderate size — a good middle ground between the 8B and 14B/32B tiers. | [Hugging Face](https://huggingface.co/mradermacher/Mistral-NeMo-12B-Abliterated-i1-GGUF) |
| Qwen 2.5 14B Uncensored | 128K | ~11 GB | ~18 GB | The same model already recommended [above](#12-gb-vram--16-gb-ram) for 12–16 GB VRAM — no trade-off needed, it already has the headroom. | [Hugging Face](https://huggingface.co/bartowski/Qwen2.5-14B_Uncensored_Instruct-GGUF) |
| Qwen 2.5 32B (abliterated) | 128K | ~20 GB | ~36 GB | Noticeably smarter prose if you have the VRAM (or RAM to [offload](#offloading-to-system-ram) into). | [Hugging Face](https://huggingface.co/mradermacher/Qwen2.5-32B-Instruct-abliterated-GGUF) |
| Qwen 2.5 7B / 14B Instruct-1M | Up to 1M | ~7.5 / ~11 GB | ~12 / ~18 GB | Qwen's own long-context release — genuinely enormous context, but **not** uncensored out of the box; expect it to be more conservative with mature content than the abliterated options above. | [7B](https://huggingface.co/bartowski/Qwen2.5-7B-Instruct-1M-GGUF) · [14B](https://huggingface.co/bartowski/Qwen2.5-14B-Instruct-1M-GGUF) |

> A bigger context window doesn't have to mean a bigger model — several of these already sit in the same 12–16 GB tier covered earlier. If you're already running one of them and still seeing the warning, the fix is on the other side: shorten the request, or trim how much of your bible QuillWork is pulling into a single scene.

---

## 5. Writing

### 5.1 Opening and creating chapters

Click **New chapter** in the sidebar to add a chapter (numbered automatically). Click any chapter in the list to open it — QuillWork autosaves the chapter you're leaving before switching.

To delete a chapter, hover over it in the sidebar list — a faint **✕** appears on the right. Click it and confirm. This permanently removes the chapter's text and its entry in the search index; it cannot be undone. Deleting the chapter you currently have open returns the editor to its empty "no chapter open" state.

**Reordering and interludes.** Hover a chapter in the sidebar to reveal **↑** and **↓** arrows; each swaps the chapter's number with its neighbour's and renumbers both. The booklet icon in the chapter header marks a chapter as an **interlude**: it exports without the "Chapter N:" heading prefix, but still counts for search, extraction, continuity and pacing.

**The Bible keeps itself up to date as you write.** With **Auto-extract Bible info as I write** switched on (it is on by default, in Settings > AI model & connection), QuillWork quietly runs its character, location, relationship, fact and plot-thread extraction in the background once a chapter has grown by roughly 150 words, and at most once every three minutes per chapter. Brand-new entries are added outright; anything that would change an existing character or location goes to [Bible updates](#613-bible-updates) for you to review. It uses extra AI calls while you write, so turn it off if you prefer to trigger extraction yourself. Whatever your setting, the **Re-scan bible** button in the chapter header (after a confirmation) opens Add written chapter pre-filled with that chapter's saved text, so you can run the same extraction on demand.

### 5.2 The editor

The main editor is a distraction-light writing surface. Type directly, or use the formatting bar at the bottom:

- **¶** — insert a new paragraph break
- **H1** / **H2** / **H3** — make the current paragraph a heading or sub-heading (click again to undo)
- **Table** — insert a table
- **Source view** (the `</>` icon) — see and edit the chapter's raw Markdown source directly instead of the formatted view. This is also the only way to see exactly what's actually saved, so if something looks off after pasting from elsewhere, check here first.
- **B** / **I** / **U** / **S**: bold, italic, underline and strikethrough on the selected text (**Ctrl+B**, **Ctrl+I**, **Ctrl+U**, **Ctrl+Shift+X**)
- **Colour** (the font-colour button): eight swatches, a free colour picker, and "Default colour"
- **Embed image** (the image icon): opens a picker: upload a new image, or choose one from your [Research Workspace](#612-research-workspace). The image is inserted in its own paragraph and is stored as a normal Research Workspace item, so it is also searchable and available to the AI through its description
- Chapter **title** is editable at the top of the editor, click into it and type

**How formatting is stored, and where it goes.** Bold, italic, underline, strikethrough and colour are saved as a small set of inline tags in the chapter text, which is why you'll see them in Source view (the formatting buttons do nothing while Source view is showing). Anything you paste is converted to plain text first, with Markdown headings and tables turned into real ones, so formatting from a word processor doesn't carry across. Formatting is removed before any text reaches the AI, the search index or audiobook narration, so your colour-coded notes never leak into a generation prompt. Word, PDF and EPUB exports keep your bold, italic, underline, strikethrough, colour and embedded images natively (see [Section 11](#11-exporting-your-novel)); a submission manuscript keeps emphasis but stays plain black text with no images; plain text export removes all of it; Markdown export keeps it if you tick **Preserve rich text formatting**. Font face and size aren't available.

### 5.3 Appending text quickly

The text box at the very bottom of the screen (*"Type here to append text…"*) lets you drop in a quick line without scrolling to the end of the chapter — press **Enter** to append it as a new paragraph, **Shift+Enter** for a line break within your input first. The microphone button beside it lets you dictate instead of typing (see [Section 5.5](#55-voice-dictation)).

### 5.4 Word count

Each chapter shows its live word count in the header. The sidebar chapter list also shows per-chapter counts, and the bottom bar shows a running total.

### 5.5 Voice dictation

A microphone button next to the quick-append box (and next to the Scene beat brief, see [Section 8.1](#81-scene-beat)) lets you dictate instead of typing. Click it to start listening, click again (or just stop talking for a while) to stop — your words appear in the box as you speak, ready to review before you commit them with **Append** or **Generate**.

This runs entirely in your browser using its built-in speech recognition — nothing is sent to QuillWork's AI model or any server, and no setup is required. It works best in Chrome or Edge; the button is hidden automatically in browsers that don't support it (notably Firefox). It listens in whatever language the novel's own **Language** setting is set to (see [Section 6.6](#66-world--style)), not necessarily your browser's language — set that first if you're dictating in something other than English.

### 5.6 Chapter notes

The note icon in the chapter header (next to the title) opens a private per-chapter note — a place for your own reminders, continuity flags, or things to fix later. It's never sent to the AI in any call; it's purely for you.

The panel opens beside the chapter text, on the right, rather than covering it, so you can keep it open and glance between the two while you write. Drag its left edge to resize it to whatever width suits you — your chosen width is remembered the next time you open a note. The note icon itself lights up whenever the current chapter has a saved note, and the panel opens automatically the moment you switch to one that does.

Chapter notes, like the project-wide [Author notes](#614-author-notes), are never sent to the AI in any call. They are kept in Bible JSON exports and backups; in other exports they appear only if you tick **Author's notes** on the Export panel.

### 5.7 Scenes

The scissors icon in the chapter header (**Scenes**) opens a panel that splits the current chapter into scenes and works out who's speaking each line of dialogue — the same beside-the-editor layout as Chapter notes above.

Click **Analyse this chapter** to segment just the open chapter, or **Analyse whole manuscript** to run every chapter at once (a first run on a long novel can take a while, since it's genuinely re-reading each chapter — a progress log shows which chapter is currently being processed). Boundaries are detected from explicit scene-break markers (`***`, `# # #`, and similar) and headings, plus a blank-line gap combined with a clear time or location shift — a chapter with no detected break just becomes one scene, which is normal, not a failure. A line of nothing but break markers (or two in a row, or one straight after a heading) is only ever a break, never a scene of its own. Running analysis again leaves every scene whose text has not changed exactly as it was, along with everything the Story Analyst has worked out about it, so after an edit only the scenes you actually changed are read again.

Each scene shows a short preview of its text, who's in it, and how many lines of dialogue were found:

- **Lock** (the padlock icon) — marks a scene's boundaries as final. A locked scene is never moved by a later automatic re-segmentation, even after you've edited the chapter around it — useful once you've corrected a boundary by hand and don't want a re-run to undo that.
- **Split** — click it, then click the point in the scene's text where the new scene should begin, then **Split here**.
- **Merge with next** — folds a scene into the one immediately after it (dialogue and participants carry over correctly); only shown where there is a next scene to merge with.

Splitting or merging always locks both resulting scenes, for the same reason a manual lock does — a correction you made by hand shouldn't be silently undone by the next automatic pass.

Once a scene has been through the [Story Analyst](#812-story-analyst), its card also shows what the analysis worked out about it: the viewpoint character, the place, the story day, the mood, a one-line summary, and the jobs the scene does in the story (advances plot, reveals character, raises stakes, and so on). Click any job to open the passage its quote came from. A job the check says its quote does not fully show is marked (see [8.12](#812-story-analyst)) and still shown. The viewpoint, place, day, mood and summary are the AI's reading of the whole scene, so they carry no quote and say so: "AI-judged whole-scene readings. Your mileage may vary." Nothing extra appears until the scene has been analysed.

This segmentation is also what makes [Dialogue Fingerprints](#61-characters) and [per-character audiobook voices](#12-audiobook-narration) possible — dialogue has to be attributed to a specific character before either can work.

---

## 6. The Novel Bible

The bible is what makes QuillWork's AI calls consistent — everything here gets automatically included as context in every AI writing, suggestion, and continuity call.

### 6.1 Characters

**Characters** in the sidebar. Click **Add character** or click an existing character pill to edit. Open a character and click **Delete** to remove it (you'll be asked to confirm; Version history is the only way back).

Fields: Name, Role (protagonist / antagonist / supporting / minor), **Aliases** (comma-separated — nicknames, titles, a first name used on its own elsewhere), Age, Occupation, Personality, Physical description, Backstory, Secrets/knowledge, Arc, **Character voice**.

**Character voice** is how this character speaks, in your own plain-language words — e.g. *"Short, clipped sentences. Never uses contractions. Answers questions with questions."* It's injected into Scene Beat and Refine whenever this character is in the scene, and takes precedence over the general writing style rules for their own dialogue lines specifically (the global style still governs narration around them). This is the one field worth filling in even on a brand-new manuscript with no chapters written yet — everything below needs real dialogue to work from, but this one doesn't.

**Dialogue fingerprint.** Once a chapter has been through [Scene analysis](#57-scenes), the character editor shows real statistics measured from that character's own written dialogue — average sentence length, contraction rate, question rate, common opening words, and so on — once they have at least 10 lines of your own writing to measure (dialogue from an AI-approved draft is never counted, only lines you actually wrote or a draft you've since edited, so the tool can't quietly launder its own output back into a character's recorded voice). If the most recent stretch of dialogue has drifted noticeably from what came before, a flagged deviation appears alongside a short AI note on what changed.

**Observed voice.** Once there's a fingerprint, an **"Suggest an observed voice from their dialogue"** button generates a short description of how this character actually sounds on the page, derived from those statistics plus real example lines — shown as a suggestion card you can **Accept**, edit directly in the box first, or **Dismiss**. This is never written into Character voice automatically; the two are complementary, not competing, and both get sent together whenever a scene calls for this character's dialogue. Character voice is what you intend; observed voice is what the page actually shows so far — useful for catching a voice that's quietly drifted from what you meant, or for a character you never got around to describing whose voice has become clear from the writing itself.

**Importance over time.** Below the fingerprint, this shows how much of the plot the character drives across the book. It splits the analysed chapters into three bands and shows what percentage of the character's events they initiated in each ("Ch. 1-4: 62% initiated"), as a list or a small bar chart. It needs the [Story Analyst](#812-story-analyst) to have run; until then it says there isn't enough yet. A character who fades from driving events partway through shows up as a falling trend.

**Character psychology.** Click **Suggest character psychology (AI)** to have QuillWork infer a **Core want**, **Core fear**, **Defense mechanism** and **Wound** from what the character actually does on the page. It uses the same chain of choices, changes and discoveries as the arc simulator, and lists the moments it rests on, each with its quote and a button that opens it in the chapter ("Based on these moments"). An inference saved by an older version only lists the chapters. It is a suggestion to read, not something that overwrites your Personality, Backstory or Arc, and **Refresh** re-runs it once the character has more history. It needs the Story Analyst to have analysed enough of the character; otherwise a message says their real choices and changes aren't tracked yet. If the model was asked and could not give a usable account (it was unreachable, or it cited nothing real), the message says that instead and nothing is saved.

**Narration voice (audiobook)**, shown once [audiobook narration](#12-audiobook-narration) is turned on — assigns this character their own Chatterbox voice, same picker as the book's own narrator voice. See [Section 12](#12-audiobook-narration) for how this changes narration.

**Aliases** resolve automatically in two places: typing one into a "Characters involved" field (Timeline, see [Section 6.5](#65-timeline)) matches it back to this character instead of creating an unrelated tag, and the AI is told they're the same person in every writing/continuity call, so "Mara" and "Ms. Kessler" are read as "Mara Kessler." During manuscript import, QuillWork also fills this in automatically when the same person is called by different names across chapters — it recognizes the alias rather than adding a duplicate character entry.

*Example:* A character with **Secrets** set to "Knows the count is the killer but has no proof" will make the AI respect that knowledge boundary — it won't write that character acting on information they shouldn't have yet, and continuity checks will flag it if a later draft breaks that.

**Where did this come from?** A character (or location, or worldbuilding element) added automatically during [manuscript import](#2-quick-start--importing-an-existing-manuscript) shows a small italicized quote near the top of its edit modal and beneath its entry in the list — the exact sentence from your manuscript that established it, with the chapter it came from. This is provenance, not an editable field: it lets you verify an AI-extracted fact against your own actual text rather than taking it on faith. Items you add by hand don't have one, since there's no extraction to cite.

**Possible duplicate characters.** Alias resolution (above) catches the same person appearing under a different name only when both names appear together somewhere QuillWork is reading at once — a character introduced fully in Chapter 1, then referred to by a new name for the first time in Chapter 20 with no reminder of who that is, can still end up as two separate entries. Two buttons at the top of the Characters panel help catch this after the fact, and **neither one ever merges anything on its own** — both only ever suggest, and you decide:

- **Check for duplicates** — instant, and free (no AI call). Flags pairs that share name words ("Voss" and "Mara Voss") or a common real-world nickname (Tommy/Thomas, Liz/Elizabeth, and similar). Runs automatically every time you add a chapter, too — you'll see any new suggestion right there without asking.
- **Deeper check (AI)** — slower, and does use the AI. Reads through your actual manuscript looking for an invented nickname or alias with no lexical relationship to the real name at all (a character nicknamed "Sparrow," for instance) — something the free check can never catch by name alone, since it only works from real textual evidence, not guesswork.

Either way, a suggested pair shows the reasoning and two buttons: **Merge** folds the two entries into one (keeping whichever details each side has that the other's missing, and adding the extra name as an alias), or **Not the same** dismisses it — permanently, that exact pair won't be suggested again.

**Check for contradictions (AI).** A third check button reads through your manuscript for moments where a character acts or speaks against their own established traits (their Personality, Backstory or Arc). Each result shows the character, the chapter, the exact quote, which trait it contradicts and why. It only ever suggests: **Dismiss** clears a card and remembers it, so the same flag never comes back on the next scan, and nothing is edited for you, since only you know whether a change is deliberate development or a slip. Characters with no personality, history or arc text are skipped.

### 6.2 Locations

**Locations**. Click **Add location** or click an existing location to edit it, or **Delete** it from its edit window (with a confirmation).

Core fields: Name, Description, Significance. Four more are optional but worth filling in when you know them, since they feed directly into generated prose (not just continuity checks): **Atmosphere** (the mood or feel of the place), **Sounds**, **Smells**, and **Who's typically here** (residents, staff, regulars). Concrete sensory detail here tends to show up in the AI's actual prose, not just in what it avoids contradicting.

A location added during manuscript import shows the source sentence it was extracted from — see [Section 6.1](#61-characters).

### 6.3 Relationships

**Relationships**. Click **Add relationship** or click an existing one to edit or **Delete** it. Pick two characters (Character A / Character B), describe the **Dynamic** (freeform — the fuller the better, this is what the AI actually reads), and set a **Tension** value (0–10). Tension is shown as a coloured bar in the list (green → gold → red as it rises) — a quick visual gauge of which relationships are simmering.

**Kind** — a set of checkboxes below Dynamic: Family, Romantic, Friendship, Professional, Mentor, Rivalry, Enemy, Ally, Secret-holder. Pick any that apply (a relationship can be several at once, e.g. Family *and* Secret-holder). This is optional and separate from the Dynamic text — Dynamic is prose for the AI to read; Kind is a small fixed category QuillWork can actually filter and reason about in code, which is what powers the kind filter below. Hover a checkbox for a one-line reminder of what each kind means, since a few are close enough to overlap (Ally vs. Friendship, Rivalry vs. Enemy) that it's worth being consistent about which one you mean.

**Indirect connections are worked out for you.** If Alice knows Bob, and Bob knows Carol, QuillWork notices Alice and Carol are connected through Bob even though there's no direct relationship entry between them — this is computed automatically and fed into continuity checks and generation, so the AI doesn't have to infer it from a flat list. You'll see these noted as "connected via…" when relevant. Any Kind tags on a relationship are also surfaced directly in what the AI reads, not just implied by the Dynamic text.

**"How does X know Y?"** — at the bottom of the Relationships panel, type two character names and click **Find connection** to see the shortest chain of relationships between them, hop by hop. The **Relationship kind** dropdown narrows the search to a specific kind — e.g. set it to Family to trace only the family network between two characters, or Secret-holder to check whether a chain of secret-keeping could plausibly connect them. Leave it on **Any** for the full, unfiltered connection. A relationship with no Kind tagged won't match a specific kind filter (there's a reminder under the dropdown) — untag everything back to "Any" if a filtered search comes up empty and you're not sure why. **Clear** resets both names, the kind filter, and the result in one click.

**List / Visual toggle**, at the top of the panel:

- **List** — the row-based view described above.
- **Visual** — every character with at least one relationship laid out as a web: names arranged in a circle, a line drawn between each connected pair, coloured and weighted by that relationship's Tension (thin and green when calm, thick and red as it rises). Click a name to see that character's relationships listed underneath the diagram — who, what the dynamic is, and the tension score — without leaving the visual. Useful for spotting at a glance who your story's actual hubs and isolated characters are, something a flat list doesn't show.

### 6.4 Plot threads

**Plot threads**. Each thread has a name, a **status** (open / developing / resolved), details, and the chapter it was introduced in. The sidebar badge shows a live count of threads still open or developing. AI tools like Plot Ideas and the A → B Bridge reference open threads directly and can be asked to advance or complicate them. A thread can be removed with **Delete** in its edit window.

**List / Visual toggle.** **Visual** draws a bar for each thread from the chapter it was introduced to the last chapter with an event that advances it, coloured by status (open, developing, resolved). The bars extend past the introduction only after the [Story Analyst](#812-story-analyst) has run, because that is where the "advances this thread" links come from; until then you'll see "No chapter data for this thread". Drag the handle on the panel's left edge to widen it.

### 6.5 Timeline

**⟳ Timeline**. A chronological log: chapter number, in-story day, and event description. Useful for catching "that's only three days after the last chapter, but he's fully healed" type errors — the continuity checker uses this.

Click **Add event** to log one, or click any existing entry to edit or **Delete** it.

**Tagging events.** Two optional fields — **Characters involved** and **Plot threads** — take a comma-separated list (e.g. *"Mara Kessler, Halvard Reyes"*). Typed names are matched case-insensitively against your real character/plot-thread list, so "mara kessler" and "Mara Kessler" resolve to the same tag rather than becoming two different things — and for characters, a known **alias** resolves too (typing "Mara" tags "Mara Kessler" if "Mara" is listed as one of her aliases, see [Section 6.1](#61-characters)). A hint under each field shows the names QuillWork already knows about. Tagging is entirely optional — untagged events still work fine in the list and continuity checks; tagging mainly unlocks the Visual view below.

**List / Visual toggle**, at the top of the Timeline panel:

- **List** — the classic chronological log, with small coloured tag pills under any event you've tagged.
- **Visual** — a lane chart, closer to a dedicated timeline tool. Choose **Group by: Characters** or **Group by: Plot threads** from the dropdown; each character or thread with at least one tagged event gets its own lane (coloured to match that character's avatar elsewhere in the app), and any untagged events sit in a shared **General** lane so nothing goes missing. Events are laid out left-to-right in story order — columns represent distinct chapter/day combinations, not a literal calendar scale, so a flashback set decades earlier doesn't stretch the chart into uselessness. An event tagged with more than one character (or thread) appears as its own bar in each relevant lane. Hover a bar for the full event text; click it to open that event for editing, same as clicking it in List view. Scroll horizontally for a timeline with many events. If a single character/thread and column combination has more than a handful of events (common after a bulk import, where dozens of events can share the same unassigned "Ch.? · Day ?" slot), the extras collapse into one **"+N more…"** bar — click it to see and open the full list. Drag the handle on the panel's left edge to widen it for a longer view.

### 6.6 World & style

**World & style** holds:
- **Novel title** and **Genre**
- **Language** — the language your novel is written in (defaults to English). When set to anything else, every AI tool is told to write its prose, summaries, synopses, and bible details in that language rather than English — so working in French, Spanish, German, and so on just works. See **Writing in another language** below.
- **Synopsis**
- **Author style notes** — POV, tense, voice, tone (e.g. *"Close third person, past tense, dry wit, short chapters"*). This is injected into every prose-writing call.
- **Prose sample** *(optional)* — paste a paragraph or two of your own actual writing here, rather than describing it. The AI is told to match its rhythm and voice, not to copy its content — useful alongside (or instead of) Author style notes when a real example says more than a description can.
- **World-building notes** — geography, magic/technology rules, factions, history. (If this book is linked to a Series, this field is shared across every book in the series — see [Section 7](#7-series--sharing-a-world-across-multiple-books).) On a brand-new project, if the genre you typed matches one QuillWork recognizes, this field starts pre-filled with a short list of genre-relevant prompts, purely a starting scaffold to edit or delete, not fake content.

- **Author voice fingerprint** *(read-only)*: the same kind of statistics QuillWork keeps for each character's dialogue, measured across your own narration (everything outside quoted dialogue): average sentence length, contraction, question and interruption rates, and your most common sentence openers. It needs at least 10 narration paragraphs and works on any project. Once there's enough, if your latest paragraphs have moved away from your earlier norm it says "Voice may be drifting" with a short AI note on what changed. It is framed as drift for you to judge, never as AI detection.
- **Author's intent constraints**: hard rules you want respected everywhere, such as "Never show violence on-page" or "Magic always has a visible cost". Type a rule and press **Add** (or Enter). Each has an On/Off switch and a delete button. Every enabled rule is sent in full with every AI generation, and [Continuity check](#84-continuity-check) tests passages against them. This is the opposite of [Author notes](#614-author-notes), which the AI never sees.

Changes in this panel save automatically as you type (a short debounce, no need to click Save).

**Writing in another language.** Two settings work together:
1. Set **Language** here so the AI writes *in* that language.
2. In **Writing style rules** (AI Tools), use the **"Load a starter pack for another language…"** dropdown to load a ready-made, language-*aware* set of prose rules for **French, Spanish, or German** — these aren't just translations; the AI-tell word lists and dialogue-punctuation guidance are correct for each language (French and Spanish use the em-dash for dialogue, German uses „…", and so on). Review and **Save**. Because the rules are just a style pack, communities can share packs for any other language too.

Setting **Language** also switches the editor's built-in **browser spell-checker** to that language automatically (and flips the editor to right-to-left for Arabic and Hebrew). You may need that language's dictionary enabled in your browser for the underlines to appear.

Your model still needs to be capable in your language — QuillWork steers it, but the model you load *is* the writer.

Setting **Language** to French, Spanish or German also shows a banner offering to apply that language's style pack for you in one click (it warns before replacing rules you've customised). If you later change the language away from an applied pack, a banner offers to reset the rules to default. **Not now** dismisses it.

### 6.7 Worldbuilding

**Worldbuilding** in the sidebar. Click **Add element** or click an existing element to edit it. This is a structured home for the deeper rules of your world — magic or power systems, factions and organizations, religions and belief systems, and constructed or in-world languages — separate from the free-form **World-building notes** field in [World & style](#66-world--style) above, which is still the right place for general geography and looser notes. Every element here is fed into the AI's context automatically, same as characters and locations.

Fields: Name, **Kind** (Magic system / Faction / Religion / Language / Other), Description, and an optional Significance note on why it matters to the story.

When you import a manuscript (see [Section 2](#2-quick-start--importing-an-existing-manuscript)), QuillWork also scans it for worldbuilding elements automatically — it only adds what the text actually establishes, never invented fantasy tropes, so a contemporary or literary novel will simply come back with none. As with characters and locations, an element added this way shows the source sentence it came from — see [Section 6.1](#61-characters).

**Check consistency (AI).** Once you've added at least one element, this button scans your manuscript for passages that appear to contradict a rule you've already established — a stated limit being exceeded, a cost or cooldown being skipped, a power used in a way the rules say it can't be. This is the single most common continuity slip in long fantasy manuscripts: a rule that held for the first ten chapters quietly drifts as the story grows, and by the time it's noticed, fixing it means real rewrites. Each flag shows the passage, which element's rule it concerns, and a one-line explanation, grounded against your actual text so it never invents a contradiction that isn't there. Nothing is changed automatically — review each flag and **Dismiss** the ones that are fine (deliberate escalation the rules already allow for, say), which is remembered so a dismissed flag won't resurface on the next check.

### 6.8 Narrator beliefs

If you're writing an **unreliable narrator** — someone who lies, misremembers, or simply doesn't know the whole truth — the rest of the bible has a problem: everything in it is treated as settled fact, so a narrator's claim that later turns out to be false would normally get flagged by the continuity checker as an error, when really it's the point. **Narrator beliefs** exists to tell QuillWork the difference.

This is entirely something **you** decide and tag — QuillWork never guesses on its own which of your narrator's statements are trustworthy.

1. Select the narrator's claim in your editor (the exact sentence or passage), then click **Mark as claim** in the bottom toolbar — this opens the panel with that text already filled in. Or open **Narrator beliefs** in the sidebar directly and click **Add claim**.
2. Fields: **Narrator** (optional — leave blank if your book has one obvious narrator), **Claim** (the actual statement), **Status**, and **What's actually true** (optional — fill this in once you've decided or revealed the real answer; leave it blank while it's still an open question even to you).
3. **Status** has three settings:
   - **Unverified** — you haven't decided yet, or the reader isn't meant to know yet either.
   - **Confirmed true** — the claim holds up; treated the same as any other established fact from here on.
   - **Confirmed false** — the claim is wrong, and **What's actually true** should say why. This is the one that changes how continuity checking behaves.

**What this actually does:** a claim marked **confirmed false** is explicitly excluded from what QuillWork treats as settled fact. A later passage that contradicts it — the actual reveal — is expected, and won't be flagged as a continuity error. What *is* still checked and flagged: the narrator contradicting **their own** earlier claim, which is a real error regardless of whether the claim itself is true.

*Example:* Your narrator says in Chapter 1, "I've never been back to that house since the accident." You know that's a lie — she's been back twice, and Chapter 14 reveals it. Tag the Chapter 1 line as a claim, set it **Confirmed false**, and fill in the truth. When you write the Chapter 14 reveal, the continuity checker recognizes it as the intended payoff instead of an error to fix.

**Check for possible claims (AI).** Instead of hunting through your own manuscript for candidates, this button reads it and suggests passages that read like an opinion or a biased claim stated as settled fact — the kind of moment worth tagging. Each suggestion shows the exact passage, who's making it, and why it caught QuillWork's attention, grounded against your real text. Nothing is added on its own: **Add as claim** opens the normal Add-claim modal pre-filled for you to review and save, and **Dismiss** just clears the suggestion.

**Multi-POV books.** If your novel has more than one POV character, set **POV narrator** on each chapter's header (an autocomplete field, next to the chapter title) to say whose viewpoint that chapter is told from. The Narrator beliefs panel then groups claims by narrator instead of one flat list, so each POV character's own unreliable moments stay easy to track separately from the others'.

### 6.9 Knowledge tracker

Belief-vs-fact is about a narrator's *wrong* claims. **Knowledge tracker** is about something different: TRUE facts, and which characters actually know them — the "who's been told, and when" problem that gets hard to hold in your head once a cast and a plot's worth of secrets both grow past a certain size.

1. Click **Add fact** in the Knowledge tracker panel. Fill in the **Fact** (the secret or piece of information itself) and, if anyone already knows it, **Known by** — one line per character, `Name, chapter number` (e.g. `Halvard, 1`). Leave it blank if nobody's supposed to know yet.
2. Every fact you track shows in the list with a chip for each character who knows it and the chapter they learned it in, or "Not yet known by anyone" if it's still a secret from the whole cast.
3. **Check awareness (AI)** scans your manuscript for a chapter where a named character's dialogue, action, or narration shows clear awareness of a tracked fact *before* the chapter you've recorded them learning it — or awareness of a fact nobody's supposed to know yet. Each flag shows the passage, the character, which fact it concerns, and why it looks like early awareness, grounded against your actual text.
4. Each flag offers two responses: **Mark as known** actually fixes the tracker — it adds that character to the fact's Known-by list as of the flagged chapter, on the assumption you really did establish it there and just forgot to record it. **Dismiss** is for a false positive; it won't resurface on a future check.

**List / Visual toggle.** **Visual** shows a matrix of your tracked facts against your characters, marking where each character knows a fact and since which chapter. The panel widens and gets a drag handle on its left edge while it is showing.

*Example:* Halvard has secretly been funding the lighthouse restoration since Chapter 1, but nobody else is supposed to know yet. If Mara's dialogue in Chapter 5 shows she's clearly aware of it — before you've written the scene where she actually finds out — the AI check catches it, even though nothing in the plain text says "Mara knows this."

### 6.10 Foreshadowing (Chekhov's Gun)

Track something you've deliberately planted so it doesn't quietly get forgotten before it's supposed to pay off.

1. Click **Add setup**. Fill in the **Setup** (what you planted), optionally the **Chapter planted**, and leave **Status** as Unresolved. Once you've actually written the payoff, open the entry again, set **Status** to Resolved, and fill in **Chapter resolved**.
2. The list shows unresolved setups first, so what still needs paying off stays at the top; resolved ones stay visible underneath, dimmed, showing which chapter planted them and which chapter paid them off.
3. **Check for setups (AI)** scans your manuscript for a specific, unusual, or oddly-emphasized detail introduced without an immediate payoff — the kind of thing a careful reader would expect to matter again. Each suggestion shows the passage and why it reads like a deliberate setup rather than ordinary description. **Track this** opens the Add-setup modal pre-filled for you to review and save; **Dismiss** just clears the suggestion. Nothing is ever marked *resolved* automatically — only you know whether a later scene actually paid a setup off.

### 6.11 Facts & constants

Quantitative details you want held rock-steady across the whole manuscript — prices, distances, dates, measurements, ranks, anything with a specific value that's easy to accidentally contradict three chapters later.

1. Click **Add fact**. Fill in a **Name** (e.g. "Apple price"), a **Value** (e.g. "20"), and an optional **Unit** (e.g. "chips") and **Notes**.
2. Every fact is fed into every AI writing call by default, so the model is nudged to stay consistent with it without you having to repeat it in every brief. Past 15 facts by default, some AI tools (Scene beat, Refine and Chat) switch to sending only the ones relevant to the current passage, and only naming the rest, rather than the whole list; this number, and the matching ones for worldbuilding, characters and locations, are settings you can change (Settings → AI model & connection → Bigger books: when to send only what matters). See [9.3](#93-where-retrieval-kicks-in) for exactly which tools and why.
3. **Check consistency (AI)** scans your manuscript for a passage that states a value contradicting one of your tracked facts, and shows you the passage alongside the fact it conflicts with.

4. Facts are also found for you. Manuscript import has a "Cataloguing facts & constants" stage that mines quantitative details (ages, heights, prices, dates, distances), and background auto-extract and **Re-scan bible** do the same for new writing, merging by fact name.

**Feed into every AI writing call.** Each fact has this checkbox, on by default. If you're tracking a lot of facts (a spreadsheet's worth, say), turning it off for the ones that are rarely relevant keeps every single generation call from carrying the full list — the fact is still saved and still checked by **Check consistency**, it's just left out of the prompt QuillWork sends the model. A fact with this switched off shows **Off** in the list so you can tell at a glance which ones are currently excluded.

### 6.12 Research Workspace

The Research Workspace is a visual wall for everything you'd pin up beside your desk while writing: a character's face, a floor plan, a map, a reference PDF, a spreadsheet of names, a note to yourself, a web page you don't want to lose. QuillWork doesn't just store these. Anything you leave visible is described or read, embedded into the same search index chapters and Bible entries use, and pulled into context automatically in Scene beat, Refine, Chat and Continuity check wherever it is relevant.

**Opening it.** There is no sidebar entry. A small **Research** tab sits at the top centre of the editor, just under the top bar. Click it to open the panel at full height, or press and hold and drag it down: the panel follows your pointer and stops wherever you let go, up to the top of the bottom toolbar. While the panel is open the tab rides on its bottom edge, so drag it back up to close it (or use the panel's ✕). You can also press **Ctrl+K** and type "Research Workspace".

**Adding things.** Click **Add Research** and choose:

- **New note**: a title, caption and free text of your own.
- **Upload files**: pick one or many files, or drag them onto the panel. QuillWork accepts images (PNG, JPEG, GIF, WebP, BMP), PDFs, text files (.txt, .md), and documents (.doc, .docx, .xls, .xlsx, .ppt, .pptx, .rtf, .odt, .ods, .odp, .csv), up to 20 MB each.
- **Add web reference**: a URL, a title, and your own notes. QuillWork stores the address and your notes; it does not fetch the page.

**What QuillWork does with each kind.** Images are described by your AI model (physical details, spatial layout, anything that keeps prose consistent), and that description is what makes them searchable. PDFs and text files have their text read directly, and the first 8,000 characters become the searchable description; PDFs also get a first-page thumbnail. Word, Excel, PowerPoint, OpenDocument, RTF and CSV documents are stored and can be opened, but QuillWork does not read their content, so put anything you want the AI to know in the item's Description or Caption. Every description is editable: correct a wrong AI reading, or type one yourself if no vision model is loaded.

**Topics, nested to any depth.** Once you have at least one topic, the panel opens on a wall of topic tiles, each showing its item count, plus an **All items** tile (everything, flat) and an **Untagged** tile (items in no topic). Click a topic to drill in: its sub-topics appear as tiles above the items filed directly under it, a breadcrumb (Topics / Parent / Child) takes you back up any level, and a row of chips lets you jump sideways to any topic. Typing in the search box or changing the kind filter always searches the whole workspace, not just the topic you're in.

Click **Manage topics** to add a topic (choosing its parent, or "Top level"), rename one in place, move one under a different parent (QuillWork won't let you create a loop), or delete one. Deleting a topic never deletes its items, and its sub-topics move up to the top level rather than disappearing. The same window lists your **tags** with a count each; deleting a tag removes it from every item but keeps the items. An item can belong to several topics, and you add tags by typing them, separated by commas, in the item's own window.

**Working with a card.** Click a card to open its window: title, caption, description, topics (an indented checklist), tags, and a tick box **Include in AI context and search**. The eye icon on a card does the same job in one click: a hidden item stays in your library but is left out of every AI call and the search index. The bin icon deletes it after a confirmation. **Double-click** a PDF, text or document card to open the stored file in whichever program your computer normally uses for that kind of file. The search box and the kind filter (All kinds, Images, PDFs, Text files, Documents, Notes, Web references) always work across the whole library.

**The vision model, and switching to it.** Describing an image needs a vision-capable model. A status line at the top of the panel tells you whether one is available, so you find out before an upload rather than after. You can name a separate model for this in **Settings > AI model & connection > Vision model** (see [Section 4](#optional-a-vision-model)). With LM Studio, adding an image while a vision model is set opens a **Use vision model?** window with **Switch and describe** or **No, just upload**. Switching unloads your writing model, loads the vision model, describes the image, and then asks whether to **Process another image** (keeps the vision model loaded) or **Reload writing model**. While that swap is in effect the panel says "Vision model active for this session" and offers a Reload writing model link as a safety net. With Ollama no swap is needed: the upload uses your vision model directly. If no vision model is available at all, the image is still stored, with a warning; load one (look for "VL" or "vision" in the name), then delete and re-upload the image to get its description.

**Continuity check citing a reference.** Because an uploaded image's description is retrievable the same way everything else is, Continuity check can catch a passage that contradicts what a reference image actually shows, a stated eye colour that doesn't match a face reference, a room layout that doesn't match a floor plan, and cites the file by name as its evidence.

**Embedding an image in a chapter.** The image button in the editor's bottom toolbar (see [5.2](#52-the-editor)) inserts a Research Workspace image straight into your chapter text, and it goes into Word, PDF and EPUB exports.

Requires your project to be on QuillWork's current storage format (any project opened in a recent version already is). A project still on the older format shows a message asking you to reopen it first.

### 6.13 Bible updates

The queue of things QuillWork noticed while extracting from your chapters that conflict with what's already in the bible — a character's description filled in one way, then a later chapter implying something different for the same field. Nothing here is applied automatically.

Open it from the **Bible updates** entry in the sidebar (the count badge shows how many are waiting). Each entry shows the field in question, what the bible currently says, what the new chapter suggests instead, and the source quote it came from.

Suggestions land here on their own after an import, after [Add written chapter](#87-add-written-chapter), and from background auto-extraction as you write. You can also run **Re-scan bible** in a chapter's header (see [5.1](#51-opening-and-creating-chapters)) to add anything it finds to this queue.

- **Accept** replaces the current value with the new one.
- **Keep what I have** dismisses the suggestion and leaves the bible untouched. QuillWork remembers your answer, so the same proposed change is not suggested again later.

There's no automatic merge yet — accepting always replaces the field with either the suggested value or whatever you edit it to, rather than an AI-assisted combination of old and new. If the same field has more than one pending suggestion (say, two different chapters each added something about a character's backstory), accepting one refreshes what the others are comparing against, so you're never accepting a sibling suggestion against a value that's already out of date — but each is still applied one at a time, in whatever order you handle them, not merged together into one final version automatically.

### 6.14 Author notes

**Author notes** in the sidebar's Bible section is a place for project-wide scratch notes. Everything in it, and every per-chapter note ([5.6](#56-chapter-notes)), is never sent to the AI: it is kept out of extraction, generation, continuity and search. Both are always kept in Bible JSON exports, backups and snapshots. In other exports they are included only if you tick **Author's notes** on the Export panel (Markdown ticks it by default; the manuscript format never includes them).

---

## 7. Series — Sharing a World Across Multiple Books

If you're writing a trilogy or an ongoing series, **Series** lets multiple books share the same characters, locations, worldbuilding elements, relationships, and world-building notes — write it once, and it's available (and stays consistent) in every linked book.

### 7.1 What's shared vs. what stays per-book

| Shared across the series | Stays specific to each book |
|---|---|
| Characters | Chapters and their text |
| Locations | Timeline |
| Worldbuilding elements | Plot threads |
| Relationships | Synopsis, title, genre, author style notes |
| World-building notes | |

This split is deliberate: recurring cast and world rules should be consistent across a series, but each book's plot, timeline, and specific arc are its own.

### 7.2 Creating and linking a series

1. Open **Series**.
2. Either **link to an existing series** from the dropdown, or **create a new one** by typing a name and clicking **Create & link**.
3. Once linked, the panel shows the series name, which other saved books are part of it, and lists of the shared characters/locations/worldbuilding elements with **Remove** buttons (removing here takes the item out of the series for *every* linked book).

### 7.3 Marking an item as shared

Once a book is linked to a series, every Character/Location/Worldbuilding/Relationship form gains a **"Shared across series"** checkbox:

- **Checked** → this item lives in the series, editable and visible from any linked book. A small 📚 badge appears next to it in lists.
- **Unchecked** → this item is local to this book only (e.g. a one-off minor character who never appears elsewhere in the series).

You can flip this at any time — checking it later "promotes" an existing local character into the shared series; unchecking it "demotes" it back to local-only (and removes it from the series, so do this deliberately).

*Example:* Writing Book 2 of a trilogy — your protagonist and their home city are marked **shared** (defined once in Book 1, referenced automatically in Book 2 and Book 3). A merchant who only appears in one scene of Book 2 stays **local** — no need to clutter the shared series data with a character who won't recur.

### 7.4 Unlinking

**Unlink** disconnects the current book from the series. Nothing is deleted — the series keeps all its data, and the book keeps a static local copy of the world notes as they stood at the moment of unlinking. You can re-link later.

---

## 8. AI Writing Tools

The tools that draft or review your prose (Scene beat, Refine, Plot ideas and the Un-AI scan) carry the [anti-AI-prose rules](#16-reference--anti-ai-prose-rules), so you don't need to ask for "less robotic" prose. The Synopsis generator and Query letter follow their own conventions instead, and Bridge plans what happens rather than writing prose, so those three do not use the rules.

### 8.1 Scene beat

The main way to generate new prose. Click **Scene beat** at the bottom of the screen. It needs a chapter open: without one, Generate asks you to open a chapter first.

1. Describe what happens next — who's involved, tone, key events, emotional beat. The microphone button beside the box lets you dictate this by voice instead of typing (see [Section 5.5](#55-voice-dictation)).
2. Pick how much room the AI has to work with — Short (a beat or gesture), Medium (a scene moment), Long (a developed scene), or Very long (an extended scene). These set an upper bound, not a promise — actual length varies with the scene and the model you've loaded (see [Section 4](#4-connecting-an-ai-model)).
3. Click **Generate**. QuillWork continues from the closing lines of the open chapter (roughly the last hundred words), and the prose streams into an amber-edged **draft block** at the end of the chapter, below your existing text. It is not inserted at your cursor.
4. The draft is **fully editable** — click into it and revise before deciding what to do with it.
5. **Stop** halts a generation and keeps what has arrived. **Approve ✓** commits the draft as permanent paragraphs at the end of your chapter. **Regenerate** runs the same brief again for another version without retyping it. **Discard** removes the draft with no trace.

Multiple drafts can be in flight in the same chapter at once if you want to try a couple of directions before committing to one.

Press **Ctrl+Enter** in the brief box to generate without reaching for the button. Beside Generate is a small model chip (labelled "default"): choose another model to use for just this generation. It is not saved and resets when you reload. Refine has the same chip. If you turn on **Check continuity when I approve a Scene beat draft** in Settings ([Section 4](#three-more-settings-switches)), a small card also runs a continuity check on the passage you just approved, without blocking you.

*Example brief:* *"Mara finds the letter her sister hid. She doesn't cry — she gets angry. Ends with her deciding to confront their father."*

**Optional: state the scene's intended effect.** Click **+ Intended effect (optional)** to reveal a set of checkboxes — advances plot, reveals character, raises stakes, and so on. Tick any that apply before generating, and QuillWork both aims the draft at them and, once it's done, checks the actual result against what you asked for: *"Asked for: Raises stakes — Detected: Reveals information."* This is purely informational — it never blocks Approve, and a mismatch just means the draft did something a little different than planned, worth a glance before you commit to it, not an error.

**Optional: ask for a momentum target.** Click **+ Momentum target (optional)** for a finer version of the same idea, aimed at what actually changes rather than what kind of scene it is. Set a target momentum (a minimum number of real state changes) and, if you like, name up to three specific things that must change: a relationship between two characters, an open question or promise from the Story Analyst's ledger, or a character's own stated intention. After generating, QuillWork tells you what it found: a real count of state-changing edges extracted from the draft itself, exactly the same way Story Analyst > Patterns > Narrative momentum counts a saved scene, never a model guessing whether it thinks it succeeded, and a check mark or a miss against each named thing you asked for. Like Intended effect, this is information, not a gate: a miss is reported plainly and never silently retried, and Approve stays available either way.

### 8.2 Plot ideas

**Plot ideas**. Pick a type (next chapter arc, resolution for an open plot thread, character development moment, complication/obstacle, twist/reversal, sub-plot development, relationship turning point, pay off an overdue promise, future consequences of a chapter's events, or give a reactive character the initiative), optionally add context/constraints, and click **Get ideas**. Returns 3 distinct suggestions, each with dramatic potential, character impact, and which plot threads it touches.

**Pay off an overdue promise.** Choose this type and a second picker lists every open question or promise your manuscript has raised, ranked by how overdue it is (how long it has been open, weighted by how central it is to the story). Pick one, and the three ideas aim specifically at resolving it. The list fills from the [Story Analyst](#812-story-analyst); until you've run it, the picker says no open questions or promises were found yet. If you generate without picking one, the ideas are general, and the result begins with a note saying so.

**Future consequences of a chapter's events.** Pick a chapter, and QuillWork tells the model the real events in it and what the causality graph already shows following from them, then asks for three new consequences that have not been written yet. It is the mirror of the Domino test: instead of "what breaks if I cut this?", it asks "what should follow from this?". A chapter the Story Analyst has not read has no events to work from, so the ideas are then general and the result begins with a note saying so.

**Give a reactive character the initiative.** Pick a character (the ones who initiate the least are listed first, with their percentage) and QuillWork tells the model how much of the plot they currently drive and what has recently happened to them, then asks for three ideas in which they make a deliberate choice that drives what happens next.

### 8.3 A → B Bridge

**A → B bridge**. For when you know where the story is and where it needs to end up, but not how to get there.

1. Describe **Point A** — the current situation, location, who's present, mood, constraints.
2. Describe **Point B** — the destination situation, what needs to have changed, who's involved.
3. Click **Find the paths**. QuillWork generates **3 distinct narrative paths** from A to B, each including:
   - The catalyst that sets the path in motion
   - How it unfolds, beat by beat
   - Which characters drive it and *why* — tied to their established traits/secrets/relationships
   - Which plot threads it advances
   - The dramatic/tonal flavour of that path

The model is given your bible and told to keep every path consistent with it: no character acting against their established personality, no knowledge they don't have, no convenient rescue from nowhere. That is an instruction to the model, not a check QuillWork runs afterwards, so read each path against what you know of your characters before you build on it. The three paths are also asked for, not enforced: if the model returns fewer or more, use what it gave you.

*Example:* Point A: *"Two rival heirs are publicly cordial but privately at war over the inheritance."* Point B: *"They're forced into an uneasy alliance against a shared threat."* — the Bridge tool won't just say "a bigger threat appears"; it'll propose three genuinely different mechanisms (a frame-up neither could have caused, a shared secret coming to light, an external attack that only one has the resources to survive) each keyed to what's already established about those two characters.

### 8.4 Continuity check

**Continuity check**. Paste (or select text in the editor first) a passage, and click **Run check**. QuillWork checks it against the bible for:

1. Character trait contradictions
2. Physical description errors
3. Timeline violations
4. Location errors
5. Relationship inconsistencies
6. Plot thread contradictions
7. Knowledge errors (a character knowing something they shouldn't yet)
8. Narrator self-contradiction, for a book using [Narrator beliefs](#68-narrator-beliefs): does this passage contradict the narrator's own earlier claim, as opposed to contradicting the actual established facts, which is expected for an unreliable narrator and not flagged as an error
9. A contradicted [Research Workspace](#612-research-workspace) reference: a stated detail that conflicts with what an uploaded image or document actually shows, cited by filename
10. A broken [author's intent constraint](#66-world--style): a passage that breaks one of the rules you set in World & style, quoting the rule itself as the evidence

Each issue is flagged **MINOR / MAJOR / CRITICAL** with the established fact it contradicts and a suggested fix. There's also a **Check** shortcut in the bottom toolbar for quick access while writing.

### 8.5 Refine selection

**Refine selection**. Select text in the editor (or paste it), give an instruction, and click **Refine**. Quick preset chips are available: *Cut adverbs*, *Sharpen dialogue*, *Add tension*, *Sensory detail*, *Remove AI-isms*, *Vary rhythm*, *Deeper POV*. Use **Replace selection** to swap the refined text back into your editor in place. There's also a **Refine** shortcut in the bottom toolbar.

If any character has a Character voice or an observed voice on file (see [Section 6.1](#61-characters)), a dropdown appears alongside the preset chips — pick a character and a **"Match [Name]'s voice"** chip appears, ready to fill the instruction box the same way the fixed presets do.

### 8.6 Un-AI text

**Un-AI text**. A dedicated scanner for catching AI-sounding writing in prose you've already written (your own draft, an AI-generated passage you approved earlier, or an imported manuscript) and proposing human rewrites — interactively, so nothing changes without your review.

1. **If text is selected in the editor**, the button reads **"Scan selected text"** and only that selection is scanned. Otherwise it reads **"Scan chapter"** and scans the whole open chapter.
2. Click it. A progress bar shows percentage complete and an elapsed/estimated-remaining time. **Cancel scan** (after a confirmation) stops it. Results appear only when the whole scan has finished, so a cancelled scan leaves nothing to keep, and if you switch chapter while it runs the results are discarded, because they were found in the other chapter's text.
3. Results appear as cards, each showing:
   - The **original** flagged text (struck through)
   - A **reason** (e.g. *"banned word 'suddenly'"*, *"named emotion instead of showing it"*)
   - An **editable rewrite** — tweak it however you like before accepting
   - A checkbox to include/exclude that specific change
4. Click **Apply selected changes**. Only checked items are applied; the chapter is updated and autosaved. If the chapter holds an unapproved Scene beat draft, you are asked first, because applying discards it. A phrase that appears more than once in the chapter is skipped, not guessed at, since QuillWork cannot tell which occurrence the suggestion was about; the confirmation says how many were skipped, and you can make those changes by hand.

This is the same rule set as every other writing call in QuillWork, just run as an audit pass rather than baked into generation — useful for cleaning up text imported from elsewhere, or double-checking your own prose hasn't drifted into cliché.

### 8.7 Add written chapter

**Add written chapter**. For adding a single chapter you've already written outside QuillWork into an *existing* project (as opposed to a full manuscript import, which is for starting a brand-new project — see [Section 2](#2-quick-start--importing-an-existing-manuscript)).

1. Paste the chapter text. Chapter number is optional (auto-assigned if blank).
2. Click **Process chapter**. QuillWork summarises it, checks it for new characters and plot threads (merging anything new into the bible without duplicating existing entries), and runs a continuity check against everything already established.
3. The continuity report appears below — review it for anything the new chapter contradicts. When the chapter has been processed, the paste box is cleared, so you can see that the whole operation finished.

**Already have the chapter open in QuillWork and just want the bible updated from what's there now?** With **Auto-extract Bible info as I write** on (the default), QuillWork does this in the background as you write. To run it on demand, click **Re-scan bible** in the chapter header: after a confirmation it opens this panel pre-filled with that chapter's saved text and number, and nothing changes until you click **Process chapter**. If a stage fails, a "Chapter import ran into a problem" window offers **Abandon** or **Retry** (which restarts from the failed stage, optionally with a different model).

### 8.8 Synopsis generator

**Synopsis generator**, under the **Submission** section of the sidebar. Generates a proper **submission synopsis** — the kind agents and publishers ask for. This is fundamentally different from back-cover copy: a submission synopsis must reveal the entire plot, **including how it ends**. Agents use it to judge whether your story actually resolves before requesting the full manuscript.

Choose **1 page** (~500 words) or **2 pages** (~1000 words) and click **Generate synopsis**. Works best once your chapters have summaries — these get generated automatically during [manuscript import](#2-quick-start--importing-an-existing-manuscript) or [Add written chapter](#87-add-written-chapter); without them, the synopsis draws on the bible's synopsis field and plot threads alone.

### 8.9 Query letter

**Query letter**, under **Submission**. Drafts a standard-structure query letter to a literary agent: a personalized opening, a one-paragraph hook, a one-paragraph plot pitch (like back-cover copy — this one does **not** reveal the ending, unlike the synopsis), a short bio paragraph, comparable titles, and your word count and genre.

A query letter goes to a real agent, so QuillWork gives the model your own details and tells it not to invent any. The bio paragraph is built from **About the author** in [Book setup](#111-book-setup--front-and-back-matter), and the model is told to use nothing else. If that box is empty, the model is asked to leave a bracketed placeholder such as *[Add your bio: writing credentials, relevant experience]*. Comparable titles you don't supply are treated the same way, and the model is told not to invent anything about the agent. That is an instruction, not a guarantee, so read the letter for any credential, title or detail that is not yours, and fill every square bracket in before you send it.

Optional fields — fill in what you have:
- **Agent name** — personalizes the greeting
- **Why this agent** — e.g. "represents upmarket fantasy with morally grey leads" — informs the opening hook
- **Comparable titles** — published books yours resembles, e.g. *"THE FINAL EMPIRE meets THE GOBLIN EMPEROR"*

Click **Draft query letter**. Treat the result as a strong first draft — review and personalize before sending, especially the agent-specific details.

### 8.10 Chat

**Chat**. A free-form question-and-answer interface over your own manuscript and bible — "who is Halvard again?", "what have I established about the lighthouse?", "has Mara met Dr. Voss yet?". The model is told to answer only from your actual bible, the [Story Analyst](#812-story-analyst)'s calculated figures once it has run (who drives the plot, what is most overdue, which scenes lead nowhere, how long reveals took, so "who actually drives this story?" and "what's still unresolved?" get real answers), and (on a long novel) retrieved passages from your chapters via the [Search index](#9-search-index--working-with-very-long-novels) — QuillWork is told to say so plainly rather than invent an answer when something hasn't been established yet.

Chat works with whatever model you already have loaded, including one chosen for creative prose (Scene beat, Refine) rather than instruct-style chat. Early testing found that asking a prose-tuned model for a free-text reply could make it keep going past one answer — inventing and answering its own follow-up questions. QuillWork now asks the model for a single structured reply rather than free text, which stops generation the moment that one answer is complete — this held up even on the same model that misbehaved before, so no particular model choice is required.

Chat is also one of the "routine" calls covered by the **Fast model** setting (see [Section 4](#4-connecting-an-ai-model)) — if you've set one, Chat answers come from it automatically, not your main writing model, so it stays quick even while your main model is busy or unloaded.

Type a question and press **Enter** (Shift+Enter for a new line) or click the send button. The conversation stays on screen so you can ask follow-ups, including when you close the panel and open it again, but it is **not saved**: reloading QuillWork or switching to another project clears it. This is a lookup tool, not a place to draft prose.

A status banner also shows whether an embedding model is available (same check as Search Index) — Chat still works without one, using the bible alone, but answers about earlier chapters are more precise once retrieval is set up.

### 8.11 Pacing

**Pacing** shows a simple line chart of narrative tension across your chapters — 0 (quiet/reflective) to 10 (maximum tension/climax) — so you can see the overall shape of your pacing at a glance: a saggy stretch of low-tension chapters in the middle, or a run of chapters that all land at the same intensity. This is a rough, relative signal meant to prompt a look, not a scientific measure — judge the actual chapters, not just the number.

Early testing found a model tuned for creative prose continuation tended to label nearly every chapter the same, regardless of what was actually happening in it — asked in plain text, it defaulted to a generic middling score rather than genuinely judging the scene. QuillWork now asks for a structured rating rather than a free-text one, which measurably fixed this on the same model that struggled before (a quiet scene and a climactic one now score clearly apart), so no particular model choice is required.

New chapters get scored automatically (manuscript import, Add written chapter). A long chapter is scored in parts and the most tense part sets its score, so a chapter that ends in a climax reads as a climax. If the model cannot give a score for a chapter, it is left unscored (a grey dot) or keeps its earlier score, and the run says which chapters failed. QuillWork never puts in a middling score to fill the gap. Chapters from before this feature existed show as grey, unscored dots; click **Analyse chapters** to score everything at once, the same one-time catch-up as rebuilding the search index after a bulk import. Hover any point for the chapter's title, score, and a short label (e.g. "Rising action", "Quiet aftermath"); click it to jump straight to that chapter in the editor.

**Suspense markers.** Once the [Story Analyst](#812-story-analyst) has analysed your chapters, small triangles above each chapter on the chart show where dramatic irony, suspense, an open mystery and a revelation land, so you can see whether they cluster where tension should be building. This costs no model call and needs no visit to the Story Analyst first, but it only shows for chapters that have been analysed.

### 8.12 Story Analyst

**Story Analyst** (sidebar > AI Tools > Story Analyst, or **Ctrl+K** then "Story Analyst") reads what actually happens in your story: events, what causes what, who knows what and when, and the questions the reader is still waiting on. Everything it finds becomes a structure you can see and correct. This is **read-only analysis**: nothing here ever changes your manuscript, and nothing it finds is silently trusted, because every row is reviewable, editable or deletable.

**Calculated, AI-judged, or both.** Everything QuillWork works out or writes to inform you carries a small label saying how it was arrived at, so nothing looks more certain than it is. **Calculated** means it is worked out from your story data by counting and comparing, and the same data gives the same answer every time. **AI-judged** means the AI produced it, so it can vary between runs; where it says something about your text, the quotes it rests on are shown. **Calculated + AI-judged** means part is calculated and part is the AI's judgement, and each judged part shows its quotes. None of these describes how well the book is written. They describe your story's structure: what happens, who knows what, what is left open.

The labels appear beside every analysis, check, score and suggestion QuillWork produces, not only in the Story Analyst:

| Label | Where you see it |
|---|---|
| Calculated | The structural score and its five checks; Narrative Debt, Who drives the plot, Narrative momentum, Dead-weight scenes, Suspense architecture, Domino test, Reveal timing, Dialogue fingerprint comparison, Facts the reader learns before the protagonist, Emotional echoes and Parallel scenes (the candidate pairs); the overdue-promises list; Characters > Check for duplicates. |
| AI-judged | Events & causality, Questions & promises and Known facts; every finding the AI writes in a health report; each chapter's tension in Pacing; the Continuity check; the Un-AI text scan; Plot ideas; A → B Bridge paths; Chat answers; the Synopsis and Query letter; Bible updates; every check marked (AI) in the Characters, Worldbuilding, Facts, Narrator beliefs, Knowledge and Foreshadowing panels. |
| Calculated + AI-judged | The Health report as a whole; What if…; Motifs, symbols & themes; the Character arc simulator; the Evidence check; Characters > Deeper check (AI). |

Your own words and records are not labelled, and neither are plain status lines such as "3 chapters indexed". Text you asked the AI to write for you to use, such as a scene beat or a refined passage, is marked by where it appears instead (an amber draft block, or the Refine result).

**Running an analysis.** Story Analyst reads *scenes*, so split your chapters into scenes first: open a chapter, click **Scenes** in its header, then **Analyse this chapter** or **Analyse whole manuscript** (see [Section 5.7](#57-scenes)). A chapter with no scenes yet is skipped with a message, not treated as an error. Then, in Story Analyst, click **Analyse this chapter** to scan only the open chapter, or **Analyse whole manuscript** for everything. **More run options** lets you analyse a range of chapters, or re-analyse everything even where a scene hasn't changed. For each scene it works out the scene's facts, the events, who knows what, what causes what, the questions raised or answered, and what job the scene does. Progress streams in below the buttons with a real percentage, and **Cancel** stops between scenes and keeps everything found so far. Re-running after a small edit is cheap: already-analysed scenes are skipped, so only what changed is re-read, and what the analyst made of a scene before is kept as an earlier reading (see below). That includes after you change model: a scene whose text has not changed is not read again by the new model unless you use **Re-analyse everything**. If the AI cannot answer for a scene (it times out, runs out of room to finish, or replies with something unusable), that step is marked as not finished, with the reason, and the summary says how many steps that was. It is never saved as "nothing found": the next run tries exactly those steps again, and whatever an earlier run found for that scene is kept until a new answer replaces it. Pressing **Stop AI** ends the run instead of moving on to the next step. It works best once your Bible has its characters, locations and plot threads, because the analysis matches names against them and drops any name it can't match rather than inventing a character. Which model does what is explained under [the Fast model](#optional-a-second-fast-model-for-analytical-work). After a scene's other steps, one more step reads every result against the quote it rests on (see **Is the quote really about it?** below).

**How long it takes.** Reading a scene is several separate calls to the model, so it is slow on a model running on your own computer, and the time depends on the scene's length, the model and your hardware. In our tests on one computer (a 12 GB graphics card and a 24B model too large to fit that card fully, so part of it ran on the processor instead), a 500-word scene took about 18 minutes and a 1,500-word scene about 30, and the quote check made up roughly 3 to 5 minutes of that. That is two scenes on one machine, so use it as a rough guide, not a promise: a model that fits your video memory in full will be markedly faster than this. At that speed a whole novel is many hours of running time. Start with one chapter to see what your setup does, and leave a whole manuscript to run when you are away from the computer: **Cancel** keeps everything found so far and a run that is interrupted can be resumed. A smaller model, a stronger computer, a model on another computer on your network, or turning on **Run a scene's passes together** (see above) when your model fits your video memory, is faster, and [Choosing a model](#choosing-a-model-what-it-changes-in-quillwork) explains what that costs in quality.

**Keeping it up to date as you write.** This is your choice, and nothing runs until you have made it. The installer asks, with what you get and what it costs, and if you skipped that or updated from a version that did not have this option, QuillWork asks the first time it starts; the question stays on screen until you answer it. Say yes and the analysis keeps itself up to date. QuillWork compares each chapter's text with what was last analysed, and when they differ (you wrote or edited in it, imported it, synced it, or restored a version) it analyses that chapter in the background: it cuts the chapter into scenes, reads every scene that changed with every step above, scores the chapter's tension and refreshes its summary. It starts only when you have not changed that chapter for a couple of minutes and have not asked the model for anything for a minute, it works on one chapter at a time, and it gives way at once when you ask the model for something. Clicking **Analyse** yourself stops the background run and takes over. A scene whose words did not change is not read again, so after the first pass only what you changed costs anything. After an import every chapter is due, so the first pass over a whole manuscript happens in the background instead of as one big run you have to start. It is many model calls, so on a slow computer it can keep your graphics card busy for a long time. A line in the sidebar and a status line at the top of the Story Analyst say which chapter it is working on and at which step, how many chapters are up to date, and what it could not finish: a chapter it fails on is tried again later, each wait longer than the last, and after five failures on the same words it waits until you change them. Turn it off, or on again, with the **Auto-analyse** switch beside Scene beat at the bottom of the screen, under **Settings > AI model & connection > Keep the Story Analyst up to date as I write**, or with **Turn off** on the status line. The analysis then changes only when you run it. It does not run the Health report, which reads the whole manuscript at once and is yours to run. "Up to date" means only that the analysis matches your text; it does not say the analysis is right.

If a previous run was interrupted (QuillWork closed, or the computer restarted mid-analysis), a banner offers to **Resume**. It restarts with the same scope the interrupted run began with (one chapter, a range, or the whole manuscript) and picks up exactly where it left off, at no extra cost for the work already done.

**Seven tabs**, switched along the top of the panel:

- **Events & causality**: every extracted event, grouped by chapter, with who did it, whether they chose it or it happened to them, and whether it is irreversible. Beneath each event are its causal links to other events, characters, threads or facts, in words ("raises the stakes for Halvard Reyes"); click the small ✕ beside a link to remove it if it's wrong. On any event you can click **Edit** (correct the description, the acting character, who chose it, and irreversible), **Add a link** (add a missing link by hand: this event causes, reveals, pays off or changes a relationship with another event, a character, a fact or a plot thread), **Show in chapter** (jump to the exact passage it came from), or **Delete**. The **List / Visual** switch turns the tab into the **causality graph**: one column per chapter and one box per event, word-wrapped, coloured by the acting character with the name underneath, a red dot on an irreversible event, and curved arrows for event-to-event links (causes, reveals, pays off, advances a thread). Click a box to highlight its arrows and see its full card below the graph; click it again to deselect. While any Visual view is open, a thin handle on the panel's left edge lets you drag it wider.
- **Questions & promises**: everything the reader is left wondering about, or that the narrative has promised will matter later, each tagged by how central it is. A status dropdown lets you correct it: mark one **Answered** or **Partially answered** if the extraction missed it, or use **Red herring**, **Intentionally left open** or **Abandoned** for calls only you can make. The analysis never assigns those three itself, and marking a long-open item "Intentionally left open" stops the health report flagging it. Turn on **Track Chekhov's Gun objects** (Settings > AI model & connection) and a third kind joins the ledger: significant objects planted with apparent narrative weight, at or above the minimum significance you choose there, so the ledger doesn't end up listing every teacup. An object's own "Answered" status reads **Paid off** instead. **Suggest payoffs (AI)** at the top of this tab scans the manuscript for a moment that pays one of your tracked objects off, showing each candidate with its quote and chapter for you to **Mark as paid** or dismiss; nothing is ever marked automatically.
- **Known facts**: every narrative fact the analysis has tracked, with the chapter it was established in, flagged if it is something a character believes or claims that isn't true in the story. **Track flow** on a fact shows, chapter by chapter, who knows it, suspects it, conceals it or is wrong about it (the reader included), as a list or as swim-lanes by character.
- **Health report**: see below.
- **What if…**: the Counterfactual Laboratory, see below.
- **Patterns**: a set of collapsible analyses, described below.
- **Evidence check**: what every AI-made result rests on, and whether it still does (see below).

**Every row is grounded.** An event, link, question or fact only ever lands here if it's backed by a short quote genuinely found in your own chapter text; nothing is invented, and nothing is attributed to a character who isn't already in your Bible. A correction you make is remembered as yours: a later re-run of the same chapter never silently overwrites it. **Show in chapter.** Nearly every result has a **Show in chapter** button: findings, events and their links, questions and when they were answered, facts, momentum and dead-weight scenes, echoes and parallel scenes, the health report's items, the consistency scans and Bible updates. It closes the panels, opens the chapter and selects the passage the result rests on; a result that names only a scene opens the start of that scene. Because you keep editing between analyses, it never guesses. If the words have been reworded it shows where they began; if they are gone it shows the start of the scene they came from; if the scene can't be found it opens the chapter. In each case a note above the chapter says so, with a button to analyse the chapter again. A phrase that appears more than once in a chapter opens the match inside the right scene, and the note says when it had to choose. Results that are about the whole book, such as a character's overall agency, the score or a count, have no single passage and say so. The scans (magic, facts, knowledge, foreshadowing, unreliable claims, contradictions) and Bible updates report what a model said, so if their exact words are not in the chapter the note says they may have been paraphrased, not that you changed them.

**Is the quote really about it?** A quote that is really in your text is not the same as a quote that shows what the result says: a model can quote a genuine sentence that has little to do with the claim it is attached to. So after each scene's other steps, a separate call to your main model reads every result of that scene (each event, link, who-knows-what row, question, answer and scene function) against its quote and says whether the quote shows it fully, only partly, or not at all. A result whose quote does not fully show it is marked where you see it, on its event card, its link, its question or answer, its who-knows-what row, or its scene function, with the model's one-line reason. It is never hidden, changed or deleted: the mark is information, and your own judgement decides. It is a judgement too, so it is labelled AI-judged and can differ between runs, and a result you edit yourself is yours and is not put to it. If you edit a result the mark lapses by itself, and if the model gives no usable answer for a scene the step is marked as not finished and tried again next run.

**Evidence check.** The Evidence check tab counts and lists every AI-made result that does not stand on good evidence, so nothing rests unexamined. It sorts them into: **Out of date** (the quote is no longer in the chapter as it is written now, or the scene it came from has been edited since it was analysed; analyse the chapter again to refresh it), **Too thin to show anything** (the quote is only where a scene starts, or a word or two), **No quote** (nothing from your text is stored), and **Quote may not show it** (the check above said the quote shows only part of the result, or none of it). It also lists each scene's summary, viewpoint, place, day and mood, which carry no quote by design ("AI-judged whole-scene readings. Your mileage may vary."). A result is listed once, under the first of those that applies. The counts at the top show how many results were checked, how many hold up, and how many have not been through the quote check yet. Each listed result has a **Show in chapter** button, and **Keep as mine** and **Remove**: keep turns the result into yours, so no later reading replaces it and the check stops questioning it; remove takes it out (an answer reverts its question to open rather than deleting the question itself), and it stays out unless a later reading finds it again. The counts and the first three lists are calculated from what is stored; the fourth is the AI's reading, and the tab says so. It never changes anything on its own: only Keep and Remove edit anything, everything else is a list to read and act on. Long lists show the first hundred, with a button for the rest. When a reading finds results that no longer match your text, whether you ran it or it happened in the background, a note at the top of the Story Analyst panel says how many and offers to take you straight to this tab.

**Earlier readings.** Reading a scene again replaces what the analyst made of it before, so the earlier reading is not lost: before anything is replaced it is copied, whole, and kept under its chapter in the **Events & causality** tab as **Earlier readings**. Each entry says which scene it was, why it was kept (the scene was read again, it was cut differently, or it was set aside when you put an older reading back), when, and what it holds. **Look** lists its events, links, scene jobs and questions, each with its quote and whether that quote is still in the chapter as it stands now. **Keep** turns one item into your own: it is added to the live analysis marked as yours, and no later reading replaces it (a link can only be kept once both of its events are there). **Put this reading back** replaces the scene's current reading with the earlier one. The current one is kept as another earlier reading first, and anything you kept as your own stays. It is refused while an analysis is running, which would only replace it again. **Delete** removes one earlier reading for good, after a confirmation. A scene that was cut differently, for example after you edited its words, keeps its earlier reading under its chapter; you choose which of the chapter's scenes to keep each item on, with the scene its quote is in already selected. How many readings of each scene are kept is a setting — Settings → AI model & connection → **Earlier readings kept for each scene** — five by default; a reading identical to the newest one is not stored twice. Only what the model made is kept this way: anything you wrote or edited yourself is never replaced in the first place. Earlier readings are labelled AI-judged, like the rest of the analysis.

A chapter's **summary** and **tension score** work the same way: when a reading replaces them, the ones that were there are kept right beside a chapter's Earlier readings, as **Earlier summaries and tension scores**, each with its score, its reason and when it was made. **Restore** puts one back (the current summary and score are kept first, so nothing is lost either way) and **Delete** removes it for good. The same setting controls how many of these are kept.

**Reader-knowledge and arc injection.** Once Story Analyst has tracked what the reader has been told and by which chapter, **Scene beat**, **A → B Bridge** and **Refine selection** automatically factor it in: the model is told plainly what the reader already knows (so it doesn't repeat an established fact as if it were new) and what the reader doesn't know yet (so it doesn't accidentally spoil it early). For a character with a stated Arc it also tells the model which stage of that arc they are in at this chapter. This happens quietly in the background; there is nothing to turn on beyond having run an analysis.

#### Health report

Click **Run health report** (in the Health report tab) for a deeper pass over the whole manuscript, or use **More run options** for a range of chapters or a full re-judge. It judges whether each character's arc actually earns its transformation, explains genuine emotional echoes and structural parallels between scenes (quoting, from each of the two scenes, the words that echo, and checking each quote against its own scene, so a finding is never written without both), traces how each motif or theme you track develops, checks what narrative function each scene serves, and runs five structural checks: no dead-weight scenes, no long-open promises, no long flat stretch with nothing changing, no character with real presence who never drives anything, and no chapter that could be cut without changing anything downstream. Like the analysis, it can be resumed if interrupted, and re-running only re-judges what has changed.

The report opens with a **Structural integrity** percentage, derived only from the five structural checks, never from anything judged, so it stays stable between runs unless the manuscript itself changes. Under it, a small **Score history** line chart shows each finished run's score, the change since the previous run, and whether that run covered the whole manuscript or a range, so you can watch the number move as you revise. Click any check to see why it passed or failed. Below that: **Issues** and **Worth examining** (every problem found, most serious first, each with the real passage it is grounded in, a **Show in chapter** button, and a **Dismiss** button for anything you've decided isn't a problem), **Most developed elements** (calculated signals: a character driving real consequences, a promise fully paid off), and **Things you may not have noticed** (emotional echoes, motif trajectories, structural parallels, reveals that tighten toward the end, a breakdown of dramatic irony, suspense and mystery across your manuscript, and any reveal that lands with no earlier suspense or irony built around it). A finding listed under Issues or Worth examining is not repeated under Things you may not have noticed. Every item in the report, including the score, each check, each finding and each entry under Most developed elements and Things you may not have noticed, carries its own label. The score and everything beside it describes how your story's threads, causes and characters connect; it does not measure how well the book is written.

A row of filter chips (**Characters / Plot / Information / Craft / Meaning / Problems**) narrows the report to just that kind of finding; **Problems** shows every issue and thing worth examining together, regardless of category. The **List / Visual** switch shows the score as a filled bar, a bar per check whose length is that check's share of the score (red if flagged, green if passed), issues by area, and a stacked passed/flagged/excluded bar.

#### What if… (Counterfactual Laboratory)

Explore a hypothetical: remove a character's actions from a chapter onward, and see what your manuscript's own causality graph says would still happen. It is grounded in the real events it removes and never rewrites anything you have written.

1. Open the **What if…** tab.
2. Give the exploration a short **Name** (your own label, for the list below), pick a **Character** and the chapter to diverge **From**, and describe the **Premise** in your own words.
3. Click **Explore**.

QuillWork assembles every real event that character is responsible for from that chapter onward, traces what depends on them through the causality graph (the same reachability calculation the Domino test uses), shows what percentage of the story's other events would still occur along with how many events were removed, how many depend on them, and how many facts and answered questions would be lost, and narrates what the divergence would actually mean: **would unravel the plot**, **would have ripple effects**, or **would barely matter**, backed by the specific removed events it is grounded in. The events removed are always all of that character's actions from the chosen chapter onward; your premise guides the narration but does not change which events are removed.

This needs a character with real recorded actions from the chosen chapter onward. Running the Story Analyst on more of the manuscript first, or picking an earlier chapter, will surface more to work with. **Past explorations** stay listed below the form; delete one with the bin icon (after a confirmation). Nothing here ever touches your actual manuscript or Bible.

#### Patterns

Every section in the Patterns tab is collapsible and carries its label.

- **Narrative Debt** (Calculated): one number for everything the manuscript still owes the reader, with its breakdown underneath. It rolls up three figures already shown elsewhere on this screen: overdue promises (from the Questions & promises ledger, weighted by how long they've been open and how central they are), dead-weight scenes, and characters whose share of self-initiated actions has fallen sharply since their first real stretch in the book. Every contributing item is listed underneath, worst first, each with **Show in chapter** or **Open chapter**. It is never a quality score: it only counts unpaid debt, and it can only ever disagree with the sections it's built from if one of them has changed since the last read.
- **Suspense architecture** (Calculated): for every fact and character, classifies each moment as **dramatic irony** (the reader knows, the character doesn't), **suspense** (the character suspects or knows what the reader hasn't been told), **mystery** (neither the reader nor the character knows yet) or **revelation** (both learn it in the same chapter). List, or Visual with one lane per fact and a coloured dot per chapter; click a dot for its detail.
- **Domino test** (Calculated): pick a chapter and press **Run check** to see what would stop making sense if it were cut, as a real count rather than a High/Medium/Low guess: the events that depend on it, the facts no longer learned, scenes losing their motivation, questions left unanswered, foreshadowing setups losing their payoff, and relationship changes that would no longer occur. If nothing depends on the chapter it says so plainly. Visual draws a mini causality graph of the cut chapter's own events and everything downstream.
- **Reveal timing** (Calculated): per fact, the number of chapters between the reader first suspecting it and it being confirmed, longest first; a fact revealed with no earlier suspicion is left out. Visual draws a bar per fact.
- **Dialogue fingerprint comparison** (Calculated): every character with at least 10 lines of your own dialogue, side by side on average sentence length, contractions (per word), questions and interruptions (per line). Needs Scenes analysis to have run.
- **Character arc simulator** (Calculated chain, AI-judged verdict): pick a character with a written Arc (in their own editor) to see their chain of choices, belief, goal and relationship changes, and discoveries in chapter order, plus a badge saying whether a health run judged the arc **Earned**, **Partially earned** or **Not earned**, with reasoning. The panel never calls the model itself, so it says "Not judged yet" until you have run a health report. Chapters the verdict cites are highlighted.
- **Who drives the plot (Character agency)** (Calculated): for every character, how many actions they initiated versus merely reacted to, how many were irreversible, and how many led to consequences, counted from your events and never rated by the AI; a bar chart in Visual view. **Did anyone become more reactive?** lets you pick a chapter and compares each character's share of self-initiated actions before it with the share from that chapter on; a drop of 25 percentage points or more is flagged, and the threshold is stated so you can see why it fired.
- **Narrative momentum** (Calculated): counts what actually changes in each scene (goals, relationships and beliefs shifting, reveals, raised stakes, options removed, irreversible events), per scene and per chapter, beside each chapter's tension score from Pacing. It flags "tense, but little actually changes" and "quiet, but a lot changes", the kind of mismatch two AI opinions can't reliably expose.
- **Dead-weight scenes** (Calculated): scenes where none of the events lead anywhere, with a button to open each chapter. One live event is enough to keep a scene off the list.
- **Facts the reader learns before the protagonist** (Calculated): choose your protagonist; every fact the reader already knows or strongly suspects while the protagonist still doesn't is listed with the size of the gap, the sign of a mystery solved too early for the reader.
- **Motifs, symbols & themes** (Calculated finding, AI-judged development): track a recurring image, object or idea by typing the words to look for (several allowed, separated by commas, for example "lighthouse, beacon") and choosing Motif, Symbol or Theme. QuillWork finds every scene that mentions it, lists the passages (each with **Show in chapter**), and plots which chapters it appears in. The Health report then judges how it develops across the book. QuillWork only observes these; it never writes one into your prose.
- **Emotional echoes** and **Parallel scenes** (Calculated): press **Find echoes** or **Find parallel scenes** to compare the meaning of every scene. Echoes are scenes at least three chapters apart that share a character and read alike; parallel scenes are structurally very similar scenes that aren't adjacent, which may be a deliberate echo or accidental repetition. Each pair shows the similarity and both passages. This needs an embedding model; if you don't have one, the panel says so and points you to [Search index](#9-search-index--working-with-very-long-novels). The Health report adds the AI's view of what reversed or whether the repetition looks intentional.

#### Where else the Analyst's findings show up

- **Pacing** shows suspense markers ([8.11](#811-pacing)).
- **Plot threads > Visual** draws each thread across the chapters it advances ([6.4](#64-plot-threads)).
- **Plot ideas** can pay off an overdue promise, work from a chapter's future consequences, or give a reactive character the initiative ([8.2](#82-plot-ideas)).
- **Chat** can answer from calculated figures such as who drives the plot and what is still unresolved ([8.10](#810-chat)).
- **Characters** show their importance over time and inferred psychology ([6.1](#61-characters)).
- **Scenes** show each analysed scene's facts and functions ([5.7](#57-scenes)).
- **Scene beat's "Intended effect"** lists the same scene jobs, then checks the draft against what you asked for ([8.1](#81-scene-beat)).
- **Scene beat's "Momentum target"** re-uses Narrative momentum's own counting rule, plus the promise ledger, to check a draft against a target and any named relationship, question or intention ([8.1](#81-scene-beat)).

---

## 9. Search Index — Working with Very Long Novels

A full novel bible plus every chapter's text can easily exceed what fits in a model's context window — especially past 100,000 words. QuillWork solves this with a local **semantic search index**, built directly into your project's own database rather than a separate program: chapters (in passages), your characters, locations, facts, worldbuilding entries, relationships, scenes, and [Research Workspace](#612-research-workspace) uploads are all embedded, so when the AI needs to know "what happened with this character 40 chapters ago," or which of fifty tracked facts actually matters to this scene, it retrieves the *specific relevant material* rather than needing everything in context at once.

This runs automatically in the background — most users won't need to think about it — but it does require a small **embedding model** loaded alongside your writing model.

### 9.1 Setting up an embedding model

Open **Search index** in the sidebar. It shows a status banner:

- 🟢 **Embedding model working** — an embedding model is reachable, and the banner says how many dimensions its vectors have.
- 🟡 **No embedding model detected** — with the reason. Click **Set up embedding model automatically**. QuillWork asks you to confirm, then looks for an embedding model your backend already has and, if it finds one, uses it ("Found existing embedding model"). If there is none, **with Ollama** it downloads `nomic-embed-text` (about 270 MB) through Ollama and shows the progress. **With LM Studio** it asks LM Studio to download `text-embedding-nomic-embed-text-v1.5`; not every LM Studio version can do that on request, and when yours cannot QuillWork says so and tells you to download an embedding model yourself in LM Studio, load it, and click the button again.
- 🔴 **Could not reach the server** — the check itself failed.

If you already know the name of your embedding model, type it into **Embedding model name** and click **Rebuild search index**.

An embedding model is **not** your writing model — it's a small second model that only converts text into a numeric representation for search. **It has no effect on NSFW content or the writing model's behaviour** — embedding models can't refuse or filter anything; there's no "generation" step for them to censor.

### 9.2 How indexing happens

- Every time you save a chapter (manual save, autosave, or switching chapters), and when you add one with [Add written chapter](#87-add-written-chapter), it is re-embedded in the background **only if the text actually changed**: saving the same text again makes no request to the embedding model.
- The same applies to characters, locations, facts, worldbuilding entries and relationships: adding, editing, deleting or merging one, or bringing some in with an import, queues a background re-embed, again only for what actually changed. A fact or entry you have switched off for AI context is never embedded.
- As a safety net, about once a minute QuillWork checks that the index still matches your chapters and Bible entries, and brings it back in step if it does not, whatever changed them. It never starts building an index that was never built: that is your choice, below.
- **Embed manuscript** (sidebar, Story section, after asking you to confirm) and **Rebuild search index** (in the Search index panel) force a full rebuild of the chapters, Bible entries and research assets, whether or not they changed. Use this after a bulk import from an older QuillWork version, after upgrading from a version that predates this section, or if you've made large manual edits outside the normal save flow. Scenes are embedded when they are analysed, for Emotional echoes and Parallel scenes.
- The **Search index** panel shows how much is indexed, counted apart: chapters (and the passages they were cut into), Bible entries, scenes and research items.
- Upgrading an existing project to the newer storage format triggers a one-time automatic re-embed of every chapter and Bible entry already in it. There's nothing to do on your end, and retrieval simply falls back to a plain, unscoped bible view until it finishes (the same graceful fallback Chat already uses when no embedding model is set up at all).

### 9.3 Where retrieval kicks in

Relevant earlier chapter passages are automatically pulled into context for Scene beat generation, Continuity checks, Chat, and the A → B Bridge tool, the places where knowing "what actually happened earlier" matters most.

Scene beat, Refine, and Chat go further: once your Bible is big enough they scope down to what the passage at hand needs, rather than sending everything on every call (see [6.11](#611-facts--constants)). By default, with more than 15 facts, or more than 10 worldbuilding entries, the search picks the ones relevant to the passage. With more than 10 characters, or more than 8 locations, the ones named (by name or alias) in what you asked for and the text just before it are given in full. Each of these four numbers is a setting (Settings → AI model & connection → Bigger books: when to send only what matters); a lower number scopes down sooner, 0 always scopes down, and a higher number sends more of your bible in full on every call. Relationships follow the characters: only those involving a character in the passage are listed in full, and the indirect connections between characters are still worked out from all of them. Nothing is deleted from your bible by this. The characters, locations, facts and worldbuilding left out of a prompt are still named in it, marked as not in this passage, and relationships that involve no character in the passage are left out of that one prompt. A character actually present in the scene, and their relationships, are always included regardless of how well they happen to match the search. Without an embedding model the facts and worldbuilding are simply sent in full. Continuity check keeps the full bible in view instead, since cross-referencing everything at once is its whole job, and adds retrieval on top for earlier chapters and relevant [Research Workspace](#612-research-workspace) references.

---

## 10. Projects — Saving, Loading, Switching Novels

**Projects** in the top bar.

- **New project** — starts a blank bible with a title and genre.
- **Project list** — shows every saved novel with its chapter count and total word count. Click one to load it as the active book (the current one is saved to its project file first if it has unsaved project-level changes).
- Click the bin icon on a project to delete it permanently, after a confirmation. Deleting the project you have open resets the editor.
- Projects are stored as individual files in a `projects` folder inside your QuillWork data folder, so you can back them up, copy them, or move them between installs directly. **Settings > Data & storage** shows where that folder is (by default `%LOCALAPPDATA%\QuillWork` on Windows and `~/.local/share/quillwork` on Linux) and can move it anywhere.

Saving a project snapshots the current bible (chapters, characters, everything) under a project ID. If the book is linked to a Series, only the *local* data is stored in the project file — shared series data lives in its own series file and isn't duplicated.

---

## 11. Exporting Your Novel

### 11.1 Book setup — front and back matter

**Book setup** in the sidebar. Fill these in once and every export format (Word, PDF, EPUB) automatically builds a proper title page, copyright page, dedication, epigraph, table of contents, and back matter around your chapters — no manual formatting needed. Leave any field blank and that page is simply skipped.

| Field | Produces |
|---|---|
| **Author name** | Byline on the title page, and the name used in the copyright notice |
| **Publication year** | Used in the copyright notice (defaults to the current year if blank) |
| **ISBN** | Included as EPUB metadata; stored for your reference in other formats |
| **Copyright notice** | A dedicated copyright page. Auto-generated as *"Copyright © {year} {author}. All rights reserved."* if left blank |
| **Dedication** | A dedicated dedication page |
| **Epigraph** and **Epigraph attribution** | A dedicated epigraph page, a quotation before the story begins, and who said it |
| **Preface** | An optional page of its own right before Chapter 1 |
| **Acknowledgments** | A back-matter page after the last chapter |
| **About the author** | A back-matter author bio page, and the only source for the bio paragraph in the Query letter |
| **Call to action / review request** | A closing back-matter page — e.g. asking readers to leave a review |

If this book is linked to a [Series](#7-series--sharing-a-world-across-multiple-books), an **"Also in This Series"** back-matter page is generated automatically from the other books linked to it — you don't need to type anything for this.

A separate **Submission info** section holds contact details (real name, address, phone, email) used only by the [manuscript export format](#114-manuscript-format--traditional-submission) and query letters — these never appear in a finished book export.

Changes save automatically as you type, same as World & style.

### 11.2 Formats

| Format | Use for |
|---|---|
| **Word (.docx)** | Formatted, print-ready manuscript |
| **PDF** | Print-ready, fully typeset |
| **EPUB** | E-readers, Kindle, Apple Books, Kobo |
| **Markdown** | Pandoc, Obsidian, other plain-text tooling. Tick **Preserve rich text formatting** to keep bold, italic, underline, strikethrough, colour and images as embedded HTML |
| **Plain text** | Universal, minimal |
| **Bible JSON** | Full structured backup of everything — characters, locations, relationships, threads, timeline, chapters |
| **Manuscript** | Agent/publisher submission format — see [11.4](#114-manuscript-format--traditional-submission) |

Choose whether to include **Chapter text**, the **Novel bible** and **Author's notes** (off by default, on for Markdown, and never included in the manuscript format), then click **Export & download**. A progress bar shows the export running, and the file downloads as `Title_date_time.ext`. If you set a **Default export folder** in Settings > Data & storage, a copy is also saved there.

**Formatting in exports.** Bold, italic, underline, strikethrough, colour and embedded chapter images are written natively into the formats that can hold them:

| Format | Bold, italic, underline, strikethrough | Colour | Embedded images |
|---|---|---|---|
| **Word (.docx)** | Kept | Kept | Kept, scaled to fit the page |
| **PDF** | Kept | Kept | Kept, scaled to fit the page |
| **EPUB** | Kept | Kept | Kept, packaged in the book |
| **Markdown** | Kept if you tick Preserve rich text formatting | Same | Same |
| **Manuscript** | Kept (emphasis is normal in a submission) | Left out: plain black text | Left out |
| **Plain text** | Removed | Removed | Removed |

Formatting is never sent to the AI, the search index or audiobook narration.

### 11.3 Print typesetting (Word & PDF)

When exporting to Word or PDF, a **Trim size** selector appears — this sets the actual page dimensions and margins to match how the book will be printed:

| Trim size | Typical use |
|---|---|
| **6 × 9 in** | Trade paperback — the most common size for self-published fiction |
| **5.5 × 8.5 in** | Digest |
| **5 × 8 in** | Novel / mass-market style |
| **A4** | International standard |
| **US Letter** | Manuscript-style printing |

Both formats automatically include:
- A **running header** alternating between the book title and author name on facing pages, with **page numbers**, starting from the first page after the title page
- An ornamental mark at the start of every chapter
- **Smart typography** — straight quotes and apostrophes become proper curly quotes, `--` becomes an em dash (—), and `...` becomes a proper ellipsis (…). This only affects the exported file — your text in the editor is never modified
- A real, auto-updating **table of contents** in the Word export (right-click it and choose "Update Field" after opening in Word)

**Scene breaks:** if a paragraph in your chapter consists only of a break marker — `***`, `* * *`, `# # #`, `- - -`, or similar — QuillWork renders it as a proper centred ornament (❦) instead of printing the literal asterisks. Just type one of these on its own line/paragraph wherever a scene break belongs.

### 11.4 Manuscript format — traditional submission

Select **Manuscript** as the export format for a document formatted to the industry-standard (Shunn) convention agents and publishers expect — a completely different shape from the "finished book" formats above:

- **US Letter, 1-inch margins, 12pt Times New Roman, double-spaced** throughout
- **Title page**: your contact details (real name, address, phone, email — from [Book setup's Submission info](#111-book-setup--front-and-back-matter)) in the top-left, approximate word count top-right, and the title centred roughly a third of the way down, with "by [author name]" beneath it
- **Running header** on every page after the title page: `Surname / TITLE KEYWORD / page number`
- **No front or back matter at all** — no dedication, no epigraph, no copyright page, no table of contents, no ornaments. Scene breaks render as a plain centred `#`, matching manuscript convention exactly
- Ends with **"END"** — or **"— end of excerpt —"** if you've exported a partial manuscript

**Chapters to include** — most agents and publishers ask for a sample, not the full manuscript:
- **Full manuscript** — every chapter
- **First 3 / First 5 chapters** — the most commonly requested sample sizes
- **Custom range** — specify exact start and end chapter numbers

---

## 12. Audiobook Narration

**Narrate**, in the sidebar's **Audio** section. Generates an audiobook narration of your novel using a local text-to-speech engine — [Chatterbox TTS Server](https://github.com/devnen/Chatterbox-TTS-Server) — running separately on your machine (QuillWork talks to it over HTTP; it doesn't install or manage it for you).

**Audiobook narration is an optional, opt-in feature** — QuillWork works fully without it, and by default there's no audio UI at all (no Narrate button, no prompts). You only turn it on if you want it.

### 12.1 Setup

1. Install the Chatterbox TTS server once (see its own documentation) — by default it runs at `http://localhost:8004`, which is what QuillWork expects out of the box.
2. Open **Settings** → **Audiobook narration** and switch on **Enable audiobook narration**. This reveals the audio controls and adds a **Narrate** item to the sidebar's Audio section. (Turn the toggle back off any time to hide it all again.)
3. In that same Settings section you can point QuillWork at your Chatterbox install — its **server address**, its **folder**, and (advanced) its **Python** — all with guidance beneath each field. Then **Start server** launches Chatterbox in a separate console window and waits for it to come online (this can take a while the first time, while the model loads); **Stop** shuts it down. If you'd rather start Chatterbox yourself, you can — QuillWork just needs the server address to be right.
4. Open **Book setup** and choose a **Narrator voice type**:
   - **Predefined voice** — one of Chatterbox's ~30 built-in voices
   - **Cloned voice** — a reference audio clip already set up on the Chatterbox side (e.g. a voice you've recorded or cloned yourself)

   Then pick the specific voice from the dropdown below it — both lists are pulled live from the running Chatterbox server, so it must be online for them to populate.

QuillWork doesn't install or configure Chatterbox — Start/Stop just launches and stops the server you've already set up.

### 12.2 Generating a narration

1. Choose **Chapters to narrate**: the full manuscript, the first 3 chapters, or **selected text** — highlight a passage in the editor first, then pick this option and only that selection is narrated (useful for previewing a voice or re-doing one troublesome paragraph without regenerating the whole chapter). A note under the dropdown confirms how much text is selected, or warns if nothing's highlighted yet.
2. Click **Generate audiobook**. A progress bar shows which chapter is being narrated, with elapsed and estimated remaining time — this can take a while for a full novel, since each chapter is synthesized in full.
3. When complete, a ZIP file downloads automatically — one MP3 per chapter, or a single `selection.mp3` when narrating just a selection.

**What QuillWork does automatically:**
- Scene-break markers (`***`, `# # #`, etc.) are stripped before narration — they're stage directions for print layout, not something that should be read aloud.
- **Retried automatically if the audio comes back near-silent.** Text-to-speech occasionally produces a near-silent clip for a chunk of text — particularly text trailing off with an ellipsis (`…`), which fiction dialogue does constantly. QuillWork checks the loudness of every generated chunk and retries (up to 3 times) if it looks broken, keeping the best attempt.
- **Unchanged chapters are skipped on repeat runs.** If you regenerate the audiobook after only editing a couple of chapters, QuillWork reuses the cached audio for everything that hasn't changed rather than re-narrating the whole book from scratch.

**Current scope:** each chapter becomes its own MP3 file rather than one single stitched whole-book file.

### 12.3 Per-character voices

By default, every chapter narrates in a single consistent narrator voice throughout — nothing below changes anything until you assign at least one character their own voice.

Once a chapter has been through [Scene analysis](#57-scenes) (so QuillWork knows which lines of dialogue belong to which character), open a character in the Bible and set their **Narration voice** (same predefined-or-cloned picker as the book's own narrator voice, see [Setup](#121-setup) above). From then on, that character's own attributed dialogue is spoken in their assigned voice, while everything else — narration, and any dialogue belonging to a character with no voice assigned — stays in the book's narrator voice. A chapter is stitched together from several short clips under the hood rather than one continuous read, but the result is still one MP3 per chapter, same as before. The near-silence retry and unchanged-audio caching from [Generating a narration](#122-generating-a-narration) both still apply, just to each of those clips individually rather than to a whole chapter at once.

A chapter that hasn't been through Scene analysis yet, or where no character has a voice assigned, narrates exactly as it always has — the single narrator voice, no change in behaviour.

---

## 13. Saving, Autosave, and Closing QuillWork

- **Manual save**: **Save** in the top bar, or **Ctrl+S** anywhere.
- **Autosave**: on by default (toggle in the top bar), saves the current chapter automatically ~30 seconds after you stop typing, and whenever you switch chapters.
- **Save status** next to the project name shows `saved` / `saving` / `unsaved` at a glance.
- Several other things happen in the background too (snapshots, Bible extraction, search indexing, linked-file sync, backups). They are all listed, with where to see them and how to switch them off, in [Appendix A.12](#a12-things-that-happen-automatically).
- **Closing QuillWork**: use the **Close** button in the top bar (autosaves, shuts the server down cleanly, closes the browser tab) rather than just closing the tab — this ensures the server process actually stops rather than continuing to run in the background. `Stop QuillWork.bat` does the same thing if you started via the console launcher.

### 13.1 Version history

Saving keeps your *current* work safe; **version history** lets you go *back*. Open **Version history** in the sidebar's Story section.

- **Automatic snapshots** — QuillWork snapshots the whole novel when you open it and roughly every 10 minutes while you work. Identical states aren't snapshotted twice, so the list stays meaningful. Automatic snapshots are pruned to the most recent 40 per novel.
- **Named versions** — click **Save a version now** and give it a name (e.g. "First draft done", "Before the big rewrite") at any milestone. Named versions are **kept forever** — they're never pruned.
- **Compare** — click **Compare** on any version to see exactly which chapters changed versus your current novel: each chapter is marked *unchanged / modified / added / removed* with the word-count change. Click a modified chapter to see a paragraph-level diff — added text highlighted green, removed text struck through in red.
- **Restore** — click **Restore** to roll the whole novel back to that snapshot. Before it does anything, QuillWork takes a **safety snapshot of your current state** and puts it at the top of the list — so a restore is itself undoable; you can never lose your place by going back. The search index is brought back in step with the version you restored, so Chat and Continuity check read the chapters you are looking at.

Everything is stored locally: each snapshot is an ordinary `.zip` file (containing a single `bible.json`) in a `snapshots` folder inside your QuillWork data folder (Settings > Data & storage shows where), so a version can be recovered by hand in your file manager even without the app. Nothing is ever uploaded.

**About the newer storage format.** Each project moves, automatically and one project at a time, from a single JSON file into a small local database the first time you open it on a build that supports this. Before that conversion touches anything, QuillWork writes a full backup zip of all your projects into a `pre_migration_backups` folder inside your data folder. It then converts that one project and immediately checks its own work by exporting the new database straight back out and comparing it, piece by piece, against what went in. If anything doesn't match exactly, the conversion is abandoned there and then and the project quietly stays on the old JSON format, unchanged and fully working; nothing is lost and nothing is left half-converted. Either way you're told what happened: a brief confirmation when a project upgrades successfully, or a dialog explaining that it didn't (and where the backup is) if it doesn't. The old JSON file is never deleted or renamed, and stays fully up to date on every save regardless of whether that project has moved to the new format, so rolling back to an older QuillWork build for any reason still finds real, working data.

**Important: don't point a sync client at your QuillWork `data` folder.** An older version of this manual suggested doing exactly that (Dropbox, OneDrive, Syncthing) for cross-machine history and off-machine backup. That was fine when every project was a single JSON file, because a save was always a whole-file replacement. It is **not** safe once a project has moved to the newer database format described above: that project's live database sits in the `data` folder as an open file plus two small sidecar files, and a sync client copying those mid-write can produce a corrupted database. **Keep the live `data` folder local, and use Cloud backup (13.2) below instead**, including its own continuous-copy option, which is the safe, database-aware equivalent of the old tip.

### 13.2 Cloud backup

Open **Cloud backup** in the sidebar's Story section. This backs up your whole novel to a folder in **your own** cloud — QuillWork hosts nothing and never sees your work.

**Why it works this way:** the first time you open the panel, a card explains it — in short, your manuscript never passes through us, there's no account or subscription with us, you choose the provider (including end-to-end-encrypted ones like Proton Drive or Sync.com), and it keeps working forever because nothing depends on a server we run. You can reopen that explanation with the **"Why we do it this way →"** link.

**How to use it:**
1. In Dropbox / OneDrive / Google Drive / Proton Drive (whichever you use), note a folder that your provider's app keeps synced — or make one, e.g. `…\Dropbox\QuillWork backups`.
2. Paste that folder's full path into **Backup folder**. A green tick confirms QuillWork can see it.
3. Click **Back up now** — QuillWork writes a dated `.zip` (`QuillWork-backup_<date>.zip`) containing all your projects, the bible, and your style rules. Your cloud's own app then uploads it, exactly as it would any other file.
4. Optionally tick **"Also back up automatically when I close QuillWork"** to write a fresh backup every time you exit.

Each backup is a self-contained `.zip` you can open anywhere, with or without QuillWork — you fully own your backups, and nothing is ever sent to us.

**Continuous backup, for a project on the newer database format.** Below the folder and on-close settings, tick **"Keep a continuous copy in my synced folder"** to get back the *continuous* protection the old data-folder tip used to give, without its corruption risk. On a timer (15 minutes by default; adjust with **Check every (minutes)**), QuillWork writes a complete, always-consistent snapshot of that project's live database into the same backup folder above, safe for your cloud app to upload the moment it changes. It's named after your project's own title so it's identifiable without opening QuillWork, and it's skipped silently (with the last successful copy time shown under the setting) if the folder is temporarily unreachable; your work in the app is never interrupted by it. This only does anything once a project has moved to the newer database format; a project still on the older JSON format is already fully covered by the dated `.zip` backup and back-up-on-close above.

---

## 14. Troubleshooting

**LLM connection dot is red.** LM Studio/Ollama isn't running, or the endpoint URL in Settings > AI model & connection doesn't match its port. Start the backend, confirm the port (1234 for LM Studio, 11434 for Ollama by default), and click Test.

**LLM connection dot is amber.** QuillWork can reach the backend, but no model is loaded yet. Load one in LM Studio/Ollama; some setups load a model automatically on first request (JIT) even while amber.

**AI tools return nothing / error out.** Check the connection dot first. If green, the model itself may have failed or timed out — try again, or check the backend's own console/logs for errors. On Ollama specifically, also check Settings → **Model** isn't accidentally pointed at an embedding model (e.g. `nomic-embed-text`) — see the note under [Section 4](#4-connecting-an-ai-model).

**Un-AI scan skips a passage with a parse error.** Rare, but can happen if the model's output doesn't match the expected format for that one section — QuillWork skips just that section safely (nothing is corrupted or applied) and continues with the rest.

**Search index shows "No embedding model detected."** See [Section 9.1](#91-setting-up-an-embedding-model) — either click the automatic setup button, or load an embedding model manually in LM Studio/Ollama.

**QuillWork won't start / installer fails.** Check `data/quillwork_error.log` in the install folder for the Flask server's own error output — this is the most reliable source of truth for startup failures.

**Narrate panel shows "Chatterbox server not reachable."** The Chatterbox TTS server is a separate program QuillWork doesn't manage — make sure it's actually running (default `http://localhost:8004`) before opening the Narrate panel or picking a narrator voice.

**"This request needs about N tokens of room... Try a shorter request, or switch to a model with a larger context window."** Scene beat, Refine, and the other AI writing tools check *before* generating whether your bible, retrieved manuscript context, and the requested passage will actually fit in your model's loaded context window — if they won't, QuillWork says so immediately instead of letting the model run for a while and hand back a passage that's silently cut off mid-sentence. Either shorten the request (a smaller target length, a leaner bible), or load a model with more room — see [Models with a larger context window](#models-with-a-larger-context-window) for a tested list with download links.

---

## 15. Beta Testing, Feedback & Licensing

During the beta, QuillWork runs on a temporary key rather than a permanent purchase. This section covers how to send feedback, and how a genuine beta report turns into a permanent license.

### 15.1 Sending a beta report

Click **Beta report** — the gold button in the top bar, next to Projects (also in the command palette) — to open a short feedback form on the QuillWork website. The link is tagged with the exact version you're running automatically, so a report is always traceable to a real build, not "whatever's current." The form asks for a rating, what worked, any bugs or issues, what's missing, and whether you'd recommend it — a real report, not a single text box.

Every report is read by hand, not auto-approved. A genuine one earns you a permanent license key back by email — no more 28-day expiry.

### 15.2 Activating a license key

Got a new key — from a beta report, or after a purchase once QuillWork leaves beta? Open **Settings → License**, paste it into the **License key** field, and click **Activate**. You don't need to wait for your current key to expire first; a new key takes over immediately.

Activating a **new** key needs an internet connection for a moment. QuillWork checks it against the license server so a key can't be shared round. A key belongs to one install at a time, but you can move it: if you reinstall, copy QuillWork to another computer or replace your computer, activate the same key again and it moves across. A key can move to a new install up to three times; after that, email and it will be sorted out. Going back to an install the key has already lived on is free. Every normal launch after activation checks the key's own signature on your computer, with no server involved.

Settings → License also shows your current license status at a glance — whether it's valid, who it's registered to, and when it expires (or, for a permanent key, that it doesn't).

### 15.3 Updating QuillWork

QuillWork can tell you when a newer version is out and install it for you, so a fix doesn't have to arrive as an email attachment.

**Check for updates.** Open **Settings → Updates** and click **Check for updates**. QuillWork asks the QuillWork server whether a newer version exists. If one does, a window shows what changed and gives you two choices: **Update now** or **Decline**. If you are up to date, it says so. **Decline** skips that version: you are not asked about it again, but you are told when a newer one is out.

**At start-up.** A few seconds after QuillWork opens, it makes the same check quietly. If a newer version exists, a small notice appears in the bottom-right corner with **See what's new**, which opens the same window. If the check cannot run (you are offline, or the server is down) you are not told: only an update is ever announced. The **x** on the notice hides it until the next start. Untick **Check for updates when QuillWork starts** to stop the automatic check; the button still works whenever you press it.

**What is sent.** The check sends your licence key, the version you are running and your platform (Windows, Linux or Mac). It sends nothing else: none of your writing, projects, Bible or settings. Nothing is downloaded until you choose **Update now**. An expired key cannot check for updates, and a copy running from a development checkout never checks.

**What Update now does.**

1. Saves the chapter you have open, so nothing typed is lost.
2. Downloads the new version's files from QuillWork's server, which fetches them from the release. A checksum confirms the download arrived intact, and QuillWork refuses anything incomplete or the wrong version. If the new version needs extra Python packages, they are installed at this point, before anything is replaced.
3. Closes QuillWork and updates the program files. It compares each file with the one already installed and replaces only the files that differ, keeping a copy of every file it replaces. A file the new version no longer uses is removed, and a copy is kept of that too. Your projects, Bible, settings and licence are separate from the program files and are never touched.
4. Starts the new version and waits for it to answer. This window then reloads by itself.

**If something goes wrong.** A failure before step 3 leaves everything exactly as it was, and the window says what happened. If a file cannot be replaced (on Windows, another program may have it open), or the new version is put in but does not start, QuillWork puts every previous file back, including any it had removed, and starts the old version again. It then tells you the update did not work and why. Nothing is lost either way. QuillWork will not start an update while an AI job is running: let the job finish, or press **Stop AI**, then try again.

**Some releases must be installed with the installer.** If a release has no update package, the window offers **Download installer** instead of **Update now**, and you install it as you did the first time. Your projects are kept.

**Manual download always works.** Switching the check off never stops you downloading a new installer yourself from the link in your beta email.

### 15.4 Diagnostic capture

If something goes wrong and you want to report it, **Settings → Updates → Diagnostic capture** can save the details for you. It is **off by default**.

Turn on **Keep diagnostic information**, reproduce the problem, then click **Save diagnostic bundle**. QuillWork saves a small zip file that you can attach to your bug report. QuillWork never sends it anywhere. While capture is on, QuillWork keeps a short rolling copy of its own recent status and error messages on your computer, capped at about 1 MB.

The bundle contains: your QuillWork version and platform, your settings with every key removed and any address stripped of a password, the recent messages, the start-up error log if there is one, and the result of the last update. It does not include your chapters, Bible, projects or research files. It is an ordinary zip file, so you can open it and read everything in it before deciding to send it. Turn the switch off at any time to stop keeping the messages.

---

## 16. Reference — Anti-AI Prose Rules

These rules are injected into the calls that draft or review your prose: Scene beat, Refine, Plot ideas and the Un-AI scan. They're the baseline for how QuillWork asks the model to write. The Synopsis generator and Query letter follow their own conventions, and Bridge plans events rather than writing prose, so they do not use these rules.

**You can edit them.** Open **Writing style rules** in the sidebar's AI Tools section (or the command palette). The panel shows the exact rules below in an editable box — tune them to your own taste (add your own banned words, change the dialogue-tag guidance, whatever) and click **Save rules**; your version is used for every creative call from then on. **Reset to default** restores QuillWork's baseline at any time. Your customisation is stored locally in `prompts.json` in your data folder.

**Style packs — share your style.** The same panel has **Export pack** and **Import pack** buttons. Export saves your current rules to a small `.json` file you can send to anyone (post it in a writing community, hand it to a co-author); Import loads a pack someone shared so you can review it and click Save to adopt it. There's no account and nothing is uploaded — a pack is just a file you own and pass around.

The defaults are:

- Write like a skilled human author, not like an AI assistant.
- Vary sentence length dramatically — short sentences land hard, longer ones build rhythm.
- No em-dash overuse.
- Banned words/phrases: *suddenly, realized, felt a pang, couldn't help but, a mix of, myriad, tapestry, whirlwind, journey (metaphorically), delve, beacon, testament to.*
- No thesaurus-brain — plain word over impressive-sounding word.
- Dialogue tags: mostly "said." Avoid *exclaimed, queried, opined, breathed.*
- Show interiority through action and concrete detail, not by naming emotions directly.
- No tidy chapter-end summarising — end mid-breath where it fits.
- Sensory detail should be specific and unexpected, not generic.
- No moral conclusions handed to the reader.

The **Un-AI text** tool ([8.6](#86-un-ai-text)) runs this same rule set as a standalone audit pass against text you've already written, for cases where prose needs a second look after the fact.

---

## Appendix A. Complete Function Reference

Every function QuillWork performs, what it does, and exactly how to reach it. Column 3 gives the menu route (read `Sidebar > Bible > Characters` as "in the left sidebar, open the Bible group, click Characters"), any hotkey, and whether the function is also in the **Ctrl+K** command palette. Hotkeys are written for Windows and Linux; on a Mac use **Cmd** where the table says **Ctrl**.

Three things apply to almost everything below:

- **Only one slide-out panel is open at a time.** Press **Esc** or the panel's ✕ to close it. Clicking outside a panel never closes it, on purpose, so a choice window can't be lost by accident.
- **The sidebar groups are collapsed by default.** Click a group name (Bible, AI Tools, Submission, Import from other tools, Audio) to expand it.
- **Some features need the newer storage format.** The Research Workspace, the Story Analyst and the continuous cloud copy need it. Opening a project migrates it automatically, with a backup kept first.

### A.1 The window, navigation and help

| Function | What it does | How to access it |
|---|---|---|
| Command palette | A searchable list of every panel, action and chapter. Type to filter, then jump. | Top bar > **Ctrl K** button. Hotkey: **Ctrl+K**. Then **↑ ↓** to move, **Enter** to run, **Esc** to close |
| Save | Saves the open chapter and the project now. | Top bar > Save. Hotkey: **Ctrl+S**. Also Ctrl+K, "Save" |
| Autosave | Saves the open chapter about 30 seconds after you stop typing and whenever you switch chapters. Can be switched off. | Top bar > Autosave toggle |
| Save status | Shows the project title and whether the chapter is unsaved, saving, saved, or not saved. | Top bar, centre |
| Themes | Cycles Light, Sepia (softer, warmer page) and Dark. Remembered in this browser. | Top bar > sun/moon button; Settings > Appearance; or Ctrl+K, "Theme" |
| Settings | Opens every setting: licence, AI connection, models, storage, language and more (see A.11). | Top bar > Settings; click the connection strip at the bottom of the sidebar; or Ctrl+K, "Settings" |
| User manual | Opens this manual inside QuillWork. Error messages deep-link into the relevant section. | Top bar > Help; or Ctrl+K, "User manual" |
| Beta report | Opens the beta report form in your browser. Nothing is sent from inside the app. | Top bar > Beta report; or Ctrl+K, "Send beta report" |
| Getting started guide | The four-step first-run wizard: welcome, connect your AI, create or import a novel, tips. Shown automatically on a brand-new install. | Settings > More > Re-run the setup guide; or Ctrl+K, "Getting started" |
| Stop AI | Force-stops every AI operation running now, in any panel. Grey when idle, red only while an AI call is in flight. | Sidebar footer > Stop AI |
| Connection strip | Shows which backend (LM Studio or Ollama) you're on and whether it is connected, has no model loaded, or is unreachable. | Sidebar footer. Click it to open Settings |
| Close | Asks about any unapproved AI draft, saves, backs up if you enabled backup-on-close, and shuts QuillWork down cleanly. | Top bar > Close (red) |
| Tooltips | Hover any control for about a third of a second for an explanation. | Hover anywhere |
| Interface language | Shows QuillWork's own buttons and menus in English (UK or US), French, German or Spanish. Separate from your novel's language. | Settings > Language |

### A.2 Writing: chapters, editor and scenes

| Function | What it does | How to access it |
|---|---|---|
| Chapter list | Every chapter with its number, title and word count. Click to open. | Sidebar > Chapters |
| New chapter | Creates and opens a blank chapter. | Sidebar > New chapter (below the list); or Ctrl+K, "New chapter" |
| Reorder chapters | Swaps a chapter with its neighbour and renumbers both. | Sidebar > Chapters > hover a row > ↑ ↓ arrows |
| Delete chapter | Permanently removes a chapter, after confirmation. | Sidebar > Chapters > hover a row > ✕ |
| Chapter title and POV | Edit the chapter title; set an optional viewpoint character (with autocomplete). | Chapter header |
| Chapter word count | Words in the open chapter (markdown symbols aren't counted). | Chapter header, right. Total for the whole book: bottom bar, right |
| Chapter note | A private note for this chapter that is never sent to the AI. The panel is resizable. | Chapter header > sticky-note icon |
| Interlude toggle | Marks a chapter as an interlude: it exports without the "Chapter N:" prefix. | Chapter header > booklet icon |
| Re-scan bible | Re-reads a chapter you edited by hand and updates the Bible from it, via Add written chapter. | Chapter header > Re-scan bible |
| Scenes panel | Splits a chapter into scenes and attributes dialogue lines to characters. Per scene: lock, split, merge with next, and once analysed its viewpoint, place, day, mood, summary and functions. This is the step the Story Analyst needs first. | Chapter header > Scenes > **Analyse this chapter** or **Analyse whole manuscript** |
| Prose editor | The writing surface. Enter starts a new paragraph. Spellcheck follows your novel's language. | Main area (open a chapter) |
| Bold, italic, underline, strikethrough | Toggle each on the selection. | Bottom toolbar B, I, U, S. Hotkeys: **Ctrl+B**, **Ctrl+I**, **Ctrl+U**, **Ctrl+Shift+X** |
| Text colour | Eight swatches, a free colour picker, and "Default colour". | Bottom toolbar > colour button |
| Headings H1 H2 H3 | Turns the current paragraph into a heading; click again to revert. | Bottom toolbar > H1, H2, H3 |
| Insert table | Inserts a table (up to 50 rows by 20 columns). | Bottom toolbar > table icon |
| Embed image | Inserts an image from your Research Workspace library, or uploads a new one into it. | Bottom toolbar > image icon |
| Markdown source view | Shows the raw text QuillWork has stored for the chapter. | Bottom toolbar > code icon |
| Paste | Pastes as plain text. Markdown headings and pipe tables become real headings and tables. | **Ctrl+V** in the editor |
| Append box | Adds what you type as a new paragraph at the end of the chapter. | Bottom bar. **Enter** appends, **Shift+Enter** starts a new line |
| Voice dictation | Speech-to-text into the append box or the Scene beat box, using your browser's speech recognition. Works best in Chrome or Edge. | Bottom bar > microphone buttons |

Bold, italic, underline, strikethrough, colour and embedded images are kept natively in Word, PDF and EPUB exports, and in Markdown export when **Preserve rich text formatting** is ticked. A submission manuscript keeps emphasis but stays plain black with no images. They are removed before anything reaches the AI, the search index, plain-text export or audiobook narration, so your colour-coded notes never leak into a prompt.

### A.3 AI writing tools

| Function | What it does | How to access it |
|---|---|---|
| Scene beat | Describe what happens next, pick a length, generate. The draft streams into an editable block: Stop, Approve, Regenerate or Discard. Optional "Intended effect" tick-boxes ask the model to aim for something specific and then report what it detected. Optional "Momentum target" asks for a minimum number of real state changes, plus up to three named things (a relationship, an open question or promise, a character's intention) that must change, then reports a real count against each, never a model guess. If you have turned on the continuity-on-approve setting, approving also runs a continuity check on that passage. | Bottom toolbar > Scene beat (gold). Hotkey: **Ctrl+Enter** in the brief box to generate |
| Per-generation model picker | Chooses a different model for one generation only. | Scene beat panel and Refine panel, the small model dropdown |
| Chat | Ask questions about your manuscript and Bible; answers are grounded in your own text and, once the Story Analyst has run, in calculated figures such as who drives the plot and what is still unresolved. | Bottom toolbar > Chat; or Sidebar > AI Tools > Chat; or Ctrl+K, "Chat". **Enter** sends, **Shift+Enter** new line |
| Plot ideas | Three distinct ideas of a chosen type, including "pay off an overdue promise", "future consequences of a chapter's events" and "give a reactive character the initiative" (pick a character, least active first). | Sidebar > AI Tools > Plot ideas |
| A → B bridge | Give a start point and an end point; get three routes between them. | Sidebar > AI Tools > A → B bridge |
| Continuity check | Checks a passage against the Bible, earlier text, narrator claims, research references and your author-intent rules, with severity and a suggested fix. | Sidebar > AI Tools > Continuity check; or bottom toolbar > Check (pre-fills your selection) |
| Refine selection | Rewrites a selected passage to an instruction, with preset chips and a "match a character's voice" picker. Replace selection writes it back. | Sidebar > AI Tools > Refine selection; or bottom toolbar > Refine |
| Un-AI text | Scans a chapter or selection for AI-sounding writing and proposes human rewrites you tick and apply. | Sidebar > AI Tools > Un-AI text |
| Add written chapter | Paste a chapter you already wrote; QuillWork summarises it, extracts characters and threads, runs a continuity check and saves it. Retry or abandon if a stage fails. | Sidebar > AI Tools > Add written chapter |
| Pacing | Scores each chapter's tension from 0 to 10 and draws a chart. Suspense markers appear once Story Analyst data exists. Click a dot to open that chapter. | Sidebar > AI Tools > Pacing > **Analyze chapters** |
| Search index | Semantic and keyword search that lets the AI work with a book too long for its context window. Set up an embedding model and rebuild the index here. | Sidebar > AI Tools > Search index; or Sidebar > Embed manuscript (starts a rebuild at once) |
| Writing style rules | The editable prose rules injected into every creative AI call. Save, reset, export or import a style pack, or load a starter pack for another language. | Sidebar > AI Tools > Writing style rules; or Settings > More |
| Mark as claim | Records a narrator claim from selected text so the AI never treats it as established fact. | Bottom toolbar > Mark as claim (select text first) |

### A.4 The novel Bible

| Function | What it does | How to access it |
|---|---|---|
| Characters | Character cards with role, aliases, personality, backstory, arc and voice. Also: duplicate check, AI deeper check, and Check for contradictions (AI). | Sidebar > Bible > Characters |
| Dialogue fingerprint | Per-character speech statistics (sentence length, contractions, questions, interruptions), a voice-drift warning, and an AI "observed voice" suggestion you accept or dismiss. Needs 10 or more of your own dialogue lines. | Characters > open a character > Dialogue fingerprint |
| Importance over time | Shows how much of the plot a character drives across three bands of the book, as a list or a chart. | Characters > open a character > Importance over time |
| Character psychology | Infers core want, core fear, defence mechanism and wound from what the character actually does on the page, with the moments cited and each quote openable in the chapter. | Characters > open a character > Suggest character psychology (AI) |
| Character contradiction check | Finds places where a character acts against their own established traits, quoting the passage. Suggestion only; Dismiss remembers. | Sidebar > Bible > Characters > Check for contradictions (AI) |
| Locations | Places with description, atmosphere, sounds, smells and who is usually there. | Sidebar > Bible > Locations |
| Worldbuilding | Structured rules: magic systems, factions, religions, languages. "Check consistency (AI)" flags prose that breaks an established rule. | Sidebar > Bible > Worldbuilding |
| Facts & constants | Numbers you assert (prices, distances, dates), fed into every AI call unless you exclude them, with an optional consistency scan. | Sidebar > Bible > Facts & constants |
| Relationships | Pairs of characters with a dynamic, a 0 to 10 tension and kinds. List view, or a visual web where line weight shows tension. "How does X know Y?" finds the shortest connecting chain. | Sidebar > Bible > Relationships |
| Plot threads | Threads with status and introduction chapter. The Visual view is a bar per thread across the chapters it appears in (needs a Story Analyst run). | Sidebar > Bible > Plot threads |
| Timeline | Events by chapter and story day. List view, or swim-lanes grouped by character or by plot thread. | Sidebar > Bible > Timeline |
| Narrator beliefs | Claims your narrator makes that may be false, with status and the real truth. "Check for possible claims (AI)" proposes candidates. | Sidebar > Bible > Narrator beliefs |
| Knowledge tracker | Who knows which secret from which chapter. A matrix view, and "Check awareness (AI)" catches a character acting on something too early. | Sidebar > Bible > Knowledge tracker |
| Foreshadowing (Chekhov's Gun) | Setups you have planted and whether they paid off. "Check for setups (AI)" proposes candidates. Resolution is marked by you. | Sidebar > Bible > Foreshadowing (Chekhov's Gun) |
| Bible updates | Review queue for changes to existing characters and locations found later. Accept your edited text, or keep what you have. | Sidebar > Bible > Bible updates |
| World & style | Title, genre, novel language, synopsis, style notes, prose sample, author voice fingerprint, world notes and Author's intent constraints. Saves itself. | Sidebar > Bible > World & style |
| Author's intent constraints | Rules such as "never show violence on-page", each switchable. Enabled rules go into every AI call and into Continuity check. | World & style > Author's intent constraints. **Enter** adds a rule |
| Author voice fingerprint | The same statistics as the dialogue fingerprint, measured on your narration, with a drift warning. Needs 10 or more narration paragraphs. | World & style > Author voice fingerprint |
| Author notes | A project-wide notes box that is never sent to the AI. | Sidebar > Bible > Author notes |
| Series | Link books into a series and share characters, locations and world elements across them. | Sidebar > Bible > Series |
| Book setup | Front and back matter for exports: author, ISBN, copyright, dedication, epigraph, preface, acknowledgments, about the author, submission contact details. | Sidebar > Bible > Book setup |
| Deleting Bible items | Deleting a character, location, world element, relationship, plot thread, timeline event, narrator claim, fact, tracked secret, foreshadowing setup or author's-intent rule always asks first. Version history can restore an earlier copy of the novel. | The Delete button in each item's edit window |
| Auto-extract Bible info | While you write, quietly adds characters, locations, threads, facts and relationships from new text. Changes to existing entries go to Bible updates. On by default. | Settings > AI model & connection > Auto-extract Bible info as I write |

### A.5 Research Workspace

| Function | What it does | How to access it |
|---|---|---|
| Research Workspace | A drop-down wall for reference material: images, PDFs, text files, office documents, notes and web references. Everything visible is searchable and used as AI context. | Pull down the **Research** tab at the top centre of the editor; or Ctrl+K, "Research Workspace" |
| Pull-down handle | A click toggles the panel. Press and drag down to open and size it; drag up to close. | The Research tab, top centre of the editor |
| Upload | Add files by button or by dragging them onto the panel. Accepts images, PDF, .txt, .md, .docx, .xlsx, .pptx, .rtf, .odt, .ods, .odp, .csv, up to 20 MB each. | Research panel > Add Research > Upload files, or drag and drop |
| AI image description | An uploaded image is described by your vision model so its details can be searched and cited. | Automatic on upload; see Vision model in A.12 |
| Vision model swap | With LM Studio, offers to unload your writing model, load the vision model, describe the image, then reload the writing model. | Prompted when you add an image and a vision model is set |
| Notes and web references | Write a note, or store a URL with your own notes. The page itself is not fetched. | Research panel > Add Research |
| Topics | Organise items into topics that nest to any depth, drilled into like folders, with breadcrumbs, an "All items" view and an "Untagged" view. | Research panel; manage them from Research panel > Manage topics |
| Tags | Free-form tags on items; manage and delete them. | Item window > Tags; Manage topics > tags list |
| Search and filter | Searches the whole library, filterable by kind. | Research panel toolbar |
| Show or hide from AI | The eye icon on a card keeps an item out of AI context and search without deleting it. | Research card > eye icon |
| Open in its own app | Opens a PDF, text file or document in whichever program your computer uses for it. | **Double-click** the card |

### A.6 Story Analyst

Open it from `Sidebar > AI Tools > Story Analyst`, or press **Ctrl+K** and type "Story Analyst". It has seven tabs: Events & causality, Questions & promises, Known facts, Health report, What if…, Patterns, Evidence check. Run **Scenes** analysis on a chapter first (A.2); the Analyst reads scenes. Every result is labelled **Calculated** (worked out from your story data, identical on every run), **AI-judged** (produced by the AI, with the quotes it rests on) or **Calculated + AI-judged** (part of each).

| Function | What it does | How to access it |
|---|---|---|
| Analyse this chapter / whole manuscript / a range | Reads each scene for events, causes, who knows what, and reader questions. Incremental: unchanged scenes are skipped. Cancel keeps partial results. | Story Analyst > Analyse this chapter, Analyse whole manuscript, or More run options > choose chapters > Run for this range |
| Re-analyse everything | Ignores the saved results and re-reads every scene in scope. | Story Analyst > More run options > Re-analyse everything |
| Resume | Restarts an interrupted run with the same scope it began with (one chapter, a range, or all). | Banner at the top of Story Analyst after an interrupted run |
| Events list | Every extracted event by chapter, with actor, who chose it, irreversible, and its links. Edit, delete, add links, or jump to the passage. | Story Analyst > Events & causality > List |
| Causality graph | A node-and-arrow diagram of what causes what. Boxes are coloured by acting character, a red dot marks an irreversible event, click a box to highlight its arrows. | Story Analyst > Events & causality > Visual |
| Edit an event | Correct the description, the acting character, whether they chose it or it happened to them, and whether it is irreversible. Your correction is kept on re-runs. | Any event card > Edit |
| Add a link | Add a missing causal link by hand: this event causes, reveals, pays off, changes a relationship with, and so on, to another event, a character, a fact or a plot thread. Remove a wrong one with its ✕. | Any event card > Add a link |
| Evidence check | Lists every AI-made result whose quote is out of date, too thin, missing, or which a check said the quote does not fully show, with counts and a button to open each. Nothing is changed. | Story Analyst > Evidence check |
| Earlier readings | Keeps what the analyst made of a scene before it was read again. Look at it, keep single items as your own, put the whole reading back, or delete it. | Story Analyst > Events & causality > a chapter's Earlier readings |
| Background analysis | Keeps the Story Analyst current: a chapter whose text changed is cut into scenes, read, scored and summarised in the background when you have paused and are not using the model. Gives way to anything you ask the model for. | Off until you choose; asked by the installer and on first start. Auto-analyse switch beside Scene beat; Settings > AI model & connection > Keep the Story Analyst up to date as I write; status line at the top of Story Analyst and in the sidebar |
| Quote may not show this | A mark on an event, link, question, answer, who-knows-what row or scene function whose quote a second AI check said does not fully show it, with its reason. The result stays. | Any result card, and the scene cards in the Scenes panel |
| Scene function quotes | Each job a scene does opens the passage its quote came from. | Scenes panel > a scene card > a job |
| Story Analyst steps on the Fast model | Chooses whether the Fast model reads events (on by default) and who-knows-what with the links between events (off by default). Judging always uses the main model. | Settings > AI model & connection > Story Analyst: what the Fast model reads |
| Run a scene's passes together | Off until you choose. Reads five of a scene's seven Story Analyst passes at once instead of one after another; faster only when your model fits your video memory. | Settings > AI model & connection > Run a scene's Story Analyst passes together instead of one after another |
| Combine import's Bible extraction | Off until you choose. Reads locations, worldbuilding, relationships, facts and plot threads in one call per passage instead of five; a smaller or VRAM-tight model can thin out one of them. | Settings > AI model & connection > Combine locations, worldbuilding, relationships, facts and plot threads into one call when importing a manuscript |
| When a big Bible sends only what matters | How many facts (15), worldbuilding entries (10), characters (10) or locations (8) a call sends in full before scoping down to what the passage needs; 0 always scopes down. | Settings > AI model & connection > Bigger books: when to send only what matters |
| Earlier readings kept for each scene | How many earlier readings, of a scene or a chapter's summary and tension, are kept before the oldest are removed; 5 by default, 0 keeps every one. | Settings > AI model & connection > Earlier readings kept for each scene |
| Show in chapter | Closes the panels, opens the chapter and selects the passage a result rests on. If the text has changed since the analysis it says so, opens the nearest place it can find, and offers to analyse the chapter again. | The "Show in chapter" button on a result |
| Drag-to-resize | While any Visual view is open, a handle on the panel's left edge widens it. | Story Analyst > any Visual view > drag the left edge |
| Questions and promises | Every question or promise the text raises, with centrality and a status you set (open, partly answered, answered, left open on purpose, red herring, abandoned). | Story Analyst > Questions & promises |
| Chekhov's Gun object tracking | Off until you choose. A third kind in the ledger above: significant objects planted with apparent narrative weight, at or above a minimum significance you set. | Settings > AI model & connection > Track Chekhov's Gun objects |
| Suggest payoffs (AI) | Scans the manuscript for a real passage that pays off a tracked object, each candidate shown with its quote and chapter to mark as paid or dismiss. Nothing is ever marked automatically, and the server re-checks the passage is still really there before marking one. | Story Analyst > Questions & promises > Suggest payoffs (AI) |
| Known facts | Facts the story establishes and who holds which state of each: knows, suspects, conceals, or believes something false. | Story Analyst > Known facts |
| Information flow | Follows one fact through the book; as a list or as swim-lanes by character. | Known facts > Track flow > List or Visual |
| Health report | A structural-integrity score from five calculated checks (dead-weight scenes, long-open promises, flat momentum, neglected characters, chapters with no consequence), plus the AI's findings. Every finding quotes the text, can be dismissed, and can be shown in the chapter. Filter by Characters, Plot, Information, Craft, Meaning or Problems. | Story Analyst > Health report > Run health report (or Run options for a chapter range or a full re-judge) |
| Score history | The score of each finished run as a small trend line, with the change since the previous run and whether it covered the whole manuscript or a range. | Story Analyst > Health report, under the score |
| Health report visual | The score, a bar per check sized by its weight, issues by area, and a pass/flag/excluded bar. | Health report > Visual |
| What if… (Counterfactual Laboratory) | Choose a character and a chapter and describe a premise. QuillWork removes that character's actions from that chapter on, follows the consequences through your causality graph, shows what percentage of the story's other events would still occur, and narrates whether the plot would unravel, ripple or barely change. Never touches your manuscript. | Story Analyst > What if… > Explore |
| Narrative Debt | One number, with its breakdown, for everything the manuscript still owes the reader: overdue promises, dead-weight scenes and characters whose importance is fading. Built entirely from figures shown elsewhere on this screen; never a quality score. Every contributing item links to its passage. | Story Analyst > Patterns > Narrative Debt |
| Suspense architecture | Classifies each moment as dramatic irony, suspense, mystery (neither reader nor character knows yet) or revelation, per fact and character. | Story Analyst > Patterns > Suspense architecture (List or Visual) |
| Suspense markers on Pacing | Small triangles on the Pacing chart showing where irony, suspense, mystery and revelation land. | Sidebar > AI Tools > Pacing (appears automatically) |
| Domino test | Pick a chapter and see what would stop making sense if it were cut, as a real count: dependent events, facts no longer learned, scenes losing their motivation, questions left unanswered, foreshadowing setups losing their payoff, and relationship changes that would no longer occur. | Story Analyst > Patterns > Domino test > Run check |
| Reveal timing | How many chapters passed between the reader first suspecting a fact and it being confirmed. | Story Analyst > Patterns > Reveal timing |
| Dialogue fingerprint comparison | Compares every character's speech statistics side by side. | Story Analyst > Patterns > Dialogue fingerprint comparison |
| Result labels | Every analysis, check, score and suggestion is labelled Calculated, AI-judged or Calculated + AI-judged, with the reason on hover. A judged finding always comes with the quotes it rests on. Nothing is presented as a measure of how well the book is written. | Beside each result, in every language. |
| Character arc simulator | For a character with a written Arc, lays out their chain of choices and changes and shows whether a health run judged the arc earned, partly earned or not earned. | Story Analyst > Patterns > Character arc simulator |
| Who drives the plot (Character agency) | For every character: actions they initiated versus reacted to, irreversible decisions, and how many led to consequences. A bar chart in Visual view. | Story Analyst > Patterns > Who drives the plot |
| Did anyone become more reactive? | Pick a chapter and compare each character's share of self-initiated actions before it and from it onward. A drop of 25 percentage points or more is flagged. | Patterns > Who drives the plot > Did anyone become more reactive? > Compare |
| Narrative momentum | Counts what actually changes in each scene (goals, relationships, beliefs, reveals, stakes, options removed, irreversible events), per scene and per chapter, beside each chapter's tension. Flags "tense but little changes" and "quiet but a lot changes". | Story Analyst > Patterns > Narrative momentum (List or Visual) |
| Dead-weight scenes | Scenes where none of the events lead anywhere. Open the chapter from each one. | Story Analyst > Patterns > Dead-weight scenes |
| Facts the reader learns before the protagonist | Choose a protagonist; every fact the reader knows or strongly suspects before they do is listed with the size of the gap, the sign of a mystery solved too early. | Story Analyst > Patterns > Facts the reader learns before the protagonist |
| Motifs, symbols & themes | Track a recurring image, object or idea by typing the words to look for (several allowed, separated by commas). QuillWork finds every scene that mentions it, lists the passages, plots which chapters it appears in, and the Health report judges how it develops. Observational only: it never writes one into your prose. | Story Analyst > Patterns > Motifs, symbols & themes |
| Emotional echoes | Scenes chapters apart that share a character and read alike, with both passages shown. Needs an embedding model. | Story Analyst > Patterns > Emotional echoes > Find echoes |
| Parallel scenes | Scenes that are structurally very similar and not adjacent: intentional echo or accidental repetition? Needs an embedding model. | Story Analyst > Patterns > Parallel scenes > Find parallel scenes |
| Scene facts and functions | For each analysed scene: viewpoint character, place, story day, mood, a one-line summary, and the jobs the scene does (advances plot, reveals character, raises stakes, and so on). | Chapter header > Scenes, on each scene card |
| Overdue promises | Ranks open promises by how long and how central they are, and feeds Plot ideas. | Plot ideas > "pay off an overdue promise"; also a Health report check |

The Analyst never changes your manuscript, never invents characters (names it cannot match to your Bible are dropped), and only saves a finding if it can quote the exact sentence it came from.

### A.7 Import

| Function | What it does | How to access it |
|---|---|---|
| Bring in your writing | Asks **What are you bringing?** (a Word or ODT document, a text or Markdown file, a Scrivener project, an Obsidian vault, an Aeon Timeline file, or nothing yet), says in one line what each will and will not bring, and opens the right importer. | Sidebar > Bring in your writing; the first-run guide; the link at the top of Import manuscript; or Ctrl+K, "Bring in your writing" |
| Import manuscript | Brings in a whole .txt or .md manuscript (drop or paste) as a new project and builds a full Bible from it. A snapshot is taken first. Cancel can restore it. | Sidebar > Import manuscript; or Ctrl+K, "Import manuscript" |
| Scan pages (OCR) | Reads photographed or scanned pages and adds the text to the import box for review. Needs Tesseract. | Import manuscript > Or scan pages > Choose page images |
| Import from Aeon Timeline | Reads a native .aeon file directly, or a CSV export, into this book. | Sidebar > Import from other tools > Aeon Timeline |
| Import from Obsidian | Scans a vault folder and merges characters, locations, relationships and threads into this book. | Sidebar > Import from other tools > Obsidian |
| Import from Scrivener | Creates a new project from a .scriv folder, or links it so later changes sync in. | Sidebar > Import from other tools > Scrivener |
| Word/ODT sync | Links a single .docx or .odt file, read-only, and keeps chapters in step with it. QuillWork never writes to your file. | Sidebar > Import from other tools > Word/ODT sync |
| Cancel with rollback | Every import can be cancelled, keeping or discarding what was found. | Each import panel > Cancel |

### A.8 Export and submission

| Function | What it does | How to access it |
|---|---|---|
| Export novel | Word, PDF, EPUB, Markdown, plain text, Bible JSON or standard manuscript format, with progress. Word, PDF and EPUB keep your bold, italic, underline, strikethrough, colour and embedded images. If a default export folder is set, a copy is also saved there. | Top bar > Export; or Ctrl+K, "Export novel" |
| Trim size | Page size for Word and PDF: 6x9 in, 5.5x8.5, 5x8, A4, US Letter. | Export panel |
| Include options | Chapter text, the Bible, and Author's notes. | Export panel |
| Manuscript format | The Shunn-style agent and publisher submission layout for the full book, first 3 or 5 chapters, or a custom range. | Export panel > Manuscript |
| Preserve rich text (Markdown) | Keeps bold, italic, underline, strikethrough, colour and images in Markdown export as embedded HTML. | Export panel > Markdown |
| Synopsis generator | A one-page or two-page submission synopsis, ending included. | Sidebar > Submission > Synopsis generator |
| Query letter | A standard-structure query letter using your Book setup contact details. | Sidebar > Submission > Query letter |

### A.9 Projects, history and backup

| Function | What it does | How to access it |
|---|---|---|
| Projects | Create, open, refresh and delete novels. | Top bar > Projects; or Ctrl+K, "Projects" |
| Version history | Automatic snapshots at start-up and every 10 minutes, named snapshots you keep, Compare with the current novel, and Restore (which first takes a safety snapshot). | Sidebar > Version history; or Ctrl+K, "Save a version (snapshot)" |
| Cloud backup | Writes a dated backup into a folder you choose inside your own synced cloud drive, optionally on close, and optionally keeps a continuous copy. QuillWork uploads nothing itself. | Sidebar > Cloud backup; or Settings > More |
| Data folder | Moves where projects, snapshots and preferences are stored. | Settings > Data & storage |

### A.10 Audiobook narration (optional)

| Function | What it does | How to access it |
|---|---|---|
| Enable narration | Turns the whole audio feature on and reveals its settings. | Settings > Audiobook narration |
| Chatterbox server | Address, folder, start and stop for the separate Chatterbox program that produces the voice. | Settings > Audiobook narration |
| Narrate | Generates an MP3 per chapter for the full book, the first 3 chapters or your selection, then downloads a zip. Cancel keeps finished chapters. | Sidebar > Audio > Narrate (only when enabled) |
| Per-character voices | Gives a character their own predefined or cloned voice for their dialogue. | Characters > open a character > Narration voice |
| Narrator voice | The voice used for narration. | Sidebar > Bible > Book setup |

### A.11 Settings, AI connection and setup

| Function | What it does | How to access it |
|---|---|---|
| Licence | Shows your licence status and activates or replaces a key. Needs the internet when a key is first activated on an install; a key can move to a new install up to three times. | Settings > License |
| Check for updates | Asks the QuillWork server whether a newer version exists, then offers Update now or Decline. Sends only your licence key, version and platform. | Settings > Updates > Check for updates |
| Update now | Saves your open chapter, downloads and verifies the new version, replaces the program files (never your projects), restarts, and puts the old version back if the new one does not start. | The update window, after Check for updates or the start-up notice |
| Check for updates at start-up | Makes the same check a few seconds after QuillWork opens and shows a notice if a newer version exists. On by default. | Settings > Updates > Check for updates when QuillWork starts |
| Diagnostic capture | Off by default. Keeps a short rolling copy of QuillWork's own messages and saves a zip you can read and attach to a bug report. Nothing is sent anywhere. | Settings > Updates > Keep diagnostic information, Save diagnostic bundle |
| Quick AI setup | Optional guided setup. Opens Ollama's official download page, waits for Ollama to respond, recommends a model tier for your hardware, then downloads your writing, vision and fast models through Ollama, skipping any it already has. Cancel download stops it and keeps what was fetched; a full disk, a dropped connection, a missing model and the other failures each say what happened and what to do, and Set up now carries on from where it stopped. Skippable. | Settings > Quick AI setup; or the link in the first-run wizard's "Connect your AI model" step |
| Mature-writing option | Chooses an uncensored writing model instead of a safety-tuned one in Quick AI setup. Off by default. | Settings > Quick AI setup |
| Backend and model | Choose LM Studio or Ollama, the address, an optional API key and the model. Test the connection and read a plain-language diagnosis. | Settings > AI model & connection |
| Fast model | An optional smaller model for routine analytical work so the main model stays free for writing. | Settings > AI model & connection > Fast model |
| Fast model on a different server | Runs the Fast model in another program or on another computer, with its own address and API key and its own Test. Routine jobs go there and writing stays on the main server. | Settings > AI model & connection > Run the Fast model on a different server |
| Vision model | An optional model that describes uploaded images. | Settings > AI model & connection > Vision model |
| Hardware fit bars | Detects your GPU and RAM and shows how much of each your chosen models will use. | Settings > AI model & connection |
| Max tokens | Optional output-length limits for the main and fast models. | Settings > AI model & connection > Max tokens |
| Check continuity when I approve a Scene beat draft | After you approve a generated passage, runs a continuity check on just that passage in the background and shows the result in a small card. Off by default. | Settings > AI model & connection > Check continuity when I approve a Scene beat draft |
| Count reworked AI dialogue in voice fingerprints | By default a character's voice fingerprint counts only dialogue you wrote yourself. Turn this on to also count lines you started from an AI draft and then edited (lines approved unchanged are never counted). | Settings > AI model & connection > Count dialogue I reworked from AI drafts in voice fingerprints |
| OCR path | Where Tesseract is, if it isn't on your PATH. | Settings > OCR import |
| Interface language | English (UK or US), French, German or Spanish. | Settings > Language |

### A.12 Things that happen automatically

These run in the background without you asking. Each row says when it runs and where you can see it or switch it off. Where a row says there is no switch, it is because the behaviour only protects your work or keeps search accurate, and never changes your writing.

| Function | What it does and when | How to see it or stop it |
|---|---|---|
| Chapter autosave | Saves the open chapter about 30 seconds after you stop typing, when there is something unsaved, and whenever you switch chapters. | The **saved / saving / unsaved** label beside the project name. Switch it off with the **Autosave** switch in the top bar; **Ctrl+S** always saves. |
| Automatic snapshots | Snapshots the whole novel when you open it and about every 10 minutes while you work. An unchanged novel is not snapshotted twice. The newest 40 automatic snapshots are kept; named versions are kept forever. | Sidebar > Version history. No switch. |
| Background Bible extraction | Once a chapter has grown by about 150 words, and at most once every three minutes per chapter, quietly adds new characters, locations, relationships, facts and plot threads. Anything that would change an existing entry waits in Bible updates for your say-so. | Settings > AI model & connection > Auto-extract Bible info as I write (on by default). Stop AI lights up while a pass runs. |
| Search re-indexing | Re-embeds a chapter after a save only if its text changed, and re-embeds Bible entries, research items and scenes when they change, so search and Chat stay accurate. | Sidebar > Search index shows the status. No switch. |
| Linked Scrivener sync | Checks a linked Scrivener project every 30 seconds and merges in only the chapters that changed. A chapter removed in Scrivener is flagged, never deleted, and a chapter you edited in QuillWork is never overwritten by an older copy. | Sidebar > Import from other tools > Scrivener. **Unlink** stops it. |
| Linked Word or ODT sync | Checks a linked .docx or .odt file every 30 seconds and merges in changed chapters, matched by title. A chapter you edited in QuillWork is never overwritten by an older copy; one changed in both places keeps your version and is named in the sync message. | Sidebar > Import from other tools > Word/ODT sync. **Unlink** stops it. |
| Continuous backup | If ticked, writes a complete, consistent copy of the project database into your backup folder every 15 minutes by default. It is checked once a minute and acts only when your interval has passed. | Sidebar > Cloud backup (or Settings > More): **Keep a continuous copy**, **Check every (minutes)**. The last copy time is shown there. |
| Backup on close | If ticked and a backup folder is set, writes a fresh backup when you leave using the **Close** button. | Sidebar > Cloud backup: **Also back up automatically when I close QuillWork**. |
| Storage upgrade | Moves an older project to the newer storage format when you open it, taking a backup first. | Automatic, once per project. |
| Draft protection | Asks before anything replaces the editor while an unapproved Scene beat draft is showing. | Automatic. |
| Continuity check on approve | After you approve a Scene beat draft, runs a continuity check on just that passage and shows a small card that never blocks you. | Settings > AI model & connection > Check continuity when I approve a Scene beat draft (off by default). |
| AI busy watch | Every few seconds the app asks whether any AI work is running, so **Stop AI** greys out when nothing is and stays lit when something is, even a background pass. | **Stop AI**, bottom of the sidebar. |
| Interrupted analysis notice | If a Story Analyst run or health report was cut off (for example the app closed), opening the Story Analyst shows a banner offering to resume it. Resume works after a restart, and finished steps are not redone. | Sidebar > Story Analyst. |
| Local model set-up check | While the optional Quick AI setup waits for Ollama to start, it re-checks every few seconds and moves on by itself when Ollama answers. | Shown in the set-up window only. |
| Search index catch-up | When QuillWork starts, after you restore a version, and after a linked-file sync, it removes search text for chapters that no longer exist and re-indexes any chapter whose text has changed. It does nothing for a project whose search index was never built. | Sidebar > Search index shows the status. No switch. |
| Narration server check | At start-up, and only if audiobook narration is switched on, QuillWork checks whether the narration engine is ready. | Settings > Audiobook narration. |
| Update check | A few seconds after start-up, asks the QuillWork server whether a newer version exists and shows a notice if so. Sends only your licence key, version and platform. A failed check is silent. Nothing is downloaded until you choose Update now. | Settings > Updates > Check for updates when QuillWork starts (on by default). |
| Diagnostic capture | Only if you turn it on: keeps a rolling copy of QuillWork's own recent messages on your computer. Never sent anywhere. | Settings > Updates > Keep diagnostic information (off by default). |

### A.13 Keyboard shortcuts and gestures

| Function | What it does | How to access it |
|---|---|---|
| Command palette | Opens the searchable list of everything. | **Ctrl+K** |
| Save now | Saves the chapter and the project. | **Ctrl+S** |
| Close the frontmost window | Closes the palette, a dialog, an open edit window, and then (next press) the panel underneath. It never closes the chapter-import retry window, which needs an answer. | **Esc** |
| Bold, italic, underline, strikethrough | Formatting on the selection in the editor. | **Ctrl+B**, **Ctrl+I**, **Ctrl+U**, **Ctrl+Shift+X** |
| Generate a scene beat | Runs Scene beat from its brief box. | **Ctrl+Enter** |
| Append text | Adds the typed text to the end of the chapter; **Shift+Enter** makes a new line. | **Enter** in the append box |
| Send a chat message | Sends it; **Shift+Enter** makes a new line. | **Enter** in the Chat box |
| Add an author-intent rule | Adds the rule you typed. | **Enter** in the constraint box |
| Open a research file | Opens it in your computer's own app. | **Double-click** a PDF, text or document card |
| Resize a panel | Widens Story Analyst, Plot threads, Timeline or Knowledge tracker while in a Visual view; resizes the chapter note, Scenes panel and append box. | Drag the handle on the panel's edge |
| Pull down Research | Opens and sizes the Research Workspace. | Click or drag the **Research** tab |
| Select a graph element | Highlights and details a causality-graph event, a suspense dot, a domino node or an arc dot. | Click it |
| Open a chapter from Pacing | Opens that chapter. | Click a dot on the Pacing chart |
| Upload or import by drag | Uploads research files; loads a .txt or .md into the import box. | Drag onto the Research panel or the import drop zone |

On a Mac, **Cmd** works wherever **Ctrl** is shown. There are no right-click menus.

---

*This manual is updated alongside every feature change to QuillWork.*
