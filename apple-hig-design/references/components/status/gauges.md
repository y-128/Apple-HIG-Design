---
title: Gauges
url: https://developer.apple.com/design/human-interface-guidelines/gauges
platforms: [iOS, iPadOS, macOS, visionOS, watchOS]
last_updated: 2022-09-23
---

# Gauges

A gauge displays a specific numerical value within a range of values.

## Core guidance

In addition to indicating the current value in a range, a gauge can provide more context about the range itself. For example, a temperature gauge can use text to identify the highest and lowest temperatures in the range and display a spectrum of colors that visually reinforce the changing values.

### Anatomy

A gauge uses a circular or linear path to represent a range of values, mapping the current value to a specific point on the path. A standard gauge displays an indicator that shows the current value's location; a gauge that uses the capacity style displays a fill that stops at the value's location on the path.

Circular and linear gauges in both standard and capacity styles are also available in a variant that's visually similar to watchOS complications. This variant — called accessory — works well in iOS Lock Screen widgets and anywhere you want to echo the appearance of complications.

> **Note (Apple):** In addition to gauges, macOS also supports level indicators, some of which have visual styles that are similar to gauges. For guidance, see the macOS section below.

### Best practices

**Write succinct labels that describe the current value and both endpoints of the range.** Although not every gauge style displays all labels, VoiceOver reads the visible labels to help people understand the gauge without seeing the screen.

**Consider filling the path with a gradient to help communicate the purpose of the gauge.** For example, a temperature gauge might use colors that range from red to blue to represent temperatures that range from hot to cold.

## Platform considerations

No additional considerations for iOS, iPadOS, visionOS, or watchOS. Not supported in tvOS.

### macOS

In addition to supporting gauges, macOS also defines a level indicator that displays a specific numerical value within a range. You can configure a level indicator to convey capacity, rating, or — rarely — relevance.

The capacity style can depict discrete or continuous values.

> *Image caption:* Continuous. A horizontal translucent track that fills with a solid bar to indicate the current value.
> *Image caption:* Discrete. A horizontal row of separate, equally sized, rectangular segments. The number of segments matches the total capacity, and the segments fill completely — never partially — with color to indicate the current value.

**Consider using the continuous style for large ranges.** A large value range can make the segments of a discrete capacity indicator too small to be useful.

**Consider changing the fill color to inform people about significant parts of the range.** By default, the fill color for both capacity indicator styles is green. If it makes sense in your app, you can change the fill color when the current value reaches certain levels, such as very low, very high, or just past the middle. You can change the fill color of the entire indicator or you can use the tiered state to show a sequence of several colors in one indicator.

> *Image caption:* Tiered level appearance.

For guidance using the rating style to help people rank something, see Rating indicators.

Although rarely used, the relevance style can communicate relevancy using a shaded horizontal bar. For example, a relevance indicator might appear in a list of search results, helping people visualize the relevancy of the results when sorting or comparing multiple items.

## Native implementation

**Related**
- Ratings and reviews

**Developer documentation**
- `Gauge` — SwiftUI
- `NSLevelIndicator` — AppKit

**Key APIs**
- `Gauge` — SwiftUI view for the gauge component, including standard, capacity, and accessory styles
- `NSLevelIndicator` — AppKit control for macOS level indicators, including the discrete, continuous, rating, and relevance styles

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A gauge shows a value within a range, not progress toward completion — the web has a purpose-built element for exactly this distinction.** The HTML `<meter>` element (and the ARIA `meter` role for custom-built equivalents) exists specifically to represent a scalar measurement within a known range — disk usage, a fuel level, a score — as opposed to `<progress>` or `role="progressbar"`, which represent an ongoing task moving toward completion. This is the same distinction Apple draws by keeping gauges and progress indicators as separate components: reach for `meter`, not `progress`, whenever the value being shown isn't "how much of this task is done."

**"Write succinct labels for the current value and both endpoints" → the accessible name and range must be programmatic, not just visual.** VoiceOver reading a gauge's visible labels only works because the underlying control exposes value and range as data, not as decoration. The `<meter>` element's `min`, `max`, and `value` attributes (or a custom widget's `aria-valuemin` / `aria-valuemax` / `aria-valuenow` / `aria-valuetext`) are the direct equivalent — set them even if you also render text labels, so assistive technology gets the same information sighted users get from the endpoints.

**The capacity style's discrete-vs-continuous choice maps to a real web tradeoff.** A continuous fill (a single bar) reads smoothly at any value; discrete segments make the value's granularity legible at a glance (e.g., "3 of 5 bars") but degrade once you have too many segments to render meaningfully — Apple's own advice to prefer continuous for large ranges is a rendering-density argument that applies identically to a web-based segmented meter.

**Tiered fill color → this is where the web's built-in `<meter>` styling actually helps you.** Browsers already support `:optimum`, `:sub-optimum`, and `:suboptimum` pseudo-classes on `<meter>` tied to the `optimum`, `low`, and `high` attributes, giving you Apple's "change fill color at significant thresholds" behavior without hand-rolling threshold logic in JavaScript — though visual styling of `<meter>` is inconsistent enough across browsers that many teams still build a custom widget for full control.

**The circular and "accessory" (complication-style) gauge variants don't have a native web equivalent.** There's no HTML element for a circular gauge; you're building it with SVG (a stroked arc, `stroke-dasharray` for the fill) or Canvas, and layering on the same `aria-valuenow`/`aria-valuemin`/`aria-valuemax`/`aria-valuetext` attributes by hand since a custom-drawn arc has no implicit accessible semantics at all. The "accessory" style specifically — designed to echo watchOS complications inside iOS Lock Screen widgets — has no web analogue whatsoever; it's a platform-specific visual quotation of another Apple surface, not a general gauge pattern.

**Relevance and rating styles are two different components wearing gauge-like clothing.** macOS's level indicator bundles capacity, rating, and relevance into one API family, but on the web these are unrelated concerns: a relevance bar in search results is really a data visualization (a horizontal bar chart cell), while rating belongs with star-rating UI patterns — see Rating indicators for that mapping. Don't reach for a single "gauge" component to cover all three on the web; the unification is an AppKit implementation detail, not a UX principle worth preserving.

## Do / Don't

| Do | Don't |
|---|---|
| Label the current value and both range endpoints succinctly | Rely on visual position alone to convey a gauge's value |
| Use a gradient fill when color helps communicate the gauge's purpose | Add color for decoration when it doesn't map to the value's meaning |
| Prefer the continuous capacity style for large value ranges | Use discrete segments so small they become illegible |
| Reserve the accessory style for Lock Screen widgets and complication-like contexts | Use the accessory style as a general-purpose gauge |
| Use the rating style for ranking, per Rating indicators guidance | Reuse the capacity or relevance style to represent a ranking |
| Reserve the relevance style for genuinely rare, comparison-focused contexts | Default to the relevance style for ordinary value display |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
