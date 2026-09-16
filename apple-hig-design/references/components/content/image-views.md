---
title: Image views
url: https://developer.apple.com/design/human-interface-guidelines/image-views
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-06-21
---

# Image views

An image view displays a single image — or in some cases, an animated sequence of images — on a transparent or opaque background.

## Core guidance

Within an image view, you can stretch, scale, size to fit, or pin the image to a specific location. Image views are typically not interactive.

### Best practices

**Use an image view when the primary purpose of the view is simply to display an image.** In rare cases where you might want an image to be interactive, configure a system-provided button to display the image instead of adding button behaviors to an image view.

**If you want to display an icon in your interface, consider using a symbol or interface icon instead of an image view.** SF Symbols provides a large library of streamlined, vector-based images that you can render with various colors and opacities. An icon (also called a glyph or template image) is typically a bitmap image in which the nontransparent pixels can receive color. Both symbols and interface icons can use the accent colors people choose.

### Content

An image view can contain rich image data in various formats, like PNG, JPEG, and PDF. For more guidance, see Images.

**Take care when overlaying text on images.** Compositing text on top of images can decrease both the clarity of the image and the legibility of the text. To help improve the results, ensure the text contrasts well with the image, and consider ways to make the text object stand out, like adding a text shadow or background layer.

**Aim to use a consistent size for all images in an animated sequence.** When you prescale images to fit the view, the system doesn't have to perform any scaling. In cases where the system must do the scaling, performance is generally better when all images are the same size and shape.

## Platform considerations

No additional considerations for iOS or iPadOS.

### macOS

**If your app needs an editable image view, use an image well.** An image well is an image view that supports copying, pasting, dragging, and using the Delete key to clear its content.

**Use an image button instead of an image view to make a clickable image.** An image button contains an image or icon, appears in a view, and initiates an instantaneous app-specific action.

### tvOS

Many tvOS images combine multiple layers with transparency to create a feeling of depth. For guidance, see Layered images.

### visionOS

Windows in visionOS apps and games can use image views to display 2D and stereoscopic images, as well as spatial photos. If your app uses RealityKit, you can also display images of any type outside of image views next to 3D content, or generate a spatial scene from an existing 2D image. For design guidance, see Images > visionOS; for developer guidance, see Image PresentationComponent.

For guidance on presenting other 3D content in a window or volume, see Windows > visionOS.

### watchOS

Use SwiftUI to create animations when possible. Alternatively, you can use WatchKit to animate a sequence of images within an image element if necessary. For developer guidance, see `WKImageAnimatable`.

## Native implementation

**Related**
- Images
- Image wells
- Image buttons
- SF Symbols

**Developer documentation**
- Image — SwiftUI
- `UIImageView` — UIKit
- `NSImageView` — AppKit

**Key APIs**
- `Image` — SwiftUI
- `UIImageView` — UIKit
- `NSImageView` — AppKit
- `WKImageAnimatable` — WatchKit, animate a sequence of images

**Videos:** Support HDR images in your app · Add rich graphics to your SwiftUI app

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Image view vs. symbol/icon → `<img>`/CSS background-image vs. an inline SVG or icon font.** Apple's distinction (a display-only bitmap or vector image versus a tintable, style-matched SF Symbol) maps to the choice between a raster/photographic `<img>` and an inline SVG icon that inherits `currentColor` and can be recolored with CSS. The reasoning is the same: an icon that needs to pick up an accent color or sit at multiple weights belongs in the SVG/icon-font category, not as a flattened bitmap.

**"Image views are typically not interactive; use a button instead" → don't wire click handlers onto a bare `<img>`.** The web equivalent of Apple's "configure a system-provided button to display the image" is wrapping the image in a real `<button>` (or `<a>`) element rather than attaching a click listener to an `<img>` or a `div` with a background image. This preserves keyboard focus, the accessible role, and Enter/Space activation for free — the things a system button gives Apple's platforms automatically.

**Overlaying text on images → contrast math applies identically, and CSS gives you more levers.** Apple's warning that compositing text over an image can wreck both the image's clarity and the text's legibility is a general design truth, not a platform one. The web adds tools Apple doesn't need to mention because they're already handled by the platform's material system: a `text-shadow`, a semi-transparent gradient scrim behind the text, or a `backdrop-filter` blur on a background layer. The underlying obligation — verify actual contrast, don't just eyeball it — is identical.

**Consistent image sizing in an animated sequence → this is a performance argument that transfers directly to `srcset`/sprite sheets.** Apple's point is that prescaling avoids runtime scaling cost. On the web, the same principle argues for serving pre-sized images via `srcset`/`sizes` rather than shipping one oversized image and letting CSS scale it down, and for using a single sprite sheet or consistent frame dimensions for any CSS/JS-driven animation sequence, so the browser isn't recomputing layout or repainting at mismatched sizes each frame.

**macOS's editable "image well" → the closest web analogue is a drag-and-drop upload zone, and the parity is only partial.** An image well supports copy, paste, drag, and Delete to clear — that's a small, well-defined interaction contract. A web file-drop zone bound to the Clipboard API and drag-and-drop events can replicate copy/paste/drag/delete, but there's no standard HTML element for it the way `NSImageView` gives macOS one for free; every part of the interaction has to be built and made keyboard-accessible by hand.

**visionOS spatial photos and 3D content → no meaningful web analogue.** Stereoscopic and spatial image presentation is tied to visionOS's rendering stack and RealityKit; nothing in the standard web platform reproduces it. WebXR is the nearest adjacent technology, but it's a different, opt-in experience model rather than a drop-in mapping for an inline image view, so this guidance is best treated as platform-specific.

## Do / Don't

| Do | Don't |
|---|---|
| Use an image view purely to display an image | Add button behaviors directly to an image view |
| Use a system-provided button to make an image interactive | Wire tap/click handling onto a plain image view |
| Use SF Symbols or an interface icon for icons | Use a full image view for something that's really an icon |
| Ensure text overlaid on an image has strong contrast | Composite text on an image without checking legibility |
| Prescale images to a consistent size for animated sequences | Mix differently sized/shaped images in one animated sequence |
| On macOS, use an image well for editable images | Build custom copy/paste/drag handling when an image well would do |
| On macOS, use an image button for a clickable image | Repurpose a plain image view as a click target |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
