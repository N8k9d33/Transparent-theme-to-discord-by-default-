#Discord-theme

A quick guide on how to customize and use this theme. 

*(Here is a quick preview of what you can achieve)*

<p align="center">
  <img width="100%" alt="Discord Theme Preview" src="https://github.com/user-attachments/assets/0360d6e4-a726-4385-a94a-705c494709be" />
</p>

---


# Customization Guide – (when they come up with a name)

What you can change in the theme and where to find it. I describe locations by the **comment name** above each section (line numbers shift with every edit). In your editor, the easiest way to find a setting is `Ctrl+F` and the variable name.

## How to apply changes

1. Open the `.theme.css` file in any editor (Notepad, VS Code).
2. Change the value and save the file (`Ctrl+S`).
3. Reload Discord with `Ctrl+R`. With BetterDiscord or Vencord, changes often apply automatically after saving.

> Only change what comes **after the colon**. Don't remove the semicolon `;` at the end of the line.

---

## 1. Main settings (very top of the file)

The `:root { ... }` block at the top. This is where you will change things most often.

| Variable | Default | What it does | Example |
|---|---|---|---|
| `--my-text-color` | `#ff2a85` | Text color across all of Discord | `#ffffff` (white), `#ffb3d9` (light pink) |
| `--my-text-brightness` | `100%` | Text brightness (does not affect backgrounds) | `70%` = darker |
| `--my-muted-brightness` | `78%` | Brightness of secondary text (timestamps, descriptions). `100%` = same as normal text | `100%` |
| `--my-glass-color` | `70, 35, 110` | Color of the glass panels in **R, G, B** format | `20, 20, 30` (dark navy) |
| `--my-glass-opacity` | `0.04` | Panel visibility: `0` = invisible, `1` = solid | `0.12` |
| `--my-glass-blur` | `3px` | Blur of the background behind the panels | `10px` |

Tips:
- Set the text color as a **hex** value with `#` (you can pick colors on [RapidTables](https://www.rapidtables.com/web/color/RGB_Color.html)).
- Set the glass color as **three numbers 0–255 separated by commas**, without `#` and without `rgb()`.
- With the default `--my-glass-opacity: 0.04` the glass color is almost invisible. Raise opacity to `0.10–0.15` to see it.
- If text is hard to read on a bright background, increase `--my-glass-opacity` or `--my-glass-blur`.

---

## 2. Background (image)

The `body { ... }` block, the `--background-image-url` line.

```css
--background-image-url: url('https://your-link.com/image.png');
```

- Replace `https://examplelink.com` with a **direct link to the file** (ending in e.g. `.png`, `.jpg`, `.webp`), not a link to a web page containing the image.
- Keep `url('...')` and the quotes.
- The image is stretched to cover the whole screen (`cover`) and centered. You can change this in the `Background image` section (`background-size`, `background-position`).
- The `examplelink.com` placeholder is not a real image, so you won't see a background until you replace it.
- Remember, you must select "Allow" to enable it to work. <img width="723" height="277" alt="obraz" src="https://github.com/user-attachments/assets/23a9c2c2-6ff1-424e-8e2a-891bd0355c2c" />

---

## 3. Look and layout (`body` block)

| Variable | Default | What it does |
|---|---|---|
| `--font` | `'figtree'` | Font. Must be installed on your system, e.g. `'Segoe UI'` |
| `--gap` | `12px` | Spacing between panels |
| `--blur-amount` | `22px` | Panel blur strength (depends on Midnight) |
| `--border-thickness` | `1px` | Border thickness |
| `--animations` | `on` | Animations: `on` or `off` |
| `--small-user-panel` | `on` | Compact user panel at the bottom |
| `--custom-window-controls` | `on` | Custom window buttons (close, minimize) |
| `--window-control-size` | `14px` | Size of those buttons |
| `--custom-chatbar` | `off` | Custom style for the message input bar |
| `--chatbar-height` | `47px` | Chat bar height (works with `--custom-chatbar: on`) |
| `--dms-icon-svg-url` | moon icon | Icon of the direct messages button |

---

## 4. Accent and status colors

The `:root, .theme-dark, .theme-light { ... }` block, section `Midnight & Glass theme settings`.

| Variable | Default | What it changes |
|---|---|---|
| `--accent-1` … `--accent-5` | shades of cyan | Accent color: buttons, links, highlights (1 = lightest, 5 = darkest) |
| `--accent-new` | `#ff4f8b` | "New" marker |
| `--online` | `#4ee7a8` | Status: online |
| `--dnd` | `#ff4f8b` | Status: do not disturb |
| `--idle` | `#ffd166` | Status: idle |
| `--streaming` | `#bd8cff` | Status: streaming |
| `--offline` | `rgba(235,242,255,0.72)` | Status: offline |
| `--mention`, `--reply` | gradients | Highlight of mentions and replies (color inside `rgba(...)`) |

To change the whole color mood, the easiest way is to replace the five `--accent-1…5` colors with shades of a single color, from light to dark.

---

## 5. Borders and hover

In the same section:

| Variable | What it changes |
|---|---|
| `--border`, `--border-light` | Border color |
| `--border-hover` | Border color on hover |
| `--hover`, `--active`, `--active-2` | Highlight of elements on hover and click (white with low opacity) |
| `--message-hover` | Highlight of a message on hover |
| `--magic-glass-border` | Border of the glass panels (invisible by default – set e.g. `rgba(255,255,255,0.1)`) |

---

## 6. Individual elements (rules at the bottom of the file)

Here you edit colors directly inside the rules. Search by the comment name.

| Comment in file | What it changes | What you can edit |
|---|---|---|
| `Search and chat bars` | Search box and message input | `border-radius: 14px` (rounding), `blur(20px)` (blur) |
| `Tooltips` | Hover tooltips | Background color `rgba(18, 22, 38, 0.68)`, border, `padding` |
| `Context menus and dialogs` | Right-click menus and dialogs | Background comes from `--background-floating` (`rgba(8, 10, 18, 0.88)`) – lower the last number to make it more transparent |
| `Attachments and embed cards` | Attachments and link previews | Border and blur |
| `Notifications / Badges` | Notification counters | `color: #c9fbff`, border and glow in `rgba(120, 230, 255, ...)` |
| `User popouts and profiles` | User profile popups | Colors `#232428` (outer) and `#2b2d31` (inner) |
| `Settings window` | Discord settings | `#313338` (content), `#2b2d31` (side menu), `#404249` (selected item) |
| `Small extras` | Scrollbar and text selection | `rgba(...)` colors of the scrollbar and `::selection` |

---

## 7. Common problems

- **Nothing changed after editing:** save the file and press `Ctrl+R` in Discord.
- **No background:** check that the link points directly to an image file, is wrapped in `url('...')`, and is not still `examplelink.com`.
- **Unreadable text:** raise `--my-glass-opacity` (e.g. `0.12`) or change `--my-text-color` to a lighter one.
- **Some panels went back to the default look after a Discord update:** the theme relies on Discord's internal class names (e.g. `container__2637a`), which Discord changes from time to time. This is not a mistake in your settings.
- **Font doesn't change:** the font from `--font` must be installed on your system.
- **Something broke after editing:** most often a semicolon `;`, quote, or bracket is missing. Undo your last change (`Ctrl+Z`).

  
## 8. Fast install
- download from my release: https://github.com/N8k9d33/Transparent-theme-to-discord-by-default-/releases
- put to 
