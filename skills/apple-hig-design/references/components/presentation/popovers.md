---
title: Popovers
url: https://developer.apple.com/design/human-interface-guidelines/popovers
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Popovers

A popover is a transient view that appears above other content when people click or tap a control or interactive area.

## Core guidance

### Best practices

**Use a popover to expose a small amount of information or functionality.** Because a popover disappears after people interact with it, limit the amount of functionality in the popover to a few related tasks. For example, a calendar event popover makes it easy for people to change the date or time of an event, or to move it to another calendar. The popover disappears after the change, letting people continue reviewing the events on their calendar.

**Consider using popovers when you want more room for content.** Views like sidebars and panels take up a lot of space. If you need content only temporarily, displaying it in a popover can help streamline your interface.

**Position popovers appropriately.** Make sure a popover's arrow points as directly as possible to the element that revealed it. Ideally, a popover doesn't cover the element that revealed it or any essential content people may need to see while using it.

**Use a Close button for confirmation and guidance only.** A Close button, including Cancel or Done, is worth including if it provides clarity, like exiting with or without saving changes. Otherwise, a popover generally closes when people click or tap outside its bounds or select an item in the popover. If multiple selections are possible, make sure the popover remains open until people explicitly dismiss it or they click or tap outside its bounds.

**Always save work when automatically closing a nonmodal popover.** People can unintentionally dismiss a nonmodal popover by clicking or tapping outside its bounds. Discard people's work only when they click or tap an explicit Cancel button.

**Show one popover at a time.** Displaying multiple popovers clutters the interface and causes confusion. Never show a cascade or hierarchy of popovers, in which one emerges from another. If you need to show a new popover, close the open one first.

**Don't show another view over a popover.** Make sure nothing displays on top of a popover, except for an alert.

**When possible, let people close one popover and open another with a single click or tap.** Avoiding extra gestures is especially desirable when several different bar buttons each open a popover.

**Avoid making a popover too big.** Make a popover only big enough to display its contents and point to the place it came from. If necessary, the system can adjust the size of a popover to ensure it fits well in the interface.

**Provide a smooth transition when changing the size of a popover.** Some popovers provide both condensed and expanded views of the same information. If you adjust the size of a popover, animate the change to avoid giving the impression that a new popover replaced the old one.

**Avoid using the word popover in help documentation.** Instead, refer to a specific task or selection. For example, instead of "Select the Show button at the bottom of the popover," you might write "Select the Show button."

**Avoid using a popover to show a warning.** People can miss a popover or accidentally close it. If you need to warn people, use an alert instead.

## Platform considerations

No additional considerations for visionOS. Not supported in tvOS or watchOS.

### iOS, iPadOS

**Avoid displaying popovers in compact views.** Make your app or game dynamically adjust its layout based on the size class of the content area. Reserve popovers for wide views; for compact views, use all available screen space by presenting information in a full-screen modal view like a sheet instead.

### macOS

**You can make a popover detachable in macOS**, which becomes a separate panel when people drag it. The panel remains visible onscreen while people interact with other content.

**Consider letting people detach a popover.** People might appreciate being able to convert a popover into a panel if they want to view other information while the popover remains visible.

**Make minimal appearance changes to a detached popover.** A panel that looks similar to the original popover helps people maintain context.

## Native implementation

**Related**
- Sheets
- Action sheets
- Alerts
- Modality

**Developer documentation**
- `popover(isPresented:attachmentAnchor:arrowEdge:content:)` — SwiftUI
- `UIPopoverPresentationController` — UIKit
- `NSPopover` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Popover → the Popover API (`popover` attribute, `popovertarget`, `showPopover()`), not `<dialog>`.** This is the cleanest mapping in this whole group of topics: Apple's popover is explicitly nonmodal, transient, anchor-positioned, and light-dismissed by an outside click — which is precisely the browser's native Popover API's behavior. It renders in the top layer without trapping focus or requiring a backdrop, closes on outside click and `Escape` by default, and needs no custom focus-management code. Where Apple's popover needs modal-like blocking (rare, and generally discouraged per "avoid showing a warning" below), that's a sign to use `<dialog>` instead — the two APIs map to Apple's modal/nonmodal split almost exactly.

**Arrow anchoring → CSS anchor positioning.** "Make sure a popover's arrow points as directly as possible to the element that revealed it" is exactly what CSS anchor positioning (`anchor()`, `position-anchor`) is for: tethering a popover's position, and optionally a CSS-drawn arrow, to its triggering element, with fallback positions when the popover would overflow the viewport. Where anchor positioning isn't yet available, a JavaScript positioning library (Floating UI or similar) fills the same role — manual `getBoundingClientRect()` math is what both are trying to replace.

**"Show one popover at a time" → the Popover API enforces most of this for you.** Native popovers of type `auto` automatically close sibling popovers when a new one opens, which mirrors Apple's rule directly. You mainly need to enforce it yourself if you mix popover implementations or use `manual` popover type.

**"Always save work when automatically closing a nonmodal popover" → applies unchanged, and is easy to get wrong.** Light-dismiss is convenient but accidental; any state a user edited inside a popover should persist automatically on light-dismiss, with an explicit Cancel/discard control reserved for intentional discarding — same logic Apple states for the native case.

**"Avoid using a popover to show a warning" → holds even more strongly on the web.** A nonmodal, light-dismissible surface is trivially missed or dismissed with a stray click; warnings that must be seen belong in a modal `<dialog>` or, per the Alerts translation, sometimes not even there — inline validation next to the relevant control is often better than either.

**Detachable popover → panel (macOS) has no clean web equivalent.** "Drag the popover and it becomes a persistent floating panel" depends on a desktop windowing model the web doesn't have. The nearest approximation is a separate, draggable floating panel component (its own top-layer element, its own drag handling) that the popover can hand off to — but this is a bespoke UI pattern to build, not something a web API provides.

## Do / Don't

| Do | Don't |
|---|---|
| Point the popover's arrow at the element that revealed it | Let a popover cover its own trigger or essential content |
| Show one popover at a time, closing others first | Cascade popovers, with one emerging from another |
| Save work automatically on light-dismiss | Discard unsaved changes on an accidental outside click |
| Size a popover to its content | Make a popover larger than its content needs |
| Animate a popover's size change | Swap popover size abruptly, implying a new popover replaced it |
| Use an alert for anything that must not be missed | Use a popover to show a warning |
| Reserve popovers for wide/regular size classes on iOS | Show a popover in a compact-width layout |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
