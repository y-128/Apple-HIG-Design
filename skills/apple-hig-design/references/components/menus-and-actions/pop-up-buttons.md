---
title: Pop-up buttons
url: https://developer.apple.com/design/human-interface-guidelines/pop-up-buttons
platforms: [iOS, macOS, iPadOS, visionOS]
last_updated: 2023-10-24
---

# Pop-up buttons

A pop-up button displays a menu of mutually exclusive options.

## Core guidance

After people choose an item from a pop-up button's menu, the menu closes, and the button can update its content to indicate the current selection.

### Best practices

**Use a pop-up button to present a flat list of mutually exclusive options or states.** A pop-up button helps people make a choice that affects their content or the surrounding view. Use a pull-down button instead if you need to:

- Offer a list of actions
- Let people select multiple items
- Include a submenu

**Provide a useful default selection.** A pop-up button can update its content to identify the current selection, but if people haven't made a selection yet, it shows the default item you specify. When possible, make the default selection an item that most people are likely to want.

**Give people a way to predict a pop-up button's options without opening it.** For example, you can use an introductory label or a button label that describes the button's effect, giving context to the options.

**Consider using a pop-up button when space is limited and you don't need to display all options all the time.** Pop-up buttons are a space-efficient way to present a wide array of choices.

**If necessary, include a Custom option in a pop-up button's menu to provide additional items that are useful in some situations.** Offering a Custom option can help you avoid cluttering the interface with items or controls that people need only occasionally. You can also display explanatory text below the list to help people understand how the options work.

## Platform considerations

No additional considerations for iOS, macOS, or visionOS. Not supported in tvOS or watchOS.

### iPadOS

**Within a popover or modal view, consider using a pop-up button instead of a disclosure indicator to present multiple options for a list item.** For example, people can quickly choose an option from the pop-up button's menu without navigating to a detail view. Consider using a pop-up button in this scenario when you have a fairly small, well-defined set of options that work well in a menu.

## Native implementation

**Related**
- Pull-down buttons
- Buttons
- Menus

**Developer documentation**
- `MenuPickerStyle` — SwiftUI
- `changesSelectionAsPrimaryAction` — UIKit
- `NSPopUpButton` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A pop-up button chooses among mutually exclusive values — that's a `<select>`, not a menu button.** This is the single most important distinction on this page, and it's the same distinction Apple draws to separate pop-up buttons from pull-down buttons. Because a pop-up button represents a *value* (the button's own content updates to show the current selection), the correct web element is a native `<select>` or, where richer visuals are required, a `role="listbox"` combobox pattern — not `role="menu"`. Reaching for a generic dropdown built from `menu`/`menuitem` roles is the most common mismatch here: it gives keyboard users menu-style Escape/arrow behavior instead of the selection-style behavior a `<select>` provides, and it drops native form semantics (the value participates in form submission, gets included in `FormData`, works with `<label for>`, and needs no JavaScript to function at all).

**"The button updates its content to indicate current selection" → this is exactly what a native `<select>` already does for free.** A styled native `<select>` shows the chosen option as its own display text automatically; a custom-built pop-up button has to replicate that binding by hand, along with keyboard type-ahead (typing a letter jumps to the matching option), which native `<select>` also provides without extra code.

**"Provide a useful default selection" → maps to picking a sensible pre-selected `<option>`, not leaving the first alphabetical value as the default by accident.** The web-specific trap is that `<select>` defaults to whichever option is first in markup order unless one is explicitly marked `selected`; that default is frequently the wrong one for the actual most-likely user choice, which is exactly the failure Apple's guidance is warning against.

**"Give people a way to predict the button's options without opening it" → an adjacent `<label>`, not placeholder text inside the control.** A `<label for="...">` sitting next to or above the `<select>` is the direct equivalent of Apple's introductory label. Using the first option as a disabled "placeholder" (a common web pattern, e.g. "Choose a size") is a weaker substitute — it consumes a real option slot and some screen reader/browser combinations announce it inconsistently — so a persistent visible label is the more faithful mapping.

**A "Custom" option that reveals more controls → still needs the same escape hatch on the web, and it's an interaction pattern, not a markup one.** Nothing platform-specific here: selecting an option that itself triggers a secondary input (a custom color field, a custom date) is a normal `onchange`-driven progressive-disclosure pattern, and Apple's advice to explain how the option works with adjacent text applies unchanged.

## Do / Don't

| Do | Don't |
|---|---|
| Use a pop-up button for a flat set of mutually exclusive options | Use a pop-up button to offer a list of independent actions |
| Provide a sensible default selection | Leave the default item to whatever happens to be first |
| Give context about the options before the menu opens | Rely on people opening the menu just to understand what it contains |
| Include a Custom option for occasionally needed values | Clutter the main interface with rarely used controls instead |
| In iPadOS, use a pop-up button for small, well-defined option sets inside a popover or modal | Force a full detail-view navigation for a two- or three-option choice |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
