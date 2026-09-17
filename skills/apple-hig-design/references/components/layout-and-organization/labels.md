---
title: Labels
url: https://developer.apple.com/design/human-interface-guidelines/labels
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-06-05
---

# Labels

A label is a static piece of text that people can read and often copy, but not edit.

## Core guidance

Labels display text throughout the interface, in buttons, menu items, and views, helping people understand the current context and what they can do next.

The term label refers to uneditable text that can appear in various places. For example:

- Within a button, a label generally conveys what the button does, such as Edit, Cancel, or Send.
- Within many lists, a label can describe each item, often accompanied by a symbol or an image.
- Within a view, a label might provide additional context by introducing a control or describing a common action or task that people can perform in the view.

> **Developer note (Apple):** To display uneditable text, SwiftUI defines two components: `Label` and `Text`.

The guidance below can help you use a label to display text. In some cases, guidance for specific components — such as action buttons, menus, and lists and tables — includes additional recommendations for using text.

### Best practices

**Use a label to display a small amount of text that people don't need to edit.** If you need to let people edit a small amount of text, use a text field. If you need to display a large amount of text, and optionally let people edit it, use a text view.

**Prefer system fonts.** A label can display plain or styled text, and it supports Dynamic Type (where available) by default. If you adjust the style of a label or use custom fonts, make sure the text remains legible.

**Use system-provided label colors to communicate relative importance.** The system defines four label colors that vary in appearance to help you give text different levels of visual importance. For additional guidance, see Color.

| System color | Example usage | iOS, iPadOS, tvOS, visionOS | macOS |
|---|---|---|---|
| Label | Primary information | `label` | `labelColor` |
| Secondary label | A subheading or supplemental text | `secondaryLabel` | `secondaryLabelColor` |
| Tertiary label | Text that describes an unavailable item or behavior | `tertiaryLabel` | `tertiaryLabelColor` |
| Quaternary label | Watermark text | `quaternaryLabel` | `quaternaryLabelColor` |

**Make useful label text selectable.** If a label contains useful information — like an error message, a location, or an IP address — consider letting people select and copy it for pasting elsewhere.

## Platform considerations

No additional considerations for iOS, iPadOS, tvOS, or visionOS.

### macOS

> **Developer note (Apple):** To display uneditable text in a label, use the `isEditable` property of `NSTextField`.

### watchOS

Date and time text components display the current date, the current time, or a combination of both. You can configure a date text component to use a variety of formats, calendars, and time zones. A countdown timer text component displays a precise countdown or count-up timer. You can configure a timer text component to display its count value in a variety of formats.

> *Image caption:* Date and time labels, and a timer label.

When you use the system-provided date and timer text components, watchOS automatically adjusts the label's presentation to fit the available space. The system also updates the content without further input from your app.

**Consider using date and timer components in complications.** For design guidance, see Complications; for developer guidance, see `Text`.

## Native implementation

**Related**
- Text fields
- Text views

**Developer documentation**
- `Label` — SwiftUI
- `Text` — SwiftUI
- `UILabel` — UIKit
- `NSTextField` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A label as read-only text with a specific role → don't reach for an `<input readonly>` or `<textarea disabled>` for genuinely static text.** Apple's model separates three roles by editability and length: a label for short uneditable text, a text field for short editable text, a text view for long text that may or may not be editable. On the web this reasoning argues for matching the element to the role rather than defaulting everything to a form control — plain text in a `<span>`, `<p>`, or `<dd>` for a label, an `<input>` for a short editable field, a `<textarea>` for long editable text. Using a disabled or read-only form control for static text adds unnecessary form semantics (and, in some screen readers, unnecessary announcements) that the content doesn't have.

**System fonts and Dynamic Type by default → inherit type styles, don't hardcode a label's font.** The reasoning is that a label should track the same legibility and scaling behavior as the rest of the interface without special-casing. The web equivalent is letting label text inherit from the page's type scale (see the Typography reference's Dynamic Type mapping) rather than setting a fixed pixel size on every label class.

**Four label colors expressing relative importance → a small, ordered set of text-color tokens, not ad hoc grays.** Apple's reasoning is that importance should be visually legible through a consistent, limited vocabulary (primary, secondary, tertiary, quaternary) rather than through arbitrary opacity or color choices scattered across the codebase. The web analogue is a small set of named text-color custom properties tied to the same primary/secondary/tertiary/quaternary levels, reused everywhere rather than re-decided per component. Where this mapping is weaker: Apple's four levels are also tuned per-platform for contrast against system materials; a web implementation needs its own contrast check against its own actual backgrounds, in both light and dark themes, rather than assuming the four-level structure alone guarantees accessible contrast.

**Selectable label text for useful information → don't disable text selection on content people plausibly need to copy.** Apple's reasoning is narrow and practical: error messages, locations, IP addresses, and similar values are things people want to select and paste elsewhere. The web default already makes text selectable, so the actionable translation is the negative case — don't apply `user-select: none` to this category of content for aesthetic reasons, and don't render it as a canvas/image or inside a component that blocks selection.

## Do / Don't

| Do | Don't |
|---|---|
| Use a label for short text people don't need to edit | Use a label where people actually need to edit the text |
| Use a text field for short editable text | Repurpose a label as a makeshift editable field |
| Use a text view for long text, editable or not | Cram a large block of text into a label |
| Use the four system label colors to signal importance | Invent ad hoc colors or opacities to show importance |
| Let useful label text (errors, IPs, locations) be selectable | Lock down selection on text people need to copy |
| Prefer system fonts and Dynamic Type support | Force custom fonts that break legibility or scaling |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
