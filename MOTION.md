# Dictus Motion

Motion in Dictus is quick UI feedback plus one shared motif: the recording waveform. Every value below comes from the linked product source. Links point to `develop`; dictus-website is a private repository.

## Durations and easings (website)

Declared once in [`src/app/globals.css`](https://github.com/getdictus/dictus-website/blob/develop/src/app/globals.css). The file describes them as "responsive UI feedback, deliberate travel between resting states".

| Token | Value | Used for |
| --- | --- | --- |
| `--motion-press` | 120 ms | Press on a button (`:active`, `scale(0.97)`). Pressing is quicker than the release. |
| `--motion-fast` | 180 ms | Button hover lift (`translateY(-2px)`), its shadow fade, colour and border changes, and the release after a press |
| `--motion-ui` | 240 ms | Interface state changes: FAQ answers opening and closing, nav background and border, Privacy card opacity |

| Token | Value | Used for |
| --- | --- | --- |
| `--ease-out` | `cubic-bezier(0.23, 1, 0.32, 1)` | Movement: transforms, FAQ open and close. Mirrored for Motion (JS) transitions as `EASE_OUT` in [`src/config/motion.ts`](https://github.com/getdictus/dictus-website/blob/develop/src/config/motion.ts). |
| `--ease-in-out` | `cubic-bezier(0.77, 0, 0.175, 1)` | Travel between two resting states. It is declared in `globals.css`; no component uses it yet. |

Colour, border and opacity changes use plain `ease`, with movement on `--ease-out`.

`src/config/motion.ts` also holds the scroll-driven values of the homepage. Step text fades out in 0.2 s, then in over 0.3 s with an 8 px shift. The Smart Modes cards switch on a spring (`duration: 0.5`, `bounce: 0.15`).

## The waveform, a shared motif

The recording waveform is the one motion motif shared by every product. It also echoes the logo's three bars.

Common shape, as dictus-ios defines it:
- 30 capsule bars, vertically centred, 2 pt or px tall at silence;
- the centre 40 % of the bars in solid brand blue; the outer bars fade towards the edges with opacity `(1 − d) × 0.9 + 0.15`, where `d` is the distance from the centre (0 to 1);
- displayed levels rise by a factor of 0.3 and fall by a decay of 0.85 per 60 Hz frame: quick to rise, slower to fall.

| Product | Source | Notes |
| --- | --- | --- |
| iOS | [`DictusCore/Sources/DictusCore/Design/BrandWaveform.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusCore/Sources/DictusCore/Design/BrandWaveform.swift) | The reference. Centre bars `#6BA3FF` (`dictusGradientStart`); outer bars white in dark mode, grey in light mode. |
| Android | [`core/.../ui/WaveformBars.kt`](https://github.com/getdictus/dictus-android/blob/develop/core/src/main/java/dev/pivisolutions/dictus/core/ui/WaveformBars.kt), gated by [`SyntheticMotionPolicy.kt`](https://github.com/getdictus/dictus-android/blob/develop/core/src/main/java/dev/pivisolutions/dictus/core/ui/SyntheticMotionPolicy.kt) | Ported from iOS: centre bars `AccentHighlight` (`#6BA3FF`), outer bars white with falling opacity. While transcribing, the bars show a travelling sine wave. |
| Website | [`src/components/Hero/BrandWaveform.ts`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Hero/BrandWaveform.ts) | Hero pill, light glass. Centre `#3D7EFF`, outer bars navy `#0F3460` with an opacity floor of 0.4, gaps of 1 px. There is no microphone: the bars come from a seeded synthetic voice, the same on every load. The newest level enters on the left and travels right, with the walker (iOS appends on the right). |

## Reduced motion

Each product follows the system setting. Decorative motion stops and a meaningful still frame is shown instead. Feedback that carries information stays.

### Website

- **Everywhere** under `prefers-reduced-motion: reduce`: animations and transitions are cut to 0.01 ms, animations run once, and smooth scrolling is turned off ([`globals.css`](https://github.com/getdictus/dictus-website/blob/develop/src/app/globals.css)).
- **Buttons:** the lift and the press movement are dropped; the shadow and colour changes stay ([`globals.css`](https://github.com/getdictus/dictus-website/blob/develop/src/app/globals.css)).
- **Drawn scenes:** `ScenePlayer` draws its chosen still moment (`stillAt`) once and never loops ([`ScenePlayer.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/shared/ScenePlayer.tsx)).
- **Hero:** the walker video is not loaded; her still frame stays. The scene shows the first phrase fully written and the waveform mid-word ([`HeroScene.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/Hero/HeroScene.tsx)).
- **Pinned steps** jump instead of scrolling smoothly ([`PinnedSteps.tsx`](https://github.com/getdictus/dictus-website/blob/develop/src/components/shared/PinnedSteps.tsx)).

### iOS (Reduce Motion)

- **Onboarding intro:** every page shows its still image instead of the video ([`IntroVideoView.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusApp/Onboarding/IntroVideoView.swift)). Drawn scenes show their still moment and never move ([`AnimatedScenePlayer.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusApp/Onboarding/AnimatedScenePlayer.swift)).
- **Mic button:** the idle glow stops breathing and holds at 0.45 opacity, the midpoint of its 0.3–0.6 range ([`AnimatedMicButton.swift`](https://github.com/getdictus/dictus-ios/blob/develop/DictusCore/Sources/DictusCore/Design/AnimatedMicButton.swift)).

### Android (animator duration scale, battery saver)

- `SyntheticMotionPolicy` turns decorative waveform motion off when the system animator duration scale is 0 or battery saver is on, and follows changes live ([`SyntheticMotionPolicy.kt`](https://github.com/getdictus/dictus-android/blob/develop/core/src/main/java/dev/pivisolutions/dictus/core/ui/SyntheticMotionPolicy.kt)). The transcribing wave then stays static. **Live microphone levels stay visible**, because they are functional recording feedback ([`TranscribingScreen.kt`](https://github.com/getdictus/dictus-android/blob/develop/ime/src/main/java/dev/pivisolutions/dictus/ime/ui/TranscribingScreen.kt), [`RecordingScreen.kt`](https://github.com/getdictus/dictus-android/blob/develop/app/src/main/java/dev/pivisolutions/dictus/recording/RecordingScreen.kt)).
- **Onboarding intro:** every page shows its still, as on iOS ([`IntroVideoView.kt`](https://github.com/getdictus/dictus-android/blob/develop/app/src/main/java/dev/pivisolutions/dictus/onboarding/IntroVideoView.kt)).
