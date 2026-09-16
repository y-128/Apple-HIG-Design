---
title: Pull-down buttons
url: https://developer.apple.com/design/human-interface-guidelines/pull-down-buttons
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: 2022-09-14
---

# Pull-down buttons

A pull-down button displays a menu of items or actions that directly relate to the button's purpose.

## Core guidance

After people choose an item in a pull-down button's menu, the menu closes, and the app performs the chosen action.

### Best practices

**Use a pull-down button to present commands or items that are directly related to the button's action.** The menu lets you help people clarify the button's target or customize its behavior without requiring additional buttons in your interface. For example:

- An Add button could present a menu that lets people specify the item they want to add.
- A Sort button could use a menu to let people select an attribute on which to sort.
- A Back button could let people choose a specific location to revisit instead of opening the previous one.

**If you need to provide a list of mutually exclusive choices that aren't commands, use a pop-up button instead.**

**Avoid putting all of a view's actions in one pull-down button.** A view's primary actions need to be easily discoverable, so you don't want to hide them in a pull-down button that people have to open before they can do anything.

**Balance menu length with ease of use.** Because people have to interact with a pull-down button before they can view its menu, **listing a minimum of three items** can help the interaction feel worthwhile. If you need to list only one or two items, consider using alternative components to present them, such as buttons to perform actions and toggles or switches to present selections. In contrast, listing too many items in a pull-down button's menu can slow people down because it takes longer to find a specific item.

**Display a succinct menu title only if it adds meaning.** In general, a pull-down button's content — combined with descriptive menu items — provides all the context people need, making a menu title unnecessary.

**Let people know when a pull-down button's menu item is destructive, and ask them to confirm their intent.** Menus use red text to highlight actions that you identify as potentially destructive. When people choose a destructive action, the system displays an action sheet (iOS) or popover (iPadOS) in which they can confirm their choice or cancel the action. Because an action sheet appears in a different location from the menu and requires deliberate dismissal, it can help people avoid losing data by mistake.

**Include an interface icon with a menu item when it provides value.** If you need to clarify an item's meaning, you can display an icon or image after its label. Using SF Symbols for this purpose can help you provide a familiar experience while ensuring that the symbol remains aligned with the text at every scale.

## Platform considerations

No additional considerations for macOS or visionOS. Not supported in tvOS or watchOS.

### iOS, iPadOS

> **Note (Apple):** You can also let people reveal a pull-down menu by performing a specific gesture on a button. For example, in iOS 14 and later, Safari responds to a touch and hold gesture on the Tabs button by displaying a menu of tab-related actions, like New Tab and Close All Tabs.

**Consider using a More pull-down button to present items that don't need prominent positions in the main interface.** A More button can help you offer a range of items where space is constrained, but it can also hinder discoverability. Although people generally understand that a More button offers additional functionality related to the current context, the ellipsis icon doesn't necessarily help them predict its contents. To design an effective More button, weigh the convenience of its size against its impact on discoverability to find a balance that works in your app.

## Specifications

| Item | Value |
|---|---|
| Recommended minimum items in a pull-down menu | 3 |

## Native implementation

**Related**
- Pop-up buttons
- Buttons
- Menus

**Developer documentation**
- `MenuPickerStyle` — SwiftUI
- `showsMenuAsPrimaryAction` — UIKit
- `pullsDown` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A pull-down button triggers actions, so it belongs to the ARIA `menu` family, not `listbox`.** This is the mirror image of the pop-up-button mapping: because choosing an item here *performs an action* and doesn't set the button's own displayed value, the correct pattern is a button with `aria-haspopup="menu"` and `aria-expanded`, controlling a `role="menu"` of `role="menuitem"` entries — the same disclosure-button-plus-menu pattern used for dropdown navigation and split-action buttons across the web. Using a native `<select>` here (as you would for a pop-up button) would be wrong, because a `<select>`'s job is to hold and report a value, and a pull-down menu's items don't represent a persistent value at all — the button's own label typically stays the same after you choose "Sort by Date" from a Sort button.

**"Minimum of three items to make the interaction feel worthwhile" → a genuinely useful threshold for web disclosure patterns too, and frequently ignored.** A very common web anti-pattern is a "..." or chevron button that opens a menu with a single item — which is strictly worse than making that one action a plain visible button. Apple's reasoning (an extra tap/click to reveal something has to be worth the cost) transfers directly and is a good gut-check before collapsing anything into a dropdown menu.

**Destructive-action confirmation flow → the pattern (menu item → separate confirmation surface) is the right shape; the specific surfaces don't exist on the web.** iOS's action sheet and iPadOS's popover are platform-specific presentation types. The web equivalent is any modal confirmation — a `<dialog>` element or a focus-trapped confirmation overlay — deliberately placed away from the triggering menu item so a second, separate action is required, which is the actual mechanism Apple credits for preventing accidental data loss, not the specific chrome used to present it.

**A More button using an ellipsis icon → the discoverability tradeoff Apple names is worse on the web, not equivalent.** Apple's own text admits the ellipsis icon "doesn't necessarily help them predict its contents" even on a platform where people already have some shared vocabulary for it from other apps. On the web, that shared vocabulary is thinner and inconsistent across sites, so an icon-only More button benefits even more from a visible text label ("More", "Options") or at minimum a robust `aria-label`, rather than relying on the icon to carry meaning by itself.

**A pull-down button's menu content is often dynamic** (it depends on the current item or selection) — on the web this means the `menu` region's contents should be built fresh each time the button opens rather than statically in markup, and focus should move into the menu on open and return to the trigger button on close or selection, matching the focus-management expectations screen reader users have for any ARIA `menu` widget.

## Do / Don't

| Do | Don't |
|---|---|
| Use a pull-down button for commands or items tied to the button's own action | Use a pull-down button for a set of mutually exclusive states |
| List at least three items in the menu | Hide one or two items behind an interaction that isn't worth the extra step |
| Confirm destructive menu choices in a separate action sheet or popover | Execute a destructive pull-down action immediately with no confirmation |
| Add a menu title only when it adds real meaning | Add a redundant title that repeats the button's own label |
| Use icons on menu items only when they clarify meaning | Decorate every item with an icon regardless of whether it helps |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
