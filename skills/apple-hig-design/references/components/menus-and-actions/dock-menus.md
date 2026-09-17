---
title: Dock menus
url: https://developer.apple.com/design/human-interface-guidelines/dock-menus
platforms: [macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Dock menus

On a Mac, people can secondary click an app's or game's icon in the Dock to reveal a Dock menu, which presents both system-provided and custom items.

## Core guidance

The system-provided Dock menu items can vary depending on whether the app is open. For example, the Dock menu for Safari includes menu items for actions like viewing a current window or creating a new window.

> **Note (Apple):** Although iOS and iPadOS don't support a Dock menu, people can reveal a similar menu of system-provided and custom items — called Home Screen quick actions — when they long press an app icon on the Home Screen or in the Dock. For guidance, see Home Screen quick actions.

### Best practices

**As with all menus, you need to label Dock menu items succinctly and organize them logically.** For guidance, see Menus.

**Make custom Dock menu items available in other places, too.** Not everyone uses a Dock menu, so it's important to offer the same commands elsewhere, like in your menu bar menus or within your interface.

**Prefer high-value custom items for your Dock menu.** For example, a Dock menu can list all currently or recently open windows, making it a convenient way to jump to the window people want. Also consider listing a few of the actions that are most likely to be useful when your app isn't frontmost or when there are no open windows. For example, Mail includes items for getting new mail and composing a new message in addition to listing all open windows.

## Platform considerations

Not supported in iOS, iPadOS, tvOS, visionOS, or watchOS. Dock menus exist only in macOS; iOS and iPadOS provide the related but distinct Home Screen quick actions instead (see Home Screen quick actions).

## Native implementation

**Related**
- Menus
- Home Screen quick actions

**Developer documentation**
- applicationDockMenu(_:) — AppKit

**Key APIs**
- `applicationDockMenu(_:)` — AppKit, supplies the custom items an app adds to its Dock menu

## Web translation *(derived — not from Apple)*

This topic is platform-bound and has no meaningful web analogue. A Dock menu depends on a persistent, OS-managed icon that stays present and secondary-clickable whether or not the app is frontmost or even running — a web page has no equivalent standing presence outside an open browser tab. A pinned or installed Progressive Web App icon on a taskbar or dock (on platforms that support installable PWAs) comes closest, and some desktop operating systems do let an installed PWA register a right-click jump list with a handful of actions. Where that capability exists, the one principle that does transfer is Apple's core guidance: keep the list short, high-value, and duplicated elsewhere in the app's own UI, since most people will never discover it. Anything beyond that — the specific menu structure, the open-window listing, the frontmost/backgrounded distinction — is native window-management behavior a web page cannot replicate.

## Do / Don't

| Do | Don't |
|---|---|
| Label Dock menu items succinctly and organize them logically | Rely on a Dock menu as the only place to offer a command |
| List a few high-value actions, including ones useful when the app isn't frontmost | Fill the Dock menu with low-value or rarely-used items |
| Offer custom Dock menu commands elsewhere too (menu bar, in-app UI) | Assume everyone discovers or uses the Dock menu |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
