---
title: Designing for visionOS
url: https://developer.apple.com/design/human-interface-guidelines/designing-for-visionos
platforms: [visionOS]
last_updated: 2024-02-02
---

# Designing for visionOS

When people wear Apple Vision Pro, they enter an infinite 3D space where they can engage with your app or game while staying connected to their surroundings.

## Core guidance

As you begin designing your app or game for visionOS, start by understanding the fundamental device characteristics and patterns that distinguish the platform. Use these characteristics and patterns to inform your design decisions and help you create immersive and engaging experiences.

### Fundamental device characteristics

**Space.** Apple Vision Pro offers a limitless canvas where people can view virtual content like windows, volumes, and 3D objects, and choose to enter deeply immersive experiences that can transport them to different places.

**Immersion.** In a visionOS app, people can fluidly transition between different levels of immersion. By default, an app launches in the Shared Space where multiple apps can run side-by-side and people can open, close, and relocate windows. People can also choose to transition an app to a Full Space, where it's the only app running. While in a Full Space app, people can view 3D content blended with their surroundings, open a portal to view another place, or enter a different world.

**Passthrough.** Passthrough provides live video from the device's external cameras, and helps people interact with virtual content while also seeing their actual surroundings. When people want to see more or less of their surroundings, they use the Digital Crown to control the amount of passthrough.

**Spatial Audio.** Apple Vision Pro combines acoustic and visual-sensing technologies to model the sonic characteristics of a person's surroundings, automatically making audio sound natural in their space. When an app receives a person's permission to access information about their surroundings, it can fine-tune Spatial Audio to bring custom experiences to life.

**Eyes and hands.** In general, people perform most actions by using their eyes to look at a virtual object and making an indirect gesture, like a tap, to activate it. People can also interact with a virtual object by using a direct gesture, like touching it with a finger.

**Ergonomics.** While wearing Apple Vision Pro, people rely entirely on the device's cameras for everything they see, both real and virtual, so maintaining visual comfort is paramount. The system helps maintain comfort by automatically placing content so it's relative to the wearer's head, regardless of the person's height or whether they're sitting, standing, or lying down. Because visionOS brings content to people — instead of making people move to reach the content — people can remain at rest while engaging with apps and games.

**Accessibility.** Apple Vision Pro supports accessibility technologies like VoiceOver, Switch Control, Dwell Control, Guided Access, Head Pointer, and many more, so people can use the interactions that work for them. In visionOS, as in all platforms, system-provided UI components build in accessibility support by default, while system frameworks give you ways to enhance the accessibility of your app or game.

> **Note (Apple):** When building your app for Apple Vision Pro, be sure to consider the unique characteristics of the device and its spatial computing environment, and pay special attention to your user's safety; for more details about these characteristics, see the Apple Vision Pro User Guide. For example, Apple Vision Pro should not be used while operating a vehicle or heavy machinery. The device is also not designed to be used while moving around unsafe environments such as near balconies, streets, stairs, or other potential hazards. Apple Vision Pro is designed to be fit and used only by individuals 13 years of age or older.

### Best practices

Great visionOS apps and games are approachable and familiar, while offering extraordinary experiences that can surround people with beautiful content, expanded capabilities, and captivating adventures.

**Embrace the unique features of Apple Vision Pro.** Take advantage of space, Spatial Audio, and immersion to bring life to your experiences, while integrating passthrough and spatial input from eyes and hands in ways that feel at home on the device.

**Consider different types of immersion as you design ways to present your app's most distinctive moments.** You can present experiences in a windowed, UI-centric context, a fully immersive context, or something in between. For each key moment in your app, find the minimum level of immersion that suits it best — don't assume that every moment needs to be fully immersive.

**Use windows for contained, UI-centric experiences.** To help people perform standard tasks, prefer standard windows that appear as planes in space and contain familiar controls. In visionOS, people can relocate windows anywhere they want, and the system's dynamic scaling helps keep window content legible whether it's near or far.

**Prioritize comfort.** To help people stay comfortable and physically relaxed as they interact with your app or game, keep the following fundamentals in mind.

- Display content within a person's field of view, positioning it relative to their head. Avoid placing content in places where people have to turn their head or change their position to interact with it.
- Avoid displaying motion that's overwhelming, jarring, too fast, or missing a stationary frame of reference.
- Support indirect gestures that let people interact with apps while their hands rest in their lap or at their sides.
- If you support direct gestures, make sure the interactive content isn't too far away and that people don't need to interact with it for extended periods.
- Avoid encouraging people to move too much while they're in a fully immersive experience.

**Help people share activities with others.** When you use SharePlay to support shared activities, people can view the spatial Personas of other participants, making it feel like everyone is together in the same space.

## Platform considerations

This page is specific to visionOS. Apple Vision Pro's spatial computing model — windows in space, passthrough, Spatial Audio, eye-and-hand input — has no equivalent on other Apple platforms. See the corresponding "Designing for" page for iOS, iPadOS, macOS, tvOS, and watchOS.

## Native implementation

**Related**
- Apple Design Resources

**Developer documentation**
- visionOS Pathway
- Creating your first visionOS app

**Videos:** Design interactive experiences for visionOS · Design great visionOS apps · Principles of spatial design

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

Most of this page is hardware- and platform-bound and has no meaningful web analogue. Space, immersion levels (Shared Space and Full Space), passthrough, Spatial Audio, and eye-and-hand input all depend on Apple Vision Pro's cameras, sensors, and display — a browser window has no comparable notion of physical space or a wearer's field of view. WebXR exists as a technically adjacent standard, but it targets dedicated immersive experiences rather than everyday web pages, and treating it as a drop-in mapping for this guidance would be a stretch.

**Motion comfort is the one principle that transfers directly.** Apple's instruction to avoid motion that's "overwhelming, jarring, too fast, or missing a stationary frame of reference" is the same reasoning behind the web's `prefers-reduced-motion` media query: uncontrolled or disorienting motion can cause real physical discomfort, not just annoyance. A web page with large-scale parallax, autoplaying video backgrounds, or aggressive scroll-linked animation should honor that preference and offer a stationary, calmer alternative, for the same underlying reason Apple gives.

**"Find the minimum level of immersion that suits it best" → don't force the most intrusive UI pattern by default.** The general principle — match the intensity of a presentation to what the moment actually needs, rather than defaulting to the most immersive option — has a loose web parallel in restraint around full-screen takeovers, autoplaying media, and modal dialogs. It's a weak analogy, but the underlying judgment (immersion is a cost, not a default) is worth carrying over.

**Accessibility technologies (VoiceOver, Switch Control, Dwell Control, Guided Access, Head Pointer) → the web has its own independent set.** The principle that system components build in accessibility by default and frameworks let you extend it maps directly onto semantic HTML plus ARIA, but the specific technologies Apple lists are visionOS-specific and don't correspond one-to-one with web assistive technology.

## Do / Don't

| Do | Don't |
|---|---|
| Combine space, Spatial Audio, and immersion into one integrated experience | Bolt spatial features on without integrating them into the app |
| Match immersion level to what each key moment actually needs | Assume every moment needs to be fully immersive |
| Use windows for standard, UI-centric tasks | Force every interaction into a fully immersive context |
| Keep content within the wearer's field of view, relative to their head | Require people to turn or reposition themselves to interact |
| Support indirect gestures for hands-at-rest interaction | Require sustained direct touch for everyday interactions |
| Keep interactive content within comfortable reach for direct gestures | Place direct-gesture targets too far away or require prolonged reaching |
| Use SharePlay so participants share spatial Personas in the same space | Leave shared activities feeling disconnected between participants |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
