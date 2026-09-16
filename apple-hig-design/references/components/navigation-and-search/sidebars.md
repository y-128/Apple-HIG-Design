---
title: Sidebars
url: https://developer.apple.com/design/human-interface-guidelines/sidebars
platforms: [iOS, iPadOS, macOS, tvOS, visionOS]
last_updated: 2026-06-08
---

# Sidebars

A sidebar appears on the leading side of a view and lets people navigate between areas of your app or top-level collections of content, like folders and playlists.

## Core guidance

A sidebar requires a large amount of vertical and horizontal space. When space is limited or you want to devote more of the screen to other information or functionality, a more compact control such as a tab bar may provide a better navigation experience. For many apps, you don't need to choose between a tab bar or sidebar for navigation; instead, you can adopt a style of tab bar that provides both. For guidance, see Tab bars and Layout.

### Best practices

**Extend visually rich content beneath the sidebar.** In iOS, iPadOS, and macOS, as with other controls such as toolbars and tab bars, sidebars can float above content in the Liquid Glass layer. To reinforce the separation, you can extend content beneath the sidebar either by letting it horizontally scroll or by applying a background extension effect. A background extension effect mirrors adjacent content to give the impression of stretching it under the sidebar. For developer guidance, see `backgroundExtensionEffect()`.

**When possible, let people customize the contents of a sidebar.** A sidebar lets people navigate to important areas in your app, so it works well when people can decide which areas are most important and in what order they appear.

**Group hierarchy with disclosure controls if your app has a lot of content.** Using disclosure controls helps keep the sidebar's vertical space to a manageable level.

**Consider using familiar symbols to represent items in the sidebar.** SF Symbols provides a wide range of customizable symbols you can use to represent items in your app. If you need to use a custom icon, consider creating a custom symbol rather than using a bitmap image. Download the SF Symbols app from Apple Design Resources.

**Consider letting people hide the sidebar.** People sometimes want to hide the sidebar to create more room for content details or to reduce distraction. When possible, let people hide and show the sidebar using the platform-specific interactions they already know. For example, in iPadOS, people expect to use the built-in edge swipe gesture; in macOS, you can include a show/hide button or add Show Sidebar and Hide Sidebar commands to your app's View menu. In visionOS, a window typically expands to accommodate a sidebar, so people rarely need to hide it. **Avoid hiding the sidebar by default** to ensure that it remains discoverable — the collapse affordance only earns its keep once people already know the sidebar exists.

**In general, show no more than two levels of hierarchy in a sidebar.** When a data hierarchy is deeper than two levels, consider using a split view interface that includes a content list between the sidebar items and detail view. This is the load-bearing number in this document: a sidebar is for top-level navigation, and once an app's structure needs a third level, the right fix is to add a column, not to keep nesting disclosure triangles.

**If you need to include two levels of hierarchy in a sidebar, use succinct, descriptive labels to title each group.** To help keep labels short, omit unnecessary words.

**Make sure any sidebar icon colors you choose serve a clear purpose.** By default, sidebar icons use your app's accent color. In macOS, people can change the system accent color, which applies to all apps. When they do this, they expect all sidebar icons to appear in that color, so make sure your sidebar icons display the color people choose. However, if you use them sparingly, fixed colors can help clarify the meaning of an icon or draw attention to it. For example, the VIP icon in Mail uses a yellow color to set it apart from other sidebar icons, providing a visual cue about its importance.

## Platform considerations

No additional considerations for tvOS. Not supported in watchOS.

### iOS, iPadOS

When you use the `sidebarAdaptable` style of tab view to present a sidebar, you choose whether to display a sidebar or a tab bar when your app opens. Both variations include a button that people can use to switch between them. This style also adapts its appearance depending on the platform, and responds automatically to rotation and window resizing, providing a version of the control that's appropriate to the width of the view.

> **Developer note (Apple):** To display a sidebar only, use `NavigationSplitView` to present a sidebar in the primary pane of a split view, or use `UISplitViewController`.

**Consider using a tab bar first.** A tab bar provides more space to feature content, and offers enough flexibility to navigate between many apps' main areas. If you need to expose more areas than fit in a tab bar, the tab bar's convertible sidebar-style appearance can provide access to content that people use less frequently. For guidance, see Tab bars.

**If necessary, apply the correct appearance to a sidebar.** If you're not using SwiftUI to create a sidebar, you can use the `UICollectionLayoutListConfiguration.Appearance.sidebar` appearance of a collection view list layout. For developer guidance, see `UICollectionLayoutListConfiguration.Appearance`.

### macOS

A sidebar's row height, text, and glyph size depend on its overall size, which can be **small, medium, or large**. You can set the size programmatically, but people can also change it by selecting a different sidebar icon size in General settings.

**Consider automatically hiding and revealing a sidebar when its container window resizes.** For example, reducing the size of a Mail viewer window can automatically collapse its sidebar, making more room for message content.

**Avoid putting critical information or actions at the bottom of a sidebar.** People often relocate a window in a way that hides its bottom edge.

### visionOS

**If your app's hierarchy is deep, consider using a sidebar within a tab in a tab bar.** In this situation, a sidebar can support secondary navigation within the tab. If you do this, be sure to prevent selections in the sidebar from changing which tab is currently open.

## Native implementation

**Related**
- Split views
- Tab bars
- Layout

**Developer documentation**
- `sidebarAdaptable` — SwiftUI
- `NavigationSplitView` — SwiftUI
- `sidebar` — SwiftUI
- `UICollectionLayoutListConfiguration` — UIKit
- `NSSplitViewController` — AppKit

**Key APIs**
- `backgroundExtensionEffect()` — mirror adjacent content beneath a floating sidebar
- `UICollectionLayoutListConfiguration.Appearance.sidebar` — the sidebar appearance for a non-SwiftUI collection view list layout
- `UISplitViewController` — present a sidebar-only interface without tab-bar conversion in UIKit

**Videos:** Elevate the design of your iPad app

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A sidebar is a persistent navigation landmark, not a drawer.** The web has collapsed two genuinely different patterns under one visual shape: the always-visible desktop sidebar (a `nav` landmark that's part of the page grid) and the mobile "hamburger drawer" that overlays content and must be dismissed to interact with anything behind it. Apple's sidebar is squarely the first kind — it requires real width, sits in the layout rather than over it, and Apple's own advice ("avoid hiding it by default") argues against defaulting to the drawer pattern except where space genuinely forces it, which on the web means narrow viewports.

**The collapse/expand affordance → a disclosure widget with `aria-expanded`, and a remembered preference.** Apple's platform-specific interactions (edge swipe on iPadOS, a View-menu command on macOS) don't transfer literally, but the underlying contract does: the control that toggles the sidebar must expose its current state to assistive technology, and the user's choice should persist across sessions (a cookie or `localStorage` flag), just as macOS remembers a person's chosen sidebar icon size.

**"No more than two levels of hierarchy" → this is a general information-architecture rule, and it holds on the web for the same reason.** A sidebar nav with three or more nested disclosure levels stops being scannable and starts being a file-tree widget. Where the underlying structure is genuinely deeper than two levels, Apple's own escape hatch — add a middle column instead of nesting further — maps directly to adding an intermediate list view rather than indenting a third time.

**Accent-color-follows-system → CSS custom properties plus a user-configurable value, at minimum `prefers-color-scheme`.** Apple's point that people expect *their* chosen accent color to appear on sidebar icons is a case for theming via a CSS variable rather than hard-coded brand colors on every icon, so a user or app-level theme switch actually changes something. Full user-selectable accent color (matching macOS's system-wide setting) is unusual on the web outside of apps that already ship theming, but the principle — inherited color over baked-in color — is the transferable part.

**"Avoid bottom-of-sidebar for critical content" → this is really a viewport-height problem, and it applies more, not less, on the web.** macOS windows get relocated so their bottom edge is hidden; web pages get viewed in browser windows of unpredictable height, embedded iframes, and split-screen tablet views, all of which clip the bottom of a fixed-height sidebar more often than a desktop window does. Treat this as a floor recommendation, not a macOS-specific quirk.

**Where the mapping breaks down: `backgroundExtensionEffect()` and Liquid Glass depth have no equivalent on most of the web.** Extending content visually beneath a translucent sidebar to imply depth is achievable with `backdrop-filter: blur()` and careful z-index layering, but it's a deliberate visual effect Apple is spending real engineering weight on, not a default outcome of "add a sidebar." Skip it unless the app already commits to a glass/depth visual language elsewhere.

## Do / Don't

| Do | Don't |
|---|---|
| Reserve a sidebar for apps with real vertical and horizontal space to spare | Force a sidebar into a narrow or space-constrained layout |
| Let people customize which areas appear and in what order | Hard-code a fixed, unchangeable sidebar item list |
| Use disclosure controls to manage a long list of items | Let an uncollapsed sidebar sprawl past a manageable height |
| Show at most two levels of hierarchy | Nest a third level of disclosure instead of adding a column |
| Let people hide/show the sidebar with the platform's known gesture | Hide the sidebar by default and hurt its discoverability |
| Use fixed icon colors sparingly, for real semantic meaning | Recolor sidebar icons decoratively against the user's accent-color expectation |
| On macOS, keep critical actions away from the sidebar's bottom edge | Put a primary action where a resized or relocated window can hide it |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
