---
title: Scroll views
url: https://developer.apple.com/design/human-interface-guidelines/scroll-views
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2026-06-08
---

# Scroll views

A scroll view lets people view content that's larger than the view's boundaries by moving the content vertically or horizontally.

## Core guidance

The scroll view itself has no appearance, but it can display a translucent scroll indicator that typically appears after people begin scrolling the view's content. Although the appearance and behavior of scroll indicators can vary per platform, all indicators provide visual feedback about the scrolling action. For example, in iOS, iPadOS, macOS, visionOS, and watchOS, the indicator shows whether the currently visible content is near the beginning, middle, or end of the view.

### Best practices

**Support default scrolling gestures and keyboard shortcuts.** People are accustomed to the systemwide scrolling behavior and expect it to work everywhere. If you build custom scrolling for a view, make sure your scroll indicators use the elastic behavior that people expect.

**Make it apparent when content is scrollable.** Because scroll indicators aren't always visible, it can be helpful to make it obvious when content extends beyond the view. For example, displaying partial content at the edge of a view indicates that there's more content in that direction. Although most people immediately try scrolling a view to discover if additional content is available, it's considerate to draw their attention to it.

**Avoid putting a scroll view inside another scroll view with the same orientation.** Nesting scroll views that have the same orientation can create an unpredictable interface that's difficult to control. It's alright to place a horizontal scroll view inside a vertical scroll view (or vice versa), however.

**Consider supporting page-by-page scrolling if it makes sense for your content.** In some situations, people appreciate scrolling by a fixed amount of content per interaction instead of scrolling continuously. On most platforms, you can define the size of such a page — typically the current height or width of the view — and define an interaction that scrolls one page at a time. To help maintain context during page-by-page scrolling, you can define a unit of overlap, such as a line of text, a row of glyphs, or part of a picture, and subtract the unit from the page size.

**In some cases, scroll automatically to help people find their place.** Although people initiate almost all scrolling, automatic scrolling can be helpful when relevant content is no longer in view, such as when:

- Your app performs an operation that selects content or places the insertion point in an area that's currently hidden. For example, when your app locates text that people are searching for, scroll the content to bring the new selection into view.
- People start entering information in a location that's not currently visible. For example, if the insertion point is on one page and people navigate to another page, scroll back to the insertion point as soon as they begin to enter text.
- The pointer moves past the edge of the view while people are making a selection. In this case, follow the pointer by scrolling in the direction it moves.
- People select something and scroll to a new location before acting on the selection. In this case, scroll until the selection is in view before performing the operation.

In all cases, **automatically scroll the content only as much as necessary to help people retain context.** For example, if part of a selection is visible, you don't need to scroll the entire selection into view.

**If you support zoom, set appropriate maximum and minimum scale values.** For example, zooming in on text until a single character fills the screen doesn't make sense in most situations.

### Scroll edge effects

In iOS, iPadOS, and macOS, a scroll edge effect provides a visual separation between certain interface elements, such as toolbars, and the scrolling content area behind them. If you use custom bars, you might want to add this effect manually if the top layer of your interface needs extra clarity, or adjust its style from automatic to the hard or soft style.

> *Image caption:* Hard scroll edge effect
> *Image caption:* Soft scroll edge effect

**Prefer the automatic scroll edge effect style.** Where possible, use the default automatic style of the scroll edge effect. This style provides a more opaque visual separation for top toolbars that contain a large number of controls, text that appears outside of Liquid Glass controls, and pinned table headers. If you use the soft scroll edge effect style instead, thoroughly test your interface to ensure your controls maintain legibility in a variety of contexts.

**Only use a scroll edge effect when a scroll view is behind floating interface elements.** Scroll edge effects aren't decorative. They don't block or darken like overlays; they exist to ensure controls stay visually distinct.

**Apply one scroll edge effect per view.** In split view layouts on iPad and Mac, each pane can have its own scroll edge effect; in this case, keep them consistent in height to maintain alignment.

## Platform considerations

### iOS, iPadOS

**Consider showing a page control when a scroll view is in page-by-page mode.** Page controls show how many pages, screens, or other chunks of content are available and indicates which one is currently visible. For example, Weather uses a page control to indicate movement between people's saved locations. If you show a page control with a scroll view, don't show the scrolling indicator on the same axis to avoid confusing people with redundant controls.

### macOS

In macOS, a scroll indicator is commonly called a **scroll bar**.

**If necessary, use small or mini scroll bars in a panel.** When space is tight, you can use smaller scroll bars in panels that need to coexist with other windows. Be sure to use the same size for all controls in such a panel.

### tvOS

Views in tvOS can scroll, but they aren't treated as distinct objects with scroll indicators. Instead, when content exceeds the size of the screen, the system automatically scrolls the interface to keep focused items visible.

### visionOS

In visionOS, the scroll indicator has a small, fixed size to help communicate that people can scroll efficiently without making large movements. To make it easy to find, the scroll indicator always appears in a predictable location with respect to the window: vertically centered at the trailing edge during vertical scrolling and horizontally centered at the window's bottom edge during horizontal scrolling.

When people begin swiping content in the direction they want it to scroll, the scroll indicator appears at the window's edge, visually reinforcing the effect of their gesture and providing feedback about the content's current position and overall length. When people look at the scroll indicator and begin a drag gesture, the indicator enables a jog bar experience that lets people manipulate the scrolling speed instead of the content's position. In this experience, the scroll indicator reveals tick marks that speed up or slow down as people make small adjustments to their gesture, providing visual feedback that helps people precisely control scrolling acceleration.

**If necessary, account for the size of the scroll indicator.** Although the indicator's overall size is small, it's a little thicker than the same component in iOS. If your content uses tight margins, consider increasing them to prevent the scroll indicator from overlapping the content.

**Look to Scroll.** In views that support Look to Scroll, people can scroll using only their eyes. Scrolling starts when people look near the boundary of the scroll view — along the top and bottom for vertical scroll views, or along the sides for horizontal scroll views. For example, a person can look at the bottom edge of a Safari window to scroll the page down, or look at an album on the trailing edge in the Music app to scroll it horizontally toward the center of the page. Look to Scroll works in conjunction with existing behavior, so someone can choose whether to use a gesture or their eyes to scroll.

**Support Look to Scroll for reading or browsing views.** Because Look to Scroll doesn't work by default, you need to add support for it to each individual scroll view. If your app contains reading or browsing views, add support for Look to Scroll to provide a comfortable and hands-free experience.

**Avoid using Look to Scroll for secondary content.** In general, support standard gestures — but not Look to Scroll — in views that contain UI controls or dense information that requires quick, precise scrolling. For example, the Notes app offers Look to Scroll within the main view to let people easily read their content, but doesn't support it for the list of notes.

**Maintain consistency across content.** If you support Look to Scroll for one view in your app, make sure to support it for all similar views. For example, if you offer several collection views of videos throughout your app, support Look to Scroll for each of these views so people know what to expect.

**Define clear scroll areas within your app.** In views that support Look to Scroll, prefer making the view the full width or full height of the window. This gives people generous space to scroll and provides clear edges. If you inset a scroll view from a window, like in the Notes app, provide clear boundaries so people know where to look.

**If your app uses custom scroll effects or animations, remove them before supporting Look to Scroll.** Custom effects that use scroll position to change content, such as parallax effects and animations, can cause Look to Scroll to behave unexpectedly.

### watchOS

**Prefer vertically scrolling content.** People are accustomed to using the Digital Crown to navigate to and within apps on Apple Watch. If your app contains a single list or content view, rotating the Digital Crown scrolls vertically when your app's content is taller than the height of the display.

**Use tab views to provide page-by-page scrolling.** watchOS displays tab views as pages. If you place tab views in a vertical stack, people can rotate the Digital Crown to move vertically through full-screen pages of content. In this scenario, the system displays a page indicator next to the Digital Crown that shows people where they are in the content, both within the current page and within a set of pages.

**When displaying paged content, consider limiting the content of an individual page to a single screen height.** Embracing this constraint clarifies the purpose of each page, helping you create a more glanceable design. However, if your app has long pages, people can still use the Digital Crown both to navigate between shorter pages and to scroll content in a longer page because the page indicator expands into a scroll indicator when necessary. Use variable-height pages judiciously and place them after fixed-height pages when possible.

## Native implementation

**Related**
- Page controls
- Gestures
- Pointing devices

**Developer documentation**
- `ScrollView` — SwiftUI
- `UIScrollView` — UIKit
- `NSScrollView` — AppKit
- `WKPageOrientation` — WatchKit
- `look` — SwiftUI
- `PagingScrollTargetBehavior` — SwiftUI
- `ScrollEdgeEffectStyle` — SwiftUI
- `UIScrollEdgeEffect.Style` — UIKit
- `NSScrollEdgeEffectStyle` — AppKit
- `ScrollInputKind` — SwiftUI (Look to Scroll)

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Support default scrolling gestures" → don't hijack native scroll behavior.** The web's baseline — wheel scroll, trackpad gesture, touch drag, arrow/Page keys, `scrollIntoView` — already matches what Apple describes, and it comes free from the browser. The web-specific failure mode Apple's rule warns against is `overflow: hidden` plus a hand-rolled JavaScript scroll implementation that skips native momentum, elastic overscroll, and keyboard support; use native scroll containers (`overflow: auto/scroll`) unless you have a concrete reason not to.

**Elastic/bounce behavior → CSS `overscroll-behavior` plus native momentum, not a custom animation.** Apple expects scroll indicators to show elastic behavior at the ends of content. Browsers on touch devices already rubber-band by default; the web-native lever you actually control is `overscroll-behavior`, mainly to prevent scroll chaining into a parent (e.g., a modal's background scrolling when the modal's content is exhausted) — the opposite problem from Apple's, but adjacent to it.

**"Avoid nesting scroll views with the same orientation" → applies unchanged, and is a common web bug.** A vertically-scrolling `<div>` inside another vertically-scrolling container produces exactly the unpredictable, hard-to-control interface Apple describes — usually surfacing as a scroll event that "gets stuck" in the inner container. Nesting perpendicular axes (horizontal carousel inside a vertical page) is fine on the web for the same reason it's fine natively.

**Page-by-page scrolling → CSS `scroll-snap-type` / `scroll-snap-align`.** This is a close, largely free mapping: `scroll-snap-type: x mandatory` (or `y`) with `scroll-snap-align: start` on children reproduces "scroll a fixed unit per interaction" without custom JavaScript, and the browser handles touch, wheel, and keyboard input consistently. Apple's "unit of overlap" idea (subtracting a line or row from the page size so context carries over) has no CSS equivalent — that's a JavaScript scroll-position calculation if you want it.

**Automatic scroll-to-selection → `scrollIntoView({ block, inline, behavior })`.** Apple's four triggering cases (search result found, off-screen text entry, pointer-drag past an edge, pre-action scroll to a selection) all reduce to the same web primitive: call `scrollIntoView` with `block: "nearest"` so you scroll only as far as needed, matching Apple's "only as much as necessary to retain context" instruction. Auto-scroll-following-a-drag-past-the-edge has no single built-in API; it is commonly implemented as a `requestAnimationFrame` loop that nudges `scrollTop`/`scrollLeft` while the pointer sits near a scroll container's edge.

**Zoom min/max clamping → applies directly, with a web-only accessibility caveat.** Setting sane zoom bounds on custom pinch/zoom content transfers unchanged. The caveat: never disable the browser's own page zoom (`user-scalable=no` or a `maximum-scale` lock in the viewport meta tag) to enforce this — that's a WCAG failure and blocks a core accessibility feature. Constrain zoom only within your own custom-rendered content (a canvas, an image viewer), never at the page level.

**Scroll edge effects → `backdrop-filter` plus a z-indexed toolbar, no native "edge effect" primitive.** Apple's automatic/hard/soft styles describe a gradient of opacity and blur applied to a bar sitting above scrolling content. The web equivalent is a sticky or fixed-position toolbar with `backdrop-filter: blur()` and a semi-transparent background, tuned toward more opaque (hard) or more blurred (soft) depending on content density — there's no shorthand that gives you Apple's "automatic" heuristic (adjusting itself based on control density) for free; you'd choose a style per toolbar deliberately.

**Look to Scroll → platform-specific; no web analogue.** Eye-tracking-driven scrolling depends on visionOS's gaze-tracking hardware and has no counterpart in a standard browser. The one principle that generalizes: Apple's instruction to disable custom scroll-position-driven effects (parallax, etc.) before enabling an alternate input method is really a reminder that content reacting to scroll position can break in an input modality you didn't test — worth checking whenever you support scroll-linked animation alongside keyboard or switch-control navigation on the web too.

## Do / Don't

| Do | Don't |
|---|---|
| Use native scroll containers and system gestures | Hand-roll scrolling and lose elastic/momentum behavior |
| Nest scroll views only with perpendicular orientations | Nest two scroll views with the same orientation |
| Scroll only as far as necessary to restore context | Scroll an entire selection into view when part of it is visible |
| Show a page control instead of a redundant scroll indicator in page mode | Show both a page control and a same-axis scroll indicator |
| Use the automatic scroll edge effect style by default | Add a scroll edge effect where no floating element sits above the content |
| Set sane min/max zoom bounds on custom zoomable content | Let zoom shrink content to an unusable single character |
| Keep one scroll edge effect per view, consistent across split-view panes | Stack multiple inconsistent edge effects in one split view |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
