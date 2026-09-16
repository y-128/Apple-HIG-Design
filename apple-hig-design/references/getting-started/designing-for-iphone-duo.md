---
title: Designing for iPhone Duo
url: https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo
platforms: [iOS]
last_updated: 2026-09-09
---

# Designing for iPhone Duo

An app designed for iPhone Duo adapts seamlessly to both displays, providing a continuous experience as the device opens and closes.

iPhone Duo has two displays, each with its own front-facing camera. A hinge in the center lets people open and close the device, and supports a variety of ways to hold and position it. This range of display sizes and poses makes an adaptable layout more important than ever. If your app uses standard system components and you've designed it to support resizing, it automatically adapts to the device's poses with little adjustment required.

> *Image caption:* Outer display / Inner display

Although iPhone Duo is a new form factor, keep in mind that you're still designing for iPhone, and Designing for iOS patterns and best practices still apply. See [Designing for iOS](designing-for-ios.md).

## Core guidance

### Anatomy

iPhone Duo has an inner and an outer display. People interact with the outer display when the device is closed, and the system places toolbars and tab bars on the side to maximize the vertical space for content. The controls remain on the side when the device opens in landscape to ensure a consistent experience as people move between displays.

A center hinge supports a range of ways to hold and position the device. The hinge also impacts the space available for your content as the device folds.

The outer front-facing camera is in the corner and is always visible, vertically aligned with controls on the side. The inner camera is behind the display and stays hidden until the camera is active.

> *Image caption:* Outer display / Inner display

#### Device poses

People hold iPhone Duo and set it down in a number of ways: partially folded like a book, placed down on a surface, or standing on its edges.

Supporting the device's various poses doesn't mean designing a custom layout for each one: instead, use size classes so your app adapts naturally as it changes size. A compact width layout for the outer display and a regular width layout for the inner display give you the fundamentals for every pose. Don't reinvent your app when it resizes; allow the existing layout to expand based on the available space instead. See Dynamic layouts for guidance.

### Best practices

**Build your app to resize.** Because the device has two displays and supports a wide range of poses and Split View multitasking, your app can appear at many different sizes. Use size classes, layout margins, and safe area insets to lay out controls and content. Avoid fixed widths and display-specific dependencies. See Dynamic layouts below and Layout for guidance.

**Create a consistent experience across displays.** Keep functionality and the state of elements the same between displays. Maintain your app's information hierarchy, but show an additional level of hierarchy on the larger inner display if it makes sense for your content. Mail, for example, shows either a list of emails (primary) or an email (secondary) when the device is closed. When it's open, it shows both side by side.

> *Image caption:* Outer display / Inner display

**Maintain the same functionality across device poses.** Controls may overflow and content may move or change size as the interface adapts to the available area. Provide access to the same controls and content regardless of how someone holds or views the device. For guidance, see Dynamic layouts and Vertical controls.

**Follow the system's vertical layout for toolbars, tab bars, and navigation controls.** Because the outer display is wider and shorter than the display on other iPhone devices, the system moves controls to the side to preserve vertical space for content and reflect the asymmetry of the display. On the inner display, controls remain on the side in landscape to preserve a continuous experience at the same vertical height. If you use standard system components, you receive this layout automatically, but you may want to refine it based on the needs of your app. For guidance, see Vertical controls.

**Make your game playable in every device pose.** You can choose to lock to either portrait or landscape orientation, but be sure to fill the screen as the device pose changes. When resizing, keep text and control sizes as consistent as possible. Prefer changing the aspect ratio over letterboxing or pillarboxing in games; if you can't avoid letterboxing or pillarboxing, add artwork to the padding area to help the experience feel full screen. See Designing for games for additional guidance.

### Dynamic layouts

Designing for iPhone Duo means accounting for a variety of hardware and software configurations. As with all iOS devices, build your layouts with layout margins and safe area insets, and steer clear of fixed widths or anything tied to a specific display.

For guidance, see Layout. For margins and safe areas, see Apple Design Resources. For developer guidance, see `safeAreaInsets` (SwiftUI) and `safeAreaInsets` (UIKit).

#### Reserved regions

In addition to standard considerations for safe areas, available space on iPhone Duo is shaped by reserved regions. These represent areas within the display that content avoids covering, or that components adapt to accommodate. These are familiar if your layout adapts to similar areas on other platforms, such as the window controls on iPad.

The reserved regions on iPhone Duo include:

- The outer front-facing camera. This region is always present, and expands into the Dynamic Island for Live Activities. When controls are on the side, the system automatically accounts for it and arranges elements accordingly.
- The inner front-facing camera. This region is only present when the camera is active. When it's inactive, the camera isn't visible; when the camera activates, the UI moves aside to indicate the presence of the camera.
- The folding region. This region is conditional based on how a person uses the device. When the device is partially open, the folding region divides the inner display into multiple usable regions, excluding the region at the center as the display folds.

> *Image caption:* Outer display / Inner display

Many system components automatically adapt to reserved regions. Components like alerts, context menus, and sheets automatically move to account for the fold, while larger components like split views adapt their columns' width and margins to match the symmetry of the inner display. For custom components, the reserved region APIs provide a way to reposition content away from reserved regions.

**Adapt your layout when the device folds.** Prefer a layout container that adapts automatically, like the split view in Notes that adjusts the width of each pane to stay clearly visible as the device folds. In a grid-style layout, prefer an even number of columns so content divides cleanly. Use the reserved region APIs to keep important elements clear of the center if the system doesn't move them automatically.

> *Image caption:* Fully open / Partially folded

**Avoid extreme layout changes as people fold the device.** Move only what's necessary to keep elements visible and easy to tap. Controls that disappear or shift dramatically are harder to find and track, so favor small adjustments over rearrangement.

#### Split views

On iPhone Duo, a split view expands on the inner display and collapses to a single pane on the outer display, the same way it adapts between regular and compact environments on other iPhone devices. When built with standard components, split views adapt to reserved regions automatically, adjusting width and margins to adapt to the fold.

For general guidance, see split views. For developer guidance, see `NavigationSplitView` (SwiftUI) and `UISplitViewController` (UIKit).

#### Arrangement views

An arrangement view is a layout container that holds two views inside it — a primary view and a secondary view — and dynamically organizes them based on display size, orientation, and reserved regions.

There are two types of arrangement view: split and overlay.

- A split arrangement divides its area between its primary and secondary views. It splits horizontally when the arrangement is wider than it is tall, and splits vertically when the arrangement is taller than it is wide.
- An overlay arrangement positions the primary and secondary views on top of one another. When the display is partially folded, the views move to occupy each side; otherwise the primary view moves atop the secondary view.

> *Image caption:* Split arrangement / Overlay arrangement

You can limit which axes a split arrangement uses, and collapse the secondary view in an overlay arrangement when you don't want it to appear.

**Consider an arrangement view when your layout already resembles one.** A layout that places two views side by side or one above the other, such as an `HStack` or `VStack`, translates directly to a split arrangement. A layout that layers one view over another, such as a `ZStack`, translates to an overlay arrangement.

**Keep navigation outside of arrangement views.** An arrangement view lays out content but doesn't handle navigation, so place navigation containers like navigation split views and tab views around it rather than within it.

### Vertical controls

On iPhone Duo, toolbars, tab bars, and navigation controls that are typically at the top and bottom of the display move to the side, preserving vertical space for content and keeping controls within easy reach. The exception is the inner display in portrait, which has enough vertical space to keep standard horizontal bars.

Controls on the side include both system and app elements: the Dynamic Island, the status bar, the toolbar (including navigation buttons), and the tab bar.

When two apps share the inner display with Split View multitasking, each one places controls along its outer edge, so the left app has controls on the left.

Because controls on the vertical axis stay aligned with the hardware, they hold the same position relative to the camera on the outer display, and stay on the same side in right-to-left languages.

**Account for asymmetry in your layouts.** Because controls sit along one edge, the space for content is asymmetrical. Use safe areas to make sure controls don't cover your content, including controls on the opposite edge, like when two apps share the inner display with Split View multitasking.

**Keep controls consistent across device poses.** Because not every pose places controls vertically on the side, and there isn't always the same amount of space available, it's important to keep controls' relative positions as similar as possible so people don't have to relearn where actions live as they change between poses.

**Follow the standard placement order for toolbar items.** Reserve the top of the vertical axis for primary navigation controls, like Back or Close, followed by prominent actions, like Done. This preserves familiar navigation patterns while keeping important actions within reach. Keep remaining toolbar items in their original groupings; the system provides a vertical space between items from the top and bottom bars to keep them distinct.

**Prioritize frequently used toolbar items to keep them easily available.** Items overflow from bottom to top by default. Assign each item a visibility priority to change that order, starting with whole groups and then individual items within a group if you need finer control. For developer guidance, see `ToolbarItemVisibilityPriority` (SwiftUI) or `UIBarButtonItem.VisibilityPriority` (UIKit).

**Preserve frequently used actions first**, like Compose in Mail or New Note in Notes, and keep controls that convey important status, like items with badges, visible longer so people can see them at a glance.

**In general, don't override the default bar placement.** The position of controls on the vertical axis is one of the core patterns of iPhone Duo. Keeping controls in familiar positions helps people get to know how your app works right away, and reinforces the unified platform experience.

**Consider using the full display width for interfaces where bars aren't necessary.** Some layouts can span the full display, which works well for visual, immersive interfaces that don't scroll, as long as nothing conflicts with the Dynamic Island or the status bar. Calculator, for example, occupies the full width of the display. You can also combine both approaches, letting a background image or header span the full width while scrollable content stays inset.

**Group related toolbar items instead of spacing them manually.** Groups you create with `ToolbarItemGroup` (SwiftUI) or `UIBarButtonItemGroup` (UIKit) provide space between items and other groups automatically, and adapt as the available space changes, so avoid adding fixed spacing yourself. For guidance, see Toolbars.

**Locate controls near the content they affect.** When controls belong to a content area other than the one along the trailing edge, keep them with that area rather than moving them to the side. Proximity makes the relationship between controls and content clear. For example, controls that affect the list of emails in Mail stay above the leading pane to indicate that they apply to the list, rather than the contents of an individual email.

**Provide both a title and a symbol for each toolbar item that isn't text-only.** Giving both lets the system pick the right representation for the context. Include a title even when an item shows a symbol, because the system uses the title in overflow menus and expanded forms. For developer guidance, see `Label` (SwiftUI) and `UIBarButtonItem` (UIKit).

**Keep text-based buttons to a minimum.** Labels that include text stay in a horizontal bar, so prefer a symbol wherever one works.

**When space is limited, preserve either the toolbar or tab bar based on the experience that the view provides.** In navigation-focused experiences, move toolbar items into the overflow menu so the tab bar and primary destinations remain accessible. This is the default bar compression behavior.

In task-oriented experiences, minimize the tab bar to preserve the toolbar actions that are central to completing the task. This mirrors the minimized tab bar behavior present on other iPhone devices.

> *Image caption:* Toolbar compressed / Tab bar compressed

**Use the system overflow menu.** If your app has its own overflow menu, move those actions into the system menu so people find everything in one place. Reserve the ellipsis symbol for overflow, and give other menus a distinct symbol. For developer guidance, see `ToolbarOverflowMenu` (SwiftUI) and `additionalOverflowItems` (UIKit).

## Platform considerations

This page applies to iOS running on iPhone Duo only. Apple's source page has no separate "Platform considerations" section — the entire page is already scoped to this one device family within iOS, so there is no additional per-platform guidance to carry over.

## Native implementation

**Related**
- Apple Design Resources
- Designing for iOS
- Layout

**Developer documentation**

SwiftUI:
- `safeAreaInsets`
- `NavigationSplitView`
- `HStack`
- `VStack`
- `ZStack`
- `ToolbarItemVisibilityPriority`
- `ToolbarItemGroup`
- `Label`
- `ToolbarOverflowMenu`

UIKit:
- `safeAreaInsets`
- `UISplitViewController`
- `UIBarButtonItem.VisibilityPriority`
- `UIBarButtonItemGroup`
- `UIBarButtonItem`
- `additionalOverflowItems`

**Videos:** Design for iPhone Duo · Raise the bar with iPhone Duo · Strike a pose with adaptive layouts on iPhone Duo

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and this page is built entirely around a physical dual-display, hinged device. The mappings below are inference about how the same reasoning could apply to a foldable or dual-screen web experience — they are not Apple policy, and in most cases they describe emerging web standards with limited browser support rather than something you can rely on in production today.

**Reserved regions and device poses → the Viewport Segments API and the Device Posture API are the closest web analogues, but both are experimental.** The `viewport-segments` media feature and the `env(viewport-segment-*)` CSS environment variables let a page query how many logical viewport segments exist and where the fold between them falls, which mirrors Apple's folding region. The Device Posture API's `device-posture` media query (values like `continuous` and `folded`) mirrors the device-poses concept. Neither has broad, stable, cross-browser support as of this writing, so treat them as progressive enhancement, not a baseline you can depend on. There is no known web API that exposes anything like iPhone Duo's camera reserved regions — those are hardware- and OS-specific concepts with no browser equivalent at all.

**Size classes → container queries or media queries keyed to available width**, not to a specific device or breakpoint name. Apple's point — a compact-width layout for the outer display and a regular-width layout for the inner display cover every pose — translates to designing two or three width-based states and letting the layout flow between them, rather than hardcoding a layout per named device.

**Vertical controls → a side navigation rail on short, wide viewports.** When a page's viewport is much wider than it is tall (the rough web equivalent of the outer-display pose), moving primary navigation to a vertical rail along one edge preserves vertical space the same way Apple's side-mounted toolbar and tab bar do. Keep the rail on a consistent edge across states, echoing the guidance to keep controls' relative position predictable across poses.

**Toolbar item visibility priority → a priority+ navigation pattern with an overflow menu.** Assigning each action a priority and collapsing lower-priority items into a "more" menu as space shrinks is the direct web equivalent of `ToolbarItemVisibilityPriority` / `UIBarButtonItem.VisibilityPriority`, including the same instinct to keep frequently used or status-bearing actions (badges, unread counts) visible longest.

**Reserved regions and grid layouts → prefer an even number of grid columns and container-based reflow.** Apple's advice to use an even column count so content divides cleanly across the fold applies directly to any responsive grid intended to work across a segmented viewport: an odd column count guarantees a column straddles the seam.

**Avoid extreme layout changes on resize → avoid dramatic reflow on viewport or fold change.** The reasoning is the same as Apple's: controls or content that jump or disappear on a resize event are harder to track than ones that shift gradually, so prefer small, predictable adjustments driven by container queries over full layout swaps.

## Do / Don't

| Do | Don't |
|---|---|
| Use size classes, layout margins, and safe area insets to build one resizable layout | Design a separate fixed layout for every device pose |
| Keep functionality and element state identical across the outer and inner display | Remove or hide functionality on one display that's available on the other |
| Let controls overflow and content resize as the available area changes | Force content to stay a fixed size when the display area shrinks |
| Follow the system's vertical placement for toolbars, tab bars, and navigation controls | Override default bar placement without a strong reason |
| Use the reserved region APIs or an adaptive container like split views near the fold | Let content or controls sit unreadably across the folding region |
| Prefer an even number of grid columns so content divides cleanly at the fold | Use an odd column count that leaves a column straddling the seam |
| Make small, incremental layout adjustments as the device folds | Rearrange or hide controls dramatically as people fold the device |
| Assign toolbar items a visibility priority so important actions overflow last | Let items overflow in an arbitrary or unpredictable order |
| Provide both a title and a symbol for non-text-only toolbar items | Ship symbol-only items with no title for overflow menus and expanded forms |
| Group toolbar items with `ToolbarItemGroup` / `UIBarButtonItemGroup` | Add manual fixed spacing between toolbar items |
| Keep controls near the content they affect, even off the primary edge | Move all controls to the side edge regardless of what they act on |
| Keep bar-compression behavior consistent with your app's focus (navigation vs. task) | Compress both the toolbar and tab bar together when space is limited |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
