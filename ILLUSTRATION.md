# Dictus Illustration

Dictus has one illustrated character, the walking woman, and one hand-lettered line, the marker line. This page describes only what the linked files show. No images are copied here: the files stay in the product repositories. Links point to `develop`; dictus-website is a private repository.

## The walking woman

### What she looks like

As drawn in the App Store hero, the onboarding intro and the website hero:
- a jaw-length, dark navy bob with lighter blue highlights and a fringe; mouth open, speaking;
- a bright blue long-sleeved top with a V-neck, navy trousers and white trainers;
- a beige tote bag held by its handles in one hand, a navy phone held out in front of her mouth in the other;
- mid-stride, walking to the right, on a light grey tiled pavement with a soft shadow under her (App Store hero and intro scene A);
- flat colours with a thick dark outline, in the brand blues and navy.

Her voice is always drawn going from her lips towards the phone or the text. Depending on the file, it appears as blue strokes or as small bars of the Dictus waveform.

### Where she appears

| Surface | Files | What the file shows |
| --- | --- | --- |
| App Store hero, slide 1 (V16-B) | [`dictus-ios/assets/appstore/art/v16-B/`](https://github.com/getdictus/dictus-ios/tree/develop/assets/appstore/art/v16-B): `hero.png` and `hero-{de-DE,es-ES,fr-FR}.png`, built by [`heroWalk16.ts`](https://github.com/getdictus/dictus-ios/blob/develop/assets/appstore/art/v16-B/heroWalk16.ts) | Her, walking. Three blue voice strokes (`#6BA3FF`, `#3D7EFF`, `#2563EB`) leave her lips and arch to the right, with her words hand-lettered in capitals along the top stroke (English file: "THANKS FOR THE NOTES…"). The strokes are cut at the slide's right edge. |
| Onboarding intro, iOS | [`dictus-ios/assets/onboarding/intro/`](https://github.com/getdictus/dictus-ios/tree/develop/assets/onboarding/intro) ([README](https://github.com/getdictus/dictus-ios/blob/develop/assets/onboarding/intro/README.md), [issue #667](https://github.com/getdictus/dictus-ios/issues/667)) | Three looping scenes, light and dark, one render per language. **A**, walking: her voice goes into the phone as small waveform bars, and a chat reply writes itself. **B**, the metro: she stands in a rocking carriage with no network, and a mail draft writes itself. **C**, the keyboard: a full dictation on the drawn iPhone. |
| Onboarding intro, Android | [`OnboardingIntroScene.kt`](https://github.com/getdictus/dictus-android/blob/develop/app/src/main/java/dev/pivisolutions/dictus/onboarding/OnboardingIntroScene.kt), [`IntroVideoView.kt`](https://github.com/getdictus/dictus-android/blob/develop/app/src/main/java/dev/pivisolutions/dictus/onboarding/IntroVideoView.kt) | The same three scenes, ported from iOS and re-encoded in H.264 because Android phones are not required to decode HEVC Main 10 (`app/src/main/res/raw/intro_*.mp4`). |
| Google Play listing | [`dictus-android/tools/play-listing/art/`](https://github.com/getdictus/dictus-android/tree/develop/tools/play-listing/art) | The App Store V16-B hero, unchanged ([README](https://github.com/getdictus/dictus-android/blob/develop/tools/play-listing/README.md)). |
| Website hero | [`dictus-website/public/images/hero/walker@2x.webm`](https://github.com/getdictus/dictus-website/blob/develop/public/images/hero/walker%402x.webm) (VP9 with alpha), [`walker@2x-hevc-alpha.mov`](https://github.com/getdictus/dictus-website/blob/develop/public/images/hero/walker%402x-hevc-alpha.mov) (HEVC with alpha, Safari), [`walker@2x.webp`](https://github.com/getdictus/dictus-website/blob/develop/public/images/hero/walker%402x.webp) (still, frame 0) | Her alone on a transparent ground, walking. The site draws the rest in SVG ([`HeroScene.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Hero/HeroScene.tsx), [`strokes.ts`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Hero/strokes.ts)): three felt-pen strokes in light, mid and deep blue carry her voice into the Dictus pill, and the result is written in Kalam. |

### One character

The App Store hero V16-B is drawn with the intro's own code ([`assets/onboarding/intro/src/woman.ts`](https://github.com/getdictus/dictus-ios/blob/develop/assets/onboarding/intro/src/woman.ts)), posed as scene A's first frame. The listing's first picture and the app's first screen therefore show the same woman ([`heroWalk16.ts`](https://github.com/getdictus/dictus-ios/blob/develop/assets/appstore/art/v16-B/heroWalk16.ts), [issue #758](https://github.com/getdictus/dictus-ios/issues/758)). A change to `woman.ts` changes slide 1 the next time it is rebuilt. New art of her reuses that code, "not a copy of it", as `heroWalk16.ts` puts it.

The art is code-drawn with the [anidoodle](https://github.com/alexgreensh/anidoodle) engine and is deterministic: a frame depends only on its number and its appearance (intro README, "Determinism").

## The hand-lettered marker line

Text inside the illustrations is hand-lettered in a **marker line**, not set in a font. The source is [`assets/onboarding/intro/src/handLettering.ts`](https://github.com/getdictus/dictus-ios/blob/develop/assets/onboarding/intro/src/handLettering.ts):
- each glyph is a set of single marker strokes in a unit box (x-height 1, capitals and ascenders 1.6, descenders to −0.6);
- text is written letter by letter, in time with the voice;
- accents are composed on the base letter (acute, grave, circumflex, diaeresis, cedilla);
- the same text can lie flat on a card or in perspective on the drawn phone.

The intro stills show it in the chat bubbles and the mail draft, in lowercase handwriting. The App Store hero letters her words in capitals along the voice stroke.

Each language has its own render, so the art speaks the device's language. Every line is in [`src/strings.ts`](https://github.com/getdictus/dictus-ios/blob/develop/assets/onboarding/intro/src/strings.ts). A character with no glyph stops the render ([issue #771](https://github.com/getdictus/dictus-ios/issues/771), intro README "One render per language").

The marker line is not Kalam. Kalam is a font, used as a typographic accent (see [Typography](TYPOGRAPHY.md)); the marker line is drawn, and lives only inside the illustrations.

## Grounds

The intro videos are rendered on the onboarding's page colours, light `#F2F2F7` and dark `#0A1628`, matched exactly so the video edge does not show (intro README).
