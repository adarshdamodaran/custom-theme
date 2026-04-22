# Blue Custom Theme Reference (Beginner Friendly)

This guide explains what is available in your Blue Custom theme, how to use it, and where to make changes safely.

## 1) Quick Mental Model

Your styling comes from three places:

1. Bulma framework classes (global, many prebuilt components)
2. Blue Custom theme files (your project-level design rules)
3. Page-local styles (inside each HTML file's style tag)

For consistency across pages, prefer theme-level classes and variables.

---

## 2) Where Things Live

Main files for the Blue Custom theme:

- `scss/material-3-blue-custom.scss`
  - Sets Bulma base configuration (primary color, fonts, radii, spacing)
- `scss/_overrides-material-3-blue-custom.scss`
  - Theme dictionary: custom tokens and component overrides
- `css/material-3-blue-custom.css`
  - Compiled output used by pages (generated)

Build command:

```bash
npm run build:themes
```

---

## 3) Variable Dictionary (Design Tokens)

These are the most important tokens in `scss/_overrides-material-3-blue-custom.scss`.

### 3.1 Motion Tokens

| Variable | Meaning | Typical Use |
|---|---|---|
| `--m3-easing-standard` | Default animation curve | transitions |
| `--m3-easing-decelerate` | Entering movement curve | larger enter motions |
| `--m3-easing-accelerate` | Exiting movement curve | exit motions |
| `--m3-duration-short` | Short duration | hover/focus |
| `--m3-duration-medium` | Medium duration | moderate animations |
| `--m3-duration-long` | Long duration | bigger UI changes |

### 3.2 Brand + Surface Tokens

| Variable | Meaning | Example |
|---|---|---|
| `--m3c-primary-hsl` | Main brand color in HSL triplet form | `hsl(var(--m3c-primary-hsl))` |
| `--m3c-container-hsl` | Primary container background tone | container surfaces |
| `--m3c-on-container-hsl` | Text/icon color on container | readable text |
| `--m3c-navbar-hsl` | Navbar background tone | top navigation |
| `--m3c-on-navbar-hsl` | Navbar text/icon tone | navbar labels/icons |
| `--m3c-glass-alpha` | Alpha value for translucent surfaces | glass effects |

### 3.3 Derived Tonal Tokens

| Variable | Meaning | Typical Use |
|---|---|---|
| `--m3-primary-hsl` | Alias to current primary | consistent references |
| `--m3-surface-tint-1` | Light tint overlay | low elevation |
| `--m3-surface-tint-2` | Medium tint overlay | medium elevation |
| `--m3-surface-tint-3` | Stronger tint overlay | higher elevation |

### 3.4 Bulma Variables You Already Use

These are provided by Bulma and consumed by your overrides.

- `--bulma-primary`
- `--bulma-radius`
- `--bulma-radius-medium`
- `--bulma-border`
- `--bulma-border-weak`
- `--bulma-text`
- `--bulma-text-weak`
- `--bulma-text-strong`
- `--bulma-scheme-main`
- `--bulma-scheme-main-bis`
- `--bulma-duration`
- `--bulma-easing`

---

## 4) Class Dictionary (What You Can Use)

Below are classes and selectors defined in the Blue Custom override file. Use this as your practical data dictionary.

## 4.1 Reusable Utilities

| Class | What It Does | When To Use |
|---|---|---|
| `.has-text-tabular` | Uses tabular numerals for aligned numbers | metrics, tables, KPIs |
| `.has-text-mono` | Forces monospace family | IDs, codes, logs |
| `.is-skeleton-pulsing` | Pulsing loading animation | skeleton placeholders |
| `.is-density-compact` | Reduces table cell spacing | dense data views |
| `.is-density-comfortable` | Increases table spacing | readability-first views |

## 4.2 Brand + Icon Helpers

| Class | What It Does | When To Use |
|---|---|---|
| `.navbar-brand .brand-link` | Aligns brand icon + text | navbar branding |
| `.brand-icon` | Standard icon size and coloring | SVG brand icon |
| `.material-symbols-outlined` | Normalizes material icon sizing | icon text spans |

## 4.3 Menu / Sidebar Helpers

| Class / Selector | What It Does | Required Markup |
|---|---|---|
| `.menu.has-tint` | Adds subtle tinted sidebar background | put on menu container |
| `.menu-label` | Menu section heading style | use on heading element |
| `.menu-divider` | Horizontal divider between groups | `hr` element |
| `.menu-label-toggle` | Resets button styles for label button | button inside menu label |
| `.menu-label-toggle.with-caret` | Adds caret layout spacing | label button with caret |
| `.menu-label-toggle.with-caret::before` | Draws caret triangle | automatic pseudo-element |
| `.menu-label-toggle[aria-expanded="false"].with-caret::before` | Rotates caret for collapsed state | set aria-expanded in JS |
| `.menu-list.is-collapsed` | Hides menu list when collapsed | toggle class in JS |

## 4.4 Component-Level Overrides

These use Bulma classes but are themed by your overrides:

- `.navbar`
- `.hero.is-primary`
- `.card`, `.card-header`, `.card-header-title`
- `.button`, `.button.is-primary`, `.button.is-light`, `.button.is-outlined`
- `.tabs`
- `.table`
- `.input`, `.textarea`, `.select select`
- `.tag` and semantic variants (`.is-primary`, `.is-info`, `.is-success`, `.is-warning`, `.is-danger`)
- `.message`, `.message-header`
- `.panel`, `.panel-heading`, `.panel-block.is-active`
- `.breadcrumb`
- `.notification`
- `progress.progress`

---

## 5) Copy-Paste Usage Patterns

### 5.1 Basic Tinted Sidebar

```html
<nav class="menu has-tint">
  <p class="menu-label">Core</p>
  <ul class="menu-list">
    <li><a class="is-active" href="#">Overview</a></li>
    <li><a href="#">Queue</a></li>
  </ul>
</nav>
```

### 5.2 Collapsible Menu Label (Caret + Toggle)

```html
<p class="menu-label">
  <button type="button" class="menu-label-toggle with-caret" aria-expanded="true" aria-controls="core-menu">
    Core
  </button>
</p>
<ul id="core-menu" class="menu-list">
  <li><a href="#">Overview</a></li>
</ul>
```

```js
const toggles = document.querySelectorAll('.menu-label-toggle');

toggles.forEach((toggle) => {
  toggle.addEventListener('click', () => {
    const id = toggle.getAttribute('aria-controls');
    const list = id ? document.getElementById(id) : null;
    if (!list) return;

    const expanded = toggle.getAttribute('aria-expanded') === 'true';
    toggle.setAttribute('aria-expanded', expanded ? 'false' : 'true');
    list.classList.toggle('is-collapsed', expanded);
  });
});
```

### 5.3 Use Theme Tokens in Page CSS

```css
.custom-callout {
  background: hsla(var(--m3c-primary-hsl), 0.08);
  border: 1px solid hsla(var(--m3c-primary-hsl), 0.2);
  color: hsl(var(--m3c-on-container-hsl));
}
```

---

## 6) Safe Editing Guide (For Limited CSS Experience)

### 6.1 If you want to change colors globally

Edit only token values near `:root` in:

- `scss/_overrides-material-3-blue-custom.scss`

Then run build.

### 6.2 If you want to change spacing/shape globally

Edit Bulma configuration in:

- `scss/material-3-blue-custom.scss`

Look for:

- `$radius`, `$radius-medium`, `$radius-large`
- `$block-spacing`

Then run build.

### 6.3 If you want a page-only experiment

Use the page `style` block in that HTML file first.

If it proves useful in multiple pages, move it into:

- `scss/_overrides-material-3-blue-custom.scss`

### 6.4 If something "does not change"

Check this order:

1. Is the page loading `css/material-3-blue-custom.css`?
2. Did you run `npm run build:themes`?
3. Is another rule more specific (or using `!important`)?
4. Is the style in page-local CSS overriding theme CSS?

---

## 7) How To Discover Available Classes Yourself

Run these commands from project root:

```bash
# List top-level class selectors in Blue Custom overrides
rg "^\\.[a-zA-Z0-9_-]+" scss/_overrides-material-3-blue-custom.scss

# Find all CSS variables used in the override file
rg "--m3|--m3c|--bulma" scss/_overrides-material-3-blue-custom.scss

# Find where collapsible menu styles are defined
rg "menu-label-toggle|with-caret|is-collapsed" scss/_overrides-material-3-blue-custom.scss
```

---

## 8) Scope Rules (Important)

- Theme scope (recommended for reuse):
  - `scss/_overrides-material-3-blue-custom.scss`
- Page scope (one-off layout tweaks):
  - page `style` blocks, like in `blue-custom-clean.html`

A good rule:

- If used in 2 or more pages, move to theme.
- If it is unique to one page layout, keep local.

---

## 9) Build and Verification Workflow

Use this every time:

```bash
npm run build:themes
```

Then refresh the page.

If needed, verify generated output contains your selector:

```bash
rg "menu-label-toggle|menu-divider|has-tint" css/material-3-blue-custom.css
```

---

## 10) What This Guide Covers vs Bulma Docs

This guide covers:

- Your custom theme tokens
- Your custom helpers
- Your override behavior on core components

Bulma docs still remain the best source for all base framework class combinations.

---

## 11) Suggested Next Step

If you want, the next useful improvement is an auto-generated inventory script that outputs:

- all custom selectors
- all custom properties
- where each is defined

into a single JSON file for fast lookup.
