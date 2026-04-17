---
name: text-wireframe
description: >
  Create text-based wireframes and UI mockups using ASCII/Unicode box-drawing characters.
  Use this skill whenever the user wants to plan, sketch, or document a UI layout in text form —
  even if they don't say "wireframe" explicitly. Trigger on phrases like: "wireframe", "mockup",
  "ASCII UI", "text-based layout", "lo-fi sketch", "plan this UI", "show me the layout",
  "draw this component", "how should this screen look", or when a user shares a UI image
  and asks to replicate or extend it as text. Also trigger when the user pastes a rough
  text-based layout and wants it cleaned up or refined. Default to box-drawing style unless
  the user requests plain ASCII.
---

# Text Wireframe Skill

Produce clean, readable text-based wireframes using Unicode box-drawing characters and
consistent annotation conventions. The goal is a wireframe that reads like documentation
and communicates layout at a glance.

---

## Core Style: Box-Drawing

Use Unicode box-drawing characters by default:

```
┌─────────────── TITLE ───────────────┐
│ Content here                        │
│                                     │
│ [ Button label → ]                  │
└─────────────────────────────────────┘
```

**Character reference:**
| Element         | Chars            |
|----------------|-----------------|
| Box corners     | `┌ ┐ └ ┘`        |
| Box edges       | `─` (horiz) `│` (vert) |
| Section divider | `├───────────────┤` |
| Centered title in border | `┌─── LABEL ───┐` |
| Double box (modal/focus) | `╔═══════╗ ║ ║ ╚═══════╝` |

---

## Layout Primitives

### Grid Layout

Use bracketed row labels and side-by-side boxes separated by spaces (3 spaces = gap):

```
[ ROW 1 ]

┌─────────── LEFT ───────────┐   ┌─────────── RIGHT ──────────┐
│ Content A                  │   │ Content B                  │
└────────────────────────────┘   └────────────────────────────┘

[ ROW 2 ]

┌────────────────── FULL WIDTH ──────────────────┐
│ Content C                                      │
└────────────────────────────────────────────────┘
```

### State Annotations

Use `STATE N — DESCRIPTION` headers to show multiple states:

```
STATE 0 — DEFAULT (ALL COLLAPSED)
─────────────────────────────────

STATE 1 — CARD EXPANDED
─────────────────────────
```

### Interactive Element Notation

| UI Element        | Notation                              |
|------------------|---------------------------------------|
| Button (primary)  | `[ Label → ]`                         |
| Button (secondary)| `[ Label ]`                           |
| Dropdown          | `[ ▼ Label ]`                         |
| Toggle (off/on)   | `[ ○ OFF ]` / `[ ● ON ]`              |
| Input field       | `[ _________________ ]`               |
| Checkbox          | `[ ] Label` / `[✓] Label`             |
| Link              | `~ Label ~`                           |
| Active/selected   | `> Item <`                            |
| Badge/tag         | `(label)`                             |
| Avatar            | `[👤]` or `[ AV ]`                    |
| Icon              | Use emoji or `[icon-name]`            |

### Content Placeholders

| Content type      | Notation                              |
|------------------|---------------------------------------|
| Body text         | `Lorem ipsum...` or `[ text block ]`  |
| Image             | `[ 🖼 Image caption ]`                |
| Gradient/fade     | `(gradient fade ↓)`                   |
| Hidden content    | `+ N more items`                      |
| Loading state     | `[ ░░░░░░░░ loading ]`                |
| Empty state       | `~ nothing here yet ~`                |

---

## Annotation Layer

Add annotations outside the boxes using `←`, `→`, `↑`, `↓` arrows or side comments:

```
┌────── CARD ──────┐
│ Title            │ ← clickable, opens modal
│ [ Action → ]     │ ← primary CTA
└──────────────────┘
     ↑
     anchored to top of viewport
```

For state transitions:
```
[ ▼ Lihat semua ]  →  on click  →  expands card height, shows full list
```

---

## Scale and Alignment Rules

1. **Consistent column widths** — when two boxes are side by side, keep their widths proportional to their intended screen size. Equal columns = same width.
2. **Label centering** — center section titles inside the top border: `┌──── TITLE ────┐`
3. **Inner padding** — always leave 1 space of padding inside boxes: `│ content  │`
4. **Alignment** — align content to the left inside boxes unless it's a centered/hero element
5. **Spacing between columns** — use 3 spaces as the gap between side-by-side columns

---

## Full Example: Card Grid

```
STATE 0 — DEFAULT (ALL COLLAPSED)
──────────────────────────────────


[ ROW 1 ]

┌────────────── IT ──────────────┐   ┌──────────────── IPA ───────────────┐
│ Programming, AI, Data Science  │   │ Biologi, Fisika, Kimia             │
│                                │   │                                    │
│ (gradient fade ↓)              │   │ (gradient fade ↓)                  │
│ + 6 sub-bidang lainnya         │   │ + 4 sub-bidang lainnya             │
│ [ ▼ Lihat semua ]              │   │ [ ▼ Lihat semua ]                  │
│ [ Masuk IT → ]                 │   │ [ Masuk IPA → ]                    │
└────────────────────────────────┘   └────────────────────────────────────┘


[ ROW 2 ]

┌────────────── DESAIN ──────────────┐   ┌──────────────── BISNIS ────────────┐
│ UI/UX, Visual Design, Photo        │   │ Ekonomi, Manajemen, Investasi      │
│                                    │   │                                    │
│ (gradient fade ↓)                  │   │ (gradient fade ↓)                  │
│ + 3 sub-bidang lainnya             │   │ + 2 sub-bidang lainnya             │
│ [ ▼ Lihat semua ]                  │   │ [ ▼ Lihat semua ]                  │
│ [ Masuk Desain → ] │               │   │ [ Masuk Bisnis → ]                 │
└────────────────────────────────────┘   └────────────────────────────────────┘


[ ROW 3 ]

┌──────────────────────────── BAHASA ────────────────────────────────────────┐
│ Bahasa Indonesia, English, Mandarin                                        │
│                                                                            │
│ (gradient fade ↓)                                                          │
│ + 6 sub-bidang lainnya                                                     │
│ [ ▼ Lihat semua ]                                                          │
│ [ Masuk Bahasa → ]                                                         │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## Workflow

1. **Understand the UI** — ask clarifying questions if the layout is ambiguous. What are the columns? What are the interactive states?
2. **Pick a state to start** — usually STATE 0 (default/collapsed). Add more states only if needed.
3. **Sketch the grid** — row by row, place boxes proportionally.
4. **Fill in content** — use placeholders for unknown copy, real content where provided.
5. **Add annotations** — note interactions, behaviors, or open questions.
6. **Offer to generate code** — only if the user asks: "Want me to turn this into HTML/React?"

---

## Output Format

Always wrap the wireframe in a code block with no language tag (or `text`):

````
```
[wireframe here]
```
````

This ensures monospace rendering in all interfaces.

---

## Wikilink Support

When the user uses `[[double bracket]]` syntax or mentions "wikilink", treat it as an **Obsidian-style internal link** and preserve the `[[]]` format consistently in all wireframe output. Never convert to markdown links `[text](url)` or plain text.

Use wikilinks inside wireframes to reference other pages/screens:

| Context              | Notation                                  |
|---------------------|-------------------------------------------|
| Nav link to a page   | `~ [[Page Name]] ~`                       |
| Button navigating    | `[ Go to [[Dashboard]] → ]`               |
| Breadcrumb           | `[[Home]] > [[Category]] > Current`       |
| Card linking out     | `│ → [[Detail Page]]  │`                  |
| Annotation reference | `← see [[ComponentName]] for full spec`   |

Example:
```
┌────────── NAV ──────────────────────────────┐
│ ~ [[Home]] ~  ~ [[Explore]] ~  ~ [[Profile]] ~ │
└─────────────────────────────────────────────┘

┌────────── CARD ──────────┐
│ IT — [[IT Overview]]     │ ← links to detail page
│ [ Masuk IT → ]           │
└──────────────────────────┘
```

**Rule:** If the user's prompt contains `[[...]]`, mirror that convention throughout the entire wireframe output without altering the bracket format.

---

## Tips

- When converting an image to text wireframe: analyze the visual hierarchy first, then map each region to a box. Don't try to be pixel-perfect — capture structure and interactions.
- For mobile layouts, use a single narrow column (~40 chars wide).
- For responsive notes, add: `// mobile: stack vertically` as a comment below the layout.
- Keep it scannable — a wireframe that needs explanation has failed.