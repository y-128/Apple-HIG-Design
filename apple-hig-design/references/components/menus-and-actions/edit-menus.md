---
title: Edit menus
url: https://developer.apple.com/design/human-interface-guidelines/edit-menus
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: 2023-06-21
---

# Edit menus

An edit menu lets people make changes to selected content in the current view, in addition to offering related commands like Copy, Select, Translate, and Look Up.

## Core guidance

In addition to text, an edit menu's commands can apply to many types of selectable content, such as images, files, and objects like contact cards, charts, or map locations. In iOS, iPadOS, and visionOS, the system automatically detects the data type of a selected item, which can result in the addition of a related action to the edit menu. For example, selecting an address can add an item like Get directions to the edit menu.

Edit menus can look and behave slightly differently in different platforms.

- In iOS, the edit menu displays commands in a compact, horizontal list that appears when people touch and hold or double-tap to select content in a view. People can tap a chevron on the trailing edge to expand it into a context menu.
- In iPadOS, the edit menu looks different depending on how people reveal it. When people use touch interactions to reveal the menu, it uses the compact, horizontal appearance. In contrast, when people use a keyboard or pointing device to reveal it, the edit menu opens directly in a context menu.
- In macOS, people can access editing commands in a context menu they can reveal while in an editing task, as well as through the app's Edit menu in the menu bar.
- In visionOS, people use the standard pinch and hold gesture to open the edit menu as a horizontal bar, or they can open it in a context menu.

Editing content is rare in tvOS and watchOS experiences, so the system doesn't provide an edit menu in these platforms.

### Best practices

**Prefer the system-provided edit menu.** People are familiar with the contents and behavior of the system-provided component, so creating a custom menu that presents the same commands is redundant and likely to be confusing. For a list of standard edit menu commands, see UIResponderStandardEditActions.

**Let people reveal an edit menu using the system-defined interactions they already know.** For example, people expect to touch and hold on a touchscreen, pinch and hold in visionOS, or use a secondary click with an attached trackpad or keyboard. Although the interactions to reveal an edit menu can differ based on platform, people don't appreciate having to learn a custom interaction to perform a standard task.

**Offer commands that are relevant in the current context, removing or dimming commands that don't apply.** For example, if nothing is selected, avoid showing options that require a selection, such as Copy or Cut. Similarly, avoid showing a Paste option when there's nothing to paste.

**List custom commands near relevant system-provided ones.** For example, if you offer custom formatting commands, you can help maintain the ordering people expect by listing them after the system-provided commands in the format section. Avoid overwhelming people with too many custom commands.

**When it makes sense, let people select and copy noneditable text.** People appreciate being able to paste static content — such as an image caption or social media status — into a message, note, or web search. In general, let people copy content text, but not control labels.

**Support undo and redo when possible.** Like all menus, an edit menu doesn't require confirmation before performing its actions, so people can easily use undo and redo to recover a previous state. For guidance, see Undo and redo.

**In general, avoid implementing other controls that perform the same functions as edit menu items.** People typically expect to choose familiar edit commands in an edit menu, or use standard keyboard shortcuts. Offering redundant controls can crowd your interface, giving you less space for presenting actions that people might not already know about.

**Differentiate different types of deletion commands when necessary.** For example, a Delete menu item behaves the same as pressing a Delete key, but a Cut menu item copies the selected content to the system pasteboard before deleting it.

### Content

**Create short labels for custom commands.** Use verbs or short verb phrases that succinctly describe the action your command performs. For guidance, see Labels.

## Platform considerations

No additional considerations for visionOS. Not supported in tvOS or watchOS.

### iOS, iPadOS

**Ensure your edit menu works well in both styles.** The system displays the compact, horizontal style when people use Multi-Touch gestures to reveal the edit menu, and the vertical style when people use a keyboard or pointing device to reveal it. For guidance using the vertical menu layout, see Menus > iOS, iPadOS.

**Adjust an edit menu's placement, if necessary.** Depending on available space, the default menu position is above or below the insertion point or selection. The system also displays a visual indicator that points to the targeted content. Although you can't change the shape of the menu or its pointer, you can change the menu's position. For example, you might need to move the menu to prevent it from covering important content or parts of your interface.

### macOS

To learn about the order of items in a macOS app's Edit menu, see the standard Edit menu described in The menu bar.

## Native implementation

**Related**
- Menus
- Context menus
- The menu bar
- Undo and redo

**Developer documentation**
- UIEditMenuInteraction — UIKit
- NSMenu — AppKit

**Key APIs**
- `UIEditMenuInteraction` — UIKit, attaches the system edit menu to a view
- `UIResponderStandardEditActions` — the standard set of edit menu commands (Copy, Cut, Paste, Select, and related actions)
- `NSMenu` — AppKit, macOS's context and menu bar Edit menu

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Prefer the system-provided edit menu" → prefer the browser's native selection and context menu wherever possible.** Browsers already provide Copy, Cut, Paste, and Select All on any selectable text through the native context menu and standard keyboard shortcuts. Building a custom in-page edit menu duplicates behavior people already have, and — unlike native platform menus — a web reimplementation can't intercept the OS clipboard as smoothly, since clipboard API access is permission-gated and inconsistent across browsers.

**"Let people reveal it using interactions they already know" → don't replace the native context menu unless you're adding real value.** Overriding `contextmenu` to show a custom menu removes the browser's built-in options (Inspect, Open Link, Search With…) unless you deliberately re-add them, which is a worse trade than it looks. If you do offer a custom edit/selection menu (for example, a rich-text editor's floating toolbar), make it additive — appearing alongside or after a text selection — rather than a full replacement of native behavior.

**"Offer commands relevant in the current context, dimming what doesn't apply" → is a direct, unmodified transfer.** Any custom selection toolbar in a web editor should only show Cut when there's an editable selection, only show Paste when the Clipboard API confirms there's content to paste (where that check is available), and so on.

**Detecting a selected data type and offering a related action (Apple's "Get directions" example) → has no reliable client-side equivalent.** iOS's system-level data detectors run with OS access to a person's contacts, maps, and locale that a web page does not have. A web app can approximate this only by running its own lightweight text-classification heuristics (recognizing an address-shaped string, a phone number pattern) and offering a matching action — a much narrower capability than the system-wide feature Apple describes.

**Noneditable text → `user-select` should default to allowing copy.** Apple's rule that people should be able to copy content text but not control labels maps to CSS `user-select`: leave body copy and captions selectable, and reserve `user-select: none` for interactive chrome (button labels, tab titles) where a selection would be visual noise rather than useful content.

## Do / Don't

| Do | Don't |
|---|---|
| Prefer the system-provided (or browser-native) edit menu | Build a custom menu that duplicates standard commands |
| Let people reveal the menu with the interaction they already know | Require a custom, undocumented interaction to reach editing commands |
| Show only commands relevant to the current selection | Show Copy/Cut when nothing is selected, or Paste when the clipboard is empty |
| List custom commands after system-provided ones, in the same section | Scatter custom commands ahead of or between standard ones |
| Let people copy noneditable content text | Let people copy interface control labels |
| Support undo and redo for edit menu actions | Require confirmation dialogs before an edit menu action |
| Use a Delete item for delete-without-clipboard, Cut for delete-with-clipboard | Use ambiguous naming like Erase or Clear in place of Delete |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
