---
title: Steppers
url: https://developer.apple.com/design/human-interface-guidelines/steppers
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Steppers

A stepper is a two-segment control that people use to increase or decrease an incremental value.

## Core guidance

A stepper sits next to a field that displays its current value, because the stepper itself doesn't display a value.

### Best practices

**Make the value that a stepper affects obvious.** A stepper itself doesn't display any values, so make sure people know which value they're changing when they use a stepper.

**Consider pairing a stepper with a text field when large value changes are likely.** Steppers work well by themselves for making small changes that require a few taps or clicks. By contrast, people appreciate the option to use a field to enter specific values, especially when the values they use can vary widely. On a printing screen, for example, it can help to have both a stepper and a text field to set the number of copies.

## Platform considerations

No additional considerations for iOS, iPadOS, or visionOS. Not supported in watchOS or tvOS.

### macOS

**For large value ranges, consider supporting Shift-click to change the value quickly.** If your app benefits from larger changes in a stepper's value, it can be useful to let people Shift-click the stepper to change the value by more than the default increment (by 10 times the default, for example).

## Native implementation

**Related**
- Pickers
- Text fields

**Developer documentation**
- `UIStepper` — UIKit
- `NSStepper` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**The native match is closer than most controls in this collection.** `<input type="number">` renders as a text field with built-in up/down spinner arrows in most browsers, which is structurally the same pairing Apple describes: a value display sitting next to increment/decrement controls, not a stepper that displays no value of its own. Reaching for it first satisfies Apple's core requirement, "the value a stepper affects must be obvious," automatically, since the number is always visible in the field itself.

**Where the native element under-delivers.** Browser-rendered spinner arrows are small, inconsistently styled across browsers, and in several browsers (notably Firefox and Safari) hard to target precisely with a mouse or trackpad, let alone a touch target. If your product needs a stepper that's comfortably tappable, you're building a custom pair of increment/decrement buttons next to a number input rather than relying on the browser's own arrows — at which point you take on the accessibility work `<input type="number">` gave you for free: labeling the buttons for screen readers (they must announce what they do, not just render a glyph), and wiring `aria-live` or an accessible name update so assistive technology hears the new value after each click, since a purely visual update to an adjacent field is silent to a screen reader unless the field itself is the thing being read.

**"Pair with a text field for large changes" is really an argument for `<input type="number">` over a plus/minus-only widget.** Apple's reasoning is that a stepper alone is fine for small nudges but painful for large jumps, so pair it with a directly-editable field. On the web this argument resolves itself if you build on `<input type="number">` in the first place, since the field is directly editable and typable by definition; a custom stepper built as two buttons with no adjoining editable field reintroduces the exact problem Apple is warning against, forcing dozens of clicks to reach a large value.

**No web equivalent for Shift-click acceleration, but the underlying need still applies.** There's no browser-native modifier-click convention for number inputs. If large-increment jumps matter for your use case, the honest web translation of Apple's macOS advice is a visible, discoverable large-step control (a labeled button, not a hidden modifier key), because a keyboard shortcut nobody can discover fails the same people a stepper-only widget already fails.

## Do / Don't

| Do | Don't |
|---|---|
| Show the current value next to the stepper, never inside it | Rely on a stepper that displays no value of its own |
| Pair a stepper with an editable field when large jumps are likely | Force many taps or clicks to reach a distant value |
| Make it unambiguous which value a stepper is changing | Place a stepper where its target value is unclear |
| On macOS, consider Shift-click for large-increment changes | Hide the only way to make large changes behind an undiscoverable gesture |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
