# Blue Custom Theme — Quick Cheat Sheet

> One-page reference. Full details: `docs/blue-custom-theme-reference.md` and `docs/blue-custom-api-reference.md`

---

## Build

```bash
npm run build:themes
```

Output: `css/material-3-blue-custom.css`

---

## Top 10 Custom Tokens (paste directly into CSS)

```css
/* Brand color as tinted background */
background: hsla(var(--m3c-primary-hsl), 0.08);

/* Brand solid color */
background: hsl(var(--m3c-primary-hsl));

/* Container surface (light blue tint) */
background: hsl(var(--m3c-container-hsl));

/* Text on container */
color: hsl(var(--m3c-on-container-hsl));

/* Navbar color */
background: hsl(var(--m3c-navbar-hsl));

/* Text on navbar */
color: hsl(var(--m3c-on-navbar-hsl));

/* Elevation tints (add on top of card/surface bg) */
background-image: linear-gradient(var(--m3-surface-tint-1), var(--m3-surface-tint-1)); /* low */
background-image: linear-gradient(var(--m3-surface-tint-2), var(--m3-surface-tint-2)); /* medium */
background-image: linear-gradient(var(--m3-surface-tint-3), var(--m3-surface-tint-3)); /* high */

/* Standard transition */
transition: background-color var(--m3-duration-short) var(--m3-easing-standard);
```

---

## Most-Used Bulma Classes at a Glance

### Layout

| Class | What it does |
|---|---|
| `.columns` | Starts a column row (flexbox) |
| `.column` | One column (equal width by default) |
| `.column.is-3` | Fixed width: 3/12 of row |
| `.section` | Page section with padding |
| `.container` | Centers content with max-width |
| `.container.is-fluid` | Full-width container |
| `.level` | Horizontal bar with left/right sides |

### Cards

| Class | What it does |
|---|---|
| `.card` | M3 elevated card surface |
| `.card-header` | Top bar of a card |
| `.card-header-title` | Title inside card header |
| `.card-content` | Main body area |
| `.card-footer` | Bottom bar |
| `.card-footer-item` | One item inside footer |

### Buttons

| Class | What it does |
|---|---|
| `.button` | M3 Elevated button (white, shadow) |
| `.button.is-primary` | M3 Filled button (brand blue) |
| `.button.is-light` | M3 Tonal button (light blue bg) |
| `.button.is-outlined` | M3 Outlined button (border only) |
| `.button.is-small/medium/large` | Size variants |
| `.buttons` | Groups buttons with spacing |

### Forms

| Class | What it does |
|---|---|
| `.field` | Wraps label + control |
| `.label` | Form label |
| `.control` | Wraps input |
| `.input` | Text input |
| `.textarea` | Multi-line text input |
| `.select` | Wraps a `<select>` element |
| `.help` | Small note below field |
| `.help.is-danger` | Red error message |

### Tables

| Class | What it does |
|---|---|
| `.table` | Base table |
| `.table.is-fullwidth` | Stretches to 100% width |
| `.table.is-striped` | Alternating row bg |
| `.table.is-hoverable` | Row highlight on hover |
| `.table.is-narrow` | Compact row padding |

### Tags / Chips

| Class | What it does |
|---|---|
| `.tag` | Default chip/tag |
| `.tag.is-primary` | Blue chip |
| `.tag.is-success` | Green chip |
| `.tag.is-warning` | Amber chip |
| `.tag.is-danger` | Red chip |
| `.tag.is-info` | Teal chip |
| `.tags` | Groups tags |

### Feedback Components

| Class | What it does |
|---|---|
| `.notification` | Inline alert banner |
| `.notification.is-primary/success/warning/danger` | Colored alert |
| `.message` | M3 Banner (larger, with optional header) |
| `.message-header` | Heading bar of message |
| `.message-body` | Content area of message |
| `.progress` | Linear progress bar |

### Navigation

| Class | What it does |
|---|---|
| `.navbar` | Dark navy top app bar |
| `.navbar-brand` | Left logo section |
| `.navbar-item` | Nav link item |
| `.navbar-item.is-active` | Currently selected nav item |
| `.tabs` | Horizontal tab strip |
| `.tabs li.is-active` | Active tab with primary underline |
| `.breadcrumb` | Breadcrumb trail |

### Sidebar / Menu

| Class | What it does |
|---|---|
| `.menu` | Sidebar navigation container |
| `.menu.has-tint` | Tinted sidebar background |
| `.menu-label` | Section heading in sidebar |
| `.menu-list` | List of nav links |
| `.menu-list a.is-active` | Active sidebar link |
| `.menu-divider` | Horizontal rule between sections |
| `.menu-label-toggle` | Button that resets to label style |
| `.menu-label-toggle.with-caret` | Adds animated caret |
| `.menu-list.is-collapsed` | Hides menu section |

### Panel (selectable list)

| Class | What it does |
|---|---|
| `.panel` | M3-styled card-like panel |
| `.panel-heading` | Panel header bar |
| `.panel-block` | Clickable row in panel |
| `.panel-block.is-active` | Selected row |

---

## Custom Utility Classes

| Class | What it does |
|---|---|
| `.has-text-tabular` | Tabular numerals (for aligned numbers) |
| `.has-text-mono` | Monospace font |
| `.is-skeleton-pulsing` | Pulsing loading animation |
| `.is-density-compact` | Tight table row padding |
| `.is-density-comfortable` | Relaxed table row padding |

---

## Common Spacing Helpers

Bulma uses a `0–6` scale. Add to any element.

| Prefix | What it does |
|---|---|
| `m-{0–6}` | All-direction margin |
| `p-{0–6}` | All-direction padding |
| `mt-{0–6}` | Margin top |
| `mb-{0–6}` | Margin bottom |
| `ml-{0–6}` | Margin left |
| `mr-{0–6}` | Margin right |
| `mx-{0–6}` | Margin left + right |
| `my-{0–6}` | Margin top + bottom |
| `pt-{0–6}` / `pb-{0–6}` | Padding top / bottom |

---

## Copy-Paste Snippets

### Tinted sidebar with collapsible section

```html
<nav class="menu has-tint">
  <p class="menu-label">
    <button type="button" class="menu-label-toggle with-caret"
            aria-expanded="true" aria-controls="nav-section-1">
      Section Name
    </button>
  </p>
  <ul id="nav-section-1" class="menu-list">
    <li><a class="is-active" href="#">Active Page</a></li>
    <li><a href="#">Other Page</a></li>
  </ul>
  <hr class="menu-divider" />
</nav>
```

```js
// Collapse toggle (add once to page)
document.querySelectorAll('.menu-label-toggle').forEach(btn => {
  btn.addEventListener('click', () => {
    const list = document.getElementById(btn.getAttribute('aria-controls'));
    const open = btn.getAttribute('aria-expanded') === 'true';
    btn.setAttribute('aria-expanded', open ? 'false' : 'true');
    list?.classList.toggle('is-collapsed', open);
  });
});
```

### Metric card

```html
<div class="card">
  <div class="card-content">
    <p class="is-size-7 has-text-weight-medium" style="color: var(--bulma-text-weak);">Revenue</p>
    <p class="is-size-3 has-text-weight-bold has-text-tabular">$14,200</p>
  </div>
</div>
```

### Status tag / chip

```html
<span class="tag is-success">Active</span>
<span class="tag is-warning">Pending</span>
<span class="tag is-danger">Failed</span>
```

### Colored notification

```html
<div class="notification is-primary">
  Your changes have been saved.
  <button class="delete"></button>
</div>
```

### Custom element using theme tokens

```css
.my-callout {
  padding: 1rem;
  background: hsla(var(--m3c-primary-hsl), 0.07);
  border-left: 3px solid hsl(var(--m3c-primary-hsl));
  border-radius: var(--bulma-radius);
  transition: background var(--m3-duration-short) var(--m3-easing-standard);
}
```

---

## Dark Mode

Add `data-theme="dark"` to `<html>` to activate dark mode:

```html
<html data-theme="dark">
```

All theme colors automatically swap to M3 dark palette.
