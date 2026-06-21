# XMB Launcher Themes

Theme repository for the XMB Launcher — an Android TV home screen inspired by the PS3 XrossMediaBar.

## Structure

A theme is a `.xmbtheme` ZIP file containing a single `theme.json` at the root.

The index file `themes.json` lists available themes — the launcher fetches this to populate the Online Themes browser.

## Creating a Theme

Start from the Midnight Red theme or the defaults below. All fields are optional — omitted values fall back to the Default theme's built-in settings.

### `theme.json` Reference

```jsonc
{
  "name": "My Theme",
  "author": "Your Name",
  "version": 1,

  // ===== COLORS =====
  "colors": {
    "accent": "#00d4ff",        // Primary accent (highlights, headers)
    "accentDim": "#0064c8",     // Dimmed accent (separators)
    "textPrimary": "#ffffff",   // Main text color
    "textSecondary": "#a0c8dcff", // Secondary/subtitle text
    "textAccent": "#c800d4ff",  // Accent-colored text (status bar)
    "categoryLabel": "#b4c8dcff", // Category label text
    "categoryFadeAlpha": 0.5,   // Fade opacity of non-selected categories
    "categoryIconScale": 0.5,   // Scale of non-selected category icons
    "statusBg": "#b4000000"     // Status bar background
  },

  // ===== CATEGORY STRIP =====
  "categoryStrip": {
    "background": "#c8050514",  // Background color (category strip at top)
    "iconSizeDp": 36,           // Category icon size
    "labelSizeSp": 10           // Category label text size
  },

  // ===== ITEMS (app list) =====
  "items": {
    "spacingDp": 72,            // Vertical spacing between items
    "rowHeightDp": 96,          // Height of each item row
    "selectedYDp": 230,         // Y position of the selection crossbar
    "iconSizeDp": 28,           // Item icon size within the strip
    "iconTextSizeSp": 16,       // Icon label text size
    "labelSizeSp": 11,          // Item label text size
    "indicatorColor": "#dc00d4ff", // Selection indicator color
    "indicatorWidthDp": 2,
    "indicatorHeightDp": 36,
    "stripBackground": "#c8050514", // Background of the item strip area
    "stripWidthDp": 120,        // Width of the item strip panel
    "labelMarquee": true        // Whether item labels scroll when focused
  },

  // ===== CROSSBAR =====
  "crossbar": {
    "color": "#3c00d4ff",       // Crossbar line color
    "heightDp": 2               // Crossbar line thickness
  },

  // ===== SELECTION OVERLAY =====
  "selection": {
    "gradient": ["#4678dcff", "#1900d4ff", "#00000000"],
    "lineColor": "#dc00d4ff",   // Bottom line on the selection overlay
    "lineHeightDp": 3,          // Bottom line thickness
    "shadowColor": "#a0b4dcff", // Drop shadow color
    "shadowRadius": 10          // Drop shadow radius
  },

  // ===== CONTEXT MENU =====
  "contextMenu": {
    "background": "#eb0f0f1e",  // Menu card background
    "borderColor": "#5000d4ff", // Menu card border
    "borderRadiusDp": 16,       // Menu card corner radius
    "selectionColor": "#3c00d4ff", // Highlighted option background
    "titleColor": "#c800d4ff",  // Menu title text color
    "cancelColor": "#b4ff6464"  // Cancel/Back option text color
  },

  // ===== ANIMATED WAVE BACKGROUND =====
  "wave": {
    "layers": [
      {
        "color": "#1c0064c8",       // ARGB hex color
        "amplitude": 0.35,          // Wave height (0-1)
        "frequency": 0.018,         // Wave frequency
        "speed": 0.30,              // Animation speed
        "verticalAnchor": 0.50      // Vertical center point (0-1)
      }
      // ... add up to 4 layers for depth
    ]
  },

  // ===== CATEGORY GRADIENTS =====
  // Background gradient for each category strip cell
  "categoryGradients": {
    "Settings": ["#1a1a2e", "#16213e"],
    "Music": ["#2d1b3d", "#1a1a2e"],
    "Video": ["#1b2d1b", "#1a1a2e"],
    "Photos": ["#2d2b1b", "#1a1a2e"],
    "Games": ["#1b1b2d", "#1a1a2e"],
    "Network": ["#1b2d2d", "#1a1a2e"]
  },

  // ===== CUSTOM FONT =====
  // Path to a .ttf file inside the ZIP (e.g. "fonts/myfont.ttf")
  "font": ""
}
```

### Including Assets

Place files (fonts, sounds, icons) inside the ZIP alongside `theme.json`:

```
my-theme.xmbtheme
├── theme.json
└── fonts/
    └── myfont.ttf
```

> **Note:** Sound and icon overrides are defined in `theme.json` but the referenced files must be bundled in the ZIP. This feature is not yet implemented in the launcher — tracked for future release.

## Publishing

1. ZIP your `theme.json` (and any assets) as a `.xmbtheme` file
2. Upload to a public URL (e.g. GitHub Releases)
3. Submit a PR adding an entry to `themes.json`:

```json
{
  "name": "My Theme",
  "author": "Your Name",
  "description": "Brief description of the theme",
  "url": "https://example.com/path/to/My Theme.xmbtheme"
}
```

> The URL must be URL-encoded (spaces as `%20`).

## Color Format

All colors use hex `AARRGGBB`:
- `AA` = alpha (00 = transparent, ff = opaque)
- `RR` = red
- `GG` = green
- `BB` = blue

Examples: `#ff4444` (opaque red), `#3c00d4ff` (semi-transparent bright blue), `#00000000` (fully transparent black).
