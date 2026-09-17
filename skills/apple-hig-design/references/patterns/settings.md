---
title: Settings
url: https://developer.apple.com/design/human-interface-guidelines/settings
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2024-06-10
---

# Settings

People expect apps and games to just work, but they also appreciate having ways to customize the experience to fit their needs.

## Core guidance

On all Apple platforms, the system-provided Settings app lets people adjust things like the overall appearance of the system, network connections, account details, accessibility requirements, and language and region settings. On some platforms, the system-provided Settings app can also include settings for specific apps and games, often letting people adjust whether the app or game can access location information, use device features like microphone or camera, and integrate with system features like notifications, Siri, or Search.

When necessary, you can provide a custom settings area within your app or game to offer general settings that affect your overall experience, like interface style or game-saving behavior. If you need to offer settings that affect only a specific task, you can provide these options within the task itself, so people don't have to leave the experience to customize it.

### Best practices

**Aim to provide default settings that give the best experience to the largest number of people.** For example, you can automatically maximize performance for the device your game is running on instead of asking players to make this choice after your game launches (for developer guidance, see Improving your game's graphics performance and settings). When you choose appropriate default settings, people may not have to make any adjustments before they can start enjoying your app or game.

**Minimize the number of settings you offer.** Although people appreciate having control over an app or game, too many settings can make the experience feel less approachable, while also making it hard to find a particular setting.

**Make settings available in ways people expect.** For example, when a physical keyboard is connected, people often use the standard Command-Comma (,) keyboard shortcut to open an app's settings, whereas in a game, players often use the Esc (Escape) key.

**Avoid using settings to ask for setup information you can get in other ways.** For example, a game can automatically detect a connected controller or accessory instead of asking the player to identify it; an app can detect whether people are currently using Dark Mode.

**Respect people's systemwide settings and avoid including redundant versions of them in your custom settings area.** People expect to use the system-provided Settings app to manage global options like accessibility accommodations, scrolling behavior, and authentication methods, and they expect all apps and games to adhere to their choices. Including custom versions of global options in your settings area is likely to confuse people because it implies that systemwide settings may not apply to your app or game and that changing your custom version of a global setting may affect other apps and games, too.

### General settings

**Put general, infrequently changed settings in your custom settings area.** People must suspend what they're doing to open an app's or game's settings area, so you want to include options that people don't need to change all the time. For example, an app might list options for adjusting window configuration; a game might let players specify game-saving behavior or keyboard mappings; both apps and games might offer options related to people's accounts.

### Task-specific options

**When possible, prefer letting people modify task-specific options without going to your settings area.** For example, if people can adjust things like showing or hiding parts of the current view, reordering a collection of items, or filtering a list, make these options available in the screens they affect, where they're discoverable and convenient. Putting this type of option in a separate settings area disconnects it from its context, requiring people to suspend their task to make adjustments, and often hiding the results until people resume the task.

> **Note (Apple):** In games, players tend to adjust their approach to a specific task as part of the gameplay, not as a settings option to change.

### System settings

**Add only the most rarely changed options to the system-provided Settings app.** If it makes sense to add your app's or game's settings to the system-provided Settings app, consider providing a button that opens it directly from your interface.

## Platform considerations

No additional considerations for iOS, iPadOS, tvOS, or visionOS.

### macOS

When people choose the Settings item in your app's or game's App menu, your custom settings window opens. Typically, a custom settings window contains a toolbar that includes buttons for switching between views — called panes — that each contain a group of related settings.

**Include a settings item in the App menu.** Avoid adding settings buttons to a window's toolbar, because doing so decreases the space available for essential commands that people use frequently. If you provide document-level options, add this item to your app's File menu.

**Dim a settings window's minimize and maximize buttons.** It's quick to open a custom settings window using the standard Command–Comma (,) keyboard command, so there's no need to keep the window in the Dock, and because a settings window accommodates the size of the current pane, people don't need to expand the window to see more.

**In your settings window, use a noncustomizable toolbar that remains visible and always indicates the active toolbar button.** A settings window's toolbar identifies the areas people can customize and helps people navigate among those areas. People rely on a stable settings interface to help them find what they need.

**Update the window's title to reflect the currently visible pane.** If your settings window doesn't have multiple panes, use the title *App Name* Settings.

**Restore the most recently viewed pane.** People often adjust related settings more than once, so it can be convenient when a settings window opens to the last pane people used.

### watchOS

In watchOS, apps and games don't add custom settings to the system-provided Settings app. As an alternative, consider making a small number of essential options available at the bottom of the main view or letting people use a More menu to reconfigure objects.

## Native implementation

**Related**
- Onboarding

**Developer documentation**
- Settings — SwiftUI
- `UserDefaults` — Foundation
- Preference Panes

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Provide defaults that work for the largest number of people" → the strongest lever on the web is that most visitors never open settings at all.** Apple's reasoning holds even more forcefully on the web, where the friction to find a settings page is often higher than a native app's Command-Comma shortcut. A web product's default configuration is, for most users, its only configuration; treat every default as a decision made on their behalf, not a placeholder waiting to be corrected in a preferences panel almost no one will visit.

**"Minimize the number of settings" → every toggle is a permanent maintenance and testing liability, on the web more than most platforms.** A native app's settings combine multiplicatively with device and OS versions; a web app's settings combine multiplicatively with settings *and* browsers *and* viewport sizes *and* input methods. The combinatorial cost of an extra toggle is higher on the web, which strengthens rather than weakens Apple's minimize-settings advice.

**"Make settings available in expected ways" → Command/Ctrl+, has no browser-reserved meaning, so borrow the convention deliberately if you use it.** Unlike a native macOS app, a web app can't rely on the OS routing that shortcut to it system-wide, and the browser doesn't reserve it. If you choose to bind it, you're adopting a convention users bring from native apps, not one the web platform enforces — bind it in a way that doesn't conflict with the browser's own shortcuts, and don't assume people will discover it without a visible affordance too.

**"Don't ask for setup information you can get another way" → maps directly onto `prefers-color-scheme`, `prefers-reduced-motion`, and similar media queries.** Apple's Dark Mode example is close to literal: a web app can detect the OS-level color-scheme preference instead of asking people to pick light or dark inside its own settings, and can detect a stated preference for reduced motion the same way. This is one of the cleanest one-to-one mappings in this whole document — the browser exposes the same category of ambient system state Apple is telling native developers to read instead of re-asking for.

**"Respect systemwide settings, don't offer redundant custom versions of them" → respect the OS/browser preference by default, and be honest about when you're deliberately overriding it.** A web app that ships its own light/dark toggle *in addition to* ignoring `prefers-color-scheme` reproduces exactly the confusion Apple describes: a custom setting that implies the systemwide choice doesn't apply here. Where a genuine product reason exists to let people override the ambient preference (many apps do this reasonably, since browser support for reading the preference varies and users sometimes want independent control), make it default to the system preference and let the override be additive, not a fight against it.

**"Task-specific options belong with the task, not in a separate settings area" → this is a stronger argument for the web than it is natively, because the web has near-zero cost for inline controls.** A view toggle, sort order, or filter belongs as a control in the toolbar of the view it affects, addressable via the URL (a query parameter) so the choice survives a reload or a shared link — something native apps generally can't offer as cheaply. Burying a list's sort order in a global settings page is worse on the web than on iOS, because the web could have made it a URL-visible, shareable, reload-safe inline control almost for free.

**General settings persistence → `localStorage`/account-synced preferences are the direct equivalent of `UserDefaults`, with the same caveat about scope.** `UserDefaults` is per-device unless explicitly synced; `localStorage` is per-browser-per-origin and doesn't sync across devices unless you build that yourself (account-backed settings, synced via your backend). If a setting genuinely feels like it should follow the person rather than the device — which is Apple's implicit assumption for "general, infrequently changed settings" tied to an account — plan for server-side persistence, not just local storage, or the parity with Apple's model breaks the first time someone opens the app on a second device.

**Where the mapping is weakest: there is no web equivalent of a single system-provided Settings app that other apps can register into.** Apple's model assumes a shared, OS-level settings surface that any app can add a pane to, and a strong convention that only "rarely changed options" belong there. The web has no analogous shared surface — every site's settings live entirely inside that site. The closest partial equivalent is the browser's own per-site permission and preference panel (camera, location, notifications), which is genuinely outside your app's control and which Apple's "respect systemwide settings" principle argues you should defer to rather than duplicate.

## Do / Don't

| Do | Don't |
|---|---|
| Choose defaults that work for most people out of the box | Make people configure the app before it's usable |
| Keep the settings surface small and focused | Offer a setting for every possible variation |
| Detect information you can infer instead of asking | Ask people to restate what the system already knows |
| Respect systemwide preferences by default | Duplicate a systemwide setting inside your own app |
| Put task-specific options in the task's own view | Bury frequently needed task options in a settings screen |
| Put only rarely changed options in a custom settings area | Make people visit settings for something they adjust often |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
