---
title: Immersive experiences
url: https://developer.apple.com/design/human-interface-guidelines/immersive-experiences
platforms: [visionOS]
last_updated: 2025-06-09
---

# Immersive experiences

In visionOS, you can design apps and games that extend beyond windows and volumes, immersing people in your content.

## Core guidance

### Shared Space and Full Space

You can choose whether your visionOS app or game launches in the Shared Space or in a Full Space. In the Shared Space, your software runs alongside other experiences, and people can switch between them much as they do on a Mac; in a Full Space, your app or game runs alone, hiding other experiences and helping people immerse themselves in your content. Apps and games can support different types of immersion, and can transition fluidly between the Shared Space and a Full Space at any time.

### Immersion and passthrough

In visionOS, people use passthrough to see their physical surroundings. Passthrough provides real-time video from the device's external cameras, helping people feel comfortable and connected to their physical context.

People can also use the Digital Crown at any time to manage app or game content or adjust passthrough. For example, people can press and hold the Digital Crown to recenter content in their field of view or double-click it to briefly hide all content and show passthrough for a clear view of their surroundings.

The system also helps people remain comfortable by automatically changing the opacity of content in certain situations. For example, if someone gets too close to a physical object in mixed immersion, the content in front of them dims briefly so they can see their immediate physical surroundings more clearly. **In more immersive experiences — such as in the progressive and full styles — the system defines a boundary that extends about 1.5 meters from the initial position of the wearer's head.** As their head gets close to this boundary, the entire experience begins to fade and passthrough increases. When their head moves beyond this boundary, the immersive visuals are replaced in space by the app's icon, and are restored when the wearer returns to their original location or recenters their view using the Digital Crown.

#### Immersion styles

When your app or game transitions to a Full Space, the system hides other apps so people can focus on yours. In a Full Space, you can display 3D content that isn't bound by a window, in addition to content in standard windows and volumes. For developer guidance, see `automatic`.

visionOS offers several ways to immerse people in your content in the Shared Space as well as when you transition to a Full Space:

**Use dimmed passthrough to bring attention to your content.** You can subtly dim or tint passthrough and other visible content to bring attention to your app in the Shared Space without hiding other apps and games, or create a more focused experience in a Full Space. While passthrough is tinted black by default, you can apply a custom tint color to create a dynamic experience in your app. For developer guidance, see `SurroundingsEffect`.

> *Image caption:* Side-by-side screenshots labeled "Without dimmed passthrough" and "With dimmed passthrough."

**Create unbounded 3D experiences.** Use the mixed immersion style in a Full Space to blend your content with passthrough. When your app or game runs in a Full Space, you can request access to information about nearby physical objects and room layout, helping you display virtual content in a person's surroundings. **The mixed immersion style doesn't define a boundary.** Instead, when a person gets too close to a physical object, the system automatically makes nearby content semi-opaque to help them remain aware of their surroundings. For developer guidance, see `mixed` and `ARKit`.

**Use progressive immersion to blend your custom environment with a person's surroundings.** You can use the progressive style in a Full Space to display a custom environment that partially replaces passthrough. You can also define a specific range of immersion that works best with your app or game, and display content in portrait or landscape orientation. **While in your immersive experience, people can use the Digital Crown to adjust the amount of immersion within either the default range of 120- to 360-degrees or a custom range, if you specify one.** The system automatically defines an approximately 1.5-meter boundary when an experience transitions to the progressive style. For developer guidance, see `progressive`.

> *Image caption:* A progressive-immersion demo showing an on-screen immersion-level control (reading "1.00") with decrease/increase buttons and a Play control.

**Use full immersion to create a fully immersive experience.** You can use the full style in a Full Space to display a 360-degree custom environment that completely replaces passthrough and transports people to a new place. As with the progressive style, the system defines an approximately 1.5-meter boundary when a fully immersive experience starts. For developer guidance, see `full`.

> *Image caption:* Three screenshots labeled "Full Space (Mixed)," "Full Space (Progressive)," and "Full Space (Immersive)," each showing content at a different immersion style.
> *Image caption:* Mixed immersion style in a Full Space blending in-app objects with real-world surroundings.

> **Source limitation:** The captured PDF preserves image *labels* (e.g., "Without dimmed passthrough," "Full Space (Mixed)") but not the images themselves, and one interactive demo — a progressive-immersion slider control — rendered only as fragmentary on-screen text ("1.00," "−," "+," "Play") rather than a full description of the control's appearance or behavior. The surrounding prose guidance is complete; only the visual content of the figures is unavailable in this source.

### Best practices

**Offer multiple ways to use your app or game.** In addition to giving people the freedom to choose their experiences, it's essential to design your software to support the accessibility features people use to personalize the ways they interact with their devices.

**Prefer launching your app or game in the Shared Space or using the mixed immersion style.** Launching in the Shared Space lets people reference your app or game while using other running software, and enables seamless switching between them. If your app or game provides a fully immersive or progressive style experience, launching in the mixed immersion style or with a window-based experience in the Shared Space gives people more control, letting them choose when to increase immersion.

**Reserve immersion for meaningful moments and content.** Not every task benefits from immersion, and not every immersive task needs to be fully immersive. Although people sometimes want to enter a different world, they often want to stay grounded in their surroundings while they're using your app or game, and they can appreciate being able to use other software and system features at the same time. Instead of assuming that your app or game needs to be fully immersive most of the time, design ways for people to immerse themselves in the individual tasks and content that make your experience unique. For example, people can browse their albums in Photos using a familiar app window in the Shared Space, but when they want to examine a single photo, they can temporarily transition to a more immersive experience in a Full Space where they can expand the photo and appreciate its details.

**Help people engage with key moments in your app or game, regardless of the level of immersion.** Cues like dimming, tinting, motion, scale, and Spatial Audio can help draw people's attention to a specific area of content, whether it's in a window in the Shared Space or in a completely immersive experience in a Full Space. Start with subtle cues that gently guide people's attention, strengthening the cues only when there's a good reason to do so.

**Prefer subtle tint colors for passthrough.** In visionOS 2 and later, you can tint passthrough to help a person's surroundings visually coordinate with your content, while also making their hands look like they belong in your experience. Avoid bright or dramatic tints that can distract people and diminish the sense of immersion. For developer guidance, see `SurroundingsEffect`.

### Promoting comfort

**Be mindful of people's visual comfort.** For example, although you can place 3D content anywhere while your app or game is running in a Full Space, prefer placing it within people's field of view. Also, make sure you display motion in comfortable ways while your software runs in a Full Space to avoid causing distraction, confusion, or discomfort.

**Choose a style of immersion that supports the movements people might make while they're in your app or game.** It's essential to choose the right style for your immersive experience because it allows the system to respond appropriately when people move. Although people can make minor physical movements while in an immersive experience — such as shifting their weight, turning around, or switching between sitting and standing — making excessive movements can cause the system to interrupt some experiences. **In particular, avoid using the progressive or full immersion styles, or transition back to the mixed immersion style, if you think people might need to move beyond the 1.5-meter boundary.**

**Avoid encouraging people to move while they're in a progressive or fully immersive experience.** Some people may not want to move, or are unable to move because of a disability or their physical surroundings. Design ways for people to interact with content without moving. For example, let people bring a virtual object closer to them instead of expecting them to move closer to the object.

**If you use the mixed immersion style, avoid obscuring passthrough too much.** People use passthrough to help them understand and navigate their physical surroundings, so it's important to avoid displaying virtual objects that block too much of their view. If your app or game displays virtual objects that could substantially obscure passthrough, use the full or progressive immersion styles instead of mixed.

**Adopt ARKit if you want to blend custom content with someone's surroundings.** For example, you might want to integrate virtual content into someone's surroundings or use the wearer's hand positions to inform your experience. If you need access to these types of sensitive data, you must request people's permission. For developer guidance, see `SceneReconstructionProvider`.

### Transitioning between immersive styles

**Design smooth, predictable transitions when changing immersion.** Help people prepare for different experiences by providing gentle transitions that let people visually track changes. Avoid sudden, jarring transitions that might be disorienting or uncomfortable. For developer guidance, see `CoordinateSpaceProtocol`.

**Let people choose when to enter or exit a more immersive experience.** It can be disorienting for someone to suddenly enter a more immersive experience when they're not expecting it. Instead, provide a clear action to enter or exit immersion so people can decide when to be more immersed in your content, and when to leave. For example, Keynote provides a prominent Exit button in its fully immersive Rehearsal environment to help people return to the slide-viewing window. Avoid requiring people to use system controls to reduce immersion in your experience.

**Indicate the purpose of an exit control.** Make sure your button clarifies whether it returns people to a previous, less immersive context or quits an experience altogether. If exiting your immersive experience also quits your app or game, consider providing controls that let people pause or return to a place where they can save their progress before quitting.

### Displaying virtual hands

When your immersive app or game transitions to a Full Space, it can ask permission to hide a person's hands and instead show virtual hands that represent them.

**Prefer virtual hands that match familiar characteristics.** For example, match the positions and gestures of the viewer's hands so they can continue to interact with your app or game in ways that feel natural. Hands that work in familiar ways help people stay immersed in the experience when in fully virtual worlds.

**Use caution if you create virtual hands that are larger than the viewer's hands.** Virtual hands that are significantly bigger than human hands can prevent people from seeing the content they're interested in and can make interactions feel clumsy. Also, large virtual hands can seem out of proportion with the space, appearing to be too close to the viewer's face.

**If there's an interruption in hand-tracking data, fade out virtual hands and reveal the viewer's own hands.** Don't let the virtual hands become unresponsive and appear frozen. When hand-tracking data returns, fade the virtual hands back in.

### Creating an environment

When your app or game transitions to a Full Space, you can replace passthrough with a custom environment that partially or completely surrounds a person, transporting them to a new place. The following guidelines can help you design a beautiful environment that people appreciate.

**Minimize distracting content.** To help immerse people in a primary task like watching a video, avoid displaying a lot of movement or high-contrast details in your environment. Alternatively, when you want to draw people's attention to certain areas of your environment, consider techniques like using the highest quality textures and shapes in the important area while using lower quality assets and dimming in less important areas.

**Help people distinguish interactive objects in your environment.** People often use an object's proximity to help them decide if they can interact with it. For example, when you place a 3D object far away from people, they often don't try to touch or move toward it, but when you place a 3D object close to people, they're more likely to try interacting with it.

**Keep animation subtle.** Small, gentle movements, like clouds drifting or transforming, can enrich your custom environment without distracting people or making them uncomfortable. Always avoid displaying too much movement near the edges of a person's field of view.

**Create an expansive environment, regardless of the place it depicts.** A small, restrictive environment can make people feel uncomfortable and even claustrophobic.

**Use Spatial Audio to create atmosphere.** In visionOS, you use Spatial Audio to play sound that people can perceive as coming from specific locations in space, not just from speakers. As you design a soundscape that enhances your custom environment, keep the experience fresh and captivating by avoiding too much repetition or looping. If people can play other audio while they're in your environment — for example, while watching a movie — be sure to lower the volume of the soundscape or stop it completely.

**In general, avoid using a flat 360-degree image to create your environment.** A 360-degree image doesn't tend to give people a sense of scale when they view it in an environment, so it can reduce the immersiveness of the experience. Prefer creating object meshes that include lighting, and use shaders to implement subtle animations like the movements of clouds or leaves or the reflections of objects.

**Help people feel grounded.** Always provide a ground plane mesh so people don't feel like they're floating. If you must use a flat 360-degree image in your environment, adding a ground plane mesh can help it feel more realistic.

**Minimize asset redundancy.** Using the same assets or models too frequently tends to make an environment feel less realistic.

## Platform considerations

**This entire document is visionOS-only.** The source states plainly: "Not supported in iOS, iPadOS, macOS, tvOS, or watchOS." None of the concepts below have a counterpart on Apple's other platforms.

- **Shared Space vs. Full Space.** The Shared Space is the multitasking context, comparable to a Mac desktop, where your software runs alongside other apps and games. A Full Space hides everything else so a single app or game can own the person's attention. This binary choice, and the ability to transition between the two at any time, doesn't exist as a concept on iOS, iPadOS, macOS, tvOS, or watchOS.
- **Windows, volumes, and unbound 3D content.** In the Shared Space, content is presented in windows and volumes, the same building blocks used elsewhere in visionOS. Only in a Full Space can an app or game display 3D content that is not bound by a window at all.
- **Three immersion styles plus automatic.** visionOS distinguishes `mixed` (passthrough stays fully visible, virtual content blends in with no defined boundary), `progressive` (a custom environment partially replaces passthrough within an adjustable 120°–360° range, bounded by a ~1.5-meter safety boundary), and `full` (a 360-degree custom environment completely replaces passthrough, also bounded by a ~1.5-meter boundary), selected via `automatic` or explicitly by the developer.
- **Passthrough as a first-class concept.** Passthrough — the real-time video feed of a person's physical surroundings — and the system's automatic dimming/boundary behavior for keeping people aware of their surroundings have no equivalent on a 2D screen.
- **Digital Crown.** The hardware control that lets people recenter content or instantly reveal full passthrough is specific to visionOS's headset form factor.

## Specifications

The source presents immersion-style values as prose rather than as a single reference table. The table below consolidates every numeric threshold and named style value mentioned in the guidance above; it is a synthesis for reference, not a table reproduced verbatim from Apple's page.

| Immersion style | Passthrough | Boundary | Adjustable range | Orientation |
|---|---|---|---|---|
| Shared Space (no immersion) | Full | None | — | — |
| Mixed | Full, blended with virtual content | None defined (system makes nearby content semi-opaque instead) | — | — |
| Progressive | Partial (custom environment blends with passthrough) | ~1.5 meters from the wearer's initial head position | 120°–360° by default, or a custom range | Portrait or landscape |
| Full | None (custom environment completely replaces passthrough) | ~1.5 meters from the wearer's initial head position | 360° | — |

Additional values mentioned in the source:

- Passthrough tint: black by default; a custom tint color is available starting in **visionOS 2**.
- Boundary behavior: as the wearer's head approaches the ~1.5-meter boundary in progressive or full immersion, the experience fades and passthrough increases; beyond the boundary, immersive visuals are replaced in space by the app's icon.

## Native implementation

**Related**
- Spatial layout
- Motion

**Developer documentation**
- Creating fully immersive experiences in your app — visionOS
- Incorporating real-world surroundings in an immersive experience — visionOS
- ImmersionStyle — visionOS
- Immersive spaces — SwiftUI

**Key APIs**
- `ImmersionStyle` — protocol describing an immersive space's immersion style; the source references its `automatic`, `mixed`, `progressive`, and `full` values
- `ImmersiveSpace` — SwiftUI scene type used to present Full Space content ("Immersive spaces — SwiftUI")
- `.immersionStyle(selection:in:)` — SwiftUI scene modifier used to set and constrain which `ImmersionStyle` values an `ImmersiveSpace` supports
- `SurroundingsEffect` — API for tinting or dimming passthrough
- `SceneReconstructionProvider` — ARKit API for accessing nearby physical objects and room layout in a Full Space
- `CoordinateSpaceProtocol` — referenced for coordinating transitions between immersive styles
- `openImmersiveSpace` / `dismissImmersiveSpace` — SwiftUI environment actions used to implement explicit enter/exit controls for immersion

**Videos:** Design immersive environments for visionOS apps and the spatial web · Principles of spatial design · Design spatial SharePlay experiences

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy — and for this topic, the inference has to be qualified more heavily than usual.

Most of this document simply has no web equivalent, and it's worth saying so directly rather than stretching a mapping to fit. **Immersion levels, passthrough, and custom spatial Environments are properties of a headset that shares a person's physical field of view with rendered 3D content.** A 2D document viewed on a screen has no field of view to share, no physical surroundings to blend with, and no boundary a person's head can approach. There is no meaningful web translation of "mixed immersion style," "passthrough tint," or "1.5-meter boundary" — inventing one would misrepresent both Apple's guidance and how the web works. The one place a real analogue exists is **WebXR**, which gives browsers actual access to headset immersion styles, passthrough, and spatial tracking — but that is a narrow, non-mainstream use case (VR/AR web experiences), not something that generalizes to ordinary web design.

Where a genuinely transferable principle does exist, it's not about immersion mechanics but about **respect for a person's attention and physical/situational context**, and it maps cleanly:

**"Reserve immersion for meaningful moments and content" → don't force a takeover state for trivial content.** Apple's warning against assuming an app needs to be fully immersive most of the time has a direct web analogue: don't auto-request fullscreen, don't hijack scrolling into a full-bleed takeover, and don't interrupt someone's task with a modal unless the moment genuinely warrants full attention.

**"Let people choose when to enter or exit a more immersive experience" → progressive, reversible entry into a more immersive UI state.** Fullscreen video, a distraction-free reading mode, or a modal that takes over the viewport are the web's closest equivalents to entering a Full Space. The underlying rule carries over intact: the person, not the software, decides when to enter that state.

**"Indicate the purpose of an exit control" → label the exit clearly and make it easy to find.** Apple's distinction between "return to a less immersive context" and "quit entirely" maps to the web distinction between closing a modal (returning to the page underneath) and navigating away entirely (losing the current view). A close button, a working Escape key, and a visible label for what closing does are the direct equivalents.

**"Avoid sudden, jarring transitions" → animate state changes, and respect `prefers-reduced-motion`.** Apple's comfort-driven preference for gentle transitions when changing immersion has an honest web parallel in transitioning between a page's normal state and a fullscreen/modal takeover, but the mechanism differs: the web has no physical vestibular system to protect, only a documented preference (`prefers-reduced-motion`) to honor.

Two pieces of guidance don't translate at all, and it would be dishonest to imply otherwise: **the Digital Crown** is a physical hardware input with no web counterpart, and **Spatial Audio positioned in 3D space** has a narrow technical parallel in the Web Audio API's spatial panner nodes, but using it is itself a niche, largely game- or WebXR-specific choice rather than something that applies to typical web content.

## Do / Don't

| Do | Don't |
|---|---|
| Launch in the Shared Space or use the mixed immersion style by default | Launch directly into a fully immersive experience without giving people a choice |
| Reserve full or progressive immersion for meaningful moments and content | Assume your app or game needs to be fully immersive most of the time |
| Provide gentle, predictable transitions when changing immersion | Use sudden, jarring transitions that might be disorienting |
| Give people a clear, visible action to enter or exit immersion | Require system controls as the only way to reduce immersion |
| Indicate whether an exit control returns to a less immersive view or quits entirely | Leave people uncertain about what an exit button will do |
| Choose progressive or full immersion only when people can stay within the ~1.5-meter boundary | Use progressive or full immersion when people might need to move beyond the boundary |
| Fade virtual hands out and reveal a person's real hands when hand-tracking is interrupted | Let virtual hands become unresponsive and appear frozen |
| Use the full or progressive style if virtual objects would substantially obscure passthrough | Let the mixed immersion style obscure too much of a person's real surroundings |
| Keep environment animation subtle and away from the edges of the field of view | Fill an environment with a lot of movement or high-contrast detail near the edges |
| Provide a ground plane mesh so people feel grounded | Use a flat 360-degree image without any sense of scale or ground |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
