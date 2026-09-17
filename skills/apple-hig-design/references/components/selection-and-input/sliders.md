---
title: Sliders
url: https://developer.apple.com/design/human-interface-guidelines/sliders
platforms: [iOS, iPadOS, macOS, visionOS, watchOS]
last_updated: 2023-06-21
---

# Sliders

A slider is a horizontal track with a control, called a thumb, that people can adjust between a minimum and maximum value.

## Core guidance

### Overview

As a slider's value changes, the portion of track between the minimum value and the thumb fills with color. A slider can optionally display left and right icons that illustrate the meaning of the minimum and maximum values.

### Best practices

**Customize a slider's appearance if it adds value.** You can adjust a slider's appearance — including track color, thumb image and tint color, and left and right icons — to blend with your app's design and communicate intent. A slider that adjusts image size, for example, could show a small image icon on the left and a large image icon on the right.

**Use familiar slider directions.** People expect the minimum and maximum sides of sliders to be consistent in all apps, with minimum values on the leading side and maximum values on the trailing side (for horizontal sliders) and minimum values at the bottom and maximum values at the top (for vertical sliders). For example, people expect to be able to move a horizontal slider that represents a percentage from 0 percent on the leading side to 100 percent on the trailing side.

**Consider supplementing a slider with a corresponding text field and stepper.** Especially when a slider represents a wide range of values, people may appreciate seeing the exact slider value and having the ability to enter a specific value in a text field. Adding a stepper provides a convenient way for people to increment in whole values. For related guidance, see Text fields and Steppers.

## Platform considerations

Not supported in tvOS.

### iOS, iPadOS

**Don't use a slider to adjust audio volume.** If you need to provide volume control in your app, use a volume view, which is customizable and includes a volume-level slider and a control for changing the active audio output device. For guidance, see Playing audio.

### macOS

Sliders in macOS can also include tick marks, making it easier for people to pinpoint a specific value within the range.

In a linear slider either with or without tick marks, the thumb is a narrow lozenge shape, and the portion of track between the minimum value and the thumb is filled with color. A linear slider often includes supplementary icons that illustrate the meaning of the minimum and maximum values.

In a circular slider, the thumb appears as a small circle. Tick marks, when present, appear as evenly spaced dots around the circumference of the slider.

> *Image caption:* Linear slider without tick marks, linear slider with tick marks, and circular slider.

**Consider giving live feedback as the value of a slider changes.** Live feedback shows people results in real time. For example, your Dock icons are dynamically scaled when adjusting the Size slider in Dock settings.

**Choose a slider style that matches peoples' expectations.** A horizontal slider is ideal when moving between a fixed starting and ending point. For example, a graphics app might offer a horizontal slider for setting the opacity level of an object between 0 and 100 percent. Use circular sliders when values repeat or continue indefinitely. For example, a graphics app might use a circular slider to adjust the rotation of an object between 0 and 360 degrees. An animation app might use a circular slider to adjust how many times an object spins when animated — four complete rotations equals four spins, or 1440 degrees of rotation.

**Consider using a label to introduce a slider.** Labels generally use sentence-style capitalization and end with a colon. For guidance, see Labels.

**Use tick marks to increase clarity and accuracy.** Tick marks help people understand the scale of measurements and make it easier to locate specific values.

**Consider adding labels to tick marks for even greater clarity.** Labels can be numbers or words, depending on the slider's values. It's unnecessary to label every tick mark unless doing so is needed to reduce confusion. In many cases, labeling only the minimum and maximum values is sufficient. When the values of the slider are nonlinear, like in the Energy Saver settings pane, periodic labels provide context. It's also a good idea to provide a tooltip that displays the value of the thumb when people hold their pointer over it.

### visionOS

**Prefer horizontal sliders.** It's generally easier for people to gesture from side to side than up and down.

### watchOS

A slider is a horizontal track — appearing as a set of discrete steps or as a continuous bar — that represents a finite range of values. People can tap buttons on the sides of the slider to increase or decrease its value by a predefined amount.

> *Image caption:* Discrete slider versus continuous slider.

**If necessary, create custom glyphs to communicate what the slider does.** The system displays plus and minus signs by default.

## Native implementation

**Related**
- Steppers
- Pickers

**Developer documentation**
- `Slider` — SwiftUI
- `UISlider` — UIKit
- `NSSlider` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Linear slider → `<input type="range">`, and it already gives you more than it looks like.** The native range input handles arrow-key increment/decrement, `Home`/`End` jumps to min/max, drag with the mouse or touch, and — critically — reports an accessible name, current value, and min/max/step to assistive technology automatically via its implicit ARIA role of `slider`. A custom div-based slider has to reimplement all of that by hand with `role="slider"`, `aria-valuenow`, `aria-valuemin`, `aria-valuemax`, and manual keyboard handling; it's easy to build one that works with a mouse and quietly fails for keyboard or screen-reader users. Default to the native element whenever the geometry is a straight line.

**"Use familiar slider directions" → this is a labeling requirement, not just a visual convention, on the web.** A range input's accessible name still needs to come from a `<label>` (or `aria-label`/`aria-labelledby`); the direction convention Apple describes (minimum leading, maximum trailing) only reads correctly to assistive technology if the label states what the slider measures, since a screen reader announces the numeric value but not which end is which. RTL locales flip the leading/trailing convention automatically under logical CSS properties, but a raw `<input type="range">` in a right-to-left document does not reverse its visual min/max sides in every browser — verify rather than assume.

**Circular slider → no native element; this is a genuine web capability gap.** There's no HTML input for a value that "repeats or continues indefinitely" the way Apple's rotation and spin-count examples describe. Building one means a fully custom `role="slider"` widget with pointer-angle math and hand-rolled keyboard support — real work, and worth doing only when the value genuinely wraps (rotation, hue) rather than as a stylistic choice. For values with a fixed start and end, Apple's own advice (use horizontal, not circular) applies just as strongly on the web, because it's the case the native element already covers well.

**Tick marks → the `<datalist>` element, with real limitations.** Pairing an `<input type="range">` with a `<datalist>` via the `list` attribute renders native tick marks in most browsers and can enable snapping, which covers Apple's "use tick marks to increase clarity" guidance directly. But per-tick text labels — Apple's example of numeric or word labels under specific ticks — aren't part of the datalist rendering in any browser; you'd need to position labels yourself with CSS, calculated from track width and the values in the datalist, and keep them in sync if the range is resized.

**Live value tooltip on hover → `<output>` bound to the input via `oninput`, not a native tooltip.** Range inputs don't show their current value by default the way Apple's macOS pointer-hover tooltip does; you have to render it yourself, typically an `<output>` element updated on the `input` event and positioned near the thumb. Wire it to the `input` event rather than `change` so it updates continuously, matching Apple's "live feedback" guidance.

**Nonlinear scale (Energy Saver-style) → the input's own range must stay linear; remap the display only.** `<input type="range">` has no concept of a nonlinear scale between its `min` and `max` — the thumb position is always linearly proportional to the value. To reproduce Apple's Energy Saver example, keep the underlying input linear (say, 0–100) and apply your own mapping function when displaying the value and tick labels, the same way a custom NSSlider subclass would need to on macOS.

**Volume slider ("don't use a slider for audio volume" on iOS) → there is no dedicated web volume widget either.** The web has no analogue to Apple's system volume view. If you're building in-page audio volume control, it's still a `<input type="range">` in practice; the part of Apple's guidance that transfers is the reasoning, not the specific component — give it an unambiguous accessible name ("Volume", not just "Slider") so it isn't confused with an unrelated numeric control.

## Do / Don't

| Do | Don't |
|---|---|
| Keep minimum on the leading/bottom side, maximum on trailing/top | Reverse slider direction from what people expect across apps |
| Use a horizontal slider for a fixed start-to-end range | Use a circular slider for values with a fixed start and end |
| Use a circular slider for values that repeat or continue indefinitely | Force a wrapping value (like rotation) into a linear slider without adaptation |
| Add tick marks to increase clarity and accuracy (macOS) | Label every tick mark when only min/max labeling is needed |
| Pair a slider with a text field and stepper for wide ranges | Leave people guessing the exact value on a wide-range slider |
| Give live feedback as the value changes | Delay visible feedback until after the interaction ends |
| Use a volume view for audio volume (iOS, iPadOS) | Build audio volume control from a plain slider |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
