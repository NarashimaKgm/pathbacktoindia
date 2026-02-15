# Naga

Static website documenting learnings from a US-to-India transition. Plain HTML + CSS, no build tools, no dependencies.

## Tech Stack

- HTML5 + CSS3 (no frameworks, no JavaScript libraries)
- Google Fonts (Inter: 400, 500, 600, 700) loaded via CDN
- Minimal inline `<script>` on every page for mobile nav toggle — no external JS
- Open `index.html` directly in a browser to preview — no server needed

## File Structure

```
pathbacktoindia/
├── index.html              Landing page — hero + vertical timeline with 3 phases
├── before.html             Phase page — card grid for "Before the Move" (3 cards)
├── during.html             Phase page — card grid for "During the Transition" (3 cards)
├── after.html              Phase page — card grid for "After Settling In" (3 cards)
├── topic-template.html     Reusable template for individual topic pages
├── css/
│   └── style.css           Single shared stylesheet (all design tokens + components)
└── assets/
    └── icons/              SVG icons (currently empty — all icons are inline SVG)
```

### Current content status

Phase pages link to topic pages that **do not exist yet**. These are the planned topic pages:

| Phase    | Card title            | Expected file             |
|----------|-----------------------|---------------------------|
| Before   | Visa & Paperwork      | `before-visa.html`        |
| Before   | Finances & Banking    | `before-finances.html`    |
| Before   | Housing & Lease       | `before-housing.html`     |
| During   | Shipping & Logistics  | `during-shipping.html`    |
| During   | Travel Planning       | `during-travel.html`      |
| During   | Temporary Housing     | `during-housing.html`     |
| After    | Banking & Finances    | `after-banking.html`      |
| After    | Healthcare            | `after-healthcare.html`   |
| After    | Career & Work         | `after-career.html`       |

## Design System

All design tokens live in `css/style.css` under `:root`.

### Colors

| Token               | Value     | Usage                           |
|----------------------|-----------|---------------------------------|
| `--color-bg`         | `#FFFFFF` | Page background                 |
| `--color-surface`    | `#F7F8FA` | Hero section, card icon bg      |
| `--color-primary`    | `#1B2A4A` | Navy — headings, nav, links     |
| `--color-accent`     | `#D4A373` | Gold — hover accents, markers   |
| `--color-text`       | `#2D3436` | Body text                       |
| `--color-muted`      | `#636E72` | Secondary/meta text             |
| `--color-border`     | `#E0E0E0` | Borders and dividers            |
| `--color-tip`        | `#D4A373` | Tip callout border (gold)       |
| `--color-warning`    | `#E17055` | Warning callout border (red)    |
| `--color-note`       | `#74B9FF` | Note callout border (blue)      |

### Typography

| Token              | Value      |
|--------------------|------------|
| `--font-size-sm`   | `0.875rem` |
| `--font-size-base` | `1rem`     |
| `--font-size-lg`   | `1.15rem`  |
| `--font-size-xl`   | `1.75rem`  |
| `--font-size-2xl`  | `2.25rem`  |
| `--font-size-3xl`  | `3rem`     |

### Other tokens

| Token           | Value                              |
|-----------------|------------------------------------|
| `--radius`      | `12px`                             |
| `--shadow-sm`   | `0 1px 3px rgba(0,0,0,0.06)`      |
| `--shadow-md`   | `0 4px 12px rgba(0,0,0,0.08)`     |
| `--shadow-lg`   | `0 8px 24px rgba(0,0,0,0.12)`     |
| `--transition`  | `0.25s ease`                       |

## CSS Components

| Class                   | Used on            | Purpose                            |
|-------------------------|--------------------|------------------------------------|
| `.nav`                  | All pages          | Sticky top navbar (64px height)    |
| `.nav__brand`           | All pages          | Logo/home link (currently empty)   |
| `.nav__links`           | All pages          | Horizontal nav items               |
| `.nav__hamburger`       | All pages          | Mobile menu toggle (hidden >768px) |
| `.hero`                 | `index.html`       | Landing hero section               |
| `.timeline`             | `index.html`       | Vertical timeline container        |
| `.timeline__item`       | `index.html`       | Single timeline entry              |
| `.timeline__marker`     | `index.html`       | Circle dot on timeline line        |
| `.breadcrumb`           | Phase/topic pages  | Navigation breadcrumb              |
| `.phase-header`         | Phase pages        | Phase title + description          |
| `.card-grid`            | Phase pages        | Responsive 3→2→1 column grid      |
| `.card`                 | Phase pages        | Topic card with hover lift         |
| `.card__link`           | Phase pages        | Wrapping `<a>` around card         |
| `.article`              | Topic pages        | Content container (max-width 720px)|
| `.callout`              | Topic pages        | Styled info box (tip/warning/note) |
| `.back-link`            | Topic pages        | "Back to phase" link at bottom     |
| `.footer`               | All pages          | Centered footer text               |

## Adding Content

### New topic card on a phase page

In `before.html`, `during.html`, or `after.html`, find the `<!-- ADD MORE CARDS BELOW -->` comment and copy the card template provided there. Update `href`, icon SVG, title, and description.

### New topic page

1. Copy `topic-template.html` and rename using the convention: `{phase}-{topic}.html` (e.g., `before-visa.html`, `after-banking.html`)
2. Search for `<!-- EDIT -->` comments in the copied file — they mark every spot you need to update (title, breadcrumb, nav active state, back link)
3. Write content between `YOUR CONTENT STARTS HERE` and `YOUR CONTENT ENDS HERE`

### Available content blocks in topic pages

- `<h2>` / `<h3>` — section headings
- `<p>`, `<ul>`, `<ol>` — body content
- `.callout.callout--tip` — gold tip box (title color: `#B8860B`)
- `.callout.callout--warning` — red warning box (title color: `#C0392B`)
- `.callout.callout--note` — blue info box (title color: `#2E86C1`)

## Conventions

- BEM-style CSS class naming: `.block__element--modifier`
- Inline SVG icons (Feather icon style — stroke-based, 24x24 viewBox)
- All pages share the same nav, footer, and mobile hamburger toggle script (inline `<script>` at bottom of `<body>`)
- Responsive breakpoints: 1024px (3→2 cols), 768px (2→1 col + hamburger nav)
- Nav active state: add `class="active"` to the current phase's `<a>` in `.nav__links`
- File naming: `{phase}-{topic}.html` for topic pages
- The `.nav__brand` text is currently empty on all pages
