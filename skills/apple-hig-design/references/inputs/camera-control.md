---
title: Camera Control
url: https://developer.apple.com/design/human-interface-guidelines/camera-control
platforms: [iOS]
last_updated: 2024-09-09
---

# Camera Control

The Camera Control provides direct access to your app's camera experience.

## Core guidance

On iPhone 16 and iPhone 16 Pro models, the Camera Control quickly opens your app's camera experience to capture moments as they happen. When a person lightly presses the Camera Control, the system displays an overlay that extends from the device bezel.

The overlay allows people to quickly adjust controls. A person can view the available controls by lightly double-pressing the Camera Control. After selecting a control, they can slide their finger on the Camera Control to adjust a value to capture their content as they want.

> *Image caption:* Controls in the overlay.

### Anatomy

The Camera Control offers two types of controls for adjusting values or changing between options:

- A **slider** provides a range of values to choose from, such as how much contrast to apply to the content.
- A **picker** offers discrete options, such as turning a grid on and off in the viewfinder.

> *Image caption:* Slider control.
> *Image caption:* Picker control.

In addition to custom controls that you create, the system provides a set of standard controls that you can optionally include in the overlay to allow someone to adjust their camera's zoom and exposure.

> *Image caption:* Zoom factor control.
> *Image caption:* Exposure bias control.

### Best practices

**Use SF Symbols to represent control functionality.** The system doesn't support custom symbols; instead, pick a symbol from SF Symbols that clearly denotes a control's behavior. iOS offers thousands of symbols you can use to represent the controls your app shows in the overlay. Symbols for controls don't represent their current state. To view available symbols, see the Camera & Photos section in the SF Symbols app.

> *Image caption:* The `bolt.fill` symbol that represents a control for the camera flash.
> *Image caption:* The `camera.filters` symbol that represents a control for filters.

**Keep names of controls short.** Control labels adhere to Dynamic Type sizes, and longer names may obfuscate the camera's viewfinder.

**Include units or symbols with slider control values to provide context.** Providing descriptive information in the overlay, such as EV, %, or a custom string, helps people understand what the slider controls. For developer guidance, see `localizedValueFormat`.

> *Image caption:* Value with context.
> *Image caption:* Value without context.

**Define prominent values for a slider control.** Prominent values are ones people choose most frequently, or values that are evenly spaced, like the major increments of zoom factor. When a person slides on the Camera Control to adjust a slider control, the system more easily lands on prominent values you define. For developer guidance, see `prominentValues`.

**Make space for the overlay in the viewfinder.** The overlay and control labels occupy the screen area adjacent to the Camera Control in both portrait and landscape orientations. To avoid overlapping the interface elements of your camera capture experience, place your UI outside of the overlay areas. Maximize the height and width of the viewfinder and allow the overlay to appear and disappear over it.

**Minimize distractions in the viewfinder.** When capturing a photo or video, people appreciate a large preview image with as few visual distractions as possible. Avoid duplicating controls, like sliders and toggles, in your UI and the overlay when the system displays the overlay.

> *Image caption:* Keep UI minimal.
> *Image caption:* Avoid showing controls in the viewfinder that people access in the overlay.

**Enable or disable controls depending on the camera mode.** For example, disable video controls when taking photos. The overlay supports multiple controls, but you can't remove or add controls at runtime.

**Consider how to arrange your controls.** Order commonly used controls toward the middle to allow quick access, and include lesser used controls on either side. When a person lightly presses the Camera Control to open the overlay again, the system remembers the last control they used in your app.

**Allow people to use the Camera Control to launch your experience from anywhere.** Create a locked camera capture extension that lets people configure the Camera Control to launch your app's camera experience from their locked device, the Home Screen, or from within other apps. For guidance, see Camera experiences on a locked device.

## Platform considerations

Not supported in iPadOS, macOS, watchOS, tvOS, or visionOS. The Camera Control is a physical control available only on iPhone 16 and iPhone 16 Pro models.

## Native implementation

**Related**
- SF Symbols
- Controls

**Developer documentation**
- Enhancing your app experience with the Camera Control — AVFoundation
- `AVCaptureControl` — AVFoundation
- `LockedCameraCapture`

**Key APIs**
- `AVCaptureControl` — define custom slider and picker controls for the Camera Control overlay
- `localizedValueFormat` — attach units or a custom string to a slider control's displayed value
- `prominentValues` — define values a slider more easily lands on while sliding
- `LockedCameraCapture` — launch your camera experience from the Camera Control on a locked device

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and this topic has no meaningful web analogue. The Camera Control is a dedicated physical button and slide surface on specific iPhone hardware, wired directly into the system's app-launch and camera-overlay behavior — light press, double press, and slide-to-adjust are gestures a touchscreen-only web page cannot detect at all, since there is no browser API for a side-mounted capacitive button. Launching an app's camera experience from the lock screen or Home Screen via a hardware control is likewise entirely outside what a web page, sandboxed inside a browser tab, can do.

The one thing worth noting is that a web app using `getUserMedia()` for its own camera capture UI faces an analogous *design* problem even without analogous hardware: it still needs on-screen sliders and pickers for zoom, exposure, or filters, and Apple's advice to label them with SF Symbols-equivalent icons, keep labels short, and show units alongside slider values is generic UI advice that applies regardless of what triggers the panel. That's a shared design problem, not a shared platform capability.

## Do / Don't

| Do | Don't |
|---|---|
| Use an SF Symbol that clearly denotes each control's function | Use custom symbols — the system doesn't support them |
| Keep control names short | Use long names that obscure the viewfinder at larger Dynamic Type sizes |
| Show units or a custom string with slider values | Show a bare number with no context |
| Define prominent values for sliders people adjust often | Leave every point on a slider equally hard to land on |
| Keep your own UI outside the overlay's screen area | Let your interface overlap the Camera Control overlay |
| Show a large, distraction-free viewfinder | Duplicate overlay controls like sliders and toggles in your own UI |
| Disable controls that don't apply to the current camera mode | Leave irrelevant controls active for the wrong mode |
| Order frequently used controls toward the middle | Scatter commonly used controls unpredictably |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
