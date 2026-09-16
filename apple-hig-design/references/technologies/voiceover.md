---
title: VoiceOver
url: https://developer.apple.com/design/human-interface-guidelines/voiceover
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-03-07
---

# VoiceOver

VoiceOver is a screen reader that lets people experience your app's interface without needing to see the screen.

## Core guidance

By supporting VoiceOver, you help people who are blind or have low vision access information in your app and navigate its interface and content when they can't see the display.

VoiceOver is supported in apps and games built for Apple platforms. It's also supported in apps and games developed in Unity using Apple's Unity plug-ins.

### Descriptions

You inform VoiceOver about your app's content by providing alternative text that explains your app's interface and the content it displays.

**Provide alternative labels for all key interface elements.** VoiceOver uses alternative labels (which aren't visible onscreen) to audibly describe your app's interface. System-provided controls have generic labels by default, but you should provide more descriptive labels that convey your app's functionality. Add labels to any custom elements your app defines. Be sure to keep your descriptions up-to-date as your app's interface and content change.

**Describe meaningful images.** If you don't describe key images in your app's content, people can't use VoiceOver to fully experience them within your app. Because VoiceOver helps people understand the interface surrounding images too, such as nearby captions, describe only the information the image itself conveys.

**Make charts and other infographics fully accessible.** Provide a concise description of each infographic that explains what it conveys. If people can interact with the infographic to get more or different information, make these interactions available to people using VoiceOver, too. The accessibility APIs offer ways to represent custom interactive elements so that assistive technologies can help people use them.

**Exclude purely decorative images from VoiceOver.** It's unnecessary to describe images that are decorative and don't convey useful or actionable information. Excluding these images shows respect for people's time and reduces cognitive load when they use VoiceOver.

### Navigation

**Use titles and headings to help people navigate your information hierarchy.** The title is the first information someone receives from an assistive technology when arriving on a page or screen in your app. Offer unique titles that succinctly describe each page's content and purpose. Likewise, use accurate section headings that help people build a mental model of each page's information hierarchy.

**Specify how elements are grouped, ordered, or linked.** Proximity, alignment, and other visible contextual cues help sighted people perceive the relationships between elements. Examine your app for places where relationships among elements are visual only. Then, describe these relationships to VoiceOver.

VoiceOver reads elements in the same order people read content in their active language and locale. For example, in US English, this is top-to-bottom, left-to-right.

> *Image caption:* Ungrouped related elements make it hard for VoiceOver to accurately describe the UI (each image is read before moving on to captions). Grouped related elements help VoiceOver accurately describe the UI (each image is read with its respective caption).

**Inform VoiceOver when visible content or layout changes occur.** People may find an unexpected content or layout change confusing because it means their mental map of the content is no longer accurate. It's crucial to report visible changes so VoiceOver and other assistive technologies can help people update their understanding of the content.

**Support the VoiceOver rotor when possible.** People can use an interface element called the VoiceOver rotor to navigate a document or webpage by headings, links, and other content types. You can help people navigate content in your app by identifying these elements to the rotor. The rotor can also bring up the braille keyboard.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, or watchOS.

### visionOS

**Be mindful that custom gestures aren't always accessible.** When VoiceOver is turned on in visionOS, apps and games that define custom gestures don't receive hand input by default. This ensures people can explore the interface using their voice, without an app responding to hand input at the same time. A person can opt out of this behavior by enabling Direct Gesture mode, which disables standard VoiceOver gestures and lets apps process hand input directly.

## Native implementation

**Related**
- Accessibility
- Inclusion

**Developer documentation**
- Accessibility
- VoiceOver
- Supporting VoiceOver in your app
- Accessibility modifiers
- Charts
- `accessibilityHidden(_:)`
- `accessibilityElement`
- `isAccessibilityElement`
- `shouldGroupAccessibilityChildren`
- `AccessibilityNotification`
- `AccessibilityRotorEntry` (SwiftUI)
- `UIAccessibilityCustomRotor` (UIKit)
- `NSAccessibilityCustomRotor` (AppKit)
- Improving accessibility support in your visionOS app

**Videos:** Writing Great Accessibility Labels · Tailor the VoiceOver experience in your data-rich apps · VoiceOver efficiency with custom rotors

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, but this is the one topic in this set where the mapping is not really an inference — VoiceOver and the web's screen readers (VoiceOver on Safari/macOS/iOS itself, NVDA, JAWS, TalkBack) solve the identical problem through the identical mechanism: an accessibility tree built from semantic structure, read aloud in a predictable order, with an API for exposing what plain markup can't express. Apple's rules here are screen-reader design principles stated once for their platform; the reasoning under each one is directly portable to any markup you write for the web, because HTML's accessibility tree and VoiceOver's UIKit/AppKit/SwiftUI accessibility tree are the same idea implemented on different platforms.

**"Provide alternative labels for all key interface elements" → this is exactly what accessible names are for on the web, and it's more automatic there than Apple's guidance implies.** Native UIKit controls need an explicit `accessibilityLabel` because a plain view has no inherent semantics. HTML controls often get their accessible name for free from visible text — a `<button>` with text content, a `<label>` wrapping an `<input>` — precisely because HTML elements carry built-in roles UIKit views don't. The obligation Apple states ("system-provided controls have generic labels by default, but you should provide more descriptive ones") becomes, on the web, an obligation to *not paper over* that free semantic labeling with a `<div>` styled to look like a button. Where the web genuinely needs the ARIA equivalent of `accessibilityLabel` is for controls that have no visible text — an icon-only button needs `aria-label` or visually-hidden text, the same gap Apple is describing for a custom icon-only control in UIKit.

**"Describe meaningful images, exclude purely decorative ones" → this is `alt` text policy, verbatim.** A meaningful image gets a concise, non-redundant `alt` description — Apple's instruction to describe "only the information the image itself conveys" because "VoiceOver helps people understand the interface surrounding images too" is precisely why web guidance says not to repeat a caption inside `alt` text; the screen reader will announce both, so redundant `alt` text produces the exact same double-reading problem VoiceOver has on any platform. A decorative image gets `alt=""` (or `role="presentation"` / `aria-hidden="true"`), which is the direct counterpart to `accessibilityHidden(_:)` — both remove noise from the tree rather than describe nothing usefully.

**"Make charts and infographics fully accessible" → this is a genuinely harder problem on the web than Apple's phrasing suggests, and worth being honest about.** A native chart built with Swift Charts can expose data points to the accessibility tree as discrete, navigable elements because the framework owns both the rendering and the accessibility representation. A web chart is very often an SVG or `<canvas>` drawing with no inherent semantics at all — `<canvas>` in particular is an accessibility dead end unless you separately maintain a parallel accessible representation (an offscreen data table, or ARIA-described regions). The reasoning transfers (concise summary plus, if the sighted version is interactive, an accessible way to get the same interactivity) but the implementation cost is higher: you're building the equivalent of Apple's accessibility API by hand rather than calling into a system-provided one.

**"Use titles and headings to convey your information hierarchy" → this is the single most direct transfer on the page, and it's where ARIA reasoning and VoiceOver reasoning are the same reasoning.** Apple's point that "the title is the first information someone receives... when arriving on a page or screen" is the exact justification for a unique, descriptive `<title>` element and a single well-placed `<h1>` per page. "Use accurate section headings that help people build a mental model of each page's information hierarchy" is a description of why a correct, non-skipping `<h1>`–`<h6>` outline matters — a screen reader's heading-navigation mode (jump by heading) is the direct web equivalent of the VoiceOver rotor's "navigate by headings" mode described later on this same page. Get the heading levels wrong (skip from `h2` to `h4` for visual-size reasons, or use headings for styling rather than structure) and you've broken the exact navigation aid Apple is asking developers to support.

**"Specify how elements are grouped, ordered, or linked" → this is the core justification for semantic HTML over div-soup, and for ARIA landmarks and grouping roles where semantics run out.** Apple's example — captions visually near an image read as separate, disconnected content unless VoiceOver is told they're related — is precisely the failure mode `<figure>`/`<figcaption>` exists to prevent, and the more general case (a custom widget where relationship is conveyed only by CSS proximity) is what `aria-labelledby`, `aria-describedby`, and landmark roles (`role="region"`, `<nav>`, `<main>`) are for. Visual grouping is not semantic grouping on either platform; both need an explicit relationship declared in the accessibility tree, not inferred from layout.

**"VoiceOver reads elements in the reading order of the active language and locale" → this is DOM order, and it's the reason CSS-only reordering is a trap.** A screen reader (VoiceOver on the web included) generally follows source/DOM order regardless of how CSS visually repositions elements with `order`, `flex-direction: row-reverse`, or absolute positioning. Apple's framing — that VoiceOver order should match the order sighted people read in — is the same rule that makes "make the DOM order match the visual reading order, and use CSS rather than DOM reordering for anything else" a load-bearing web accessibility rule, not a nice-to-have. Tab order (driven by DOM order and `tabindex`) inherits the same constraint for keyboard users, who face a closely related version of this problem.

**"Inform VoiceOver when visible content or layout changes occur" → this is ARIA live regions, and it's the place native and web accessibility diverge in a way worth naming.** Apple's `AccessibilityNotification` API lets a native app explicitly post "this changed" to VoiceOver. The web's `aria-live="polite"` / `aria-live="assertive"` regions do the same job, but they're a blunter instrument — get the live-region scope wrong (wrap too much, or forget to isolate the region that actually changes) and you get either silence or an overwhelming announcement flood, a failure mode that's easier to hit on the web because there's no single "post a notification" call, just a DOM mutation inside a region a screen reader is already watching. The underlying obligation is identical: any content update invisible sighted users would notice but a screen reader user wouldn't (a toast, an inline validation error, a live score) needs an explicit announcement path, not silent DOM mutation.

**"Support the VoiceOver rotor when possible" → the rotor's "navigate by headings, links, landmarks" modes are only as good as the semantic structure and ARIA landmarks you provide — there's no separate API to "support," the rotor consumes what correct markup already produces.** This is worth stating plainly because it inverts the usual native-to-web translation: on native platforms you often opt in to accessibility support with an explicit API call; on the web, correct use of headings, `<nav>`, `<main>`, `<button>` vs `<div onclick>`, and form `<label>`s *is* the rotor support. There's no additional step once the markup is right — which also means there's no way to bolt rotor-equivalent navigation onto bad markup after the fact; ARIA can patch labeling and state, but it can't retroactively give a document the same tree a native accessibility API can construct top-down from code.

Where the platforms genuinely diverge: visionOS's Direct Gesture mode — letting a VoiceOver user explicitly opt out of voice-driven exploration to let an app process hand input directly — has no web equivalent, because the web has no comparable default-blocks-custom-input-when-a-screen-reader-is-active behavior; a web page's pointer and keyboard event handlers run regardless of whether a screen reader is active, so the entire category of guidance ("custom gestures aren't always accessible, here's the opt-out") is native-only. This is a case where the platform imposes a safety default the web simply doesn't have, and a web app doing anything gesture-heavy has to build its own accessible alternative path rather than relying on the browser to arbitrate.

## Do / Don't

| Do | Don't |
|---|---|
| Provide descriptive labels for custom and icon-only controls | Rely on generic default labels for controls that need specific meaning |
| Describe images that convey information | Describe purely decorative images (or omit `alt` entirely and force a filename read-out) |
| Give every page/screen a unique, descriptive title and a correct heading outline | Skip heading levels for visual sizing, or use headings purely for styling |
| Explicitly relate visually-grouped elements (captions to images, labels to controls) | Rely on proximity or CSS alone to imply a relationship |
| Match reading order to DOM/source order | Use pure visual reordering that leaves reading order mismatched with layout |
| Announce visible content or layout changes to assistive tech | Mutate content silently and expect people to notice |
| Build genuine markup/semantics so rotor- and landmark-style navigation works | Treat accessible navigation as a bolt-on patch over generic `<div>` markup |
| Give people an accessible path to any interaction available only via custom gesture or hand input | Make an experience entirely inaccessible without sight or precise gesture input |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
