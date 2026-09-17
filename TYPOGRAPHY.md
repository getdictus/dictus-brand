# Dictus Typography

Typography follows each product surface. DM Sans is not a universal requirement for Dictus interfaces.

## Platform conventions

| Surface | Current convention |
| --- | --- |
| iOS app | System fonts. Dedicated title styles use the rounded design; body text, captions, and keyboard keys use the default system design. The onboarding “Dictus” wordmark uses the rounded system font at 42 pt, ultraLight. |
| Desktop app | System sans-serif stack, with the rendered family depending on the OS. The “Dictus” wordmark uses `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif` at weight 600. Recording overlay text also uses a system stack. |
| Android app and keyboard | DM Sans, bundled as five TTF files, supplies nine styles in the shared theme. Some Material styles, including `headlineSmall`, are not overridden; explicitly monospace technical text is another exception. |
| Website | DM Sans is loaded through Next.js and applied globally. The “Dictus” wordmark uses weight 200 and letter spacing of `-0.04em`. |
| Existing marketing assets | DM Sans is used in the website's Remotion videos and for headings/body copy in the iOS App Store screenshot template. DM Mono is used for terminal text in the videos and eyebrow labels in the screenshot template. |

DM Mono is also configured on the website, but the audit found no use of its font token in site components. It is not the default body font.

## Brand and production guidance

- Match the website's “Dictus” wordmark with DM Sans at weight 200 and letter spacing of `-0.04em`. The previous kit's lowercase spelling is not a universal brand rule; app wordmarks follow the platform-specific conventions above.
- Match the actual platform typography when reproducing app interfaces in screenshots or videos.
- Choose promotional headlines and the closing signature separately from embedded app UI. DM Sans remains the existing marketing reference; a replacement has not been selected for the new promo.
- The three-bar logo symbol is SVG geometry and does not depend on any font.
- Changing the brand reference alone does not migrate Android, the website, or existing marketing assets. Their font loaders also do not require a manual font installation on the production Mac; an editor such as After Effects needs access to whichever font is chosen for editable text.

## Source references

Based on the [local typography audit dated 17 September 2026](../dictus-promo/AUDIT-TYPOGRAPHIE.md). This documents inspected source code, not a verification of installed or published binaries. Links assume sibling repositories under the same parent directory; commit identifiers and audit scope are recorded in the audit.

- **iOS:** [shared typography](../dictus/DictusCore/Sources/DictusCore/Design/DictusTypography.swift), [onboarding wordmark](../dictus/DictusApp/Onboarding/WelcomePage.swift), [keyboard theme](../dictus/DictusKeyboard/Vendored/Models/Theme.swift).
- **Desktop:** [app styles](../dictus-desktop/src/App.css), [wordmark](../dictus-desktop/src/components/icons/DictusLogo.tsx), [recording overlay](../dictus-desktop/src/overlay/RecordingOverlay.css).
- **Android:** [typography](../dictus-android/core/src/main/java/dev/pivisolutions/dictus/core/theme/DictusTypography.kt), [shared theme](../dictus-android/core/src/main/java/dev/pivisolutions/dictus/core/theme/DictusTheme.kt), [keyboard theme usage](../dictus-android/ime/src/main/java/dev/pivisolutions/dictus/ime/ui/KeyboardScreen.kt).
- **Website:** [font loading](../dictus-website/src/app/%5Blocale%5D/layout.tsx), [font tokens](../dictus-website/src/app/globals.css), [wordmark](../dictus-website/src/components/Nav/Logo.tsx).
- **Marketing:** [Remotion composition](../dictus-website/video/src/compositions/DictusPromo.tsx), [terminal](../dictus-website/video/src/components/ClaudeCodeTerminal.tsx), [App Store screenshot template](../dictus/assets/appstore/screenshots.html).
