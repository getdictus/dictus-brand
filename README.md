# Dictus Brand Assets

Single source of truth for Dictus brand assets across all platforms.

## Structure

```
dictus-brand/
├── TYPOGRAPHY.md               # Typefaces, wordmark, licences
├── MOTION.md                   # Durations, easings, waveform motif, reduced motion
├── ILLUSTRATION.md             # The walking woman and the hand-lettered marker line
├── source/                     # Source files (SVG + brand kit)
│   ├── appicon-light.svg       # App icon — light mode
│   ├── appicon-dark.svg        # App icon — dark mode
│   ├── appicon-tinted.svg      # App icon — tinted/monochrome
│   ├── logo-standalone.svg     # Logo bars only (transparent bg, for dark surfaces)
│   ├── logo-standalone-dark.svg  # Same as above (alias for clarity)
│   ├── logo-standalone-light.svg # Logo bars for light surfaces
│   └── dictus-brand-kit.html   # Full brand reference (colors, gradients)
├── ios/
│   └── AppIcon.appiconset/     # Drop into Xcode Assets.xcassets
│       ├── AppIcon-1024.png
│       ├── AppIcon-1024-dark.png
│       ├── AppIcon-1024-tinted.png
│       └── Contents.json
├── android/
│   ├── drawable/               # Vector Drawables for Adaptive Icons
│   │   ├── ic_launcher_foreground.xml
│   │   ├── ic_launcher_background.xml
│   │   └── ic_launcher_monochrome.xml
│   ├── mipmap-mdpi/            # 48x48
│   ├── mipmap-hdpi/            # 72x72
│   ├── mipmap-xhdpi/           # 96x96
│   ├── mipmap-xxhdpi/          # 144x144
│   ├── mipmap-xxxhdpi/         # 192x192
│   └── play-store/             # 512x512 (Play Store listing)
└── web/
    ├── favicon.ico             # Multi-size favicon
    ├── favicon-16.png
    ├── favicon-32.png
    ├── apple-touch-icon.png    # 180x180
    ├── icon-192.png            # PWA icon
    ├── icon-512.png            # PWA icon
    ├── appicon.svg             # Full app icon as SVG
    ├── logo.svg                # Standalone logo (dark surfaces)
    ├── logo-dark.svg           # Standalone logo (dark surfaces)
    ├── logo-light.svg          # Standalone logo (light surfaces)
    └── site.webmanifest        # PWA manifest
```

## Brand Colors

Values from the product code: [`DictusColors.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusCore/Sources/DictusCore/Design/DictusColors.swift) (iOS), [`DictusColors.kt`](https://github.com/getdictus/dictus-android/blob/develop/core/src/main/java/dev/pivisolutions/dictus/core/theme/DictusColors.kt) (Android) and [`globals.css`](https://github.com/getdictus/dictus-website/blob/develop/src/app/globals.css) (website, private repo).

### Accent and state colours

| Name             | Hex       | Use |
|------------------|-----------|-----|
| Accent           | `#3D7EFF` | Brand blue: mic, links, icons, large text |
| Accent highlight | `#6BA3FF` | Waveform centre bars, logo bar gradient start |
| Button blue      | `#2563EB` | Filled buttons, badges and icon tiles (gradient `#2563EB` → `#1D4ED8`) |
| Recording        | `#EF4444` | Recording state |
| Success          | `#22C55E` | Success state |

### Backgrounds and surfaces

| Role | Light | Dark |
|------|-------|------|
| Background | `#F2F2F7` | `#0A1628` |
| Surface    | `#FFFFFF` | `#161C2C` |
| Website secondary ground | `#EFF1F5` | `#111827` |

iOS declares the background and surface pairs in `DictusColors.swift` (`dictusBackground`, `dictusSurface`). The website declares the same pairs plus the secondary ground as `--theme-bg-primary`, `--theme-surface` and `--theme-bg-secondary` in `globals.css`.

### Button blue and contrast

White text on the accent `#3D7EFF` measures 3.73:1, under WCAG AA for normal text. Filled buttons, badges and icon tiles therefore use `#2563EB` with white text (5.17:1; 6.70:1 on the gradient end `#1D4ED8`), drawn as a 135° gradient `#2563EB` → `#1D4ED8`. Navy is no longer used for buttons: it is kept for the logo tile.

Other rules from the same source:
- small text on white or grey never uses `#3D7EFF`; it uses `#1F5FE0` (5.57:1 on white);
- white on `#3D7EFF` only at large sizes (24 px regular or 18.66 px bold and up);
- body text on navy uses `#B8C4D9` (10.3:1).

Source: dictus-website [PR #127](https://github.com/getdictus/dictus-website/pull/127) (merged 2 November 2026) for [issue #118](https://github.com/getdictus/dictus-website/issues/118), contrast notes and `.button-blue` in [`globals.css`](https://github.com/getdictus/dictus-website/blob/develop/src/app/globals.css).

### Smart Modes are blue: violet `#8B5CF6` is retired

Smart Modes use the brand blues (`#3D7EFF`, `#6BA3FF`), like the rest of the product. Violet `#8B5CF6` is no longer a brand colour: never a fill, a ring or a badge.

- **iOS** removed it in commit [`cade31cf5`](https://github.com/getdictus/dictus-ios/commit/cade31cf5) ([issue #789](https://github.com/getdictus/dictus-ios/issues/789)): "Smart Modes are blue, never purple". The `dictusSmartMode` token is gone; its callers use `dictusAccent`. The armed Smart Mode mark on the mic is the mode's glyph in accent blue on a white disc ([`AnimatedMicButton.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusCore/Sources/DictusCore/Design/AnimatedMicButton.swift)).
- **Website:** [`scripts/check-no-violet.mjs`](https://github.com/getdictus/dictus-website/blob/develop/scripts/check-no-violet.mjs) fails on any violet or purple colour in `src/` (a local check, not wired into CI).
- **Android** still declares a leftover `SmartMode = Color(0xFF8B5CF6)` token, mapped to the Material `tertiary` colour ([`DictusColors.kt`](https://github.com/getdictus/dictus-android/blob/develop/core/src/main/java/dev/pivisolutions/dictus/core/theme/DictusColors.kt), [`DictusTheme.kt`](https://github.com/getdictus/dictus-android/blob/develop/core/src/main/java/dev/pivisolutions/dictus/core/theme/DictusTheme.kt)). It is to be removed there.

## Logo

3 vertical waveform bars (heights: 18pt / 42pt / 27pt).
Center bar = gradient `#6BA3FF` to `#2563EB`.
Side bars = white at 45% and 65% opacity.
Icon background = gradient `#0D2040` to `#071020` at 135deg.
Bar border radius = 4.5pt.

## Typography

DM Sans is the brand typeface (Android, website, and iOS since November 2026, paywall first). DM Mono sets section eyebrows and technical labels on the website; Kalam is the handwritten accent face. Desktop stays on the system stack. The wordmark is "Dictus" in DM Sans 200 at `-0.04em`. See [Typography](TYPOGRAPHY.md) for platform details, usage rules and licences.

## Motion and illustration

- [Motion](MOTION.md): durations, easings, the waveform motif and how each product handles reduced motion.
- [Illustration](ILLUSTRATION.md): the walking-woman character and the hand-lettered marker line.

## Marketing assets

These live in the product repositories. They are linked here, not copied.

| Asset | Where |
|-------|-------|
| iOS onboarding intro scenes (three looping videos, light and dark, per language) | [`dictus-ios/assets/onboarding/intro/`](https://github.com/getdictus/dictus-ios/tree/develop/assets/onboarding/intro), with its [README](https://github.com/getdictus/dictus-ios/blob/develop/assets/onboarding/intro/README.md) ([issue #667](https://github.com/getdictus/dictus-ios/issues/667)) |
| App Store captures (de-DE, en-GB, es-ES, fr-FR) | [`dictus-ios/assets/appstore/captures/`](https://github.com/getdictus/dictus-ios/tree/develop/assets/appstore/captures) |
| App Store hero art (current: V16-B) | [`dictus-ios/assets/appstore/art/v16-B/`](https://github.com/getdictus/dictus-ios/tree/develop/assets/appstore/art/v16-B) |
| Google Play listing texts and images | [`dictus-android/fastlane/metadata/android/`](https://github.com/getdictus/dictus-android/tree/develop/fastlane/metadata/android) |
| Google Play image generator | [`dictus-android/tools/play-listing/`](https://github.com/getdictus/dictus-android/tree/develop/tools/play-listing) |
| Promo films (After Effects and Remotion) | [`getdictus/dictus-promo`](https://github.com/getdictus/dictus-promo) (private repository) |

## Usage

### Android
Copy `android/drawable/` into `app/src/main/res/drawable/` and `android/mipmap-*/` into `app/src/main/res/`.

### iOS
Copy `ios/AppIcon.appiconset/` into your Xcode `Assets.xcassets/`.

### Web
Copy `web/` contents into your public/static directory. Add to HTML:
```html
<link rel="icon" href="/favicon.ico" sizes="any">
<link rel="icon" href="/appicon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="/apple-touch-icon.png">
<link rel="manifest" href="/site.webmanifest">
```
