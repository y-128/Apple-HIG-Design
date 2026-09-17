---
title: Home Screen quick actions
url: https://developer.apple.com/design/human-interface-guidelines/home-screen-quick-actions
platforms: [iOS, iPadOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Home Screen quick actions

Home Screen quick actions give people a way to perform app-specific actions from the Home Screen.

## Core guidance

People can get a menu of available quick actions when they touch and hold an app icon (on a 3D Touch device, people can press on the icon with increased pressure to see the menu). For example, Mail includes quick actions that open the Inbox or the VIP mailbox, initiate a search, and create a new message. In addition to app-specific actions, a Home Screen quick action menu also lists items for removing the app and editing the Home Screen.

Each Home Screen quick action includes a title, an interface icon on the left or right (depending on your app's position on the Home Screen), and an optional subtitle. The title and subtitle are always left-aligned in left-to-right languages. Your app can even dynamically update its quick actions when new information is available. For example, Messages provides quick actions for opening your most recent conversations.

### Best practices

**Create quick actions for compelling, high-value tasks.** For example, Maps lets people search near their current location or get directions home without first opening the Maps app. People tend to expect every app to provide at least one useful quick action; you can provide a total of **four**.

**Avoid making unpredictable changes to quick actions.** Dynamic quick actions are a great way to keep actions relevant. For example, it may make sense to update quick actions based on the current location or recent activities in your app, time of day, or changes in settings. Make sure that actions change in ways that people can predict.

**For each quick action, provide a succinct title that instantly communicates the results of the action.** For example, titles like "Directions Home," "Create New Contact," and "New Message" can help people understand what happens when they choose the action. If you need to give more context, provide a subtitle too. Mail uses subtitles to indicate whether there are unread messages in the Inbox and VIP folder. Don't include your app name or any extraneous information in the title or subtitle, keep the text short to avoid truncation, and take localization into account as you write the text.

**Provide a familiar interface icon for each quick action.** Prefer using SF Symbols to represent actions. For a list of icons that represent common actions, see Standard icons; for additional guidance, see Menus.

If you design your own interface icon, use the Quick Action Icon Template that's included with Apple Design Resources for iOS and iPadOS.

**Don't use an emoji in place of a symbol or interface icon.** Emojis are full color, whereas quick action symbols are monochromatic and change appearance in Dark Mode to maintain contrast.

## Platform considerations

No additional considerations for iOS or iPadOS. Not supported in macOS, tvOS, visionOS, or watchOS.

## Specifications

| Item | Value |
|---|---|
| Maximum quick actions per app | 4 |

## Native implementation

**Related**
- Menus

**Developer documentation**
- Add Home Screen quick actions — UIKit

**Key APIs**
- `UIApplicationShortcutItem` — UIKit, defines a static or dynamic Home Screen quick action
- SF Symbols — recommended source for quick action icons

## Web translation *(derived — not from Apple)*

This topic is platform-bound and has no meaningful web analogue. Home Screen quick actions depend on a native app icon that the OS lets people touch and hold to reveal a system-managed menu — a capability tied to the app being installed as a first-class OS object, not a browser tab. The closest partial equivalent is the web app manifest's `shortcuts` member, which lets an installed Progressive Web App register up to a handful of jump-list-style actions on platforms that support installable PWAs and read that manifest field; support and the resulting interaction (long-press versus right-click, depending on OS) vary by platform and are far less consistent than Apple's native mechanism. Where that capability is available, the transferable principles are the same ones Apple states for the native feature: keep the list to a handful of genuinely high-value actions, give each a short and unambiguous label, and don't put your app's own name in the label since the icon and context already identify the app.

## Do / Don't

| Do | Don't |
|---|---|
| Reserve quick actions for compelling, high-value tasks | Add a quick action for every minor feature |
| Keep changes to dynamic quick actions predictable | Change quick actions in ways people can't anticipate |
| Write succinct titles that communicate the result | Include your app name or extraneous text in the title |
| Use a subtitle for extra context when needed | Overload the title with information that belongs in a subtitle |
| Use SF Symbols or a template-based custom icon | Use an emoji in place of a symbol or interface icon |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
