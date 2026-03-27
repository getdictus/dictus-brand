# Dictus Brand Assets

Single source of truth for Dictus brand assets across all platforms.

## Structure

```
dictus-brand/
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

| Name             | Hex       |
|------------------|-----------|
| Background       | `#0A1628` |
| Accent           | `#3D7EFF` |
| Accent highlight | `#6BA3FF` |
| Surface          | `#161C2C` |
| Recording        | `#EF4444` |
| Smart mode       | `#8B5CF6` |
| Success          | `#22C55E` |

## Logo

3 vertical waveform bars (heights: 18pt / 42pt / 27pt).
Center bar = gradient `#6BA3FF` to `#2563EB`.
Side bars = white at 45% and 65% opacity.
Icon background = gradient `#0D2040` to `#071020` at 135deg.
Bar border radius = 4.5pt.

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
