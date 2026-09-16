---
title: Page controls
url: https://developer.apple.com/design/human-interface-guidelines/page-controls
platforms: [iOS, iPadOS, tvOS, visionOS, watchOS]
last_updated: 2023-06-21
---

# Page controls

A page control displays a row of indicator images, each of which represents a page in a flat list.

## Core guidance

The scrolling row of indicators helps people navigate the list to find the page they want. Page controls can handle an arbitrary number of pages, making them particularly useful in situations where people can create custom lists.

Page controls appear as a series of small indicator dots by default, representing the available pages. A solid dot denotes the current page. Visually, these dots are always equidistant, and are clipped if there are too many to fit in the window.

### Best practices

**Use page controls to represent movement between an ordered list of pages.** Page controls don't represent hierarchical or nonsequential page relationships. For more complex navigation, consider using a sidebar or split view instead.

**Center a page control at the bottom of the view or window.** To ensure people always know where to find a page control, center it horizontally and position it near the bottom of the view.

Although page controls can handle any number of pages, **don't display too many.** More than about **10 dots** are hard to count at a glance. If your app needs to display more than 10 pages as peers, consider using a different arrangement — such as a grid — that lets people navigate the content in any order.

### Customizing indicators

By default, a page control uses the system-provided dot image for all indicators, but it can also display a unique image to help people identify a specific page. For example, Weather uses the `location.fill` symbol to distinguish the current location's page.

If it enhances your app or game, you can provide a custom image to use as the default image for all indicators and you can also supply a different image for a specific page.

**Make sure custom indicator images are simple and clear.** Avoid complex shapes, and don't include negative space, text, or inner lines, because these details can make an icon muddy and indecipherable at very small sizes. Consider using simple SF Symbols as indicators or design your own icons.

**Customize the default indicator image only when it enhances the page control's overall meaning.** For example, if every page you list contains bookmarks, you might use the `bookmark.fill` symbol as the default indicator image.

**Avoid using more than two different indicator images in a page control.** If your list contains one page with special meaning — like the current-location page in Weather — you can make the page easy to find by giving it a unique indicator image. In contrast, a page control that uses several unique images to mark several important pages is hard to use because people must memorize the meaning of each image. A page control that displays more than two types of indicator images tends to look messy and haphazard, even when each image is clear.

> *Image caption:* Using several different indicators can make a page control look busy and difficult to use.
> *Image caption:* Using only two different indicators looks well-organized and provides a consistent experience.

**Avoid coloring indicator images.** Custom colors can reduce the contrast that differentiates the current-page indicator and makes the page control visible on the screen. To ensure that your page control is easy to use and looks good in different contexts, let the system automatically color the indicators.

## Platform considerations

Not supported in macOS.

### iOS, iPadOS

A page control can adjust the appearance of indicators to provide more information about the list. For example, the control highlights the indicator of the current page so people can estimate the page's relative position in the list. When there are more indicators than fit in the space, the control can shrink indicators at both sides to suggest that more pages are available.

People interact with page controls by **tapping** or **scrubbing** (to scrub, people touch the control and drag left or right). Tapping on the leading or trailing side of the current-page indicator reveals the next or previous page; in iPadOS, people can also use the pointer to target a specific indicator. Scrubbing opens pages in sequence, and scrubbing past the leading or trailing edge of the control helps people quickly reach the first or last page.

> **Developer note (Apple):** In the API, tapping is a discrete interaction, whereas scrubbing is a continuous interaction; for developer guidance, see `UIPageControl.InteractionState`.

**Avoid animating page transitions during scrubbing.** People can scrub very quickly, and using the scrolling animation for every transition can make your app lag and cause distracting visual flashes. Use the animated scrolling transition only for tapping.

A page control can include a translucent, rounded-rectangle background appearance that provides visual contrast for the indicators. You can choose one of the following background styles:

- **Automatic** — Displays the background only when people interact with the control. Use this style when the page control isn't the primary navigational element in the UI.
- **Prominent** — Always displays the background. Use this style only when the control is the primary navigational control in the screen.
- **Minimal** — Never displays the background. Use this style when you just want to show the position of the current page in the list and you don't need to provide visual feedback during scrubbing.

**Avoid supporting the scrubber when you use the minimal background style.** The minimal style doesn't provide visual feedback during scrubbing. If you want to let people scrub a list of pages in your app, use the automatic or prominent background styles.

### tvOS

**Use page controls on collections of full-screen pages.** A page control is designed to operate in a full-screen environment where multiple content-rich pages are peers in the page hierarchy. Inclusion of additional controls makes it difficult to maintain focus while moving between pages.

### visionOS

In visionOS, page controls represent available pages and indicate the current page, but people don't interact with them.

### watchOS

In watchOS, page controls can be displayed at the bottom of the screen for horizontal pagination, or next to the Digital Crown when presenting a vertical tab view. When using vertical tab views, the page indicator shows people where they are in the navigation, both within the current page and within the set of pages. The page control transitions between scrolling through a page's content and scrolling to other pages.

**Use vertical pagination to separate multiple views into distinct, purposeful pages.** Give each page a clear purpose, and let people scroll through the pages using the Digital Crown. In watchOS, this design is more effective than horizontal pagination or many levels of hierarchical navigation.

**Consider limiting the content of an individual page to a single screen height.** Embracing this constraint encourages each page to serve a clear and distinct purpose and results in a more glanceable design. Use variable-height pages judiciously and, if possible, only place them after fixed-height pages in your app design.

## Native implementation

**Related**
- Scroll views

**Developer documentation**
- `PageTabViewStyle` — SwiftUI
- `UIPageControl` — UIKit
- `UIPageControl.InteractionState` — UIKit
- `preferredIndicatorImage` — UIKit
- `setIndicatorImage(_:forPage:)` — UIKit
- `backgroundStyle` — UIKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Page control → a carousel's dot indicators, built as real controls, not decoration.** The visual form — a row of small dots, one solid to mark the current page — is trivial to reproduce in CSS. The part worth being deliberate about is semantics: each dot should be a real button (or a radio-group of buttons) with an accessible label like "Page 3 of 7," not a `<div>` styled to look clickable. Apple's control is natively focusable and VoiceOver-readable; a div-based carousel indicator usually isn't, unless you add the roles and labels yourself.

**"Represents an ordered, flat list, not hierarchy" → keep the same restriction.** This is a navigation-semantics rule, not a rendering one, and it transfers directly: don't repurpose a page-control-style dot row for a nonsequential set of tabs or a hierarchical section list. If the relationship between "pages" isn't linear and peer-level, a page control (native or web) is the wrong control regardless of platform.

**Center at the bottom → a layout convention, not a technical constraint.** Nothing prevents a web carousel's dots from living elsewhere, but Apple's placement rule reflects a genuinely learned convention across mobile and desktop software; deviating from it costs discoverability for no real benefit, so it's worth keeping unless there's a strong reason not to.

**"More than about 10 dots are hard to count" → the number is Apple's own usability threshold and travels as-is.** There's nothing platform-specific about the claim — it's about the limits of at-a-glance counting, not about pixel density or gesture area. If a web carousel would need more than 10 dots, switch to the same fallback Apple recommends: a grid or another arrangement that supports non-sequential navigation, rather than compressing indicators until they're unreadable.

**Tap vs. scrub interaction → pointer/touch event handling, with a11y as the harder part.** Discrete tap-to-advance is a plain click handler. Continuous scrub (drag across the control to sweep through pages) requires pointer-move tracking with a distance-to-page-index mapping — there's no CSS or native HTML behavior that gives you this; every carousel library implements it by hand. Whatever you build, keep arrow-key navigation working on the indicator's focused control, since scrub gestures assume a pointer device Apple's own control doesn't require either (VoiceOver users on iOS still get discrete next/previous).

**"Avoid animating transitions during scrubbing" → matches a general web-perf rule: don't force a full transition on every fast-fired input event.** Running a CSS transition or JS animation on every scrub-drag event, rather than only on discrete taps, produces exactly the lag and visual flashing Apple describes — throttle or skip the animation during continuous drag and only animate the settle-to-final-page step.

**Automatic/Prominent/Minimal background styles → a straightforward opacity/visibility state machine in CSS, no native equivalent needed.** These map directly to conditional classes toggled on hover/interaction state; nothing about them depends on a platform capability the web lacks.

## Do / Don't

| Do | Don't |
|---|---|
| Use a page control only for an ordered, flat list of pages | Use a page control for hierarchical or nonsequential navigation |
| Center the control near the bottom of the view | Place the control somewhere people won't expect to find it |
| Keep the indicator count to about 10 or fewer | Let a page control grow past 10 dots without switching to a grid |
| Use at most two distinct indicator images | Use several unique indicator images that people must memorize |
| Let the system color the indicators | Apply custom colors that reduce current-page contrast |
| Animate the scrolling transition only for taps | Animate every scrub event and cause lag or flashing |
| Provide visual scrub feedback with the automatic/prominent style | Support scrubbing while using the minimal background style |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
