# MaidOwn Style Guide

Source of truth for all landing page styling. All CSS tokens are defined in `styles.css`.
Design assets live in `assets/`. Full brand spec: `G:\My Drive\SoftwareBusinesses\MaidOwn\designDocs\maidown-brand-spec.md`

---

## Colors

Always use CSS custom properties — never hardcode hex values.

### Mint scale (primary brand color)
| Token            | Hex           | Use                                                      |
|------------------|---------------|----------------------------------------------------------|
| `--mint-50`      | `#E8F7F1`     | Pill backgrounds, hover surfaces, guarantee banners      |
| `--mint-200`     | `#BCE8D7`     | Pill/banner borders, decorative accents                  |
| `--mint-400`     | `#6FCFAB`     | Info graphics only                                       |
| **`--mint-600`** | **`#0EA381`** | **Primary buttons, links, step numbers, active accents** |
| `--mint-800`     | `#0A6B53`     | Button hover state, text on mint-50 surfaces             |
| `--mint-900`     | `#04342C`     | Deep contrast (rarely used)                              |

### Neutrals
| Token                      | Hex       | Use                                   |
|----------------------------|-----------|---------------------------------------|
| `--neutral-page`           | `#FAFBFA` | Page/body background                  |
| `--neutral-surface`        | `#FFFFFF` | Cards, nav, footer, modals            |
| `--neutral-border-soft`    | `#EEF1EE` | Table row dividers                    |
| `--neutral-border`         | `#E8EBE9` | Card borders, nav/footer borders      |
| `--neutral-border-strong`  | `#D5DAD7` | Form inputs, secondary button borders |
| `--neutral-text-secondary` | `#4B5651` | Body copy, helper text, muted labels  |
| `--neutral-text-primary`   | `#0F1A17` | Headings, primary data, nav items     |

### Semantic (status only — use nowhere else)
| Token               | Hex       | Use                    |
|---------------------|-----------|------------------------|
| `--status-paid`     | `#0EA381` | Paid/success states    |
| `--status-due-soon` | `#D97706` | Warning/pending states |
| `--status-overdue`  | `#DC2626` | Error/overdue states   |
| `--status-draft`    | `#6B7280` | Inactive/draft states  |

### NEVER use
- `#2563EB` (developer-default blue) — replaced entirely by mint
- `#15803D` or `#16A34A` (generic green) — use mint scale
- Any color not listed above (no fifth color for "info")

---

## Typography

### Fonts (loaded via Google Fonts on every page)
- **Headings:** `'Geist'` (fallback: `'Inter'`)
- **Body:** `'Inter'`
- Use `var(--font-heading)` and `var(--font-body)` — never raw font names inline

### Weights
**Only 400, 500, and 600.** No 700, 800, or italic. Hierarchy comes from size and color.
- 400 = regular body text
- 500 = emphasized labels, button text, sub-headings
- 600 = headings, price numbers, step numbers

### Scale
| Element       | Size                               | Weight | Letter-spacing  | Line-height |
|---------------|------------------------------------|--------|-----------------|-------------|
| `h1` (hero)   | `clamp(1.875rem, 5vw, 2.75rem)`    | 600    | -0.8px          | 1.15        |
| `h2`          | `clamp(1.375rem, 3.5vw, 1.875rem)` | 600    | -0.4px          | 1.2         |
| `h3`          | 1rem                               | 500    | -0.2px          | 1.4         |
| Body          | 15px                               | 400    | 0               | 1.55        |
| Small/caption | 0.875rem                           | 400    | 0               | 1.4         |
| Eyebrow label | 11px                               | 500    | 1px (uppercase) | 1.2         |
| Price/stat    | 2.25–2.5rem                        | 600    | -0.8px          | 1           |

Price numbers: always add `font-variant-numeric: tabular-nums`.

---

## Logo

### Files in `assets/`
| File                     | Use                                               |
|--------------------------|---------------------------------------------------|
| `maidown-horizontal.svg` | Nav bar on all pages (`height: 28px`)             |
| `maidown-stacked.svg`    | Login screen, splash pages, print                 |
| `maidown-icon.svg`       | Favicons, social avatars (handled by favicon set) |

### Favicon set (already in `<head>` on all pages)
```html
<link rel="icon" href="assets/favicon.ico" sizes="any">
<link rel="icon" type="image/svg+xml" href="assets/favicon.svg">
<link rel="apple-touch-icon" href="assets/apple-touch-icon.png">
<link rel="manifest" href="manifest.webmanifest">
```

### Logo rules
- Never recolor — mint is mint
- Never add shadows, gradients, or outlines
- Never distort — scale uniformly only
- Never place on green/teal backgrounds
- Never use text "MaidOwn" as a nav logo — always use the SVG image

---

## Components

### Buttons

**Primary** (one per page max):
```css
background: var(--mint-600);
color: #fff;
border-radius: var(--radius-md); /* 8px */
height: 40px (default) / 48px (lg);
padding: 0 18px (default) / 0 24px (lg);
font-weight: 500;
```
Hover: `background: var(--mint-800)`

**Secondary**:
```css
background: var(--neutral-surface);
color: var(--neutral-text-primary);
border: 0.5px solid var(--neutral-border-strong);
border-radius: var(--radius-md);
```
Hover: `border-color: var(--mint-600)`

**Tertiary** (inline/text link):
```css
color: var(--mint-800);
background: transparent;
border: none;
```

**Destructive**:
```css
background: #FEF2F2;
color: #B91C1C;
border: 0.5px solid #FECACA;
```

Use shared `.btn`, `.btn-primary`, `.btn-secondary`, `.btn-lg` classes from `styles.css`.

### Cards
```css
background: var(--neutral-surface);
border: 0.5px solid var(--neutral-border);
border-radius: var(--radius-lg); /* 12px */
padding: 1.5rem–2rem;
/* NO box-shadow — borders are the elevation system */
```

Featured/highlighted card: increase border to `1px solid var(--mint-600)`.

### Status Pills
```css
background: var(--mint-50);
color: var(--mint-800);
font-size: 11px;
font-weight: 500;
padding: 3px 8px;
border-radius: 999px;
```
Use `.pill` class from `styles.css`. Never use solid status colors as backgrounds.

### Section Eyebrow Labels
```css
font-size: 11px;
font-weight: 500;
text-transform: uppercase;
letter-spacing: 1px;
color: var(--mint-600);
```
Use `.section-label` class from `styles.css`.

### Nav
- White background (`--neutral-surface`)
- `0.5px solid var(--neutral-border)` bottom border
- Logo: `<img src="assets/maidown-horizontal.svg" height="28">`
- Right side: either `.nav-cta` (mint) or `.nav-link` (secondary text)

---

## Spacing & Radii

| Token         | Value | Use                                  |
|---------------|-------|--------------------------------------|
| `--radius-sm` | 6px   | Small badges                         |
| `--radius-md` | 8px   | Buttons, form inputs, small cards    |
| `--radius-lg` | 12px  | Feature cards, pricing cards, tables |

Section padding: `5rem 0` (desktop), `3.5rem 0` (mobile ≤600px).

---

## Shared CSS File

`styles.css` defines all tokens and base component styles. Every page must link it:
```html
<link rel="stylesheet" href="styles.css">
```
Page-specific styles go in a `<style>` block in the `<head>` of each HTML file.

---

## Don'ts

1. No `#2563EB` (blue) anywhere
2. No `box-shadow` on any component — use borders
3. No font weights 700 or 800
4. No `font-family` set inline — use `var(--font-heading)` or `var(--font-body)`
5. No hardcoded hex values — always use CSS custom properties
6. No text "MaidOwn" as nav logo — use `assets/maidown-horizontal.svg`
7. No serif fonts
8. No exclamation marks in UI text (headings, labels)
9. No stock-photo language in copy
10. No `font-style: italic`
