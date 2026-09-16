---
title: Image wells
url: https://developer.apple.com/design/human-interface-guidelines/image-wells
platforms: [macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Image wells

An image well is an editable version of an image view.

## Core guidance

After selecting an image well, people can copy and paste its image or delete it. People can also drag a new image into an image well without selecting it first.

### Best practices

**Revert to a default image when necessary.** If your image well requires an image, display the default image again if people clear the content of the image well.

**If your image well supports copy and paste, make sure the standard copy and paste menu items are available.** People generally expect to choose these menu items — or use the standard keyboard shortcuts — to interact with an image well. For guidance, see Edit menu.

For related guidance, see Image views.

## Platform considerations

Not supported in iOS, iPadOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Image views

**Developer documentation**
- `NSImageView` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**There is no native HTML element for an image well.** `<input type="file" accept="image/*">` handles picking a file from disk, but it does not display the chosen image as a persistent, editable, in-place preview, does not support drag-and-drop replacement out of the box, and does not support copy/paste of image data without extra JavaScript wired to the Clipboard API. An image well on the web is necessarily a custom composite: a preview element plus a file input plus drag-and-drop handlers plus clipboard event handlers, not a single control.

**"Revert to a default image when cleared" → treat the default image as the field's real empty state, not a placeholder graphic.** Apple's rule matters because a required image well should never render visually empty. On the web this means the fallback image should be the same `<img>` element with its `src` swapped back, not a CSS `background-image` placeholder that behaves differently for assistive technology and print. If the well is required, disable or hide any "clear" affordance that would leave it in a state your validation would reject, or make the revert automatic as Apple specifies.

**"Standard copy and paste menu items must be available" → the accessibility gap is real and it's the crux of this component.** This is where the web genuinely falls short of what Apple describes. macOS gives `NSImageView` copy/paste for free through the system Edit menu and standard keyboard shortcuts, and critically, that same menu and those same shortcuts are what VoiceOver users and keyboard-only users rely on to operate the well without a mouse. A custom web image well built only with drag-and-drop and a hidden file input is invisible to a keyboard-only or screen-reader user unless you deliberately wire up `paste` event handling on a focusable element, expose a visible and keyboard-reachable "choose image" button (not just a drop zone), and provide a reachable "remove image" control. Building a beautiful drag-and-drop zone without those three things reproduces the visual metaphor while dropping the actual interaction the majority of Apple's guidance is protecting.

**Drag-to-replace without first selecting → supported, but needs an explicit drop-target affordance.** The HTML Drag and Drop API supports dropping a file onto an element without that element having focus first, matching Apple's "no selection required" behavior. But web drag-and-drop has no built-in visual cue that a given element accepts drops; you must style `dragenter`/`dragover` states yourself so the target is visually obvious, since a browser gives no hint by default the way a system-drawn well might.

## Do / Don't

| Do | Don't |
|---|---|
| Revert to the default image when a required well is cleared | Leave a required image well visibly empty |
| Expose copy, paste, and delete for the well's image | Make the well operable only by drag-and-drop |
| Provide a focusable, keyboard-reachable way to choose or remove an image | Rely solely on a drop zone with no keyboard path |
| Let people drop a new image in without selecting the well first | Require a click-to-select step before every drag replacement |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
