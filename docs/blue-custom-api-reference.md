# Blue Custom Theme — Full API Reference

> JavaDoc-style reference for every CSS variable, custom class, and Bulma component class
> used in the Blue Custom / Material 3 theme system.
>
> **File:** `scss/_overrides-material-3-blue-custom.scss`
> **Compiled output:** `css/material-3-blue-custom.css`
> **Build:** `npm run build:themes`

---

## How to read this document

Each entry follows this format:

```
Name        — The variable name or class selector
Type        — CSS Variable | Custom Class | Bulma Class | Bulma Modifier
Defined in  — Which file sets/overrides this
Description — Plain-English explanation of what it is
Usage       — How to apply it in HTML or CSS
Notes       — Edge cases, dependencies, or important gotchas
```

---

# Part 1 — CSS Custom Properties (Design Tokens)

Custom properties (CSS variables) are declared in the `:root` block and are available on every element in the page.

---

## Motion Tokens

---

### `--m3-easing-standard`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `cubic-bezier(0.2, 0, 0, 1)` |

**Description**
The default Material 3 "standard" easing curve. Use this for most UI transitions such as hover effects, state changes, and color fades. It starts quickly and decelerates smoothly — the most common motion feel in M3.

**Usage**

```css
transition: background-color var(--m3-duration-short) var(--m3-easing-standard);
```

---

### `--m3-easing-decelerate`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `cubic-bezier(0, 0, 0, 1)` |

**Description**
Used for elements that enter the screen from off-screen (e.g. a drawer sliding in, a dialog appearing). Decelerates very fast — the item arrives and settles immediately.

**Usage**

```css
transition: transform var(--m3-duration-medium) var(--m3-easing-decelerate);
```

---

### `--m3-easing-accelerate`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `cubic-bezier(0.3, 0, 1, 1)` |

**Description**
Used for elements that exit the screen (e.g. a panel sliding out, an item being dismissed). Starts slow and accelerates — the item leaves decisively.

**Usage**

```css
transition: transform var(--m3-duration-medium) var(--m3-easing-accelerate);
```

---

### `--m3-duration-short`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `200ms` |

**Description**
Short transition duration. Used for hover effects, focus rings, and state-layer opacity changes. Feels instant but still smooth.

**Usage**

```css
transition: color var(--m3-duration-short) var(--m3-easing-standard);
```

---

### `--m3-duration-medium`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `300ms` |

**Description**
Medium duration. Suitable for expanding/collapsing elements, tabs switching, tooltips appearing. Noticeable but not slow.

**Usage**

```css
transition: max-height var(--m3-duration-medium) var(--m3-easing-standard);
```

---

### `--m3-duration-long`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `500ms` |

**Description**
Long duration. Used for large, dramatic transitions — full screen dialogs, page-level entering elements. Avoid overusing; it should feel deliberate.

**Usage**

```css
transition: opacity var(--m3-duration-long) var(--m3-easing-decelerate);
```

---

## Brand / Color Tokens

---

### `--m3c-primary-hsl`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `212, 91%, 40%` |

**Description**
The main brand blue color expressed as a bare HSL triplet (no `hsl()` wrapper). This is intentional — it lets you combine it with different alpha values and `hsl()` / `hsla()` as needed. This is the single source of truth for your brand color.

**Usage**

```css
/* Solid brand color */
background: hsl(var(--m3c-primary-hsl));

/* Brand with transparency (8% alpha tint) */
background: hsla(var(--m3c-primary-hsl), 0.08);
```

**Notes**
To change your brand color globally, edit only this token value. The rest of the theme will follow. Corresponds to Bulma's `$primary` in `material-3-blue-custom.scss`.

---

### `--m3c-container-hsl`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `210, 72%, 84%` |

**Description**
The "Primary Container" surface color from the Material 3 tonal palette. This is a soft, high-lightness version of the brand blue. Used as the background for hero sections, active menu items, panel headings, and selected chips/tags.

**Usage**

```css
background: hsl(var(--m3c-container-hsl));
```

---

### `--m3c-on-container-hsl`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `214, 100%, 16%` |

**Description**
The text/icon color to use when placed on top of a `--m3c-container-hsl` surface. Very dark blue that passes contrast requirements against the light container background.

**Usage**

```css
color: hsl(var(--m3c-on-container-hsl));
```

**Notes**
Always use this alongside `--m3c-container-hsl`. Using arbitrary text colors on container surfaces breaks contrast requirements.

---

### `--m3c-navbar-hsl`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `213, 70%, 18%` |

**Description**
The background color of the top navigation bar. Dark navy — much darker than the brand blue. Chosen to create strong contrast for white navbar text and to give the app a professional, enterprise feel.

**Usage**

```css
background: hsl(var(--m3c-navbar-hsl));
```

**Notes**
Used internally by the `.navbar` override. You rarely need to consume this directly unless building a custom header component.

---

### `--m3c-on-navbar-hsl`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `210, 60%, 94%` |

**Description**
The near-white color used for text and icons placed on the dark navbar background. Slightly cool-tinted white, matching the blue brand hue.

**Usage**

```css
color: hsl(var(--m3c-on-navbar-hsl));
```

---

### `--m3c-glass-alpha`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `0.92` |

**Description**
The default opacity value for glass / translucent surfaces. Use with a background color to create a frosted-glass effect. Typically used with `backdrop-filter`.

**Usage**

```css
background: hsla(var(--m3c-navbar-hsl), var(--m3c-glass-alpha));
backdrop-filter: blur(10px);
```

---

## Tonal Elevation Tokens

---

### `--m3-primary-hsl`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | Aliased to `var(--m3c-primary-hsl)` |

**Description**
An internal alias that points to `--m3c-primary-hsl`. Used by the surface tint tokens and dark mode overrides. Allows dark mode to swap the primary hue independently without touching the brand root token.

**Notes**
Prefer `--m3c-primary-hsl` for new code. This token exists for internal use by the surface tint system.

---

### `--m3-surface-tint-1`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `hsla(var(--m3-primary-hsl), 0.05)` — 5% opacity blue |

**Description**
A very faint primary-colored tint applied as an overlay on top of neutral card/surface backgrounds. Simulates M3's "elevation level 1" tonal surface behavior — higher elevation = more primary color blended in.

**Usage**

Apply as a `background-image` (not `background-color`) so it overlays without replacing the base color:

```css
background-image: linear-gradient(var(--m3-surface-tint-1), var(--m3-surface-tint-1));
```

---

### `--m3-surface-tint-2`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `hsla(var(--m3-primary-hsl), 0.08)` — 8% opacity blue |

**Description**
Elevation level 2 tint. Slightly more visible than level 1. Used on card hover states and elevated panels.

**Usage**

```css
background-image: linear-gradient(var(--m3-surface-tint-2), var(--m3-surface-tint-2));
```

---

### `--m3-surface-tint-3`

| Field | Value |
|---|---|
| Type | CSS Variable |
| Defined in | `_overrides-material-3-blue-custom.scss` → `:root` |
| Default | `hsla(var(--m3-primary-hsl), 0.11)` — 11% opacity blue |

**Description**
Elevation level 3 tint. The most visible tint — use for highly elevated surfaces like modals, dropdowns, or popover menus.

**Usage**

```css
background-image: linear-gradient(var(--m3-surface-tint-3), var(--m3-surface-tint-3));
```

---

## Bulma-Provided Tokens (Consumed by Theme)

These variables are generated by Bulma and used throughout the override file. You do not set them directly — Bulma calculates them from your SCSS configuration.

---

### `--bulma-primary`

| Field | Value |
|---|---|
| Type | CSS Variable (Bulma-generated) |
| Defined in | `scss/material-3-blue-custom.scss` via `$primary: hsl(212, 91%, 40%)` |

**Description**
The primary brand color as a full `hsl(...)` CSS value. Use this when you want the solid brand blue on text, borders, or icon fills.

**Usage**

```css
color: var(--bulma-primary);
border-color: var(--bulma-primary);
```

---

### `--bulma-radius` / `--bulma-radius-medium` / `--bulma-radius-large`

| Field | Value |
|---|---|
| Type | CSS Variable (Bulma-generated) |
| Defined in | `scss/material-3-blue-custom.scss` |
| Values | `0.375rem` / `0.5rem` / `0.75rem` |

**Description**
The theme's border-radius scale. Use consistently across custom elements to match the M3 shape system.

**Usage**

```css
border-radius: var(--bulma-radius);
border-radius: var(--bulma-radius-medium);
```

---

### `--bulma-border` / `--bulma-border-weak`

| Field | Value |
|---|---|
| Type | CSS Variable (Bulma-generated) |

**Description**
`--bulma-border` is the standard border color. `--bulma-border-weak` is a softer, less visible version. Use for card edges, dividers, and input borders.

**Usage**

```css
border: 1px solid var(--bulma-border);
border-bottom: 1px solid var(--bulma-border-weak);
```

---

### `--bulma-text` / `--bulma-text-weak` / `--bulma-text-strong`

| Field | Value |
|---|---|
| Type | CSS Variable (Bulma-generated) |

**Description**
A three-tier text color system. `--bulma-text` is the default body text. `--bulma-text-weak` is muted/secondary text (labels, placeholders). `--bulma-text-strong` is bold/emphasized text (headings).

**Usage**

```css
color: var(--bulma-text-weak);   /* caption, subtitle */
color: var(--bulma-text-strong); /* heading, key value */
```

---

### `--bulma-scheme-main` / `--bulma-scheme-main-bis`

| Field | Value |
|---|---|
| Type | CSS Variable (Bulma-generated) |

**Description**
Page/surface background colors. `--bulma-scheme-main` is the primary background (the page canvas). `--bulma-scheme-main-bis` is a very slightly darker variant — used for table header backgrounds, sidebar tints, and alternating rows.

**Usage**

```css
background-color: var(--bulma-scheme-main);
background-color: var(--bulma-scheme-main-bis); /* slightly tinted */
```

---

### `--bulma-duration` / `--bulma-easing`

| Field | Value |
|---|---|
| Type | CSS Variable (Bulma-generated) |
| Defined in | `scss/material-3-blue-custom.scss` via `$duration: 200ms`, `$speed: 100ms` |

**Description**
Bulma's own transition timing values. Used in some Bulma-native component transitions. For M3-specific transitions, prefer `--m3-duration-*` and `--m3-easing-*` instead.

---

### `--bulma-family-code`

| Field | Value |
|---|---|
| Type | CSS Variable (Bulma-generated) |

**Description**
The monospace font family stack. Used by `.has-text-mono`, `code`, and `pre` elements.

**Usage**

```css
font-family: var(--bulma-family-code);
```

---

---

# Part 2 — Custom Classes

Classes defined in `_overrides-material-3-blue-custom.scss` that are not native Bulma classes.

---

## Utility Classes

---

### `.has-text-tabular`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
Forces numeric characters to use tabular (fixed-width) number rendering. Without this, proportional fonts render digits at varying widths — numbers won't align vertically in columns. Essential for metrics, dashboards, financial data, and tables.

**Usage**

```html
<p class="has-text-tabular">$1,234,567.00</p>
<td class="has-text-tabular">99.8%</td>
```

---

### `.has-text-mono`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
Switches the element to the monospace font family (Google Sans Mono → Roboto Mono → Consolas fallbacks). Use for IDs, transaction references, API keys, log output, or any code-like content that should look distinct from body text.

**Usage**

```html
<span class="has-text-mono">TXN-9f3c2a</span>
<pre class="has-text-mono">{"status": "ok"}</pre>
```

---

### `.is-skeleton-pulsing`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |
| Animation | `skeleton-pulse` — opacity oscillates 1 → 0.5 → 1 over 1.5s |

**Description**
Applies a gentle pulsing animation for skeleton/loading placeholder states. Place on placeholder elements shown while real content loads. The pulse is subtle and doesn't distract.

**Usage**

```html
<div class="box is-skeleton-pulsing" style="height: 3rem; background: var(--bulma-border);"></div>
<p class="is-skeleton-pulsing" style="width: 60%; height: 1em; background: var(--bulma-border);"></p>
```

**Notes**
Combine with a background color to make the placeholder visible. The class only adds the animation — size and color are your responsibility.

---

### `.is-density-compact`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |
| Applies to | `.table td` and `.table th` inside the element |

**Description**
Applies tighter cell padding (`0.3rem 0.5rem`) to all table cells inside the element. Use as a wrapper around a table to pack more rows on screen — useful for data grids, audit logs, and reporting views.

**Usage**

```html
<div class="is-density-compact">
  <table class="table is-fullwidth">
    ...
  </table>
</div>
```

---

### `.is-density-comfortable`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |
| Applies to | `.table td` and `.table th` inside the element |

**Description**
Applies generous cell padding (`0.75rem 1rem`) to table cells. Use when readability and scanability matter more than density — customer-facing views, settings tables, or any table where users need to read each row carefully.

**Usage**

```html
<div class="is-density-comfortable">
  <table class="table is-fullwidth">
    ...
  </table>
</div>
```

---

## Brand / Icon Helper Classes

---

### `.brand-link`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |
| Selector | `.navbar-brand .brand-link` |

**Description**
Applied to a link element inside `.navbar-brand`. Sets `display: inline-flex`, `align-items: center`, and `gap: 0.5rem` so an icon and text sit side-by-side in the navbar logo area.

**Usage**

```html
<div class="navbar-brand">
  <a class="navbar-item brand-link" href="/">
    <svg class="brand-icon">...</svg>
    My App
  </a>
</div>
```

---

### `.brand-icon`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
Sizes a brand SVG icon to `1.1rem × 1.1rem` and sets it as `inline-block`. Ensures the icon is the right scale next to the navbar brand name.

**Usage**

```html
<svg class="brand-icon" viewBox="0 0 24 24">...</svg>
```

---

### `.material-symbols-outlined`

| Field | Value |
|---|---|
| Type | Custom Class (third-party override) |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
Overrides the default size of Material Symbols icons to `1.25em` with `vertical-align: middle` and `line-height: 1`. Without this, Material Symbols icons often appear too large and misaligned with adjacent text.

**Usage**

```html
<span class="material-symbols-outlined">home</span>
<span class="material-symbols-outlined">settings</span>
```

**Notes**
Requires the Material Symbols font loaded via Google Fonts. The icon name is the text content of the element.

---

## Menu / Sidebar Classes

---

### `.menu.has-tint`

| Field | Value |
|---|---|
| Type | Custom Modifier (extends Bulma's `.menu`) |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
Adds a subtle two-stop gradient background using the brand primary color at very low opacity (8% → 4%). Creates the impression of a tinted sidebar surface without using a strong fill. Pairs with `.menu` and adds `padding: 1rem 0.75rem` and a rounded corner.

**Usage**

```html
<nav class="menu has-tint">
  ...
</nav>
```

---

### `.menu-label-toggle`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
A CSS reset for a `<button>` element used as a collapsible menu label toggle. Removes all default browser button styling (border, background, padding, font override) so the button looks visually identical to a plain `.menu-label` text element. Required because `<button>` elements in browsers do not inherit font properties by default.

**Usage**

```html
<p class="menu-label">
  <button type="button" class="menu-label-toggle" aria-expanded="true" aria-controls="my-list">
    Section Name
  </button>
</p>
```

**Notes**
Must be inside a `<p class="menu-label">` to inherit correct styling. Without this class, the button will appear smaller/different from `.menu-label` text.

---

### `.menu-label-toggle.with-caret`

| Field | Value |
|---|---|
| Type | Custom Compound Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
Extends `.menu-label-toggle` by adding an animated caret (triangle arrow) before the label text. The caret is drawn with a CSS border triangle via the `::before` pseudo-element. When `aria-expanded="true"` the caret points down (rotated 90°). When `aria-expanded="false"` the caret points right (0° rotation), indicating the section is collapsed.

**Usage**

```html
<button type="button" class="menu-label-toggle with-caret"
        aria-expanded="true" aria-controls="nav-list">
  Core Features
</button>
```

**Notes**
The animation is driven entirely by the `aria-expanded` attribute. Your JavaScript must toggle this attribute; the CSS handles the rotation animation automatically.

---

### `.menu-list.is-collapsed`

| Field | Value |
|---|---|
| Type | Custom State Modifier |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
Sets `display: none` on a `.menu-list` to hide it. Toggled via JavaScript when the corresponding `.menu-label-toggle` is clicked. When the class is absent, the list is visible (default).

**Usage**

```js
// Toggle collapse state
const list = document.getElementById(btn.getAttribute('aria-controls'));
const isOpen = btn.getAttribute('aria-expanded') === 'true';
btn.setAttribute('aria-expanded', isOpen ? 'false' : 'true');
list.classList.toggle('is-collapsed', isOpen);
```

---

### `.menu-divider`

| Field | Value |
|---|---|
| Type | Custom Class |
| Defined in | `_overrides-material-3-blue-custom.scss` |
| Applies to | `<hr>` elements |

**Description**
Styles an `<hr>` element as a thin horizontal rule inside a sidebar menu. Uses a primary-tinted color at 22% opacity for a subtle but visible separator. Adds `0.75rem` top and bottom margin.

**Usage**

```html
<nav class="menu">
  <ul class="menu-list">...</ul>
  <hr class="menu-divider" />
  <ul class="menu-list">...</ul>
</nav>
```

---

---

# Part 3 — Bulma Component Classes (with Theme Overrides Applied)

Bulma provides these classes. Your theme has overridden their visual style to match Material 3. You use the same class names as standard Bulma — the theme handles the look automatically.

---

## Layout

---

### `.columns`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Creates a horizontal flexbox row. Direct children must be `.column` elements. Bulma adds a negative horizontal margin to `.columns` to compensate for column gutters.

**Usage**

```html
<div class="columns">
  <div class="column">Left</div>
  <div class="column">Right</div>
</div>
```

---

### `.column`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
One column inside a `.columns` row. By default all columns share equal width. Add a size modifier to pin the width.

**Common Modifiers**

| Modifier | Width |
|---|---|
| `.is-1` | 1/12 (~8%) |
| `.is-2` | 2/12 (~17%) |
| `.is-3` | 3/12 (25%) |
| `.is-4` | 4/12 (33%) |
| `.is-6` | 6/12 (50%) |
| `.is-8` | 8/12 (67%) |
| `.is-narrow` | shrinks to content width |
| `.is-full` | forces 100% width |

**Usage**

```html
<div class="columns">
  <div class="column is-3">Sidebar (25%)</div>
  <div class="column">Main content (remaining)</div>
</div>
```

---

### `.section`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Adds consistent vertical padding (`3rem 1.5rem`) to a page region. Wraps `.container` inside it.

**Usage**

```html
<section class="section">
  <div class="container">...</div>
</section>
```

---

### `.container`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Centers content horizontally and adds a responsive max-width. Keeps page content from stretching too wide on large screens.

**Modifiers**

| Modifier | Behavior |
|---|---|
| `.is-fluid` | No max-width; fills width with side padding |
| `.is-widescreen` | Expands limit at widescreen breakpoint |
| `.is-fullhd` | Expands limit at full HD breakpoint |

---

### `.level`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
A horizontal flex row with left and right slots. Useful for title + action button layouts, or stats in a row.

**Usage**

```html
<div class="level">
  <div class="level-left">
    <div class="level-item"><h2 class="title">Reports</h2></div>
  </div>
  <div class="level-right">
    <div class="level-item"><button class="button is-primary">Export</button></div>
  </div>
</div>
```

---

## Navbar (Top App Bar)

---

### `.navbar`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
The top application bar. In this theme it is styled as a dark navy M3 Top App Bar with `position: sticky`, drop shadow, and near-white text. All Bulma navbar subcomponents automatically receive matching colors.

**Usage**

```html
<nav class="navbar" role="navigation">
  <div class="navbar-brand">...</div>
  <div class="navbar-menu">
    <div class="navbar-start">...</div>
    <div class="navbar-end">...</div>
  </div>
</nav>
```

---

### `.navbar-brand`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
The leftmost part of the navbar — holds your logo, app name, and the mobile burger button. Always visible on mobile.

---

### `.navbar-item`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
A single item (link, button, or content block) inside the navbar. On this theme, these automatically use `--m3c-on-navbar-hsl` text color with hover/focus state-layer backgrounds.

**Modifier**

| Modifier | Behavior |
|---|---|
| `.is-active` | Highlights the item as the current page |

---

### `.navbar-start` / `.navbar-end`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Alignment containers within `.navbar-menu`. `.navbar-start` aligns items to the left; `.navbar-end` aligns items to the right.

---

## Hero Banner

---

### `.hero`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
A large full-width banner section. Commonly used for page headers with a title and subtitle.

---

### `.hero.is-primary`

| Field | Value |
|---|---|
| Type | Bulma Modifier (M3 Override Applied) |

**Description**
In this theme, renders the hero with the M3 "Primary Container" background (`--m3c-container-hsl`) — a soft blue. Text uses `--m3c-on-container-hsl` — a deep navy. This is a light, accessible banner, not a dark one.

**Usage**

```html
<section class="hero is-primary">
  <div class="hero-body">
    <p class="title">Dashboard</p>
    <p class="subtitle">Good morning, Alice</p>
  </div>
</section>
```

---

### `.hero-body`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
The content area inside a `.hero`. Adds centered padding. Put your title and subtitle here.

---

## Cards

---

### `.card`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A floating surface container. In this theme, styled as an M3 "Elevated Card": white background with a subtle primary tint overlay and a multi-layer shadow. No border. Elevates on hover (tint increases, shadow deepens).

**Usage**

```html
<div class="card">
  <div class="card-content">
    <p>Card content here</p>
  </div>
</div>
```

---

### `.card-header`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
The top strip of a card. In this theme: transparent background, light bottom border, no shadow, rounded top corners. Contains `.card-header-title` and optionally `.card-header-icon`.

---

### `.card-header-title`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
The title text inside a card header. Styled at `0.875rem`, weight 500 — matches M3's "title-medium" scale.

---

### `.card-content`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
The main body area of a card. Default padding `1.5rem`. Use this as your card body for any content.

---

### `.card-footer` / `.card-footer-item`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
`.card-footer` is a bottom bar. `.card-footer-item` is one slot inside it — items are flex-distributed evenly. Use for action links like "View", "Edit", "Delete".

**Usage**

```html
<footer class="card-footer">
  <a class="card-footer-item" href="#">View</a>
  <a class="card-footer-item" href="#">Edit</a>
</footer>
```

---

## Buttons

---

### `.button`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
Default button. In this theme: M3 "Elevated Button" style — white background with a subtle shadow, weight 500, `0.375rem` radius. Has a `::after` state-layer that tints to 8% on hover and 12% on focus/active.

---

### `.button.is-primary`

| Field | Value |
|---|---|
| Type | Bulma Modifier (M3 Override Applied) |

**Description**
M3 "Filled Button" — solid brand blue background, white text. The highest emphasis action on a surface. Use for the single most important action.

---

### `.button.is-light`

| Field | Value |
|---|---|
| Type | Bulma Modifier (M3 Override Applied) |

**Description**
M3 "Tonal Button" — light blue container background, dark blue text. Medium emphasis. Use as an alternative primary action when a filled button would be too heavy.

---

### `.button.is-outlined`

| Field | Value |
|---|---|
| Type | Bulma Modifier (M3 Override Applied) |

**Description**
M3 "Outlined Button" — transparent background, `1px` border in `--bulma-border`, primary color text. Medium emphasis. Use for secondary actions alongside a filled button.

---

### `.button.is-ghost`

| Field | Value |
|---|---|
| Type | Bulma Modifier |

**Description**
M3 "Text Button" — no background, no border. Lowest emphasis. Use for tertiary actions that need to exist but shouldn't draw attention. Good for "Cancel", "Skip", "Learn more" links.

---

### `.button.is-small` / `.is-normal` / `.is-medium` / `.is-large`

| Field | Value |
|---|---|
| Type | Bulma Modifiers (M3 Override Applied) |

**Description**
Size variants for buttons. Mapped to M3's button size scale:

| Modifier | Font size | Padding |
|---|---|---|
| `.is-small` | 0.75rem | 0.25rem 0.625rem |
| `.is-normal` | 0.875rem | 0.375rem 0.875rem |
| `.is-medium` | 1rem | 0.5rem 1.125rem |
| `.is-large` | 1.125rem | 0.625rem 1.375rem |

---

### `.buttons`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
A flex container for grouping multiple `.button` elements. Handles gap and wrapping automatically.

---

## Forms

---

### `.field`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
The outer wrapper for a form field. Groups `.label`, `.control`, and `.help` together. Adds bottom margin for spacing between fields.

---

### `.label`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
The text label above a form input. Bold, small size. Screen readers associate this with the input when markup order is correct.

---

### `.control`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Wraps an input, select, or button. Manages relative positioning for icons and loading states.

**Modifiers**

| Modifier | Behavior |
|---|---|
| `.has-icons-left` | Reserves space for a left icon |
| `.has-icons-right` | Reserves space for a right icon |
| `.is-loading` | Shows a spinner on the right side |

---

### `.input`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A single-line text input. In this theme: M3 "Outlined TextField" style — `1px` border, rounded corners, white background. On hover: border darkens. On focus: border thickens to `2px` and turns brand blue, no box-shadow.

**Usage**

```html
<div class="field">
  <label class="label">Name</label>
  <div class="control">
    <input class="input" type="text" placeholder="Enter name" />
  </div>
</div>
```

---

### `.textarea`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
Multi-line text input. Same M3 styling as `.input`. Resizable vertically by default.

---

### `.select`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
Wraps a native `<select>` element. The inner `<select>` gets the same M3 outlined style as `.input`.

**Usage**

```html
<div class="control">
  <div class="select">
    <select>
      <option>Option A</option>
      <option>Option B</option>
    </select>
  </div>
</div>
```

---

### `.help`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Small helper/hint text below a form field. Neutral color by default. Combine with a color modifier for validation messages.

**Usage**

```html
<p class="help is-danger">This field is required.</p>
<p class="help is-success">Looks good!</p>
```

---

## Tables

---

### `.table`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A data table. In this theme: M3 "Data Table" style — `0.875rem` text, rounded outer corners, no border, multi-layer shadow. Header row has a subtle primary-tinted background. Rows have a primary state-layer hover effect.

**Usage**

```html
<table class="table is-fullwidth">
  <thead>
    <tr>
      <th>Name</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Alice</td>
      <td><span class="tag is-success">Active</span></td>
    </tr>
  </tbody>
</table>
```

**Modifiers**

| Modifier | Behavior |
|---|---|
| `.is-fullwidth` | Stretches table to 100% container width |
| `.is-striped` | Alternating row background color |
| `.is-hoverable` | Highlights row on cursor hover |
| `.is-narrow` | Compact cell padding (overridden by `.is-density-compact`) |
| `.is-bordered` | Adds visible cell borders |

---

## Tabs

---

### `.tabs`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A horizontal tab strip. In this theme: M3 "Primary Tabs" style — a `3px` solid primary-colored underline on the active tab, no active background fill, weight 500 labels. Tab items are `<li>` elements containing `<a>` links.

**Usage**

```html
<div class="tabs">
  <ul>
    <li class="is-active"><a>Overview</a></li>
    <li><a>Details</a></li>
    <li><a>History</a></li>
  </ul>
</div>
```

---

## Tags / Chips

---

### `.tag`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A small inline label. In this theme: M3 "Assist Chip" style — `0.8125rem` label-small size, weight 500, `0.25rem` radius, `1px` border, white background. Use for status indicators, category labels, and metadata badges.

**Usage**

```html
<span class="tag">Default</span>
```

**Semantic Color Modifiers**

| Modifier | Color Scheme | Typical Use |
|---|---|---|
| `.is-primary` | Blue container / dark blue text | primary status, main category |
| `.is-info` | Teal container / dark teal text | informational |
| `.is-success` | Green container / dark green text | success, active, completed |
| `.is-warning` | Amber container / dark amber text | pending, warning, needs action |
| `.is-danger` | Red container / dark red text | error, failed, critical |

**Additional Modifiers**

| Modifier | Behavior |
|---|---|
| `.is-rounded` | Fully pill-shaped |
| `.is-delete` | Shows an X delete button |
| `.is-light` | Lighter tint of the semantic color |

---

### `.tags`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
A flex container for grouping multiple `.tag` elements with automatic gap and wrapping.

---

## Messages (Banners)

---

### `.message`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A block-level feedback component — like an M3 "Banner". In this theme: no border, rounded corners, subtle tinted background with a faint shadow.

**Color Modifiers**

| Modifier | Use |
|---|---|
| `.is-primary` | Informational — soft blue background |
| `.is-info` | Teal informational |
| `.is-success` | Success or confirmation |
| `.is-warning` | Caution or requires action |
| `.is-danger` | Error or critical alert |

**Usage**

```html
<article class="message is-warning">
  <div class="message-header">Deprecation Notice</div>
  <div class="message-body">This API endpoint will be removed in v3.</div>
</article>
```

---

### `.message-header`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
Optional heading row inside a `.message`. In this theme: transparent background, light bottom separator, `0.875rem` size, weight 600. Automatically picks up the message color.

---

### `.message-body`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
The content area inside a `.message`. Applies padding and inherits the message background.

---

## Panel

---

### `.panel`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A grouped list component resembling an M3 "Navigation Drawer" item list. In this theme: no border, `--bulma-radius-medium` rounding, multi-layer shadow, overflow hidden (so rounded corners clip children).

---

### `.panel-heading`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
The header row of a `.panel`. In this theme: light primary-tinted background, dark primary text, `0.75rem` uppercase label style, bottom border.

---

### `.panel-block`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
A single row in a panel. Can be a link, label, or checkbox. Styled as a block-level list item with padding.

---

### `.panel-block.is-active`

| Field | Value |
|---|---|
| Type | Bulma Modifier (M3 Override Applied) |

**Description**
Highlights the currently selected row in a panel using the M3 "secondary container" fill — light blue background and dark blue text, weight 600.

---

## Navigation

---

### `.menu`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Vertical sidebar navigation container. Holds `.menu-label` headings and `.menu-list` link lists. Does not add any visual styling by itself — combine with `.has-tint` for a branded appearance.

---

### `.menu-label`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A section heading inside a `.menu`. In this theme: `0.75rem` size, primary color, no uppercase transformation (Bulma default has uppercase — this theme resets it). Use to label groups of related nav links.

**Usage**

```html
<p class="menu-label">Core Features</p>
```

---

### `.menu-list`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
An unordered list of navigation links inside a `.menu`. Each `<li>` contains an `<a>`. Handles padding, margins, and nesting automatically.

---

### `.menu-list a`

| Field | Value |
|---|---|
| Type | Bulma Selector (M3 Override Applied) |

**Description**
Individual nav links inside a `.menu-list`. In this theme: `0.875rem`, weight 500, `0.375rem` radius. Hover: 8% primary state-layer tint. Active: primary container background with a `4px` left border in brand blue.

---

### `.menu-list a.is-active`

| Field | Value |
|---|---|
| Type | Bulma Modifier (M3 Override Applied) |

**Description**
Marks the current page link in the sidebar. In this theme: primary container background, on-container text color, weight 600, and a `4px` left accent border in brand blue (M3 active indicator).

**Usage**

```html
<ul class="menu-list">
  <li><a class="is-active" href="#">Dashboard</a></li>
  <li><a href="#">Reports</a></li>
</ul>
```

---

### `.breadcrumb`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A horizontal breadcrumb trail. In this theme: `0.875rem`, primary color links with underline on hover, muted separator color.

**Usage**

```html
<nav class="breadcrumb" aria-label="breadcrumbs">
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/reports">Reports</a></li>
    <li class="is-active"><a href="#">Q1 Summary</a></li>
  </ul>
</nav>
```

---

## Feedback

---

### `.notification`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
An inline alert strip. In this theme: M3 "Snackbar" styling — rounded corners, drop shadow, `0.875rem` text, no border. Dismissible with a `.delete` button inside.

**Usage**

```html
<div class="notification is-success">
  Changes saved.
  <button class="delete"></button>
</div>
```

**Color Modifiers:** `.is-primary`, `.is-info`, `.is-success`, `.is-warning`, `.is-danger`

---

### `progress.progress`

| Field | Value |
|---|---|
| Type | Bulma Class (M3 Override Applied) |

**Description**
A linear progress bar. In this theme: `0.25rem` height (thin, M3 "Linear Progress" style), `0.25rem` border-radius.

**Usage**

```html
<progress class="progress is-primary" value="60" max="100">60%</progress>
```

---

## Text & Color Utilities

---

### `.has-text-primary` / `.has-text-success` / `.has-text-warning` / `.has-text-danger` / `.has-text-info`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Sets text color to the semantic color value.

---

### `.has-text-weight-light` / `.medium` / `.semibold` / `.bold` / `.extrabold`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Sets the font weight. Maps to weights 300 / 500 / 600 / 700 / 800.

---

### `.is-size-1` through `.is-size-7`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Sets font size from a responsive scale:

| Class | Size |
|---|---|
| `.is-size-1` | 3rem |
| `.is-size-2` | 2.5rem |
| `.is-size-3` | 2rem |
| `.is-size-4` | 1.5rem |
| `.is-size-5` | 1.25rem |
| `.is-size-6` | 1rem |
| `.is-size-7` | 0.75rem |

---

### `.has-text-left` / `.has-text-centered` / `.has-text-right`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Sets text alignment.

---

### `.is-hidden`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Sets `display: none !important`. Hides any element.

**Responsive Variants**

| Class | Hidden at |
|---|---|
| `.is-hidden-mobile` | < 769px |
| `.is-hidden-tablet` | 769px–1024px |
| `.is-hidden-desktop` | ≥ 1024px |

---

### `.is-flex`

| Field | Value |
|---|---|
| Type | Bulma Class |

**Description**
Sets `display: flex`. Use with flex helper classes:

| Helper | Property |
|---|---|
| `.is-justify-content-space-between` | `justify-content: space-between` |
| `.is-align-items-center` | `align-items: center` |
| `.is-flex-wrap-wrap` | `flex-wrap: wrap` |

---

## Spacing Utilities

Bulma's spacing system uses a `0–6` scale, where each step = `0.25rem × step` (approximately).

### Margin helpers: `m-*`, `mt-*`, `mb-*`, `ml-*`, `mr-*`, `mx-*`, `my-*`

| Class | Property |
|---|---|
| `m-0` | margin: 0 |
| `mt-4` | margin-top: 1rem |
| `mb-2` | margin-bottom: 0.5rem |
| `mx-auto` | margin-left + right: auto (centers block elements) |
| `my-5` | margin-top + bottom: 1.5rem |

### Padding helpers: `p-*`, `pt-*`, `pb-*`, `pl-*`, `pr-*`, `px-*`, `py-*`

Same pattern as margin, but for padding.

---

# Part 4 — Global Element Overrides

These rules apply to standard HTML elements globally, not via a class.

---

### `body`

Font size `0.875rem`, line-height `1.5`, letter-spacing `0.01em`. Background is Bulma's `--bulma-scheme-main`.

---

### `:focus-visible`

All interactive elements show a `2px solid var(--bulma-primary)` outline when focused via keyboard (`outline-offset: 2px`). This cannot be removed — it is required for keyboard accessibility.

---

### `::-webkit-scrollbar`

Custom `8px × 8px` scrollbars on WebKit/Blink browsers (Chrome, Edge, Safari). Track is `--bulma-scheme-main-bis`, thumb is `--bulma-border` with a `4px` radius. Thumb darkens on hover.

---

### `code` / `pre`

Font size `0.82rem`, line-height `1.6`. Uses the monospace font stack.

---

# Part 5 — Dark Mode

---

### `[data-theme="dark"]`

| Field | Value |
|---|---|
| Type | CSS Scope |
| Defined in | `_overrides-material-3-blue-custom.scss` |

**Description**
All overrides scoped inside `[data-theme="dark"]` apply when the `data-theme="dark"` attribute is set on the `<html>` element. The dark mode remaps:

- `--m3-primary-hsl` → lighter tint (M3 primary-80: `217, 100%, 75%`)
- `--m3-surface-tint-*` → recalculated from new primary
- Card backgrounds → dark neutral (`hsl(215, 6%, 14%)`)
- Navbar → darker (`hsl(213, 50%, 12%)`)
- Table header → dark primary tint
- Inputs → dark surface
- Buttons → swapped for dark contrast ratios

**Activation**

```html
<html data-theme="dark">
```

or via JavaScript:

```js
document.documentElement.setAttribute('data-theme', 'dark');
document.documentElement.removeAttribute('data-theme'); // remove to restore light
```

---

# Appendix — Quick Lookup Index

| Name | Type | Section |
|---|---|---|
| `--m3-easing-standard` | CSS Variable | Part 1 |
| `--m3-easing-decelerate` | CSS Variable | Part 1 |
| `--m3-easing-accelerate` | CSS Variable | Part 1 |
| `--m3-duration-short` | CSS Variable | Part 1 |
| `--m3-duration-medium` | CSS Variable | Part 1 |
| `--m3-duration-long` | CSS Variable | Part 1 |
| `--m3c-primary-hsl` | CSS Variable | Part 1 |
| `--m3c-container-hsl` | CSS Variable | Part 1 |
| `--m3c-on-container-hsl` | CSS Variable | Part 1 |
| `--m3c-navbar-hsl` | CSS Variable | Part 1 |
| `--m3c-on-navbar-hsl` | CSS Variable | Part 1 |
| `--m3c-glass-alpha` | CSS Variable | Part 1 |
| `--m3-primary-hsl` | CSS Variable | Part 1 |
| `--m3-surface-tint-1` | CSS Variable | Part 1 |
| `--m3-surface-tint-2` | CSS Variable | Part 1 |
| `--m3-surface-tint-3` | CSS Variable | Part 1 |
| `--bulma-primary` | CSS Variable (Bulma) | Part 1 |
| `--bulma-radius` | CSS Variable (Bulma) | Part 1 |
| `--bulma-border` | CSS Variable (Bulma) | Part 1 |
| `--bulma-text` | CSS Variable (Bulma) | Part 1 |
| `--bulma-scheme-main` | CSS Variable (Bulma) | Part 1 |
| `--bulma-duration` | CSS Variable (Bulma) | Part 1 |
| `--bulma-family-code` | CSS Variable (Bulma) | Part 1 |
| `.has-text-tabular` | Custom Class | Part 2 |
| `.has-text-mono` | Custom Class | Part 2 |
| `.is-skeleton-pulsing` | Custom Class | Part 2 |
| `.is-density-compact` | Custom Class | Part 2 |
| `.is-density-comfortable` | Custom Class | Part 2 |
| `.brand-link` | Custom Class | Part 2 |
| `.brand-icon` | Custom Class | Part 2 |
| `.material-symbols-outlined` | Custom Class | Part 2 |
| `.menu.has-tint` | Custom Class | Part 2 |
| `.menu-label-toggle` | Custom Class | Part 2 |
| `.menu-label-toggle.with-caret` | Custom Class | Part 2 |
| `.menu-list.is-collapsed` | Custom Class | Part 2 |
| `.menu-divider` | Custom Class | Part 2 |
| `.columns` / `.column` | Bulma Class | Part 3 |
| `.section` / `.container` | Bulma Class | Part 3 |
| `.level` | Bulma Class | Part 3 |
| `.navbar` | Bulma Class | Part 3 |
| `.hero` / `.hero.is-primary` | Bulma Class | Part 3 |
| `.card` | Bulma Class | Part 3 |
| `.button` | Bulma Class | Part 3 |
| `.field` / `.control` / `.label` | Bulma Class | Part 3 |
| `.input` / `.textarea` / `.select` | Bulma Class | Part 3 |
| `.table` | Bulma Class | Part 3 |
| `.tabs` | Bulma Class | Part 3 |
| `.tag` / `.tags` | Bulma Class | Part 3 |
| `.message` | Bulma Class | Part 3 |
| `.panel` | Bulma Class | Part 3 |
| `.menu` / `.menu-label` / `.menu-list` | Bulma Class | Part 3 |
| `.breadcrumb` | Bulma Class | Part 3 |
| `.notification` | Bulma Class | Part 3 |
| `progress.progress` | Bulma Class | Part 3 |
| `[data-theme="dark"]` | CSS Scope | Part 5 |
