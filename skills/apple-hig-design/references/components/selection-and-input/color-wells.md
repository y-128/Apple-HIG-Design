---
title: Color wells
url: https://developer.apple.com/design/human-interface-guidelines/color-wells
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Color wells

A color well lets people adjust the color of text, shapes, guides, and other onscreen elements.

## Core guidance

A color well displays a color picker when people tap or click it. This color picker can be the system-provided one or a custom interface that you design.

### Best practices

**Consider the system-provided color picker for a familiar experience.** Using the built-in color picker provides a consistent experience, in addition to letting people save a set of colors they can access from any app. The system-defined color picker can also help provide a familiar experience when developing apps across iOS, iPadOS, and macOS.

## Platform considerations

No additional considerations for iOS, iPadOS, or visionOS. Not supported in tvOS or watchOS.

### macOS

**When people click a color well, it receives a highlight to provide visual confirmation that it's active.** It then opens a color picker so people can choose a color. After they make a selection, the color well updates to show the new color.

**Color wells also support drag and drop**, so people can drag colors from one color well to another, and from the color picker to a color well.

## Native implementation

**Related**
- Color

**Developer documentation**
- `UIColorWell` — UIKit
- `UIColorPickerViewController` — UIKit
- `NSColorWell` — AppKit
- Color Programming Topics

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**System-provided color picker → the native `<input type="color">` element.** Apple's reasoning for preferring the system picker is consistency and a saved-color palette that follows the person across apps. The web has a direct equivalent: the browser's native color input opens the operating system's own color picker, which is the same picker system apps use and which already remembers recently used colors. Reaching for it instead of building a custom swatch grid gets you Apple's stated benefit for free, on whichever OS the visitor happens to be running.

**Where the platforms diverge.** Native `<input type="color">` is a plain sRGB well: no built-in support for alpha, no eyedropper across the whole screen, and a visually inconsistent trigger across browsers (Chromium renders a swatch with a border, Safari renders a small rounded rectangle, Firefox differs again). Apple's `NSColorWell` and `UIColorPickerViewController` support alpha, color spaces, and a system-wide eyedropper as first-class features. If your product needs alpha selection or spot-on visual consistency across browsers, you're choosing between accepting the native picker's real limitations or building a custom widget — and a custom widget forfeits the "familiar, already-learned interface" argument that is Apple's whole reason for recommending the system picker in the first place. There's no way to have both on the web today.

**The eyedropper is now available, on supporting browsers only.** The `EyeDropper` API lets a page sample any pixel on screen, which is the closest web equivalent to the system-wide color-picking a macOS color well offers. It isn't universal, so treat it as progressive enhancement layered onto the native color input, not a replacement for it.

**The highlight-on-click feedback.** Apple calls out that clicking a macOS color well highlights it to confirm activation. This is a general affordance principle, not something specific to color wells: any control that opens a picker, popover, or modal should show a visible focus or pressed state the moment it's activated, native `:focus-visible` styling on the trigger element is usually enough to satisfy it.

## Do / Don't

| Do | Don't |
|---|---|
| Prefer the system-provided color picker for a familiar, consistent experience | Build a fully custom color picker without a strong reason |
| Show a clear active/highlight state when a color well is activated | Leave people uncertain whether their click registered |
| Update the well to reflect the newly chosen color immediately | Delay or omit visual confirmation of a color change |
| Support drag and drop between color wells on macOS | Ignore drag-and-drop conventions people expect on macOS |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
