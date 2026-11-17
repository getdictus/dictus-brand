# Dictus Typography

DM Sans is the Dictus brand typeface. DM Mono sets eyebrows and technical labels, and Kalam is the handwritten accent face. Desktop stays on the system font stack.

Every statement below links to the product source it comes from. Links point to the `develop` branch of each repository; dictus-desktop and dictus-promo have no `develop` branch, so their links point to `main`. dictus-website and dictus-promo are private repositories.

## Typefaces

| Typeface | Role | Where it ships today |
| --- | --- | --- |
| **DM Sans** | Brand typeface: UI, headlines, body, wordmark | Android app and keyboard, website, iOS paywall. The rest of iOS follows ([issue #918](https://github.com/getdictus/dictus-ios/issues/918), open). |
| **DM Sans, display cut** (`opsz` axis) | Large headlines | Website hero headline |
| **DM Mono** | Section eyebrows and technical labels | Website |
| **Kalam** 700 | Handwritten accent, decorative only | Website hero result phrase. It will come back in visuals and press. |
| System stack | Desktop app UI | Desktop app |

## By platform

### iOS

- DM Sans has been bundled in the app since 6 November 2026 (commit `25ceb769f`, refs [#913](https://github.com/getdictus/dictus-ios/issues/913); merged with PR [#920](https://github.com/getdictus/dictus-ios/pull/920)). Five static faces live in [`DictusApp/Fonts/`](https://github.com/getdictus/dictus-ios/tree/develop/DictusApp/Fonts): ExtraLight, Regular, Medium, SemiBold and Bold. They are loaded through `Font.dmSans(_:size:relativeTo:)` in [`Font+DMSans.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusApp/Extensions/Font%2BDMSans.swift), which scales with Dynamic Type.
- Today only the paywall uses it ([`PaywallView.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusApp/Views/PaywallView.swift), [`PaywallSalesSections.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusApp/Views/PaywallSalesSections.swift)). Moving the whole app to DM Sans is [issue #918](https://github.com/getdictus/dictus-ios/issues/918), still open.
- Until #918 lands, the rest of iOS keeps the system fonts. Headings use SF Pro Rounded (`.system(…, design: .rounded)` in [`DictusTypography.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusCore/Sources/DictusCore/Design/DictusTypography.swift)), and the keyboard has its own theme ([`Theme.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusKeyboard/Vendored/Models/Theme.swift)).

### Android

- DM Sans is bundled as five TTF files in [`core/src/main/res/font/`](https://github.com/getdictus/dictus-android/tree/develop/core/src/main/res/font). It is set on nine text styles of the shared theme in [`DictusTypography.kt`](https://github.com/getdictus/dictus-android/blob/develop/core/src/main/java/dev/pivisolutions/dictus/core/theme/DictusTypography.kt), used by the app and the keyboard ([`DictusTheme.kt`](https://github.com/getdictus/dictus-android/blob/develop/core/src/main/java/dev/pivisolutions/dictus/core/theme/DictusTheme.kt), [`KeyboardScreen.kt`](https://github.com/getdictus/dictus-android/blob/develop/ime/src/main/java/dev/pivisolutions/dictus/ime/ui/KeyboardScreen.kt)).
- The Google Play listing images also use DM Sans ([`tools/play-listing/fonts/`](https://github.com/getdictus/dictus-android/tree/develop/tools/play-listing/fonts)).

### Website

- **DM Sans** is loaded with `next/font` and applied to the whole site ([`layout.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/app/%5Blocale%5D/layout.tsx), `--font-sans` in [`globals.css`](https://github.com/getdictus/dictus-website/blob/develop/src/app/globals.css)).
- **DM Sans display cut:** the hero headline loads DM Sans a second time with its optical-size axis (`axes: ["opsz"]`, `dmSansDisplay` in [`Hero/fonts.ts`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Hero/fonts.ts)) and sets `font-optical-sizing: auto` ([`Hero.module.css`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Hero/Hero.module.css)). At display sizes this draws the tighter cut. The site-wide DM Sans stays without the axis. Use the display cut for large headlines only.
- **DM Mono** (weights 300 and 400, `--font-mono`) sets the section eyebrows: uppercase labels at 13 px, tracking `0.1em`, accent-text colour. Examples are the Keyboard, Languages, Privacy, Pricing and Desktop sections and the blog ([`Keyboard.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Keyboard/Keyboard.tsx), [`ArticleList.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Blog/ArticleList.tsx)). It also sets technical labels: table headers, footer headings, step numbers and the hero card label ([`Pricing.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Pricing/Pricing.tsx), [`Footer.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Footer/Footer.tsx)). It is never the body font.
- **Kalam** is described below.

### Desktop

The desktop app stays on the system stack. The wordmark is drawn in `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif` at weight 600 ([`DictusLogo.tsx`](https://github.com/getdictus/dictus-desktop/blob/main/src/components/icons/DictusLogo.tsx)). The recording overlay uses the same stack ([`RecordingOverlay.css`](https://github.com/getdictus/dictus-desktop/blob/main/src/overlay/RecordingOverlay.css)). No brand font is bundled.

## Kalam, the accent typeface

Kalam is part of the brand as its handwritten **accent**. Today it writes the result phrase in the website hero: the sentence that comes out of the Dictus pill, written letter by letter along a curve ([`HeroScene.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Hero/HeroScene.tsx)). It will come back in visuals and press.

As loaded on the website ([`Hero/fonts.ts`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Hero/fonts.ts)): weight **700** only, `display: swap`, not preloaded, fallback `cursive`.

**Use it for:**
- a short phrase that stands for the result of dictation, the "written" output, inside an illustration or a visual;
- decorative accents in visuals and press material, next to DM Sans.

**Do not use it for:**
- body text, headlines, buttons, navigation or any interface text. It is never the main text;
- the wordmark;
- any text whose meaning would be lost if the face did not load. On the website it is decorative: the hero text says the same thing, and the phrase shows in the fallback face until Kalam loads.

Kalam is not the hand-lettered marker line of the illustrations: that line is drawn stroke by stroke, not set in a font (see [Illustration](ILLUSTRATION.md)).

## Wordmark

The wordmark is **"Dictus"** with a capital D, in **DM Sans weight 200**, letter spacing **`-0.04em`**. Source: the website wordmark in [`Nav/Logo.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Nav/Logo.tsx), next to the squircle three-bar icon.

iOS [issue #918](https://github.com/getdictus/dictus-ios/issues/918) planned a lowercase "dictus" at `-0.03em`, taken from the old brand kit. The brand rule is now the capitalised one above (decision of 15 November 2026).

The three-bar logo symbol is SVG geometry and does not depend on any font.

## Production guidance

- Match the real platform typography when you reproduce app interfaces in screenshots or videos. Today that means SF Pro Rounded headings on iOS outside the paywall, DM Sans on Android, and the system stack on desktop.
- For promotional headlines, use DM Sans (display cut at large sizes). Use DM Mono for eyebrows and labels, and Kalam only as an accent.
- The App Store screenshot template loads DM Sans and DM Mono from Google Fonts ([`screenshots.html`](https://github.com/getdictus/dictus-ios/blob/develop/assets/appstore/screenshots.html)). The website's Remotion videos use DM Sans, with DM Mono for terminal text ([`DictusPromo.tsx`](https://github.com/getdictus/dictus-website/blob/develop/video/src/compositions/DictusPromo.tsx), [`ClaudeCodeTerminal.tsx`](https://github.com/getdictus/dictus-website/blob/develop/video/src/components/ClaudeCodeTerminal.tsx)).
- An editor such as After Effects needs the fonts installed locally for editable text.

## Licences

All three typefaces are licensed under the **SIL Open Font License 1.1**: they may be used, bundled, embedded and redistributed, including with commercial software, but not sold by themselves. Each bundled copy must ship with the copyright notice and the licence text, as dictus-ios and dictus-android do.

| Typeface | Copyright | Licence | Sources |
| --- | --- | --- | --- |
| DM Sans | © 2014 The DM Sans Project Authors | [SIL OFL 1.1](https://openfontlicense.org/open-font-license-official-text/) | [Google Fonts licence file](https://github.com/google/fonts/blob/main/ofl/dmsans/OFL.txt), [font repository](https://github.com/googlefonts/dm-fonts), [copy shipped in dictus-ios](https://github.com/getdictus/dictus-ios/blob/develop/DictusApp/Fonts/OFL.txt), [copy shipped in dictus-android](https://github.com/getdictus/dictus-android/blob/develop/tools/play-listing/fonts/OFL.txt) |
| DM Mono | © 2020 The DM Mono Project Authors | [SIL OFL 1.1](https://openfontlicense.org/open-font-license-official-text/) | [Google Fonts licence file](https://github.com/google/fonts/blob/main/ofl/dmmono/OFL.txt), [font repository](https://github.com/googlefonts/dm-mono) |
| Kalam | © 2014 Indian Type Foundry | [SIL OFL 1.1](https://openfontlicense.org/open-font-license-official-text/) | [Google Fonts licence file](https://github.com/google/fonts/blob/main/ofl/kalam/OFL.txt), [font repository](https://github.com/itfoundry/kalam) |

The website loads all three through `next/font/google` and ships no licence file of its own.

## Sources

The earlier version of this page was based on the [typography audit of 17 September 2026](https://github.com/getdictus/dictus-promo/blob/main/AUDIT-TYPOGRAPHIE.md) (dictus-promo, private). This version was checked against the product repositories on 15–17 November 2026 (`develop` for iOS, Android and the website, `main` for desktop).
