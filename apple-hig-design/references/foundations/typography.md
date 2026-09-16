---
title: Typography
url: https://developer.apple.com/design/human-interface-guidelines/typography
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-12-16
---

# Typography

Your typographic choices can help you display legible text, convey an information hierarchy, communicate important content, and express your brand or style.

## Core guidance

### Ensuring legibility

**Use font sizes that most people can read easily.** People read your content at various viewing distances and under a variety of conditions, so follow the recommended default and minimum sizes for each platform — for both custom and system fonts. Font weight also affects readability: if a custom font has a thin weight, aim larger than the recommended size.

| Platform | Default size | Minimum size |
|---|---|---|
| iOS, iPadOS | 17 pt | 11 pt |
| macOS | 13 pt | 10 pt |
| tvOS | 29 pt | 23 pt |
| visionOS | 17 pt | 12 pt |
| watchOS | 16 pt | 12 pt |

**Test legibility in different contexts.** Game text in particular needs testing on every platform the game runs on. If text proves hard to read, use a larger type size, increase contrast by changing text or background colors, or switch to a typeface designed for legibility such as the system fonts.

> *Image caption:* Testing a game on a new platform can show where text is hard to read.
> *Image caption:* Increasing text size and adding visible background shapes can help make text easier to read.

**In general, avoid light font weights.** With system-provided fonts, prefer Regular, Medium, Semibold, or Bold. Ultralight, Thin, and Light are hard to see, especially at small sizes.

### Conveying hierarchy

**Adjust font weight, size, and color to emphasize important information.** Maintain the relative hierarchy and visual distinction between text elements even when people change text size.

**Minimize the number of typefaces**, even in a highly customized interface. Mixing too many typefaces obscures the information hierarchy, hurts readability, and makes the interface feel internally inconsistent.

**Prioritize important content when responding to text-size changes.** Not all content is equally important. Someone choosing a larger text size wants the content they care about to be easier to read — they don't necessarily want every word on screen to grow. Tab titles in a tabbed window aren't expected to scale up; in a game, players care more about a character's dialog than about transient hit-damage values.

### Using system fonts

Apple provides two typeface families covering an extensive range of weights, sizes, styles, and languages.

- **San Francisco (SF)** — sans serif family including SF Pro, SF Compact, SF Arabic, SF Armenian, SF Georgian, SF Hebrew, and SF Mono. SF Pro, SF Compact, SF Arabic, SF Armenian, SF Georgian, and SF Hebrew also come in rounded variants, useful for coordinating text with soft or rounded UI elements or providing an alternative typographic voice.
- **New York (NY)** — serif family designed to work well by itself and alongside the SF fonts.

Both ship in the **variable font format**, which combines styles in one file and supports interpolation between them.

> **Note (Apple):** Variable fonts support optical sizing — adjusting typographic design to fit different sizes. On all platforms the system fonts support *dynamic optical sizes*, merging discrete optical sizes (like Text and Display) and weights into a single continuous design, letting the system interpolate each glyph to a structure precisely adapted to the point size. You don't need discrete optical sizes unless your design tool lacks full variable-font support.

The system fonts span **Ultralight to Black**, and SF adds widths including **Condensed and Expanded**. SF Symbols use equivalent weights, so symbols and adjacent text can be weight-matched precisely at any size or style.

The system defines **text styles** — named combinations of font weight, point size, and leading that work with both families. `body` supports comfortable multi-line reading; `headline` distinguishes a heading from surrounding content. Together they form a typographic hierarchy, and they let text scale proportionately when people change the system text size or turn on Larger Text in Accessibility settings.

**Consider using the built-in text styles.** They give a consistent way to convey hierarchy, and using them with the system fonts guarantees Dynamic Type support including larger accessibility sizes.

**Modify the built-in text styles if necessary.** System APIs define *symbolic traits* that adjust aspects of a text style — the bold trait adds weight, creating another hierarchy level. Traits also adjust leading: loose leading helps people keep their place in wide columns or long passages; tight leading helps text fit where height is constrained, such as a list row. **Avoid tight leading for three or more lines of text**, even where height is limited.

> **Developer note (Apple):** Use the constants in `Font.Design` to access system fonts — don't embed system fonts in your app or game. `Font.Design.default` gets the system font on all platforms; `Font.Design.serif` gets New York.

**If necessary, adjust tracking in interface mockups.** In a running app the system font adjusts tracking automatically at every point size. For an accurate mockup you don't need to pick a discrete optical size, but you may need to set tracking manually — see Tracking values below.

### Using custom fonts

**Make sure custom fonts are legible** at various viewing distances and conditions. Follow the recommended minimum font sizes for the relevant styles and weights.

**Implement accessibility features for custom fonts.** System fonts automatically support Dynamic Type (where available) and respond to accessibility features such as Bold Text. A custom font must implement the same behaviors. In a Unity-based game, Apple's Unity plug-ins can provide Dynamic Type support; if the plug-in doesn't suit your game, let players adjust text size some other way.

### Supporting Dynamic Type

Dynamic Type is a system-level feature in **iOS, iPadOS, tvOS, visionOS, and watchOS** that lets people adjust the size of visible text on their device. (macOS does not support it.)

> *Image caption:* Mail content at the default text size, and at the largest accessibility text size.

**Make sure your app's layout adapts to all font sizes.** Verify the design scales and that text and glyphs stay legible. On iPhone or iPad, turn on Settings > Accessibility > Display & Text Size > Larger Text and confirm the app remains comfortably readable.

**Increase the size of meaningful interface icons as font size increases.** Icons carrying important information must stay viewable at larger font sizes. SF Symbols scale automatically with Dynamic Type changes.

**Keep text truncation to a minimum as font size increases.** Aim to display as much useful text at the largest accessibility size as at the largest standard size. Avoid truncating text in scrollable regions unless people can open a separate view to read the rest. Configure labels to use as many lines as needed.

**Consider adjusting your layout at large font sizes.** In a horizontally constrained context, inline items (glyphs, timestamps) and container boundaries crowd text and cause truncation or overlap. Prefer a stacked layout where text sits above secondary items. Multicolumn text also suffers at large sizes — reduce the column count as font size increases.

**Maintain a consistent information hierarchy regardless of font size.** Keep primary elements toward the top of a view even at very large font sizes, so people don't lose track of them.

## Platform considerations

| Platform | System font | Notes |
|---|---|---|
| iOS, iPadOS | SF Pro | NY also available. |
| macOS | SF Pro | NY available for apps built with Mac Catalyst. **macOS doesn't support Dynamic Type.** |
| tvOS | SF Pro | NY also available. |
| visionOS | SF Pro | If you use NY, you must specify the type styles you want. |
| watchOS | SF Compact | NY also available. Complications use SF Compact Rounded. |

### macOS — dynamic system font variants

Use these when text must match the look and feel of system-provided controls.

| Dynamic font variant | API |
|---|---|
| Control content | `controlContentFont(ofSize:)` |
| Label | `labelFont(ofSize:)` |
| Menu | `menuFont(ofSize:)` |
| Menu bar | `menuBarFont(ofSize:)` |
| Message | `messageFont(ofSize:)` |
| Palette | `paletteFont(ofSize:)` |
| Title | `titleBarFont(ofSize:)` |
| Tool tips | `toolTipsFont(ofSize:)` |
| Document text (user) | `userFont(ofSize:)` |
| Monospaced document text (user fixed pitch) | `userFixedPitchFont(ofSize:)` |
| Bold system font | `boldSystemFont(ofSize:)` |
| System font | `systemFont(ofSize:)` |

### visionOS

visionOS uses **bolder versions** of the Dynamic Type body and title styles, and adds **Extra Large Title 1** and **Extra Large Title 2** for wide, editorial-style layouts.

- **In general, prefer 2D text.** The more visual depth characters have, the harder they are to read. A small amount of 3D text can be a fun attention-drawing element, but content people must read and understand should have little or no visual depth.
- **Make sure text stays legible when people scale it.** Pick a text style that looks good at full scale, then test legibility at different scales.
- **Maximize contrast between text and its container background.** The system displays text in white by default because it contrasts strongly with the default background material. Test any other text color in a variety of contexts.
- **If text has no background, consider making it bold** to improve legibility. Avoid adding shadows for contrast here — the space may have no surface to cast an accurate shadow on, and you can't predict what shadow size and density would suit the person's current Environment.
- **Keep text facing people as much as possible.** For text anchored to a point in space (such as a label on a 3D object), use *billboarding* so the text faces the wearer regardless of movement. Otherwise people may view it from a highly oblique angle and be unable to read it. The baseline of the text needs to remain perpendicular to the person's line of sight.

## Specifications

You can display emphasized variants of system text styles using symbolic traits — the `bold()` modifier in SwiftUI, `traitBold` in the UIKit `UIFontDescriptor` API. Emphasized weights can be medium, semibold, bold, or heavy.

> **Source limitation:** Apple's page presents Dynamic Type sizes as tabbed tables (xSmall / Small / Medium / Large (default) / xLarge / xxLarge / xxxLarge, and AX1–AX5). The captured PDF contains only the **first tab of each group**. The tables below are therefore **xSmall** and **AX1** only — the default (Large) size table is **not** available in this source. For the full set, download the Dynamic Type size tables from Apple Design Resources for each platform.

### iOS, iPadOS Dynamic Type sizes — xSmall

| Style | Weight | Size (pt) | Leading (pt) | Emphasized weight |
|---|---|---|---|---|
| Large Title | Regular | 31 | 38 | Bold |
| Title 1 | Regular | 25 | 31 | Bold |
| Title 2 | Regular | 19 | 24 | Bold |
| Title 3 | Regular | 17 | 22 | Semibold |
| Headline | Semibold | 14 | 19 | Semibold |
| Body | Regular | 14 | 19 | Semibold |
| Callout | Regular | 13 | 18 | Semibold |
| Subhead | Regular | 12 | 16 | Semibold |
| Footnote | Regular | 12 | 16 | Semibold |
| Caption 1 | Regular | 11 | 13 | Semibold |
| Caption 2 | Regular | 11 | 13 | Semibold |

*Point size based on image resolution of 144 ppi for @2x and 216 ppi for @3x designs.*

### iOS, iPadOS larger accessibility type sizes — AX1

| Style | Weight | Size (pt) | Leading (pt) | Emphasized weight |
|---|---|---|---|---|
| Large Title | Regular | 44 | 52 | Bold |
| Title 1 | Regular | 38 | 46 | Bold |
| Title 2 | Regular | 34 | 41 | Bold |
| Title 3 | Regular | 31 | 38 | Semibold |
| Headline | Semibold | 28 | 34 | Semibold |
| Body | Regular | 28 | 34 | Semibold |
| Callout | Regular | 26 | 32 | Semibold |
| Subhead | Regular | 25 | 31 | Semibold |
| Footnote | Regular | 23 | 29 | Semibold |
| Caption 1 | Regular | 22 | 28 | Semibold |
| Caption 2 | Regular | 20 | 25 | Semibold |

*Point size based on image resolution of 144 ppi for @2x and 216 ppi for @3x designs.*

### macOS built-in text styles

macOS has no Dynamic Type, so this is the complete table.

| Text style | Weight | Size (pt) | Line height (pt) | Emphasized weight |
|---|---|---|---|---|
| Large Title | Regular | 26 | 32 | Bold |
| Title 1 | Regular | 22 | 26 | Bold |
| Title 2 | Regular | 17 | 22 | Bold |
| Title 3 | Regular | 15 | 20 | Semibold |
| Headline | Bold | 13 | 16 | Heavy |
| Body | Regular | 13 | 16 | Semibold |
| Callout | Regular | 12 | 15 | Semibold |
| Subheadline | Regular | 11 | 14 | Semibold |
| Footnote | Regular | 10 | 13 | Semibold |
| Caption 1 | Regular | 10 | 13 | Medium |
| Caption 2 | Medium | 10 | 13 | Semibold |

*Point size based on image resolution of 144 ppi for @2x designs.*

### tvOS built-in text styles

| Text style | Weight | Size (pt) | Leading (pt) | Emphasized weight |
|---|---|---|---|---|
| Title 1 | Medium | 76 | 96 | Bold |
| Title 2 | Medium | 57 | 66 | Bold |
| Title 3 | Medium | 48 | 56 | Bold |
| Headline | Medium | 38 | 46 | Bold |
| Subtitle 1 | Regular | 38 | 46 | Medium |
| Callout | Medium | 31 | 38 | Bold |
| Body | Medium | 29 | 36 | Bold |
| Caption 1 | Medium | 25 | 32 | Bold |
| Caption 2 | Medium | 23 | 30 | Bold |

*Point size based on image resolution of 72 ppi for @1x and 144 ppi for @2x designs.*

### watchOS Dynamic Type sizes — xSmall

| Style | Weight | Size (pt) | Leading (pt) | Emphasized weight |
|---|---|---|---|---|
| Large Title | Regular | 30 | 32.5 | Bold |
| Title 1 | Regular | 28 | 30.5 | Semibold |
| Title 2 | Regular | 24 | 26.5 | Semibold |
| Title 3 | Regular | 17 | 19.5 | Semibold |
| Headline | Semibold | 14 | 16.5 | Semibold |
| Body | Regular | 14 | 16.5 | Semibold |
| Caption 1 | Regular | 13 | 15.5 | Semibold |
| Caption 2 | Regular | 12 | 14.5 | Semibold |
| Footnote 1 | Regular | 11 | 13.5 | Semibold |
| Footnote 2 | Regular | 10 | 12.5 | Semibold |

### watchOS larger accessibility type sizes — AX1

| Style | Weight | Size (pt) | Leading (pt) | Emphasized weight |
|---|---|---|---|---|
| Large Title | Regular | 44 | 46.5 | Bold |
| Title 1 | Regular | 42 | 44.5 | Semibold |
| Title 2 | Regular | 34 | 41 | Semibold |
| Title 3 | Regular | 24 | 26.5 | Semibold |
| Headline | Semibold | 21 | 23.5 | Semibold |
| Body | Regular | 21 | 23.5 | Semibold |
| Caption 1 | Regular | 18 | 20.5 | Semibold |
| Caption 2 | Regular | 17 | 19.5 | Semibold |
| Footnote 1 | Regular | 16 | 18.5 | Semibold |
| Footnote 2 | Regular | 15 | 17.5 | Semibold |

### Tracking values

Apple publishes four tracking tables (iOS/iPadOS/visionOS, macOS, tvOS, watchOS). The first three are **identical except at 52 pt and 53 pt**, where the point values are transposed:

- iOS/iPadOS/visionOS: 52 pt → +0.33, 53 pt → +0.31
- macOS and tvOS: 52 pt → +0.31, 53 pt → +0.33

The 1/1000 em values (+6 at both sizes) are the same everywhere, so the discrepancy is a rounding artifact in Apple's tables. The single table below therefore covers **SF Pro on iOS, iPadOS, visionOS, macOS, and tvOS**.

**SF Pro** (iOS, iPadOS, visionOS, macOS, tvOS)

| Size (pt) | Tracking (1/1000 em) | Tracking (pt) |
|---|---|---|
| 6 | +41 | +0.24 |
| 7 | +34 | +0.23 |
| 8 | +26 | +0.21 |
| 9 | +19 | +0.17 |
| 10 | +12 | +0.12 |
| 11 | +6 | +0.06 |
| 12 | 0 | 0.0 |
| 13 | −6 | −0.08 |
| 14 | −11 | −0.15 |
| 15 | −16 | −0.23 |
| 16 | −20 | −0.31 |
| 17 | −26 | −0.43 |
| 18 | −25 | −0.44 |
| 19 | −24 | −0.45 |
| 20 | −23 | −0.45 |
| 21 | −18 | −0.36 |
| 22 | −12 | −0.26 |
| 23 | −4 | −0.10 |
| 24 | +3 | +0.07 |
| 25 | +6 | +0.15 |
| 26 | +8 | +0.22 |
| 27 | +11 | +0.29 |
| 28 | +14 | +0.38 |
| 29 | +14 | +0.40 |
| 30 | +14 | +0.40 |
| 31 | +13 | +0.39 |
| 32 | +13 | +0.41 |
| 33 | +12 | +0.40 |
| 34 | +12 | +0.40 |
| 35 | +11 | +0.38 |
| 36 | +10 | +0.37 |
| 37 | +10 | +0.36 |
| 38 | +10 | +0.37 |
| 39 | +10 | +0.38 |
| 40 | +10 | +0.37 |
| 41 | +9 | +0.36 |
| 42 | +9 | +0.37 |
| 43 | +9 | +0.38 |
| 44 | +8 | +0.37 |
| 45 | +8 | +0.35 |
| 46 | +8 | +0.36 |
| 47 | +8 | +0.37 |
| 48 | +8 | +0.35 |
| 49 | +7 | +0.33 |
| 50 | +7 | +0.34 |
| 51 | +7 | +0.35 |
| 52 | +6 | +0.33 (iOS/iPadOS/visionOS) · +0.31 (macOS/tvOS) |
| 53 | +6 | +0.31 (iOS/iPadOS/visionOS) · +0.33 (macOS/tvOS) |
| 54 | +6 | +0.32 |
| 56 | +6 | +0.30 |
| 58 | +5 | +0.28 |
| 60 | +4 | +0.26 |
| 62 | +4 | +0.24 |
| 64 | +4 | +0.22 |
| 66 | +3 | +0.19 |
| 68 | +2 | +0.17 |
| 70 | +2 | +0.14 |
| 72 | +2 | +0.14 |
| 76 | +1 | +0.07 |
| 80–96 | 0 | 0 |

*Not all apps express tracking values as 1/1000 em. Point size based on image resolution of 144 ppi for @2x and 216 ppi for @3x designs (tvOS: 72 ppi @1x, 144 ppi @2x).*

**SF Compact** (watchOS)

| Size (pt) | Tracking (1/1000 em) | Tracking (pt) |
|---|---|---|
| 6 | +50 | +0.29 |
| 7 | +30 | +0.21 |
| 8 | +30 | +0.23 |
| 9 | +30 | +0.26 |
| 10 | +30 | +0.29 |
| 11 | +24 | +0.26 |
| 12 | +20 | +0.23 |
| 13 | +16 | +0.20 |
| 14 | +14 | +0.19 |
| 15 | +4 | +0.06 |
| 16 | 0 | 0.00 |
| 17 | −4 | −0.07 |
| 18 | −8 | −0.14 |
| 19 | −12 | −0.22 |
| 20 | 0 | 0.00 |
| 21 | −2 | −0.04 |
| 22 | −4 | −0.09 |
| 23 | −6 | −0.13 |
| 24 | −8 | −0.19 |
| 25 | −10 | −0.24 |
| 26 | −11 | −0.28 |
| 27 | −12 | −0.30 |
| 28 | −12 | −0.34 |
| 29 | −14 | −0.38 |
| 30 | −14 | −0.42 |
| 31 | −15 | −0.45 |
| 32 | −16 | −0.50 |
| 33 | −17 | −0.55 |
| 34 | −18 | −0.60 |
| 35 | −18 | −0.63 |
| 36 | −20 | −0.69 |
| 37 | −20 | −0.72 |
| 38 | −20 | −0.74 |
| 39 | −20 | −0.76 |
| 40 | −20 | −0.78 |
| 41 | −20 | −0.80 |
| 42 | −20 | −0.82 |
| 43 | −20 | −0.84 |
| 44 | −20 | −0.86 |
| 45 | −20 | −0.88 |
| 46 | −20 | −0.92 |
| 47 | −20 | −0.94 |
| 48 | −20 | −0.96 |
| 49 | −21 | −1.00 |
| 50 | −21 | −1.03 |
| 51 | −21 | −1.05 |
| 52 | −21 | −1.07 |
| 53 | −22 | −1.11 |
| 54 | −22 | −1.13 |
| 56 | −22 | −1.20 |
| 58 | −22 | −1.25 |
| 60 | −22 | −1.32 |
| 62 | −22 | −1.36 |
| 64 | −23 | −1.44 |
| 66 | −24 | −1.51 |
| 68 | −24 | −1.56 |
| 70 | −24 | −1.64 |
| 72 | −24 | −1.69 |
| 76 | −25 | −1.86 |
| 80 | −26 | −1.99 |
| 84 | −26 | −2.13 |
| 88 | −26 | −2.28 |
| 92 | −28 | −2.47 |
| 96 | −28 | −2.62 |

*Point size based on image resolution of 144 ppi for @2x designs.*

Note: the watchOS 20 pt row (0 / 0.00) breaks the otherwise monotonic progression. This is what Apple publishes.

## Native implementation

**Related**
- Fonts for Apple platforms (download San Francisco and New York)
- SF Symbols

**Developer documentation**
- Text input and output — SwiftUI
- Text display and fonts — UIKit
- Fonts — AppKit

**Key APIs**
- `Font.Design.default` / `Font.Design.serif` — access system fonts; never embed them
- `.bold()` — SwiftUI emphasized weight; `traitBold` on `UIFontDescriptor` in UIKit
- `leading(_:)` — adjust leading via symbolic traits
- `numberOfLines` — prevent truncation in UIKit labels
- `isAccessibilityCategory` — detect accessibility text sizes to switch layout

**Videos:** Get started with Dynamic Type · Meet the expanded San Francisco font family · The details of UI typography

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Dynamic Type → respect the user's root font size.** The core of Dynamic Type is that the *user*, not the designer, picks the base size. On the web the equivalent is never setting a pixel value on `html` and expressing every type size in `rem`, so a person who raised their browser's default font size gets a proportionally larger interface. Setting `html { font-size: 62.5% }` to make "1rem = 10px" defeats this — it re-anchors everything to a designer-chosen size.

**Text styles → a named, semantic type scale.** Apple's win is that `body` and `headline` are *roles*, not sizes, so the whole hierarchy shifts coherently when the base changes. Mirror this with named scale tokens tied to roles rather than raw numbers scattered through components. Fluid sizing that interpolates with viewport width is a reasonable web-native addition, but keep a `rem`-relative floor so user zoom still works.

**"Prioritize important content when text size changes" → don't scale chrome with content.** Navigation labels, tab titles, and metadata can hold near their base size while body copy grows. This is the web analogue of Apple's tab-title example, and it is why a single global scale factor is the wrong mechanism.

**"Consider adjusting your layout at large font sizes" → container queries, not viewport breakpoints.** Apple's advice is to restack when text crowds its container. Viewport width doesn't tell you that; the container's own width relative to its text does. Reducing column count as text grows is the same instruction as Apple's multicolumn guidance.

**Minimum sizes → treat 11 pt / 17 pt as a floor, not a target.** Apple's pt is roughly a CSS px at 1x, so iOS's 17 pt default is close to the browser's 16 px default — the two ecosystems already agree. The 11 pt minimum maps to roughly 11 px, which is below what most web body-adjacent text should ever be; use it only for genuinely incidental text.

**"Avoid light font weights" → applies more strongly on the web.** Apple can rely on known displays and system-level font smoothing. Web type renders across unknown displays and rendering stacks, so Ultralight/Thin/Light weights degrade further. The Regular–Bold band Apple recommends is a safe web default too.

**Optical sizing and tracking → let variable fonts do it.** Apple's system fonts adjust tracking automatically per point size; the published tracking tables exist for mockups, not for runtime. The web equivalent is a variable font with an `opsz` axis and letting the browser apply optical sizing, rather than hard-coding `letter-spacing` per size. If you do hand-tune, the shape of Apple's table is a useful guide: tighten as size grows through the mid-range, then loosen again at display sizes.

**Bold Text accessibility setting → there is a media query for it.** The web can detect a user's preference for increased contrast and reduced motion; a stated preference for heavier text is not universally exposed, so don't assume parity. Where you can't detect it, the fallback is the same as Apple's advice for custom fonts: make sure the design still works if the user forces heavier rendering.

**Custom fonts → the accessibility obligation transfers unchanged.** Apple's rule is that a custom font must implement the same behaviors as the system font. On the web this means the custom font must ship the weights your hierarchy needs, must have adequate x-height at your minimum sizes, and must not break when the user overrides fonts entirely.

## Do / Don't

| Do | Don't |
|---|---|
| Use the built-in text styles so Dynamic Type works automatically | Embed system fonts in your app or game |
| Prefer Regular, Medium, Semibold, Bold | Use Ultralight, Thin, or Light for interface text |
| Keep the number of typefaces low | Mix many typefaces in one interface |
| Let important content scale and hold chrome steady | Scale every word on screen uniformly |
| Use loose leading for wide columns or long passages | Use tight leading for three or more lines |
| Increase meaningful interface icons with font size | Let icons stay fixed while text grows |
| Restack layout and reduce columns at large sizes | Let inline items crowd text into truncation |
| In visionOS, prefer 2D text and billboard spatial labels | Add shadows to visionOS text to boost contrast |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
