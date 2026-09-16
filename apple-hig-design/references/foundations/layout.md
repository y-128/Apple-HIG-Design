---
title: Layout
url: https://developer.apple.com/design/human-interface-guidelines/layout
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-09-09
---

# Layout

A consistent layout that adapts to various contexts makes your experience more approachable and helps people enjoy their favorite apps and games on all their devices.

Your app's layout helps ground people in your content from the moment they open it. People expect familiar relationships between controls and content to help them use and discover your app's features, and designing the layout to take advantage of this makes your app feel at home on the platform.

Apple provides templates, guides, and other resources that can help you integrate Apple technologies and design your apps and games to run on all Apple platforms. See Apple Design Resources.

## Core guidance

### Best practices

**Group related items to help people find the information they want.** For example, you might use negative space, background shapes, colors, materials, or separator lines to show when elements are related and to separate information into distinct areas. When you do so, ensure that content and controls remain clearly distinct.

**Make essential information easy to find by giving it sufficient space.** People want to view the most important information right away, so don't obscure it by crowding it with nonessential details. You can make secondary information available in other parts of the window, or include it in an additional view.

**Extend content to fill the screen or window.** Make sure backgrounds and full-screen artwork extend to the edges of the display. Also ensure that scrollable layouts continue all the way to the bottom and the sides of the device screen. Controls and navigation components like sidebars and tab bars appear on top of content rather than on the same plane, so it's important for your layout to take this into account.

When your content doesn't span the full window, use a background extension view to provide the appearance of content behind the control layer on either side of the screen, such as beneath the sidebar or inspector. For developer guidance, see `backgroundExtensionEffect()` and `UIBackgroundExtensionView`.

### Visual hierarchy

**Differentiate controls from content.** Take advantage of the Liquid Glass material to provide a distinct appearance for controls that's consistent across iOS, iPadOS, and macOS. Instead of a background, use a scroll edge effect to provide a transition between content and the control area. For guidance, see Scroll views.

**Place items to convey their relative importance.** People often start by viewing items in reading order — that is, from top to bottom and from the leading to trailing side — so it generally works well to place the most important items near the top and leading side of the window, display, or field of view. Be aware that reading order varies by language, and take right to left languages into account as you design.

**Align components with one another to make them easier to scan and to communicate organization and hierarchy.** Alignment makes an app look neat and organized and can help people track content while scrolling or moving their eyes, making it easier to find information. Along with indentation, alignment can also help people understand an information hierarchy.

**Take advantage of progressive disclosure to help people discover content that's currently hidden.** For example, if you can't display all the items in a large collection at once, you need to indicate that there are additional items that aren't currently visible. Depending on the platform, you might use a disclosure control, or display parts of items to hint that people can reveal additional content by interacting with the view, such as by scrolling.

**Make controls easier to use by providing enough space around them and grouping them in logical sections.** If unrelated controls are too close together — or if other content crowds them — they can be difficult for people to tell apart or understand what they do, which can make your app or game hard to use. For guidance, see Toolbars.

### Adaptability

Every app and game needs to adapt when the device or system context changes. In iOS, iPadOS, tvOS, and visionOS, the system defines a collection of traits that characterize variations in the device environment that can affect the way your app or game looks. Using SwiftUI or Auto Layout can help you ensure that your interface adapts dynamically to these traits and other context changes; if you don't use these tools, you need to use alternative methods to do the work.

Here are some of the most common device and system variations you need to handle:

- Different device screen sizes, resolutions, and color spaces
- Different device orientations (portrait/landscape)
- System features like Dynamic Island and camera controls
- External display support, Display Zoom, and resizable windows on iPad
- Dynamic Type text-size changes
- Locale-based internationalization features like left-to-right/right-to-left layout direction, date/time/number formatting, font variation, and text length

**Design a layout that adapts gracefully to context changes while remaining recognizably consistent.** People expect your experience to work well and remain familiar when they rotate their device, resize a window, add another display, or switch to a different device. You can help ensure an adaptable interface by respecting system-defined safe areas, margins, and guides (where available) and specifying layout modifiers to fine-tune the placement of views in your interface.

**Be prepared for text-size changes.** People appreciate apps and games that respond when they choose a different text size. When you support Dynamic Type — a feature that lets people choose the size of visible text in iOS, iPadOS, tvOS, visionOS, and watchOS — your app or game can respond appropriately when people adjust text size. To support Dynamic Type in your Unity-based game, use Apple's accessibility plug-in (for developer guidance, see Apple – Accessibility). For guidance on displaying text in your app, see Typography.

**Preview your app on multiple devices, using different orientations, localizations, and text sizes.** You can streamline the testing process by first testing versions of your experience that use the largest and the smallest layouts. Although it's generally best to preview features like wide-gamut color on actual devices, you can test on a simulated device in Device Hub to check for clipping and other layout issues. For example, if your iOS app or game supports landscape mode, you can use the simulator to make sure your layouts look great whether the device rotates left or right.

**When necessary, scale artwork in response to display changes.** For example, viewing your app or game in a different context — such as on a screen with a different aspect ratio — might make your artwork appear cropped, letterboxed, or pillarboxed. If this happens, don't change the aspect ratio of the artwork; instead, scale it so that important visual content remains visible. In visionOS, the system automatically scales a window when it moves along the z-axis.

### Guides and safe areas

A layout guide defines a rectangular region that helps you position, align, and space your content on the screen. The system includes predefined layout guides that make it easy to apply standard margins around content and restrict the width of text for optimal readability. You can also define custom layout guides. For developer guidance, see `UILayoutGuide` and `NSLayoutGuide`.

A safe area defines the area within a view that isn't covered by a toolbar, tab bar, or other views a window might provide. Safe areas are essential for avoiding a device's interactive and display features, like Dynamic Island on iPhone or the camera housing on some Mac models. For developer guidance, see `SafeAreaRegions` and Positioning content relative to the safe area.

**Respect key display and system features in each platform.** When an app or game doesn't accommodate such features, it doesn't feel at home in the platform and may be harder for people to use. In addition to helping you avoid display and system features, safe areas can also help you account for interactive components like bars, dynamically repositioning content when sizes change.

For templates that include the guides and safe areas for each platform, see Apple Design Resources.

## Platform considerations

### iOS

**Aim to support both portrait and landscape orientations.** People appreciate apps and games that work well in different device orientations, but sometimes your experience needs to run in only portrait or only landscape. When this is the case, you can rely on people trying both orientations before settling on the one you support — there's no need to tell people to rotate their device. If your app or game is landscape-only, make sure it runs equally well whether people rotate their device to the left or the right.

**Prefer a full-bleed interface for your game.** Give players a beautiful interface that fills the screen while accommodating the corner radius, sensor housing, and features like Dynamic Island. If necessary, consider giving players the option to view your game using a letterboxed or pillarboxed appearance.

**Avoid full-width buttons.** Buttons feel at home in iOS when they respect system-defined margins and are inset from the edges of the screen. If you need to include a full-width button, make sure it harmonizes with the curvature of the hardware and aligns with adjacent safe areas.

**Hide the status bar only when it adds value or enhances your experience.** The status bar displays information people find useful and it occupies an area of the screen most apps don't fully use, so it's generally a good idea to keep it visible. The exception is if you offer an in-depth experience like playing a game or viewing media, where it might make sense to hide the status bar.

### iPadOS

People can freely resize windows down to a minimum width and height, similar to window behavior in macOS. It's important to account for this resizing behavior and the full range of possible window sizes when designing your layout. For guidance, see Multitasking and Windows.

**As someone resizes a window, defer switching to a compact view for as long as possible.** Design for a full-screen view first, and only switch to a compact view when a version of the full layout no longer fits. This helps the UI feel more stable and familiar in as many situations as possible. For more complex layouts such as split views, prefer hiding tertiary columns such as inspectors as the view narrows.

**Test your layout at common system-provided sizes, and provide smooth transitions.** Window controls provide the option to arrange windows to fill halves, thirds, and quadrants of the screen, so it's important to check your layout at each of these sizes on a variety of devices. Be sure to minimize unexpected UI changes as people adjust down to the minimum and up to the maximum window size.

**Consider a convertible tab bar for adaptive navigation.** For many apps, you don't need to choose between a tab bar or sidebar for navigation; instead, you can adopt a style of tab bar that provides both. The app first launches with your choice of a sidebar or a tab bar, and then people can tap to switch between them. As the view resizes, the presentation style changes to fit the width of the view. For guidance, see Tab bars. For developer guidance, see `sidebarAdaptable`.

### macOS

**Avoid placing controls or critical information at the bottom of a window.** People often move windows so that the bottom edge is below the bottom of the screen.

**Avoid displaying content within the camera housing at the top edge of the window.** For developer guidance, see `NSPrefersDisplaySafeAreaCompatibilityMode`.

### tvOS

**Be prepared for a wide range of TV sizes.** On Apple TV, layouts don't automatically adapt to the size of the screen like they do on iPhone or iPad. Instead, apps and games show the same interface on every display. Take extra care in designing your layout so that it looks great in a variety of screen sizes.

**Adhere to the screen's safe area.** Inset primary content 60 points from the top and bottom of the screen, and 80 points from the sides. It can be difficult for people to see content that close to the edges, and unintended cropping can occur due to overscanning on older TVs. Allow only partially displayed offscreen content and elements that deliberately flow offscreen to appear outside this zone.

**Include appropriate padding between focusable elements.** When you use UIKit and the focus APIs, an element gets bigger when it comes into focus. Consider how elements look when they're focused, and make sure you don't let them overlap important information. For developer guidance, see About focus interactions for Apple TV.

#### Grids (tvOS)

The following grid layouts provide an optimal viewing experience. Be sure to use appropriate spacing between unfocused rows and columns to prevent overlap when an item comes into focus.

If you use the UIKit collection view flow element, the number of columns in a grid is automatically determined based on the width and spacing of your content. For developer guidance, see `UICollectionViewFlowLayout`.

Apple documents nine grid variants: two-column, three-column, four-column, five-column, six-column, seven-column, eight-column, and nine-column.

**Two-column grid**

| Attribute | Value |
|---|---|
| Unfocused content width | 860 pt |
| Horizontal spacing | 40 pt |
| Minimum vertical spacing | 100 pt |

> **Source limitation:** Apple's page presents the tvOS grid metrics as a tabbed group (Two-column / Three-column / Four-column / Five-column / Six-column / Seven-column / Eight-column / Nine-column). The captured PDF contains only the **first tab** of that group, so the numeric table above is the **two-column** grid only. The metrics for the three- through nine-column grids are **not** available in this source. For the full set, see the tvOS templates in Apple Design Resources.

**Include additional vertical spacing for titled rows.** If a row has a title, provide enough spacing between the bottom of the previous unfocused row and the center of the title to avoid crowding. Also provide spacing between the bottom of the title and the top of the unfocused items in the row.

**Use consistent spacing.** When content isn't consistently spaced, it no longer looks like a grid and it's harder for people to scan.

**Make partially hidden content look symmetrical.** To help direct attention to the fully visible content, keep partially hidden offscreen content the same width on each side of the screen.

### visionOS

The guidance below can help you lay out content within the windows of your visionOS app or game, making it feel familiar and easy to use. For guidance on displaying windows in space and best practices for using depth, scale, and field of view in your visionOS app, see Spatial layout. To learn more about visionOS window components, see Windows > visionOS.

> **Note (Apple):** When you add depth to content in a standard window, the content extends beyond the window's bounds along the z-axis. If content extends too far along the z-axis, the system clips it.

**Consider centering the most important content and controls in your app or game.** Often, people can more easily discover and interact with content when it's near the middle of a window, especially when the window is large.

**Keep a window's content within its bounds.** In visionOS, the system displays window controls just outside a window's bounds in the XY plane. For example, the Share menu appears above the window and the controls for resizing, moving, and closing the window appear below it. Letting 2D or 3D content encroach on these areas can make the system-provided controls, especially those below the window, difficult for people to use.

**If you need to display additional controls that don't belong within a window, use an ornament.** An ornament lets you offer app controls that remain visually associated with a window without interfering with the system-provided controls. For example, a window's toolbar and tab bar appear as ornaments. For guidance, see Ornaments.

**Make a window's interactive components easy for people to look at.** You need to include enough space around an interactive component so that visually identifying it is easy and comfortable, and to prevent the system-provided hover effect from obscuring other content. For example, place buttons so their centers are at least 60 points apart. For guidance, see Eyes, Spatial layout, and Buttons > visionOS.

### watchOS

**Design your content to extend from one edge of the screen to the other.** The Apple Watch bezel provides a natural visual padding around your content. To avoid wasting valuable space, consider minimizing the padding between elements.

**Avoid placing more than two or three controls side by side in your interface.** As a general rule, display no more than three buttons that contain glyphs — or two buttons that contain text — in a row. Although it's usually better to let text buttons span the full width of the screen, two side-by-side buttons with short text labels can also work well, as long as the screen doesn't scroll.

**Support autorotation in views people might want to show others.** When people flip their wrist away, apps typically respond to the motion by sleeping the display, but in some cases it makes sense to autorotate the content. For example, a wearer might want to show an image to a friend or display a QR code to a reader. For developer guidance, see `isAutorotating`.

## Specifications

### iOS, iPadOS device screen dimensions

| Model | Dimensions (portrait) |
|---|---|
| iPad Pro 13-inch | 1032x1376 pt (2064x2752 px @2x) |
| iPad Pro 12.9-inch | 1024x1366 pt (2048x2732 px @2x) |
| iPad Pro 11-inch 5th and 6th generation | 834x1210 pt (1668x2420 px @2x) |
| iPad Pro 11-inch 1st–4th generation | 834x1194 pt (1668x2388 px @2x) |
| iPad Pro 10.5-inch | 834x1112 pt (1668x2224 px @2x) |
| iPad Pro 9.7-inch | 768x1024 pt (1536x2048 px @2x) |
| iPad Air 13-inch | 1024x1366 pt (2048x2732 px @2x) |
| iPad Air 11-inch | 820x1180 pt (1640x2360 px @2x) |
| iPad Air 10.9-inch | 820x1180 pt (1640x2360 px @2x) |
| iPad Air 10.5-inch | 834x1112 pt (1668x2224 px @2x) |
| iPad Air 9.7-inch | 768x1024 pt (1536x2048 px @2x) |
| iPad 11-inch | 820x1180 pt (1640x2360 px @2x) |
| iPad 10.2-inch | 810x1080 pt (1620x2160 px @2x) |
| iPad 9.7-inch | 768x1024 pt (1536x2048 px @2x) |
| iPad mini 8.3-inch | 744x1133 pt (1488x2266 px @2x) |
| iPad mini 7.9-inch | 768x1024 pt (1536x2048 px @2x) |
| iPhone 17 Pro Max | 440x956 pt (1320x2868 px @3x) |
| iPhone 17 Pro | 402x874 pt (1206x2622 px @3x) |
| iPhone Air | 420x912 pt (1260x2736 px @3x) |
| iPhone 17 | 402x874 pt (1206x2622 px @3x) |
| iPhone 16 Pro Max | 440x956 pt (1320x2868 px @3x) |
| iPhone 16 Pro | 402x874 pt (1206x2622 px @3x) |
| iPhone 16 Plus | 430x932 pt (1290x2796 px @3x) |
| iPhone 16 | 393x852 pt (1179x2556 px @3x) |
| iPhone 16e | 390x844 pt (1170x2532 px @3x) |
| iPhone 15 Pro Max | 430x932 pt (1290x2796 px @3x) |
| iPhone 15 Pro | 393x852 pt (1179x2556 px @3x) |
| iPhone 15 Plus | 430x932 pt (1290x2796 px @3x) |
| iPhone 15 | 393x852 pt (1179x2556 px @3x) |
| iPhone 14 Pro Max | 430x932 pt (1290x2796 px @3x) |
| iPhone 14 Pro | 393x852 pt (1179x2556 px @3x) |
| iPhone 14 Plus | 428x926 pt (1284x2778 px @3x) |
| iPhone 14 | 390x844 pt (1170x2532 px @3x) |
| iPhone 13 Pro Max | 428x926 pt (1284x2778 px @3x) |
| iPhone 13 Pro | 390x844 pt (1170x2532 px @3x) |
| iPhone 13 | 390x844 pt (1170x2532 px @3x) |
| iPhone 13 mini | 360x780 pt (1080x2340 px @3x) |
| iPhone 12 Pro Max | 428x926 pt (1284x2778 px @3x) |
| iPhone 12 Pro | 390x844 pt (1170x2532 px @3x) |
| iPhone 12 | 390x844 pt (1170x2532 px @3x) |
| iPhone 12 mini | 360x780 pt (1080x2340 px @3x) |
| iPhone 11 Pro Max | 414x896 pt (1242x2688 px @3x) |
| iPhone 11 Pro | 375x812 pt (1125x2436 px @3x) |
| iPhone 11 | 414x896 pt (828x1792 px @2x) |
| iPhone XS Max | 414x896 pt (1242x2688 px @3x) |
| iPhone XS | 375x812 pt (1125x2436 px @3x) |
| iPhone XR | 414x896 pt (828x1792 px @2x) |
| iPhone X | 375x812 pt (1125x2436 px @3x) |
| iPhone 8 Plus | 414x736 pt (1080x1920 px @3x) |
| iPhone 8 | 375x667 pt (750x1334 px @2x) |
| iPhone 7 Plus | 414x736 pt (1080x1920 px @3x) |
| iPhone 7 | 375x667 pt (750x1334 px @2x) |
| iPhone 6s Plus | 414x736 pt (1080x1920 px @3x) |
| iPhone 6s | 375x667 pt (750x1334 px @2x) |
| iPhone 6 Plus | 414x736 pt (1080x1920 px @3x) |
| iPhone 6 | 375x667 pt (750x1334 px @2x) |
| iPhone SE 4.7-inch | 375x667 pt (750x1334 px @2x) |
| iPhone SE 4-inch | 320x568 pt (640x1136 px @2x) |
| iPod touch 5th generation and later | 320x568 pt (640x1136 px @2x) |

> **Note (Apple):** All scale factors in the table above are UIKit scale factors, which may differ from native scale factors. For developer guidance, see `scale` and `nativeScale`.

### iOS, iPadOS device size classes

A size class is a value that's either regular or compact, where regular refers to a larger screen or a screen in landscape orientation and compact refers to a smaller screen or a screen in portrait orientation. For developer guidance, see `UserInterfaceSizeClass`.

Different size class combinations apply to the full-screen experience on different devices, based on screen size.

| Model | Portrait orientation | Landscape orientation |
|---|---|---|
| iPad Pro 12.9-inch | Regular width, regular height | Regular width, regular height |
| iPad Pro 11-inch | Regular width, regular height | Regular width, regular height |
| iPad Pro 10.5-inch | Regular width, regular height | Regular width, regular height |
| iPad Air 13-inch | Regular width, regular height | Regular width, regular height |
| iPad Air 11-inch | Regular width, regular height | Regular width, regular height |
| iPad 11-inch | Regular width, regular height | Regular width, regular height |
| iPad 9.7-inch | Regular width, regular height | Regular width, regular height |
| iPad mini 7.9-inch | Regular width, regular height | Regular width, regular height |
| iPhone 17 Pro Max | Compact width, regular height | Regular width, compact height |
| iPhone 17 Pro | Compact width, regular height | Compact width, compact height |
| iPhone Air | Compact width, regular height | Regular width, compact height |
| iPhone 17 | Compact width, regular height | Compact width, compact height |
| iPhone 16 Pro Max | Compact width, regular height | Regular width, compact height |
| iPhone 16 Pro | Compact width, regular height | Compact width, compact height |
| iPhone 16 Plus | Compact width, regular height | Regular width, compact height |
| iPhone 16 | Compact width, regular height | Compact width, compact height |
| iPhone 16e | Compact width, regular height | Compact width, compact height |
| iPhone 15 Pro Max | Compact width, regular height | Regular width, compact height |
| iPhone 15 Pro | Compact width, regular height | Compact width, compact height |
| iPhone 15 Plus | Compact width, regular height | Regular width, compact height |
| iPhone 15 | Compact width, regular height | Compact width, compact height |
| iPhone 14 Pro Max | Compact width, regular height | Regular width, compact height |
| iPhone 14 Pro | Compact width, regular height | Compact width, compact height |
| iPhone 14 Plus | Compact width, regular height | Regular width, compact height |
| iPhone 14 | Compact width, regular height | Compact width, compact height |
| iPhone 13 Pro Max | Compact width, regular height | Regular width, compact height |
| iPhone 13 Pro | Compact width, regular height | Compact width, compact height |
| iPhone 13 | Compact width, regular height | Compact width, compact height |
| iPhone 13 mini | Compact width, regular height | Compact width, compact height |
| iPhone 12 Pro Max | Compact width, regular height | Regular width, compact height |
| iPhone 12 Pro | Compact width, regular height | Compact width, compact height |
| iPhone 12 | Compact width, regular height | Compact width, compact height |
| iPhone 12 mini | Compact width, regular height | Compact width, compact height |
| iPhone 11 Pro Max | Compact width, regular height | Regular width, compact height |
| iPhone 11 Pro | Compact width, regular height | Compact width, compact height |
| iPhone 11 | Compact width, regular height | Regular width, compact height |
| iPhone XS Max | Compact width, regular height | Regular width, compact height |
| iPhone XS | Compact width, regular height | Compact width, compact height |
| iPhone XR | Compact width, regular height | Regular width, compact height |
| iPhone X | Compact width, regular height | Compact width, compact height |
| iPhone 8 Plus | Compact width, regular height | Regular width, compact height |
| iPhone 8 | Compact width, regular height | Compact width, compact height |
| iPhone 7 Plus | Compact width, regular height | Regular width, compact height |
| iPhone 7 | Compact width, regular height | Compact width, compact height |
| iPhone 6s Plus | Compact width, regular height | Regular width, compact height |
| iPhone 6s | Compact width, regular height | Compact width, compact height |
| iPhone SE | Compact width, regular height | Compact width, compact height |
| iPod touch 5th generation and later | Compact width, regular height | Compact width, compact height |

### watchOS device screen dimensions

| Series | Size | Width (pixels) | Height (pixels) |
|---|---|---|---|
| Apple Watch Ultra (3rd generation) | 49mm | 422 | 514 |
| 10, 11 | 42mm | 374 | 446 |
| 10, 11 | 46mm | 416 | 496 |
| Apple Watch Ultra (1st and 2nd generations) | 49mm | 410 | 502 |
| 7, 8, and 9 | 41mm | 352 | 430 |
| 7, 8, and 9 | 45mm | 396 | 484 |
| 4, 5, 6, and SE (all generations) | 40mm | 324 | 394 |
| 4, 5, 6, and SE (all generations) | 44mm | 368 | 448 |
| 1, 2, and 3 | 38mm | 272 | 340 |
| 1, 2, and 3 | 42mm | 312 | 390 |

### tvOS safe area insets

| Edge | Inset for primary content |
|---|---|
| Top | 60 pt |
| Bottom | 60 pt |
| Leading and trailing sides | 80 pt |

## Native implementation

**Related**
- Right to left
- Spatial layout
- Layout and organization
- Apple Design Resources (templates including guides and safe areas for each platform)

**Developer documentation**
- Composing custom layouts with SwiftUI — SwiftUI
- Positioning content relative to the safe area
- About focus interactions for Apple TV
- Apple – Accessibility (accessibility plug-in for Unity-based games)

**Key APIs**
- `backgroundExtensionEffect()` — SwiftUI background extension view; `UIBackgroundExtensionView` in UIKit
- `UILayoutGuide` / `NSLayoutGuide` — predefined and custom layout guides
- `SafeAreaRegions` — safe area definition
- `sidebarAdaptable` — convertible tab bar / sidebar presentation on iPadOS
- `NSPrefersDisplaySafeAreaCompatibilityMode` — macOS camera housing accommodation
- `UICollectionViewFlowLayout` — automatic column count for tvOS grids
- `UserInterfaceSizeClass` — regular / compact size classes
- `isAutorotating` — watchOS autorotation
- `scale` / `nativeScale` — UIKit versus native scale factors
- Auto Layout — dynamic adaptation to trait and context changes

**Videos:** Get to know the new design system · Compose custom layouts with SwiftUI · Essential Design Principles

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Safe areas → the viewport is not the drawable area.** Apple's safe area exists because hardware intrudes on the display: Dynamic Island, sensor housings, rounded corners, the home indicator, and on Mac the camera notch. The web equivalent is the `env(safe-area-inset-*)` family, which browsers expose on notched devices once the viewport is set to cover the whole display. The principle transfers cleanly: full-bleed backgrounds should span the entire viewport, while text and interactive targets should respect the insets. Where the mapping breaks down is that the web's insets are static values reported by the browser, whereas Apple's safe area is a live, animatable region that shrinks and grows as bars appear. Browser chrome, the URL bar collapsing on scroll, and on-screen keyboards create the same class of problem on the web, but they are handled by different mechanisms (dynamic viewport units like `dvh`, and the visual viewport API) rather than by one unified safe area concept.

**Adaptability and traits → responsive layout driven by the container, not the device.** Apple's trait system describes the environment: screen size, orientation, text size, layout direction. The classic web answer is viewport media queries, but that answer is weaker than Apple's, because a media query knows only about the window while a trait propagates down the view hierarchy and can be overridden for a subtree. Container queries close most of that gap. A component that asks about the width of its own container behaves the way a trait-aware view does: the same component adapts correctly whether it sits in a full-width region or a narrow sidebar. Prefer container queries for component-level adaptation and reserve viewport media queries for page-level composition.

**Size classes → not breakpoints, but a coarse two-state signal.** It is tempting to read regular and compact as iPad and iPhone breakpoints, and that reading is wrong in a way worth naming. A size class is deliberately coarse: two values per axis, no pixel numbers exposed to the designer. Its purpose is to force a decision about which of two layout arrangements applies, not to fine-tune spacing. The web analogue is therefore not a long ladder of breakpoints but a small number of layout modes, with everything between them handled by fluid sizing (percentage and fractional grid tracks, `minmax()`, clamped type scales). Apple's own device table shows why: nearly every iPad is regular/regular and nearly every iPhone is compact/regular, so the class boundary marks a change of layout structure, not a change of density.

**Defer the compact layout as long as possible → prefer fluid resizing over layout switching.** Apple's iPadOS rule is that as a window narrows you should keep the full layout until it genuinely no longer fits, and drop tertiary columns such as inspectors before collapsing the whole structure. The reason is stability: each switch relocates everything the person was looking at. On the web this argues against breakpoint-heavy design where the layout reflows three or four times between mobile and desktop. Let grid tracks shrink, let columns wrap by intrinsic minimum width, and change structure only at the point where a column can no longer hold readable content. Dropping the least important column first is directly reusable.

**Extend content to fill the screen, controls float above it → layered composition.** Apple's model is that content is a continuous plane running edge to edge, and controls (sidebars, tab bars, toolbars) sit on a layer above it with translucency and a scroll edge effect at the boundary. The web can express the same relationship with a fixed or sticky control layer, a translucent backdrop, and a background that scrolls beneath it. The mapping is partial. Liquid Glass is a system material with specular and refractive behavior that no CSS property reproduces; `backdrop-filter` blur is the closest approximation and is a much flatter effect. The scroll edge effect also has no web primitive and has to be built by hand as a gradient or shadow that appears once the content scrolls under the bar.

**Alignment and grouping → grid is the honest tool.** Apple's argument for alignment is functional rather than aesthetic: aligned elements let the eye track a single edge while scrolling, and indentation plus alignment together communicate hierarchy. On the web this favors a shared grid that multiple sections opt into over per-section flexbox arrangements that happen to look similar. Grouping through negative space, background shapes, and separators translates directly, with the same caveat Apple gives: whatever you use to group must not blur the line between content and controls.

**Reading order and right to left → logical properties, not physical ones.** Apple says to place important items near the top and leading side, and explicitly warns that reading order varies by language. The web has an exact equivalent in logical properties: inline-start and inline-end, block-start and block-end, `margin-inline`, `padding-block`, and the `dir` attribute driving all of them. Writing physical left and right values is the failure mode this rule exists to prevent. This mapping is one of the cleanest, since CSS logical properties were designed for the same problem.

**Dynamic Type → the user's root font size, and layout that survives it.** Supporting Dynamic Type means the person, not the designer, sets the text size, and the layout has to absorb the result. The web equivalent is expressing type in `rem` against an unmodified root size and never setting fixed heights on anything that contains text. The layout consequence is the part usually missed: when text grows, buttons must grow with it, single-line labels must be allowed to wrap, and side-by-side controls must be allowed to stack. Apple's watchOS rule about not placing more than two or three controls in a row rests on the same reasoning, applied to a small screen instead of a large text size.

**Progressive disclosure → the affordance must be visible.** Apple's point is that hidden content needs a visible hint that it exists, whether a disclosure control or a partially visible item at the edge of a scrolling row. This transfers to the web unchanged, and the common web failure is the opposite of Apple's advice: horizontally scrolling rows that cut items off exactly at the container edge give no signal that scrolling is possible. Letting the next item peek in, or fading the edge, is the same technique Apple describes.

**Scale artwork, do not reletter it → aspect ratio preservation.** Apple's rule is that when the display context changes, you scale artwork and keep the important region visible rather than changing its aspect ratio. The web has direct tools for this in `object-fit` and `aspect-ratio`, plus focal-point positioning via `object-position`. Nothing is lost in translation here.

**Where there is no web analogue.** Three things in this document do not carry over. The tvOS overscan safe area of 60 and 80 points exists because of CRT-era television hardware and has no browser equivalent. The visionOS rules about window bounds, z-axis clipping, ornaments, and a 60-point minimum between button centers describe a spatial system with no 2D web counterpart; the underlying idea that gaze targets need generous separation is only weakly analogous to pointer hit-target sizing. And the fixed device dimension tables have no useful web equivalent at all: designing to a list of known screen sizes is precisely the approach responsive web design exists to replace.

## Do / Don't

| Do | Don't |
|---|---|
| Group related items with negative space, background shapes, colors, materials, or separator lines | Let grouping blur the distinction between content and controls |
| Give essential information enough space so it can be found immediately | Crowd essential information with nonessential detail |
| Extend backgrounds and full-screen artwork to the edges of the display | Stop scrollable layouts short of the bottom and sides of the screen |
| Use a background extension view when content doesn't span the full window | Leave a bare gap behind the control layer beside a sidebar or inspector |
| Use Liquid Glass and a scroll edge effect to differentiate controls from content | Put a plain background behind the control area to separate it from content |
| Place the most important items near the top and leading side | Assume reading order is the same in every language |
| Align components with one another to aid scanning and convey hierarchy | Leave components unaligned so the eye has no edge to track |
| Hint at hidden content with disclosure controls or partially visible items | Cut off a large collection with no indication that more items exist |
| Give controls enough surrounding space and group them logically | Place unrelated controls close together or let content crowd them |
| Respect system-defined safe areas, margins, and guides | Ignore Dynamic Island, sensor housings, or the Mac camera housing |
| Use SwiftUI or Auto Layout so the interface adapts to trait changes | Hard-code a layout to one screen size, orientation, or text size |
| Support Dynamic Type and respond to text-size changes | Assume text will always render at the default size |
| Preview on multiple devices, orientations, localizations, and text sizes | Ship after testing only one device configuration |
| Scale artwork so important visual content stays visible | Change the aspect ratio of artwork to fit a new display |
| Support both portrait and landscape orientations where possible (iOS) | Tell people to rotate their device |
| Inset buttons from the screen edges within system-defined margins (iOS) | Use full-width buttons that ignore hardware curvature and safe areas |
| Keep the status bar visible (iOS) | Hide the status bar outside in-depth experiences like games or media |
| Design for the full-screen view first and defer the compact view (iPadOS) | Switch to a compact layout before the full layout stops fitting |
| Hide tertiary columns such as inspectors as a split view narrows (iPadOS) | Restructure the entire split view at the first sign of narrowing |
| Test at halves, thirds, and quadrants of the screen (iPadOS) | Ignore the minimum and maximum window sizes |
| Consider a convertible tab bar for adaptive navigation (iPadOS) | Force a permanent choice between tab bar and sidebar |
| Keep controls and critical information away from the window bottom (macOS) | Assume the bottom edge of the window is always on screen |
| Inset tvOS primary content 60 pt top and bottom, 80 pt at the sides | Place primary content in the overscan zone at the screen edges |
| Use consistent grid spacing and pad focusable elements (tvOS) | Let focused elements grow into and overlap important information |
| Keep partially hidden offscreen content symmetrical on both sides (tvOS) | Let one side show more of a cut-off item than the other |
| Center the most important content and controls in a window (visionOS) | Let 2D or 3D content encroach on the system window controls |
| Use an ornament for controls that don't belong inside the window (visionOS) | Interfere with the system-provided window controls |
| Place buttons at least 60 pt apart center to center (visionOS) | Crowd interactive components so the hover effect obscures content |
| Extend content edge to edge and minimize padding (watchOS) | Waste screen space on padding the bezel already provides |
| Limit a row to three glyph buttons or two text buttons (watchOS) | Put more than two or three controls side by side |
| Support autorotation in views people may want to show others (watchOS) | Assume a wrist-down motion always means the display should sleep |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
