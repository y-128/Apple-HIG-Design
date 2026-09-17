---
title: Motion
url: https://developer.apple.com/design/human-interface-guidelines/motion
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-09-09
---

# Motion

Beautiful, fluid motions bring the interface to life, conveying status, providing feedback and instruction, and enriching the visual experience of your app or game.

## Core guidance

Many system components automatically include motion, letting you offer familiar and consistent experiences throughout your app or game. System components might also adjust their motion in response to factors like accessibility settings or different input methods. For example, the movement of Liquid Glass responds to direct touch interaction with greater emphasis to reinforce the feeling of a tactile experience, but produces a more subdued effect when a person interacts using a trackpad.

If you design custom motion, follow the guidelines below.

### Best practices

**Add motion purposefully, supporting the experience without overshadowing it.** Don't add motion for the sake of adding motion. Gratuitous or excessive animation can distract people and may make them feel disconnected or physically uncomfortable.

**Make motion optional.** Not everyone can or wants to experience the motion in your app or game, so it's essential to avoid using it as the only way to communicate important information. To help everyone enjoy your app or game, supplement visual feedback by also using alternatives like haptics and audio to communicate.

### Providing feedback

**Strive for realistic feedback motion that follows people's gestures and expectations.** In nongame apps, accurate, realistic motion can help people understand how something works, but feedback motion that doesn't make sense can make them feel disoriented. For example, if someone reveals a view by sliding it down from the top, they don't expect to dismiss the view by sliding it to the side.

**Aim for brevity and precision in feedback animations.** When animated feedback is brief and precise, it tends to feel lightweight and unobtrusive, and it can often convey information more effectively than prominent animation. For example, when a game displays a succinct animation that's precisely tied to a successful action, players can instantly get the message without being distracted from their gameplay. Another example is in visionOS: When people tap a panorama in Photos, it quickly and smoothly expands to fill the space in front of them, helping them track the transition without making them wait to enjoy the content.

**In apps, generally avoid adding motion to UI interactions that occur frequently.** The system already provides subtle animations for interactions with standard interface elements. For a custom element, you generally want to avoid making people spend extra time paying attention to unnecessary motion every time they interact with it.

**Let people cancel motion.** As much as possible, don't make people wait for an animation to complete before they can do anything, especially if they have to experience the animation more than once.

**Consider using animated symbols where it makes sense.** When you use SF Symbols 5 or later, you can apply animations to SF Symbols or custom symbols. For guidance, see Animations.

### Leveraging platform capabilities

**Make sure your game's motion looks great by default on each platform you support.** In most games, maintaining a consistent frame rate of 30 to 60 fps typically results in a smooth, visually appealing experience. For each platform you support, use the device's graphics capabilities to enable default settings that let people enjoy your game without first having to change those settings.

**Let people customize the visual experience of your game to optimize performance or battery life.** For example, consider letting people switch between power modes when the system detects the presence of an external power source.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, or tvOS.

### visionOS

In addition to subtly communicating context, drawing attention to information, and enriching immersive experiences, motion in visionOS can combine with depth to provide essential feedback when people look at interactive elements. Because motion is likely to be a large part of your visionOS experience, it's crucial to avoid causing distraction, confusion, or discomfort.

**As much as possible, avoid displaying motion at the edges of a person's field of view.** People can be particularly sensitive to motion that occurs in their peripheral vision: in addition to being distracting, such motion can even cause discomfort because it can make people feel like they or their surroundings are moving. If you need to show an object moving in the periphery during an immersive experience, make sure the object's brightness level is similar to the rest of the visible content.

**Help people remain comfortable when showing the movement of large virtual objects.** If an object is large enough to fill a lot of the field of view, occluding most or all of passthrough, people can naturally perceive it as being part of their surroundings. To help people perceive the object's movement without making them think that they or their surroundings are moving, you can increase the object's translucency, helping people see through it, or lower its contrast to make its motion less noticeable.

> **Note (Apple):** People can experience discomfort even when they're the ones moving a large virtual object, such as a window. Although adjusting translucency and contrast can help in this scenario, consider also keeping a window's size fairly small.

**Consider using fades when you need to relocate an object.** When an object moves from one location to another, people naturally watch the movement. If such movement doesn't communicate anything useful to people, you can fade the object out before moving it and fade it back in after it's in the new location.

**In general, avoid letting people rotate a virtual world.** When a virtual world rotates, the experience typically upsets people's sense of stability, even when they control the rotation and the movement is subtle. Instead, consider using instantaneous directional changes during a quick fade-out.

**Consider giving people a stationary frame of reference.** It can be easier for people to handle visual movement when it's contained within an area that doesn't move. In contrast, if the entire surrounding area appears to move, for example in a game that automatically moves a player through space, people can feel unwell.

**Avoid showing objects that oscillate in a sustained way.** In particular, you want to avoid showing an oscillation that has a frequency of around 0.2 Hz because people can be very sensitive to this frequency. If you need to show objects oscillating, aim to keep the amplitude low and consider making the content translucent.

### watchOS

SwiftUI provides a powerful and streamlined way to add motion to your app. If you need to use WatchKit to animate layout and appearance changes, or create animated image sequences, see `WKInterfaceImage`.

> **Note (Apple):** All layout- and appearance-based animations automatically include built-in easing that plays at the start and end of the animation. You can't turn off or customize easing.

## Native implementation

**Related**
- Feedback
- Accessibility
- Spatial layout
- Immersive experiences

**Developer documentation**
- Animating views and transitions — SwiftUI

**Key APIs**
- `WKInterfaceImage` — WatchKit; animate layout and appearance changes, and create animated image sequences. Built-in easing at the start and end cannot be disabled or customized.
- SF Symbols 5 or later — symbol animations applicable to both SF Symbols and custom symbols (see Animations)

**Videos:** Enhance your UI animations and transitions · Create custom visual effects with SwiftUI · Design considerations for vision and motion

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Purposeful motion → animate state changes, not arrivals.** Apple's rule against motion "for the sake of adding motion" exists because animation consumes attention: every moving pixel is a claim on the viewer's foveal focus, and a claim that pays nothing back is a tax. On the web the most common violation is scroll-triggered entrance animation, where content fades and slides in simply because it entered the viewport. That motion communicates nothing about state, since the content was always there, and it delays reading. The web-native version of Apple's rule is to reserve transitions and keyframe animations for moments where something genuinely changed: an item was added or removed, a panel opened, a value updated, a request succeeded or failed.

**Make motion optional → treat `prefers-reduced-motion` as a hard requirement, not a nicety.** Apple's guidance says motion must never be the only channel carrying important information. The web has a direct analogue in the `prefers-reduced-motion` media query, and the honest implementation is to author the reduced branch as a real design rather than a global animation kill switch. A blanket rule that zeroes all durations often breaks interfaces whose meaning depends on the transition, because a panel that was supposed to slide now teleports and the user loses track of where content came from. The better reading of Apple's rule is to substitute channels: replace positional movement with an opacity change or an instant state swap, and keep the non-visual channels (text, focus movement, live-region announcements) carrying the same message either way.

**Where the web genuinely differs: the preference is weaker and less reliable.** On Apple platforms, Reduce Motion is a system setting the OS itself acts on, so system components adapt whether or not the developer does anything. On the web nothing adapts automatically. The media query only reports the OS-level preference to the page, and honoring it is entirely the author's responsibility, so an untouched site animates at full strength for someone who explicitly asked the opposite. Reporting is also inconsistent across operating systems: what a user toggles in one OS's accessibility panel may map to the query differently than in another, and browser-level overrides are not universally available. Treat the query as a signal that is present when it fires but never assume its absence means consent.

**Feedback motion should follow the gesture → direction and origin must match.** Apple's example is that a view revealed by sliding down from the top should not be dismissed sideways. The underlying principle is that motion is a spatial explanation of where a thing came from and where it went, so a mismatch between entry and exit destroys the mental model rather than reinforcing it. On the web this maps to transform-origin and direction discipline: a menu anchored to a button should grow from that button, a drawer that entered from the right should leave to the right, and a dialog dismissed by a downward swipe should exit downward. Where the web adds a wrinkle, gesture-driven motion is not interruptible by default the way a native pan is, so a CSS transition triggered by a swipe will run to completion even if the user reverses the gesture mid-way.

**Brevity and precision → short durations, and no animation on frequent interactions.** Apple's rule that brief, precise feedback conveys more than prominent animation lands the same way on the web, where hover, focus, and click are high-frequency events. A 400 ms color transition on a nav link is felt as sluggishness because the user performs that interaction dozens of times per session. The source gives no numeric duration guidance, so no specific millisecond figure is being asserted here; the transferable rule is that the more often an interaction occurs, the shorter and quieter its motion should be, and for the most frequent interactions the correct amount of motion is often none.

**Let people cancel motion → never block input on an animation.** Apple's rule is that people should not wait for an animation before acting. The web equivalent is that a page must remain interactive during transitions: no overlay that swallows clicks until an entrance finishes, no disabled submit button gated on a decorative animation, and no route change that withholds the new view until an exit animation completes. The View Transitions API is worth naming here because it makes cross-document and cross-view animation trivially easy, which also makes it trivially easy to gate navigation on an animation that the user did not ask for.

**Frame rate → the web's constraint is the main thread, not the GPU budget.** Apple's 30 to 60 fps guidance is aimed at games choosing graphics settings per device. Web pages have no equivalent settings dialog and no way to negotiate a rendering budget, so smoothness is instead determined by whether animation work can stay off the main thread. Animating properties that trigger layout keeps the animation coupled to JavaScript and reflow, while compositor-friendly properties like transform and opacity survive a busy main thread. There is no web analogue at all to Apple's advice about letting players switch power modes when an external power source is detected.

**visionOS-specific guidance mostly has no web analogue.** Peripheral-vision motion, passthrough occlusion, translucency of large virtual objects, virtual world rotation, stationary frames of reference, and the 0.2 Hz oscillation sensitivity are all consequences of head-mounted, full-field-of-view rendering. A page in a flat browser window occupies a small, bounded region of the visual field, so none of these transfer directly. The one idea that does generalize is the stationary frame of reference: motion contained inside a bounded element that itself does not move is easier to tolerate than motion of the whole page, which is a reasonable argument against full-page parallax and scroll-jacked backgrounds.

## Do / Don't

| Do | Don't |
|---|---|
| Add motion purposefully, supporting the experience without overshadowing it | Add motion for the sake of adding motion, or use gratuitous or excessive animation |
| Make motion optional, and supplement visual feedback with haptics and audio | Use motion as the only way to communicate important information |
| Strive for realistic feedback motion that follows people's gestures and expectations | Use feedback motion that doesn't make sense, such as dismissing sideways a view that was revealed from the top |
| Aim for brevity and precision in feedback animations | Use prominent animation where a succinct, precisely tied one would convey more |
| Rely on the system's subtle built-in animations for standard interface elements | Add motion to UI interactions that occur frequently |
| Let people cancel motion | Make people wait for an animation to complete before they can do anything |
| Consider using animated symbols where it makes sense (SF Symbols 5 or later) | — |
| Make your game's motion look great by default on each supported platform, maintaining 30 to 60 fps | Require people to change settings before they can enjoy your game |
| Let people customize the visual experience to optimize performance or battery life | — |
| In visionOS, keep peripheral motion to a minimum, or match its brightness to the rest of the visible content | Display motion at the edges of a person's field of view |
| In visionOS, increase translucency or lower contrast when moving large virtual objects, and keep windows fairly small | Move a large object at full opacity and contrast while it occludes most of passthrough |
| In visionOS, fade an object out before relocating it and fade it back in | Move an object across locations when the movement communicates nothing useful |
| In visionOS, use instantaneous directional changes during a quick fade-out | Let people rotate a virtual world |
| In visionOS, give people a stationary frame of reference | Move the entire surrounding area, such as automatically moving a player through space |
| In visionOS, keep oscillation amplitude low and consider making the content translucent | Show sustained oscillation, especially around a frequency of 0.2 Hz |
| In watchOS, use SwiftUI for motion, or `WKInterfaceImage` when WatchKit is required | Expect to turn off or customize the built-in easing on layout- and appearance-based watchOS animations |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
