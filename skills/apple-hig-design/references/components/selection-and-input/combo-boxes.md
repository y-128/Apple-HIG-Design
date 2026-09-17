---
title: Combo boxes
url: https://developer.apple.com/design/human-interface-guidelines/combo-boxes
platforms: [macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Combo boxes

A combo box combines a text field with a pull-down button in a single control.

## Core guidance

People can enter a custom value into the field or click the button to choose from a list of predefined values. When people enter a custom value, it's not added to the list of choices.

### Best practices

**Populate the field with a meaningful default value from the list.** Although the field can be empty by default, it's best when the default value refers to the hidden choices. The default value doesn't have to be the first item in the list.

**Use an introductory label to let people know what types of items to expect.** Generally, use title-style capitalization for labels and end them with a colon. For related guidance, see Labels.

**Provide relevant choices.** People appreciate the ability to enter a custom value, as well as the convenience of choosing from a list of the most likely choices.

**Make sure list items aren't wider than the text field.** If an item is too wide, the text field might truncate it, which is hard for people to read.

For guidance, see Text fields and Pull-down buttons.

## Platform considerations

Not supported in iOS, iPadOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Text fields
- Pull-down buttons

**Developer documentation**
- `NSComboBox` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**The closest native element, and why it's not a real match.** HTML has `<input list="...">` paired with a `<datalist>`, which looks like a combo box on the surface: a text field that also offers a dropdown of suggestions, and accepts free text. In practice it's a much weaker control. Browsers give you no control over the dropdown's styling, no reliable way to detect when it's open or closed, inconsistent keyboard behavior across browsers, and no equivalent to macOS's pull-down button affordance that visually separates "type here" from "choose from list." Treat `<input list>` as a reasonable *baseline* for simple cases, not a drop-in translation of `NSComboBox`.

**Why a custom combo box is one of the highest-accessibility-debt widgets you can build.** The moment `<input list>`'s limitations force a custom implementation, you inherit the ARIA `combobox` pattern's full complexity: managing `aria-expanded`, `aria-activedescendant`, roving focus through the listbox, and matching platform-specific screen reader expectations, none of which match each other exactly. Apple's `NSComboBox` gets all of this for free from AppKit. A hand-rolled web combo box does not, and getting it wrong is worse than not offering the list at all, because it can trap keyboard and screen reader users rather than just failing to suggest values. Use a well-maintained accessible combobox implementation rather than building the interaction from scratch.

**"Default value refers to the hidden choices" → placeholder text is not a substitute for a real default.** Apple's advice to populate the field with a meaningful value, rather than leaving it blank, matters more on the web because a `placeholder` attribute disappears the instant a person interacts with the field and is not read reliably by all assistive technology as a persistent label. If the combo box needs a suggested starting value, put it in the field's actual value, and keep a separate, persistent label for what kind of input is expected — matching Apple's separate "introductory label" guidance.

**"List items must not be wider than the text field" → the same truncation problem, worse on the web.** Native `<select>` and `<datalist>` dropdowns are rendered by the OS and can be wider than their trigger, so this specific failure mode doesn't reproduce identically. But a custom-built dropdown that inherits the trigger's width will truncate long options exactly as Apple describes, and CSS text overflow with no visual indicator is a common way this goes unnoticed until a user hits it.

## Do / Don't

| Do | Don't |
|---|---|
| Populate the field with a meaningful default drawn from the list | Leave the field empty when a default value would help |
| Use a persistent introductory label for the expected input type | Rely on placeholder text as the only explanation of the field |
| Offer a relevant, reasonably short list of predefined choices | Fill the list with items wider than the text field |
| Let people type a custom value not on the list | Force people to only pick from the visible list |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
