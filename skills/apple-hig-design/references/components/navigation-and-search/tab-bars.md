---
title: Tab bars
url: https://developer.apple.com/design/human-interface-guidelines/tab-bars
platforms: [iOS, iPadOS, macOS, tvOS, visionOS]
last_updated: 2026-06-08
---

# Tab bars

A tab bar lets people navigate between top-level sections of your app.

## Core guidance

Tab bars help people understand the different types of information or functionality that an app provides. They also let people quickly switch between sections of the view while preserving the current navigation state within each section — this second clause is the operative one: a tab bar is not just a switcher, it's a set of parallel navigation stacks that each remember where they were.

### Best practices

**Use a tab bar to support navigation, not to provide actions.** A tab bar lets people navigate among different sections of an app, like the Alarm, Stopwatch, and Timer tabs in the Clock app. If you need to provide controls that act on elements in the current view, use a toolbar instead. This is the distinction the web's ARIA `tablist` pattern blurs by convention but Apple keeps sharp: a tab bar's items are destinations, not verbs.

**Make sure the tab bar is visible when people navigate to different sections of your app.** If you hide the tab bar, people can forget which area of the app they're in. The exception is when a modal view covers the tab bar, because a modal is temporary and self-contained.

**Use the appropriate number of tabs required to help people navigate your app.** As a representation of your app's hierarchy, it's important to weigh the complexity of additional tabs against the need for people to frequently access each section; keep in mind that it's generally easier to navigate among fewer tabs. Where available, consider a sidebar or a tab bar that adapts to a sidebar as an alternative for an app with a complex information structure.

**Avoid overflow tabs.** Depending on device size and orientation, the number of visible tabs can be smaller than the total number of tabs. If horizontal space limits the number of visible tabs, the trailing tab becomes a More tab in iOS and iPadOS, revealing the remaining items in a separate list. The More tab makes it harder for people to reach and notice content on tabs that are hidden, so limit scenarios in your app where this can happen.

**Don't disable or hide tab bar buttons, even when their content is unavailable.** Having tab bar buttons available in some cases but not others makes your app's interface appear unstable and unpredictable. If a section is empty, explain why its content is unavailable — the fix is an empty state inside the tab, not removing the tab.

**Include tab labels to help with navigation.** A tab label appears beneath or beside a tab bar icon, and can aid navigation by clearly describing the type of content or functionality the tab contains. Use single words whenever possible.

**Consider using SF Symbols to provide familiar, scalable tab bar icons.** When you use SF Symbols, tab bar icons automatically adapt to different contexts. For example, the tab bar can be regular or compact, depending on the device and orientation. Tab bar icons appear above tab labels in compact views, whereas in regular views, the icons and labels appear side by side. Prefer filled symbols or icons for consistency with the platform. If you're creating custom tab bar icons, see Apple Design Resources for tab bar icon dimensions.

**Use a badge to indicate that critical information is available.** You can display a badge — a red oval containing white text and either a number or an exclamation point — on a tab to indicate that there's new or updated information in the section that warrants a person's attention. Reserve badges for critical information so you don't dilute their impact and meaning. For guidance, see Notifications.

**Avoid applying a similar color to tab labels and content layer backgrounds.** If your app already has bright, colorful content in the content layer, prefer a monochromatic appearance for tab bars, or choose an accent color with sufficient visual differentiation. For more guidance, see Liquid Glass color.

## Platform considerations

No additional considerations for macOS. Not supported in watchOS.

### iOS

A tab bar floats above content at the bottom of the screen. Its items rest on a Liquid Glass background that allows content beneath to peek through.

For tab bars with an attached accessory, like the MiniPlayer in Music, you can choose to minimize the tab bar and move the accessory inline with it when a person scrolls down. A person can exit the minimized state by tapping a tab or scrolling to the top of the view. For developer guidance, see `TabBarMinimizeBehavior` and `UITabBarController.MinimizeBehavior`.

> *Image caption:* A tab bar with an attached accessory, expanded.
> *Image caption:* A tab bar with an attached accessory, minimized.

A tab bar can include a dedicated search tab at the trailing end. For guidance, see Search fields.

### iPadOS

The system displays a tab bar near the top of the screen. You can choose to have the tab bar appear as a fixed element, or with a button that converts it to a sidebar. For developer guidance, see `tabBarOnly` and `sidebarAdaptable`.

> *Image caption:* Tab bar / Sidebar — the two states of a `sidebarAdaptable` tab view.

> **Note (Apple):** To present a sidebar without the option to convert it to a tab bar, use a navigation split view instead of a tab view. For guidance, see Sidebars.

**Prefer a tab bar for navigation.** A tab bar provides access to the sections of your app that people use most. If your app is more complex, you can provide the option to convert the tab bar to a sidebar so people can access a wider set of navigation options.

**Let people customize the tab bar.** In apps with a lot of sections that people might want to access, it can be useful to let people select items that they use frequently and add them to the tab bar, or remove items that they use less frequently. For example, in the Music app, a person can choose a favorite playlist to display in the tab bar. If you let people select their own tabs, aim for a default list of five or fewer to preserve continuity between compact and regular view sizes. For developer guidance, see `TabViewCustomization` and `UITab.Placement`.

### tvOS

A tab bar is highly customizable. For example, you can:

- Specify a tint, color, or image for the tab bar background
- Choose a font for tab items, including a different font for the selected item
- Specify tints for selected and unselected items
- Add button icons, like settings and search

By default, a tab bar is translucent, and only the selected tab is opaque. When people use the remote to focus on the tab bar, the selected tab includes a drop shadow that emphasizes its selected state.

**The height of a tab bar is 68 points, and its top edge is 46 points from the top of the screen; you can't change either of these values.**

If there are more items than can fit in the tab bar, the system truncates the rightmost item by applying a fade effect that begins at the right side of the tab bar. If there are enough items to cause scrolling, the system also applies a truncating fade effect that starts from the left side.

**Be aware of tab bar scrolling behaviors.** By default, people can scroll the tab bar offscreen when the current tab contains a single main view. You can see examples of this behavior in the Watch Now, Movies, TV Show, Sports, and Kids tabs in the TV app. The exception is when a screen contains a split view, such as the TV app's Library tab or an app's Settings screen. In this case, the tab bar remains pinned at the top of the view while people scroll the content within the primary and secondary panes of the split view. Regardless of a tab's contents, focus always returns to the tab bar at the top of the page when people press Menu on the remote.

**In a live-viewing app, organize tabs in a consistent way.** For the best experience, organize content in live-streaming apps with tabs in the following order:

1. Live content
2. Cloud DVR or other recorded content
3. Other content

For additional guidance, see Live-viewing apps.

### visionOS

In visionOS, a tab bar is always vertical, floating in a position that's fixed relative to the window's leading side. When people look at a tab bar, it automatically expands; to open a specific tab, people look at the tab and tap. While a tab bar is expanded, it can temporarily obscure the content behind it.

> *Image caption:* Collapsed and expanded states of a visionOS tab bar, with a Play tab shown expanding on look.

**Supply a symbol and a text label for each tab.** A tab's symbol is always visible in the tab bar. When people look at the tab bar, the system reveals tab labels, too. Even though the tab bar expands, you need to keep tab labels short so people can read them at a glance.

**If it makes sense in your app, consider using a sidebar within a tab.** If your app's hierarchy is deep, you might want to use a sidebar to support secondary navigation within a tab. If you do this, be sure to prevent selections in the sidebar from changing which tab is currently open.

## Native implementation

**Related**
- Tab views
- Toolbars
- Sidebars
- Materials

**Developer documentation**
- `TabView` — SwiftUI
- `TabViewBottomAccessoryPlacement` — SwiftUI
- Enhancing your app's content with tab navigation — SwiftUI
- `UITabBar` — UIKit
- Elevating your iPad app with a tab bar and sidebar — UIKit

**Key APIs**
- `TabBarMinimizeBehavior` / `UITabBarController.MinimizeBehavior` — control the minimize-on-scroll behavior for a tab bar with an attached accessory (iOS)
- `tabBarOnly` / `sidebarAdaptable` — the two style options for a tab view on iPadOS
- `TabViewCustomization` / `UITab.Placement` — let people add, remove, and reorder tabs

**Videos:** Get to know the new design system · Elevate the design of your iPad app

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A tab bar is site navigation, not the ARIA `tablist` pattern.** This is the single most important — and most commonly botched — mapping in this document. WAI-ARIA's `tablist`/`tab`/`tabpanel` pattern describes a *widget* embedded within a page: activating a tab swaps content within the same view, using arrow-key roving tabindex, and the browser's back button does not (by default) participate. Apple's tab bar is the opposite: it navigates between top-level sections of an app, each with its own state and, on the web, typically its own URL. The correct web analogue for an Apple tab bar is a **persistent site-navigation bar** — a `nav` landmark with a list of links — not `role="tablist"`. Using ARIA tabs for primary navigation breaks the browser's history model, breaks deep-linking, and confuses screen reader users who hear "tab 2 of 5" for what is actually a page.

**"Preserving navigation state within each section" → each tab needs its own history stack.** Apple's tab bar remembers where you were in each section when you switch away and back. On the web this means each top-level route should own its own scroll position, form state, and back-stack behavior — typically by keeping each section mounted (or its state cached) rather than fully unmounting on tab switch, and by giving each section a real URL so the browser's own back/forward history does the remembering for free.

**"Use a tab bar for navigation, not actions" → don't overload primary nav with commands.** The toolbar-vs-tab-bar split has a clean web equivalent: primary navigation items should be `<a>` elements that change the view; contextual actions belong in a toolbar-like control (buttons, a menu) that doesn't compete with navigation for the same visual slot.

**Badges → `aria-label` must carry the count, not just visual styling.** A red dot or number on a nav item is meaningless to a screen reader unless the accessible name includes it — "Messages, 3 unread" rather than an icon plus a decorative span. Reserve it for genuinely critical information, per Apple's own guidance, since an unread-count badge that appears everywhere trains people to ignore it.

**Overflow ("More tab") → a details/menu pattern, used sparingly.** Apple's warning that overflow makes hidden tabs harder to reach and notice applies directly to responsive web nav: collapsing extra items into a hamburger or "More" menu measurably reduces engagement with whatever lands inside it. If you must collapse, put your least-important destinations there, not your most load-bearing ones.

**Bottom-fixed placement → `position: fixed` plus safe-area insets, deliberately.** iOS's bottom tab bar sits in the thumb-reachable zone. A web app aiming for the same ergonomics on mobile needs `position: fixed` with `env(safe-area-inset-bottom)` accounted for, and must reserve equivalent padding in the scrolling content so the fixed bar never occludes the last item — Apple's Liquid Glass "content peeks through" effect is a `backdrop-filter: blur()` with a translucent background, not a rule you need to replicate exactly.

**tvOS's fixed 68-point height and exact top offset has no direct web equivalent** — that specificity exists because tvOS ships one remote-driven interaction model across all apps. The web has no equivalent single input device to standardize around, so treat it as evidence of *how much* Apple is willing to standardize spacing for a controlled input model, not as a number to port.

## Do / Don't

| Do | Don't |
|---|---|
| Use a tab bar to navigate between top-level sections | Use a tab bar to trigger actions on the current view |
| Keep the tab bar visible across a section's whole hierarchy | Hide the tab bar and leave people unsure which area they're in |
| Use as few tabs as the app's structure allows | Add overflow tabs that push items into a hidden More list |
| Keep all tab buttons enabled, even for empty sections | Disable or hide tab buttons depending on content availability |
| Label tabs with a single clear word | Leave tabs unlabeled or use vague multi-word labels |
| Reserve badges for critical, actionable information | Badge every tab so the signal loses meaning |
| On iPadOS, let a complex app offer a sidebar-convertible tab bar | Force a five-tab bar on an app with dozens of sections |
| On visionOS, keep tab labels short since they only reveal on look | Rely on a sidebar-within-a-tab to also change which tab is open |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
