---
title: Layout
url: https://developer.apple.com/design/human-interface-guidelines/layout
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2026-09-09
---

# Layout

A consistent layout that adapts across display sizes, orientations, and multitasking configurations helps people understand and enjoy your app or game on all their devices.

Your layout provides the structure for people to understand your content from the moment they open your app. Familiar relationships between controls and content let people use and discover features right away, and make your design feel at home on every platform.

Apple provides templates and layout guides that can help you integrate Apple technologies and design your apps and games to run on all Apple platforms. See Apple Design Resources.

## Core guidance

### Visual hierarchy

**Order content by relative importance.** People often start by viewing content in reading order — that is, from top to bottom and from the leading to trailing side — so place the most important items near the top and leading side of the window or display. To support right-to-left languages, prefer standard system components that can automatically adapt UI elements to better reflect each language's natural reading order. For guidance, see Right to left.

**Align elements to make them easier to scan, and use indentation to convey hierarchy.** Alignment makes an app look neat and organized, and can help people track content while scrolling or moving their eyes. People assume that aligned items are related to each other, and conversely, they perceive indented items as subordinate to the item they follow. Because of this, using alignment and indentation deliberately can help people understand your information hierarchy.

**Group related items to clearly express related information or functions.** For example, you might use negative space, container shapes, or separator lines to show which elements are related and which are unrelated.

**Use progressive disclosure to make layouts cleaner and easier to interact with.** An interface with too much content and too many choices makes it harder to find information quickly, and harder to understand the choices that are available. Use disclosure triangles, menus, or nested views to reduce how much content to initially display; or use scrollable sections to showcase additional content, which is particularly useful for media-focused apps like those for video, music, or books.

**Differentiate controls from content.** Take advantage of the Liquid Glass material on all platforms that support it to provide a distinct appearance for your controls. Instead of applying a solid or semi-opaque background color beneath controls, use a scroll edge effect to visually elevate controls above content. For guidance, see Scroll views. For full-screen background content, be sure to extend it underneath sidebars, toolbars, and tab bars to fit the entire screen or window.

If scaling a background image to the full window edge results in components like sidebars or inspectors covering important parts of the image, you can use a background extension effect to flip and blur the image, mirroring it beneath adjacent components and providing the appearance that the background image extends beneath them. For developer guidance, see `backgroundExtensionEffect()` and `UIBackgroundExtensionView`.

### Adaptability

Apps and games need to adapt to different display sizes, orientation changes, window sizes, and multitasking states. In iOS, iPadOS, tvOS, and visionOS, the system defines characteristics of the device environment that can affect the way your app or game looks. Use SwiftUI or Auto Layout to ensure that your interface adapts to them.

Here are some of the most common device and system characteristics that apps need to handle:

- Regular and compact horizontal and vertical size classes
- Different device screen sizes
- Different device orientations and aspect ratios
- System features like the Dynamic Island
- External display support, Display Zoom, and resizable windows on iPad and Mac
- Text-size changes
- Locale-based internationalization features like left-to-right/right-to-left layout direction, date/time/number formatting, font variation, and text length

**Design a layout that adapts gracefully and consistently.** People expect your experience to remain familiar when they rotate their device, resize a window, add another display, or switch to a different device. You can help ensure an adaptable interface by respecting system-defined safe areas, margins, and guides (where available) and specifying layout modifiers to fine-tune the placement of views in your interface.

Even if your app is locked to a certain orientation, such as a landscape-only game, it's still important to ensure your interface resizes well to provide the best experience across devices and window sizes.

**Be prepared for text-size changes.** People use Dynamic Type to increase text size to be more readable, which occurs at the system level. Apps that don't respond to this setting can be difficult or impossible to use for people who rely on this feature. Support Dynamic Type by adjusting your layout to accommodate text at larger sizes. For example, horizontally adjacent views may need to stack vertically to provide more space for text; table rows or other containers may need to grow in height so that text isn't cropped or doesn't overlap other content; and table rows with a single line of text by default might need to grow vertically to accommodate multiple lines of text.

To support Dynamic Type in your Unity-based game, use Apple's accessibility plug-in (for developer guidance, see Apple – Accessibility). For guidance on displaying text in your app, see Typography.

**Preview your app on multiple devices, using different size classes, localizations, and text sizes.** You can streamline the testing process by first testing versions of your experience that use the largest and the smallest layouts. You can test on a simulated device in Device Hub to check for clipping and other layout issues. For example, you can use Device Hub to make sure your layout looks great when your app is resized on iPad or in iPhone Mirroring on Mac.

**When necessary, scale background artwork in response to display changes.** Viewing your app or game in a different context — such as on a screen with a different aspect ratio — might make your artwork appear cropped, letterboxed, or pillarboxed. If this happens, don't change the aspect ratio of the artwork; instead, scale it so that it fills the screen completely. Note that since windows can be very wide and short or tall and narrow, background artwork may often need to extend beyond what is typically visible in a more standard display aspect ratio.

#### Size classes

In iOS and iPadOS, size classes are an indication of how much horizontal and vertical space is available to an app's interface.

Each dimension — horizontal and vertical — is represented by one of two size classes: compact or regular. The horizontal size class determines whether an app is narrow (compact) or wide (regular), while the vertical size class determines whether it is short (compact) or tall (regular). The system sets size classes based on the device type, window configuration, and multitasking state; for example, whether an app is full screen, in Slide Over, or mirrored from an iPhone to a Mac. Depending on their environment, iOS and iPadOS apps can exist in every combination of size classes.

*(Apple's page illustrates the four combinations with images: compact width/compact height, compact width/regular height, regular width/compact height, and regular width/regular height.)*

For developer guidance, see `UITraitChangeObservable` and `UserInterfaceSizeClass`.

**Determine layout based on size classes, not device type or orientation.** Size classes describe the actual space available, regardless of whether an app is in portrait or landscape. Conversely, a device's orientation and type (also called its idiom) aren't useful for making layout decisions because they don't provide your app with information about how much space is available.

Size classes also let your app's interface adapt to a wide range of window sizes. For example, when a person runs your app in macOS with iPhone Mirroring, they can freely resize its width and height; or they can resize an iPad app when multitasking in iPadOS or when running it in macOS.

**Consider all possible combinations of size classes.** Your app can appear in a variety of size classes in both portrait and landscape aspect ratios, and it's important to consider all of them to provide a good experience. A layout solely designed for landscape on iPhone with regular width and compact height might not take advantage of the vertical space available on iPad in landscape when someone resizes the window to regular height. Conversely, designing exclusively for compact portrait could leave extra space when someone resizes the app window to a regular width on iPad.

**Keep functionality the same as size classes change, and keep layout changes recognizable and familiar to the platform.** Don't change your app's functionality based on the space it occupies. However, you can change the amount of functionality that's visible onscreen as the amount of space changes. Consider taking advantage of larger spaces to switch from a tab bar to a sidebar or expose functionality that might otherwise be grouped into an overflow menu. Similarly, while an app's size classes might change when someone resizes it, its idiom — the device type it's made for — remains the same: keep the layout recognizable and familiar to the platform even when resizing.

### Guides and safe areas

A layout guide defines a rectangular region that helps you position, align, and space your content on the screen. The system includes predefined layout guides that make it easy to apply standard margins around content and restrict the width of text for optimal readability. You can also define custom layout guides. For developer guidance, see `UILayoutGuide` and `NSLayoutGuide`.

A safe area defines the area within a window that isn't covered on the edge by a hardware feature or another view within the window, like a toolbar, tab bar, or status bar. Respecting the safe area is essential to make sure system UI and hardware features like the Dynamic Island don't obstruct content and controls. For developer guidance, see `SafeAreaRegions` and Positioning content relative to the safe area.

## Platform considerations

No additional considerations for iOS or iPadOS.

### macOS

**Avoid placing controls or critical information at the bottom of a window.** People often move windows so that the bottom edge is below the bottom of the screen.

**Avoid displaying content behind the camera housing at the top edge of the window.** For developer guidance, see `NSPrefersDisplaySafeAreaCompatibilityMode`.

### tvOS

**Adhere to the screen's safe area.** Inset primary content 60 points from the top and bottom of the screen, and 80 points from the sides. Providing these margins ensures your content is visible regardless of TV compatibility settings or overscan cropping.

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

> **Source limitation:** Apple's page presents the tvOS grid metrics as a tabbed group (Two-column / Three-column / Four-column / Five-column / Six-column / Seven-column / Eight-column / Nine-column). The 2026-09-09 PDF capture, like the prior 2025-09-09 snapshot this file was built from, contains only the **first tab** of that group, so the table above is the **two-column grid only**. The metrics for the three- through nine-column grids have never been available from either PDF capture. For the full set, see the tvOS templates in Apple Design Resources.

**Include additional vertical spacing for titled rows.** If a row has a title, provide enough spacing between the bottom of the previous unfocused row and the center of the title to avoid crowding. Also provide spacing between the bottom of the title and the top of the unfocused items in the row.

**Use consistent spacing.** When content isn't consistently spaced, it no longer looks like a grid and it's harder for people to scan.

**Make partially hidden content look symmetrical.** To help direct attention to the fully visible content, keep partially hidden offscreen content the same width on each side of the screen.

### visionOS

In visionOS, you can lay out content within a window, a bounded 3D volume, or an immersive space. The guidance below focuses on laying out content in a window or volume; for guidance on displaying content spatially and best practices for using depth, scale, and positioning, see Spatial layout. To learn more about windows and volumes in visionOS, see Windows > visionOS.

**In general, support resizing.** The ability to resize windows and volumes is standard behavior in visionOS, just as in macOS and iPadOS. When you allow resizing, make sure your layout adapts well as it changes size, and prefer to keep content horizontally centered at very large sizes so people can easily view and interact with it.

You can also choose to set a minimum and maximum size for windows, volumes, and attached UI elements like ornaments. Use these settings to keep elements from overlapping at small sizes, and to keep large layouts from becoming too unwieldy; but don't use minimum and maximum sizes as a way to prevent resizing. For example, in Safari, people can resize browser windows, but the custom navigation bar ornament has a fixed maximum size so that controls remain easy to access. For developer guidance, see Positioning and sizing windows.

**Use 3D content sparingly in windows.** While windows in visionOS can display 3D content at a fixed depth, reserve this for meaningful moments alongside 2D content. For example, an educational app might display an inline 3D model of a rocket next to information about the model. When displaying 3D content inline, place it inset in the window to avoid it colliding with other content or controls, or appearing unpredictably outside the window edge.

To display larger models or views that primarily consist of 3D content, consider using a volume or placing content in an immersive space.

**Display supplemental content in an adjacent window, not in an ornament.** While ornaments are flexible enough to act as custom components, they are best for app-specific interactive controls like toolbars and video playback controls, not supplemental content. To display a supplemental content view, open a new window next to the current one using `defaultWindowPlacement(_:)` instead of placing the content in an ornament. For developer guidance, see Positioning and sizing windows.

**Include enough space around controls for them to be easy to interact with.** Put enough space around controls to make them clearly identifiable, and to prevent the system-provided hover effect from obscuring other content. For example, place buttons so their centers are at least 60 points apart. For guidance, see Eyes, Spatial layout, and Buttons > visionOS.

### watchOS

**Avoid placing more than two or three controls side by side in your interface.** As a general rule, display no more than three buttons that contain glyphs — or two buttons that contain text — in a row. Although it's usually better to let text buttons span the full width of the screen, two side-by-side buttons with short text labels can also work well, as long as the screen doesn't scroll.

**Support autorotation in views people might want to show others.** When people flip their wrist away, apps typically respond to the motion by sleeping the display, but in some cases it makes sense to autorotate the content. For example, a wearer might want to show an image to a friend or display a QR code to a reader. For developer guidance, see `isAutorotating`.

## Specifications (removed from Apple's page)

> **Source note:** Apple removed this section from the Layout page in the September 9, 2026 revision. The tables below are retained from the September 9, 2025 snapshot for reference and are no longer maintained by Apple on this page. Verify current values in Apple Design Resources.

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
- Positioning and sizing windows
- Apple – Accessibility (accessibility plug-in for Unity-based games)

**Tools**
- Device Hub — simulated-device testing, not an API; use it to check for clipping and other layout issues across size classes, orientations, iPad resizing, and iPhone Mirroring on Mac.

**Key APIs**
- `backgroundExtensionEffect()` — SwiftUI background extension effect; `UIBackgroundExtensionView` in UIKit
- `UITraitChangeObservable` — observing device and system trait changes, including size classes
- `UserInterfaceSizeClass` — regular / compact size classes
- `UILayoutGuide` / `NSLayoutGuide` — predefined and custom layout guides
- `SafeAreaRegions` — safe area definition
- `NSPrefersDisplaySafeAreaCompatibilityMode` — macOS camera housing accommodation
- `UICollectionViewFlowLayout` — automatic column count for tvOS grids
- `defaultWindowPlacement(_:)` — visionOS supplemental window placement
- `isAutorotating` — watchOS autorotation
- SwiftUI / Auto Layout — dynamic adaptation to trait and context changes

**Videos:** Get to know the new design system · Compose custom layouts with SwiftUI · Essential Design Principles

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Reading order and right to left → logical properties, not physical ones.** Apple's rule is to place the most important items near the top and leading side, and to prefer system components that adapt automatically to each language's reading order rather than hand-rolling direction logic. The web equivalent is CSS logical properties: inline-start and inline-end, block-start and block-end, margin-inline, padding-block, together with the `dir` attribute that drives all of them. Writing physical left and right values is exactly the failure mode this rule exists to prevent, since it silently breaks in right-to-left locales.

**Alignment, indentation, and grouping → a shared grid, not per-section flexbox.** Apple's case for alignment is functional: aligned elements let the eye track a single edge while scrolling, and indentation plus alignment together communicate hierarchy. Grouping through negative space, container shapes, or separator lines works the same way on the web. This favors a small number of shared grid definitions that multiple sections opt into, over flexbox arrangements that happen to look similar section by section but drift out of alignment as content changes.

**Progressive disclosure → the affordance must stay visible.** Apple's point is that reducing what's shown up front — through a disclosure control, a nested view, or a scrollable section — only works if people can see that more exists. The common web failure runs the opposite direction: a horizontally scrolling row that cuts an item off exactly at the container edge signals nothing about further content. Letting the next item peek in, or fading the edge, reproduces the technique Apple describes.

**Differentiate controls from content → a scroll edge effect, not an opaque background.** Apple's rule against a solid or semi-opaque background behind controls, in favor of a scroll edge effect that keeps a control layer visually distinct from what scrolls beneath it, maps to a translucent or blurred control bar that reveals a hint of the content behind it as that content scrolls under it. The mapping is partial: Liquid Glass is a system material with specular and refractive behavior that no CSS property reproduces, and `backdrop-filter` blur is only the flatter, nearest approximation. There is likewise no web primitive for the scroll edge effect itself; it has to be hand-built as a gradient or shadow that appears once content passes beneath the fixed layer.

**Background extension effect → a layered background, not a hard crop.** When a full-bleed background would be covered by a sidebar or inspector, Apple's answer is to mirror and blur the image beneath that component rather than let it show a flat edge. On the web this argues for treating a full-bleed background as a layer that extends conceptually behind any fixed-position chrome — sidebar, toolbar, bottom bar — rather than sizing the background only to the visible content area, so that resizing the chrome doesn't expose a hard-edged gap.

**Adaptability and traits → layout driven by the container's available space, not the device.** Apple's trait system — size classes, orientation, text size, layout direction — describes the environment a view actually has, not the device it happens to run on. The corresponding web mistake is branching layout on user-agent or a guessed device category. Container queries are the closer match: a component that asks about its own container's width behaves the way a trait-aware view does, adapting correctly whether it sits in a full-width region or a narrow sidebar. Reserve viewport-level media queries for page-level composition and prefer container queries for anything that must adapt wherever it's placed.

**Size classes → a small number of layout modes, not a ladder of breakpoints.** Regular and compact are deliberately coarse — two values per axis, no pixel numbers exposed to the designer — because their purpose is to force a decision between layout arrangements, not to fine-tune spacing. The web analogue is therefore a small number of distinct layout modes, with everything in between handled by fluid sizing: fractional grid tracks, `minmax()`, and type scales that scale smoothly rather than stepping at arbitrary widths.

**Keep functionality identical as size classes change → change visibility, not capability.** Apple is explicit that an app's functionality must stay the same across size classes even as how much of it is shown onscreen changes — larger spaces can surface more at once, such as switching from a tab bar to a sidebar, but nothing should become unreachable at a smaller size. On the web this rules out hiding entire features behind a breakpoint; a narrow layout should reorganize or collapse functionality into an overflow affordance, never drop it.

**Dynamic Type → the user's chosen text size, and a layout that survives it.** Dynamic Type puts the text-size decision in the person's hands rather than the designer's, and the layout has to absorb whatever size they pick. The nearest web equivalent is the browser's own text-zoom setting together with type expressed in `rem` against an unmodified root size — never a fixed pixel size that resists zooming. The layout consequence, which is where implementations usually fail, is that horizontally adjacent views must be able to stack vertically, single-line labels must be allowed to wrap, and containers must be allowed to grow in height rather than clipping or overlapping text.

**Preview at the smallest and largest layouts first.** Apple's testing strategy is to check the extremes — the largest and smallest layouts, across size classes, localizations, and text sizes — before spending time on everything in between, because a layout that survives both extremes usually survives what's between them. This transfers directly: test a responsive page at its narrowest supported width and at a very large text-zoom setting before polishing intermediate breakpoints.

**Scale artwork, don't reletter it → aspect ratio preservation.** When display context changes — a different aspect ratio, a resized window — Apple's rule is to scale artwork to fill the space rather than change its aspect ratio or crop it arbitrarily. `object-fit`, `aspect-ratio`, and `object-position` for focal-point control are the direct web tools for this, and nothing is lost in translation.

**Safe areas → the viewport is not the drawable area.** Apple's safe area exists because hardware intrudes on the display: Dynamic Island, sensor housings, rounded corners, the home indicator, and on Mac the camera housing. The web equivalent is the `env(safe-area-inset-*)` family, exposed once the viewport is set to cover the whole display on notched devices. Full-bleed backgrounds should span the entire viewport while text and interactive targets respect the insets — the same relationship Apple describes between full-screen content and the safe area. The mapping isn't exact: the web's insets are static values reported once by the browser, while Apple's safe area is a live region that shrinks and grows as bars appear and disappear; on the web, browser chrome, a collapsing URL bar, and an on-screen keyboard create comparable problems but are handled by separate mechanisms — dynamic viewport units like `dvh` and the visual viewport API — rather than one unified concept.

**Where there is no web analogue.** Several things in this document don't carry over. The tvOS overscan safe area of 60 and 80 points exists because of CRT-era television hardware and has no browser equivalent. The visionOS rules about ornaments, window bounds, 3D content placement, and a 60-point minimum between button centers describe a spatial system with no 2D web counterpart; the underlying idea that interactive targets need generous separation is only weakly analogous to pointer hit-target sizing. The device dimension and size-class tables that Apple has since removed from this page (see Specifications above) have no useful web equivalent either — designing to a list of known screen sizes is precisely the approach responsive web design exists to replace.

## Do / Don't

| Do | Don't |
|---|---|
| Place the most important items near the top and leading side | Assume reading order is the same in every language |
| Align components with one another and use indentation to convey hierarchy | Leave components unaligned so the eye has no edge to track |
| Group related items with negative space, container shapes, or separator lines | Let unrelated items sit close enough to look related |
| Use disclosure triangles, menus, nested views, or scrollable sections for progressive disclosure | Show every choice at once and make people hunt for what matters |
| Differentiate controls from content with Liquid Glass and a scroll edge effect | Put a solid or semi-opaque background color behind controls |
| Use a background extension effect when a background image would be covered by a sidebar or inspector | Let scaled background art disappear behind fixed UI without accounting for it |
| Support Dynamic Type by letting views stack, grow, and wrap at larger text sizes | Crop or overlap text when it grows at larger sizes |
| Preview on multiple devices with different size classes, localizations, and text sizes, starting with the largest and smallest layouts | Ship after testing only one device configuration |
| Determine layout from size classes, not device type or orientation | Read a device's idiom or orientation as a substitute for available space |
| Consider every combination of size classes in both portrait and landscape | Design only for the orientation or size class you expect most often |
| Keep functionality identical as size classes change; vary only how much is visible onscreen | Remove or alter functionality because the window got smaller |
| Respect system-defined safe areas, margins, and guides | Let system UI or hardware features like Dynamic Island obstruct content |
| Keep controls and critical information away from the bottom of a macOS window | Assume a window's bottom edge is always on screen |
| Inset tvOS primary content 60 pt from the top and bottom, 80 pt from the sides | Place primary content in the overscan zone at the screen edges |
| Space visionOS buttons so their centers are at least 60 pt apart | Crowd interactive components so the hover effect obscures content |
| Limit a watchOS row to three glyph buttons or two text buttons | Line up more controls side by side than the screen comfortably holds |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
