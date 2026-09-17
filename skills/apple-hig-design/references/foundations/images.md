---
title: Images
url: https://developer.apple.com/design/human-interface-guidelines/images
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-12-16
---

# Images

To make sure your artwork looks great on all devices you support, learn how the system displays content and how to deliver art at the appropriate scale factors.

## Core guidance

### Resolution

Different devices can display images at different resolutions. For example, a 2D device displays images according to the resolution of its screen.

A point is an abstract unit of measurement that helps visual content remain consistent regardless of how it's displayed. In 2D platforms, a point maps to a number of pixels that can vary according to the resolution of the display; in visionOS, a point is an angular value that allows visual content to scale according to its distance from the viewer.

When creating bitmap images, you specify a scale factor which determines the resolution of an image. You can visualize scale factor by considering the density of pixels per point in 2D displays of various resolutions. For example, a scale factor of 1 (also called @1x) describes a 1:1 pixel density, where one pixel is equal to one point. High-resolution 2D displays have higher pixel densities, such as 2:1 or 3:1. A 2:1 density (called @2x) has a scale factor of 2, and a 3:1 density (called @3x) has a scale factor of 3. Because of higher pixel densities, high-resolution displays demand images with more pixels.

> *Image caption:* A side-by-side comparison of the same image at each scale factor — 1x renders at 10×10 px, 2x at 20×20 px, and 3x at 30×30 px — showing how pixel density increases with scale factor while the point size stays constant.

**Provide high-resolution assets for all bitmap images in your app, for every device you support.** As you add each image to your project's asset catalog, identify its scale factor by appending "@1x," "@2x," or "@3x" to its filename. Use the following values for guidance; for additional scale factors, see Layout.

| Platform | Scale factors |
|---|---|
| iPadOS, watchOS | @2x |
| iOS | @2x and @3x |
| visionOS | @2x or higher (see visionOS) |
| macOS, tvOS | @1x and @2x |

**In general, design images at the lowest resolution and scale them up to create high-resolution assets.** When you use resizable vectorized shapes, you might want to position control points at whole values so that they're cleanly aligned at 1x. This positioning allows the points to remain cleanly aligned to the raster grid at higher resolutions, because 2x and 3x are multiples of 1x.

### Formats

As you create different types of images, consider the following recommendations.

| Image type | Format |
|---|---|
| Bitmap or raster work | De-interlaced PNG files |
| PNG graphics that don't require full 24-bit color | An 8-bit color palette |
| Photos | JPEG files, optimized as necessary, or HEIC files |
| Stereo or spatial photos | Stereo HEIC |
| Flat icons, interface icons, and other flat artwork that requires high-resolution scaling | PDF or SVG files |

### Best practices

**Include a color profile with each image.** Color profiles help ensure that your app's colors appear as intended on different displays.

**Always test images on a range of actual devices.** An image that looks great at design time may appear pixelated, stretched, or compressed when viewed on various devices.

## Platform considerations

No additional considerations for iOS, iPadOS, or macOS.

### tvOS

Layered images are at the heart of the Apple TV user experience. The system combines layered images, transparency, scaling, and motion to produce a sense of realism and vigor that evokes a personal connection as people interact with onscreen content.

**Parallax effect**

Parallax is a subtle visual effect the system uses to convey depth and dynamism when an element is in focus. As an element comes into focus, the system elevates it to the foreground, gently swaying it while applying illumination that makes the element's surface appear to shine. After a period of inactivity, out-of-focus content dims and the focused element expands.

**Layered images are required to support the parallax effect.**

> **Important (Apple):** Your tvOS app icon must use a layered image. For other focusable images in your app, including Top Shelf images, layered images are strongly encouraged, but optional.

**Layered images**

A layered image consists of two to five distinct layers that come together to form a single image. The separation between layers, along with use of transparency, creates a feeling of depth. As someone interacts with an image, layers closer to the surface elevate and scale, overlapping lower layers farther back and producing a 3D effect.

You can embed layered images in your app or retrieve them from a content server at runtime.

> **Developer note (Apple):** If your app retrieves layered images from a content server at runtime, you must provide runtime layered images (.lcr). You can generate them from LSR files or Photoshop files using the layerutil command-line tool that Xcode provides. Runtime layered images are intended to be downloaded — don't embed them in your app.

**Use standard interface elements to display layered images.** If you use standard views and system-provided focus APIs — such as `FocusState` — layered images automatically get the parallax treatment when people bring them into focus.

**Identify logical foreground, middle, and background elements.** In foreground layers, display prominent elements like a character in a game, or text on an album cover or movie poster. Middle layers are perfect for secondary content and effects like shadows. Background layers are opaque backdrops that showcase the foreground and middle layers without upstaging them.

**Generally, keep text in the foreground.** Unless you want to obscure text, bring it to the foreground layer for clarity.

**Keep the background layer opaque.** Using varying levels of opacity to let content shine through higher layers is fine, but your background layer must be opaque — you'll get an error if it's not. An opaque background layer ensures your artwork looks great with parallax, drop shadows, and system backgrounds.

**Keep layering simple and subtle.** Parallax is designed to be almost unnoticeable. Excessive 3D effects can appear unrealistic and jarring. Keep depth simple to bring your content to life and add delight.

**Leave a safe zone around the foreground layers of your image.** When focused, content on some layers may be cropped as the layered image scales and moves. To ensure that essential content is always visible, keep it within a safe zone.

**Always preview layered images.** To ensure your layered images look great on Apple TV, preview them throughout your design process using Xcode, the Parallax Previewer app for macOS, or the Parallax Exporter plug-in for Adobe Photoshop. Pay special attention as scaling and clipping occur, and readjust your images as needed to keep important content safe. After your layered images are final, preview them on an actual TV for the most accurate representation of what people will see.

### visionOS

In visionOS, people can view images at a much larger range of sizes than in any other platform, and the system dynamically scales the image resolution to match the current size. Because you can position images at specific angles within someone's surroundings, image pixels may not line up 1:1 with screen pixels.

**Create a layered app icon.** App icons in visionOS are composed of two to three layers that provide the appearance of depth by moving at subtly different rates when the icon is in focus.

**Prefer vector-based art for 2D images.** Avoid bitmap content because it might not look good when the system scales it up.

**If you need to use rasterized images, balance quality with performance as you choose a resolution.** Although a @2x image looks fine at common viewing distances, its fixed resolution means that the system doesn't dynamically scale it and it might not look sharp from close up. To help a rasterized image look sharp when people view it from a wide range of distances, you can use a higher resolution, but each increase in resolution results in a larger file size and may impact your app's runtime performance, especially for resolutions over @6x. If you use images that have resolutions higher than @2x, be sure to also apply high-quality image filtering to help balance quality and performance.

**Spatial photos and spatial scenes**

In addition to 2D and stereoscopic images, visionOS apps and games can use RealityKit to display spatial photos and spatial scenes. A spatial photo is a stereoscopic photo with additional spatial metadata, as captured on iPhone 15 Pro or later, Apple Vision Pro, or other compatible camera. A spatial scene is a 3D image generated from a 2D image to add a parallax effect that responds to head movement.

**Make sure spatial photos render correctly in your app.** Use the stereo High-Efficiency Image Codec (HEIC) format to display a spatial photo in your app. When you add spatial metadata to a stereo HEIC, visionOS recognizes the photo as spatial and includes visual treatments that help minimize common causes of stereo-viewing discomfort.

**Prefer the feathered glass background effect to display text over spatial photos.** If you need to place text over a spatial photo in your app or game, use the feathered glass background effect. The effect adds contrast to make the text readable, and it blurs out detail to help reduce visual discomfort when people view text over spatial photos.

**Take visual comfort into consideration when you make spatial photos from existing 2D content.** When adjusting the spatial metadata of a photo for your app or game, consider how you want people to view your content. Metadata like disparity adjustment can alter how people perceive the 3D scene, and can cause visual discomfort from certain viewing positions.

**Display spatial photos and spatial scenes in standalone views.** Avoid displaying spatial photos inline with other content, as this can cause visual discomfort. Instead, showcase spatial photos or spatial scenes in a separate view, like a sheet or window. If you must display stereoscopic images inline, provide generous spacing between the image and any inline content to help people's eyes adjust to the depth changes.

**Use spatial scenes in your app for specific moments.** Each spatial scene can take up to several seconds to generate from an existing image. Design experiences with this limitation in mind. For instance, the Photos app offers an explicit action to create a spatial scene while immersed in a single photo. Avoid displaying too many spatial scenes at once. Instead, use scroll views, pagination, or explicit actions to move to new photos and keep the visual information hierarchy simple.

**When displaying immersively, prefer minimal UI.** For example, the Spatial Gallery app displays a single piece of content with a small caption and a single Back button, relying on swipe gestures to navigate between items.

**Prefer displaying larger spatial scenes that you center in someone's field of view.** When people view a spatial scene, they may move their head laterally to view the parallax effect. Smaller spatial scenes provide less of a parallax effect and may not be as impactful to viewers.

### watchOS

**In general, avoid transparency to keep image files small.** If you always composite an image on the same solid background color, it's more efficient to include the background in the image. However, transparency is necessary in complication images, menu icons, and other interface icons that serve as template images, because the system uses it to determine where to apply color.

**Use autoscaling PDFs to let you provide a single asset for all screen sizes.** Design your image for the 40mm and 42mm screens at 2x. When you load the PDF, WatchKit automatically scales the image based on the device's screen size — see Specifications for the per-screen-size scale values.

## Specifications

### Scale factor definitions

| Scale factor | Pixel density | Example (10×10 pt asset) |
|---|---|---|
| @1x | 1:1 | 10×10 px |
| @2x | 2:1 | 20×20 px |
| @3x | 3:1 | 30×30 px |

### watchOS image scale by screen size

WatchKit scales an autoscaling PDF asset — designed for the 40mm and 42mm screens at 2x — using the following per-screen-size percentages.

| Screen size | Image scale |
|---|---|
| 38mm | 90% |
| 40mm | 100% |
| 41mm | 106% |
| 42mm | 100% |
| 44mm | 110% |
| 45mm | 119% |
| 49mm | 119% |

## Native implementation

**Related**
- Apple Design Resources
- Layout — additional scale-factor guidance beyond the values listed above
- Color management — color profile guidance
- App icons — safe-zone guidance for tvOS layered images

**Developer documentation**
- Drawing sharp layer-based content in visionOS — visionOS
- Images — SwiftUI
- UIImageView — UIKit
- NSImageView — AppKit
- Parallax Previewer User Guide — adding layered images to a tvOS app
- Layer design — visionOS layered app icons
- filters — high-quality image filtering for visionOS rasterized images above @2x
- ImagePresentationComponent — RealityKit spatial photos and spatial scenes
- GlassBackgroundEffect — feathered glass background effect for text over spatial photos
- Creating spatial photos and videos with spatial metadata

**Key APIs and tools**
- `FocusState` — SwiftUI focus API; standard views paired with it get automatic parallax treatment for layered images on tvOS
- `layerutil` — Xcode command-line tool that generates runtime layered images (.lcr) from LSR or Photoshop files
- Asset catalog scale-factor suffixes — `@1x`, `@2x`, `@3x` filename suffixes that identify an image's scale factor
- Stereo HEIC — image format for stereo/spatial photos, carrying spatial metadata

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Scale factors (@1x/@2x/@3x) → density descriptors in `srcset`.** Apple's scale-factor system exists because it controls a small, closed catalog of physical displays and can therefore pre-bake exact pixel multiples for each one. The web's closest literal equivalent is `srcset` with `1x`/`2x`/`3x` density descriptors, which lets the browser pick the asset matching the device's pixel ratio. But the analogy is partial: Apple only has to solve for pixel density, because point-based layout already handles viewport variation, whereas a web page must solve for viewport width *and* density at once — which is why `srcset` with `w` descriptors plus a `sizes` attribute, not `x` descriptors, is the more common real-world choice on responsive layouts.

**"Design at the lowest resolution and scale up" → prefer vector formats, don't upscale raster.** Apple's rule about aligning vector control points to whole values at 1x exists because 2x/3x are exact multiples of 1x, so a vector asset scales losslessly across all three. The web equivalent is using SVG for anything that would qualify for Apple's "flat icons, interface icons, and flat artwork" bucket, for exactly the same reason: a vector definition sidesteps the multi-resolution export problem entirely rather than solving it per breakpoint.

**Format-by-content-type table → `picture` element art direction, plus format negotiation.** Apple's Format table assigns a format per image type (photos get JPEG/HEIC, flat art gets PDF/SVG) because each format's compression model suits different content: lossy compression hides artifacts well in photographic detail but destroys flat-color edges, while vector formats have no resolution ceiling for geometric shapes. The web mirrors this with format-by-content-type choices — WebP or AVIF for photographic content, SVG for icons and flat art — and the `picture` element lets you serve different formats (or crops) to different browsers or viewport sizes, which is the closest web analog to swapping an entire asset rather than just its resolution.

**Color profile inclusion → color-managed image pipelines and sRGB as the safe default.** Apple's reasoning is that a color profile is what keeps a color looking like the same color across differently calibrated displays. The web mostly relies on images shipping with (or defaulting to) an sRGB profile, since that's the color space nearly all browsers and displays assume without an embedded profile; wide-gamut (Display P3) images need an embedded profile or they'll look oversaturated on standard displays, which is the direct web analog of Apple's warning.

**"Test on a range of actual devices" → responsive testing across real viewports and pixel ratios, not just browser resize.** The underlying point is the same: an image evaluated only in one design-time context can look pixelated, stretched, or compressed elsewhere. On the web this means checking actual devicePixelRatio values and real network conditions, not only resizing a desktop browser window.

**visionOS's resolution-vs-performance trade-off (@2x fine at distance, diminishing returns past @6x) → `loading=lazy` and deliberate compression budgets.** Apple's underlying claim is that more pixels cost real, measurable runtime cost, so resolution should be chosen deliberately rather than maximized by default. The web version of "choose deliberately" is being disciplined about compression quality settings and byte budgets per image, and deferring offscreen images with `loading=lazy` so the performance cost is paid only when the image is actually needed.

**Where the mapping breaks down: layered images and parallax (tvOS).** Apple's parallax system is driven by a focus engine — a remote-control navigation model where exactly one element is "focused" at a time. There is no equivalent input model on the web: hover doesn't exist on touch, and scroll-triggered parallax libraries respond to a completely different signal (scroll position, not focus state). Treat any web "parallax" effect as an unrelated visual technique that happens to share a name, not a translation of Apple's system.

**Where the mapping breaks down: spatial photos and spatial scenes (visionOS).** These depend on stereoscopic capture hardware and a stereo display, neither of which the web can assume. WebXR exists for headset-targeted content, but there is no equivalent to embedding a spatial photo in an ordinary web page the way `Image` embeds one in a SwiftUI view — this is a case where the underlying principle (depth communicates realism) doesn't have a widely available web execution path yet.

**watchOS's per-screen-size autoscaling PDF → this is just responsive SVG, done more simply.** WatchKit's percentage table exists to solve a problem the web already solves natively: scaling one vector source across several fixed display sizes. An SVG sized with relative units, or scaled via CSS, achieves the same "single asset, several targets" outcome without needing a platform runtime step to rasterize per device — the web analog is actually simpler than Apple's own solution here, not weaker.

## Do / Don't

| Do | Don't |
|---|---|
| Provide @1x/@2x/@3x assets appropriate to each platform you support | Ship a single resolution and let the system upscale it |
| Design at the lowest resolution and scale up, aligning vector control points to whole values at 1x | Design at high resolution and scale down, leaving control points misaligned at 1x |
| Include a color profile with every image and test on real devices | Trust how an image looks only at design time |
| Use standard views and system focus APIs so layered images get automatic parallax (tvOS) | Build custom focus handling that bypasses the parallax treatment |
| Keep the background layer opaque and keep layering simple and subtle (tvOS) | Use excessive 3D effects or leave the background layer non-opaque |
| Prefer vector-based art for 2D images in visionOS | Use bitmap content that won't scale cleanly in visionOS |
| Use stereo HEIC with spatial metadata and display spatial content in standalone views | Display spatial photos inline without generous spacing, or show too many at once |
| Use autoscaling PDFs designed at 40mm/42mm 2x for watchOS | Add transparency to watchOS images that don't need it as template icons |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
