---
title: Spatial layout
url: https://developer.apple.com/design/human-interface-guidelines/spatial-layout
platforms: [visionOS]
last_updated: 2024-03-29
---

# Spatial layout

Spatial layout techniques help you take advantage of the infinite canvas of Apple Vision Pro and present your content in engaging, comfortable ways.

## Core guidance

### Field of view

A person's field of view is the space they can see without moving their head. The dimensions of an individual's field of view while wearing Apple Vision Pro vary based on factors like the way people configure the Light Seal and the extent of their peripheral acuity.

> **Important (Apple):** The system doesn't provide information about a person's field of view.

**Center important content within the field of view.** By default, visionOS launches an app directly in front of people, placing it within their field of view. In an immersive experience, you can help people keep their attention on important content by keeping it centered and not displaying distracting motion or bright, high-contrast objects in the periphery.

> **Source limitation:** The source page embeds interactive before/after demos (a value scrubber and a Play control) illustrating several concepts in this document — one comparing "Upright viewing" and "Angled viewing" near this section, and further unlabeled demos in the Depth and Scale sections below. The captured PDF preserved only the widget controls, not descriptive captions or the visual content itself, so those demos are noted but not reproduced here.

**Avoid anchoring content to the wearer's head.** Although you generally want your app to stay within the field of view, anchoring content so that it remains statically in front of someone can make them feel stuck, confined, and uncomfortable, especially if the content obscures a lot of passthrough and decreases the apparent stability of their surroundings. Instead, anchor content in people's space, giving them the freedom to look around naturally and view different objects in different locations.

### Depth

People rely on visual cues like distance, occlusion, and shadow to perceive depth and make sense of their surroundings. On Apple Vision Pro, the system automatically uses visual effects like color temperature, reflections, and shadow to help people perceive the depth of virtual content. When people move a virtual object in space — or when they change their position relative to that object — the visual effects change the object's apparent depth, making the experience feel more lifelike.

Because people can view your content from any angle, incorporating small amounts of depth throughout your interface — even in standard windows — can help it look more natural. When you use SwiftUI, the system adds visual effects to views in a 2D window, making them appear to have depth. For developer guidance, see "Adding 3D content to your app."

If you need to present content with additional depth, you use RealityKit to create a 3D object (for developer guidance, see RealityKit). You can display the 3D object anywhere, or you can use a volume, which is a component that displays 3D content. A volume is similar to a window, but without a visible frame. For guidance, see visionOS volumes.

**Provide visual cues that accurately communicate the depth of your content.** If visual cues are missing or they conflict with a person's real-world experience, people can experience visual discomfort.

**Use depth to communicate hierarchy.** Depth helps an object appear to stand out from surrounding content, making it more noticeable. People also tend to notice changes in depth: for example, when a sheet appears over a window, the window recedes along the z-axis, allowing the sheet to come forward and become visually prominent.

**In general, avoid adding depth to text.** Text that appears to hover above its background is difficult to read, which slows people down and can sometimes cause vision discomfort.

**Make sure depth adds value.** In general, you want to use depth to clarify and delight — you don't need to use it everywhere. As you add depth to your design, think about the size and relative importance of objects. Depth is great for visually separating large, important elements in your app, like making a tab bar or toolbar stand out from a window, but it may not work as well on small objects. For example, using depth to make a button's symbol stand out from its background can make the button less legible and harder to use. Also review how often you use different depths throughout your app. People need to refocus their eyes to perceive each difference in depth, and doing so too often or quickly can be tiring.

### Scale

visionOS defines two types of scale to preserve the appearance of depth while optimizing usability.

**Dynamic scale** helps content remain comfortably legible and interactive regardless of its proximity to people. Specifically, visionOS automatically increases a window's scale as it moves away from the wearer and decreases it as the window moves closer, making the window appear to maintain the same size at all distances.

**Fixed scale** means that an object maintains the same scale regardless of its proximity to people. A fixed-scale object appears smaller when it moves farther from the viewer along the z-axis, similar to the way an object in a person's physical surroundings looks smaller when it's far away than it does when it's close up.

To support dynamic scaling and the appearance of depth, visionOS defines a point as an angle, in contrast to other platforms, which define a point as a number of pixels that can vary with the resolution of a 2D display.

**Consider using fixed scale when you want a virtual object to look exactly like a physical object.** For example, you might want to maintain the life-size scale of a product you offer so it can look more realistic when people view it in their space. Because interactive content needs to scale to maintain usability as it gets closer or farther away, prefer applying fixed scale sparingly, reserving it for noninteractive objects that need it.

### Best practices

**Avoid displaying too many windows.** Too many windows can obscure people's surroundings, making them feel overwhelmed, constricted, and even uncomfortable. It can also make it cumbersome for people to relocate an app because it means moving a lot of windows.

**Prioritize standard, indirect gestures.** People can make an indirect gesture without moving their hand into their field of view. In contrast, making a direct gesture requires people to touch the virtual object with their finger, which can be tiring, especially when the object is positioned at or above their line of sight. In visionOS, people use indirect gestures to perform the standard gestures they already know. When you prioritize indirect gestures, people can use them to interact with any object they look at, whatever its distance. If you support direct gestures, consider reserving them for nearby objects that invite close inspection or manipulation for short periods of time. For guidance, see Gestures > visionOS.

**Rely on the Digital Crown to help people recenter windows in their field of view.** When people move or turn their head, content might no longer appear where they want it to. If this happens, people can press the Digital Crown when they want to recenter content in front of them. Your app doesn't need to do anything to support this action.

**Include enough space around interactive components to make them easy for people to look at.** When people look at an interactive element, visionOS displays a visual hover effect that helps them confirm the element is the one they want. It's crucial to include enough space around an interactive component so that looking at it is easy and comfortable, while preventing the hover effect from crowding other content. For example, place multiple, regular-size buttons so their centers are at least 60 points apart, leaving 16 points or more of space between them. Also, don't let controls overlap other interactive elements or views, because doing so can make selecting a single element difficult.

**Let people use your app with minimal or no physical movement.** Unless some physical movement is essential to your experience, help everyone enjoy it while remaining stationary.

**Use the floor to help you place a large immersive experience.** If your immersive experience includes content that extends up from the floor, place it using a flat horizontal plane. Aligning this plane with the floor can help it blend seamlessly with people's surroundings and provide a more intuitive experience.

To learn more about windows and volumes in visionOS, see Windows > visionOS; for guidance on laying out content within a window, see Layout > visionOS.

## Platform considerations

Spatial layout is **specific to visionOS**. The source states this explicitly: "Not supported in iOS, iPadOS, macOS, tvOS, or watchOS." There is no cross-platform comparison to reproduce — every guideline in this document assumes an Apple Vision Pro wearer moving through physical and virtual space, and none of it applies to the flat-display platforms.

## Specifications

| Spec | Value |
|---|---|
| Point definition on visionOS | An angle — not a pixel count. This differs from other platforms, where a point maps to a number of pixels that varies with the resolution of a 2D display. |
| Minimum spacing between adjacent regular-size buttons, center to center | At least 60 points |
| Minimum spacing between adjacent regular-size buttons, edge to edge | At least 16 points |

## Native implementation

**Related**
- Eyes
- Layout
- Immersive experiences

**Developer documentation**
- Presenting windows and spaces — visionOS
- Positioning and sizing windows — visionOS
- Adding 3D content to your app — visionOS

**Key APIs and concepts**
- `RealityKit` — used to create a 3D object when you need to present content with additional depth beyond what SwiftUI's automatic 2D-window depth effects provide
- `SwiftUI` — automatically adds visual effects to views in a 2D window so they appear to have depth
- **Volumes** — a visionOS component that displays 3D content; similar to a window but without a visible frame
- **Digital Crown** — the hardware control people press to recenter content in front of them; your app doesn't need to implement anything to support this

**Videos**
- Meet SwiftUI spatial layout
- Principles of spatial design
- Design for spatial user interfaces

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and this topic is unusually poorly suited to translation: it describes a person's physical field of view, real depth cues, and distance-based scaling inside a headset, none of which the flat, fixed-viewport web has a genuine equivalent for. The mappings below are inference, and most of them are honest stretches rather than clean analogues — flagged as such.

**Depth as hierarchy → elevation and shadow systems (a genuine, well-established analogue).** Apple's "use depth to communicate hierarchy" principle — a sheet coming forward while a window recedes — maps directly onto 2D elevation systems that use shadow, scale, and z-index to signal what's in front of what. This is the strongest analogue in this document because 2D interface design already uses simulated depth for the same reason.

**"Avoid adding depth to text" → avoid heavy drop-shadows or 3D effects on body text (genuine, minor stretch).** The underlying reasoning transfers cleanly: anything that makes text visually "pop" off its background at the expense of contrast and edge clarity slows reading. This is uncontroversial, longstanding web typography advice independent of visionOS.

**Button spacing (60pt centers / 16pt gaps) → adequate spacing between interactive elements (genuine, but the mechanism differs).** The reason visionOS specifies spacing is to keep a gaze-based hover effect from crowding neighboring elements — a precision problem specific to eye tracking. Web/touch interfaces have their own, unrelated reason to space interactive elements generously (finger contact area, motor precision), and use different numbers (commonly a 44px-class minimum target size). The two guidelines rhyme — "give interactive things breathing room so selection stays unambiguous" — but do not share a mechanism, so don't reuse Apple's exact point values on the web.

**Avoid too many windows → avoid stacking too many simultaneous modals or panels (loose stretch).** Apple's concern is that many spatial windows obscure a person's physical surroundings and become cumbersome to relocate. The nearest web idea is that too many simultaneous overlays or panels overwhelm and disorient a user — a related but not identical concern, since a web viewport has no "surroundings" to obscure.

**Indirect gestures and floor-anchored placement → WebXR, and only WebXR (narrow, technical analogue).** The one place a truly literal analogue exists is the WebXR Device API: its gaze-plus-select input model is conceptually the same as visionOS's indirect gestures, and its hit-test/plane-detection features serve the same purpose as anchoring immersive content to a detected floor plane. This applies only to web content that is itself building an immersive AR/VR experience — it has no bearing on ordinary 2D web pages.

**Field-of-view centering and head-anchoring → no honest mainstream-web equivalent.** It's tempting to map "center important content in the field of view" onto "keep key content above the fold," but the reasoning behind Apple's guidance — a physically wearable device, a person's literal head movement, real-world discomfort from static overlays — doesn't exist for a scrollable rectangle on a monitor. Presenting "above the fold" as a translation of this guidance would overstate the connection, so it is deliberately not offered as one here.

**Dynamic and fixed scale → no honest mainstream-web equivalent.** Both scale modes exist to solve a problem — an object's real, physical distance from the viewer changing continuously — that a 2D page simply does not have. Responsive typography and viewport-relative units solve a different problem (adapting to different screen sizes and user zoom levels, not to a viewer physically walking toward the screen), so presenting them as a translation of dynamic/fixed scale would be misleading rather than merely loose.

## Do / Don't

| Do | Don't |
|---|---|
| Center important content within the field of view | Fill the periphery with distracting motion or bright, high-contrast objects |
| Anchor content in people's space, so they can look around freely | Anchor content statically to the wearer's head |
| Provide visual cues (distance, occlusion, shadow) that accurately communicate depth | Leave depth cues missing or conflicting with real-world experience |
| Use depth to separate large, important elements (tab bars, toolbars) from their surroundings | Add depth to text, or to small elements like a button's symbol |
| Use dynamic scale so interactive content stays usable at any distance | Apply fixed scale broadly to interactive content |
| Reserve fixed scale for noninteractive objects that need to look physically real | Overuse changing depth levels throughout an app — refocusing too often is tiring |
| Prioritize indirect gestures so people can interact with anything they look at | Require sustained direct-touch gestures for objects at or above the line of sight |
| Space regular-size buttons at least 60 points apart (centers), 16 points or more edge to edge | Let interactive controls overlap other interactive elements or views |
| Let people use your app while remaining stationary | Require physical movement that isn't essential to the experience |
| Align floor-anchored content with a flat horizontal plane at the real floor | Display so many windows that people's surroundings and orientation get obscured |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
