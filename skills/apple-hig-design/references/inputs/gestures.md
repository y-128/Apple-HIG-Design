---
title: Gestures
url: https://developer.apple.com/design/human-interface-guidelines/gestures
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2024-09-09
---

# Gestures

A gesture is a physical motion that a person uses to directly affect an object in an app or game on their device.

## Core guidance

Depending on the device they're using, people can make gestures on a touchscreen, in the air, or on a range of input devices such as a trackpad, mouse, remote, or game controller that includes a touch surface.

Every platform supports basic gestures like tap, swipe, and drag. Although the precise movements that make up basic gestures can vary per platform and input device, people are familiar with the underlying functionality of these gestures and expect to use them everywhere. For a list of these gestures, see Standard gestures under Specifications below.

### Best practices

**Give people more than one way to interact with your app.** People commonly prefer or need to use other inputs — such as their voice, keyboard, or Switch Control — to interact with their devices. Don't assume that people can use a specific gesture to perform a given task.

**In general, respond to gestures in ways that are consistent with people's expectations.** People expect most gestures to work the same regardless of their current context. For example, people expect tap to activate or select an object. Avoid using a familiar gesture like tap or swipe to perform an action that's unique to your app; similarly, avoid creating a unique gesture to perform a standard action like activating a button or scrolling a long view.

**Handle gestures as responsively as possible.** Useful gestures enhance the experience of direct manipulation and provide immediate feedback. As people perform a gesture in your app, provide feedback that helps them predict its results and, if necessary, communicates the extent and type of movement required to complete the action.

**Indicate when a gesture isn't available.** If you don't clearly communicate why a gesture doesn't work, people might think your app has frozen or they aren't performing the gesture correctly, leading to frustration. For example, if someone tries to drag a locked object, the UI may not indicate that the object's position has been locked; or if they try to activate an unavailable button, the button's unavailable state may not be clearly distinct from its available state.

### Custom gestures

**Add custom gestures only when necessary.** Custom gestures work best when you design them for specialized tasks that people perform frequently and that aren't covered by existing gestures, like in a game or drawing app. If you decide to implement a custom gesture, make sure it's:

- Discoverable
- Straightforward to perform
- Distinct from other gestures
- Not the only way to perform an important action in your app or game

**Make custom gestures easy to learn.** Offer moments in your app to help people quickly learn and perform custom gestures, and make sure to test your interactions in real use scenarios. If you're finding it difficult to use simple language and graphics to describe a gesture, it may mean people will find the gesture difficult to learn and perform.

**Use shortcut gestures to supplement standard gestures, not replace them.** While you may supply a custom gesture to quickly access parts of your app, people also need simple, familiar ways to navigate and perform actions, even if it means an extra tap or two. For example, in an app that supports navigation through a hierarchy of views, people expect to find a Back button in a top toolbar that lets them return to the previous view with a single tap. To help accelerate this action, many apps also offer a shortcut gesture — such as swiping from the side of a window or touchscreen — while continuing to provide the Back button.

**Avoid conflicting with gestures that access system UI.** Several platforms offer gestures for accessing system behaviors, like edge swiping in watchOS or rolling your hand over to access system overlays in visionOS. It's important to avoid defining custom gestures that might conflict with these interactions, as people expect these controls to work consistently. In specific circumstances within games or immersive experiences, developers can work around this area by deferring the system gesture.

## Platform considerations

### iOS, iPadOS

In addition to the standard gestures supported in all platforms, iOS and iPadOS support a few other gestures that people expect.

| Gesture | Common action |
|---|---|
| Three-finger swipe | Initiate undo (left swipe); initiate redo (right swipe). |
| Three-finger pinch | Copy selected text (pinch in); paste copied text (pinch out). |
| Four-finger swipe (iPadOS only) | Switch between apps. |
| Shake | Initiate undo; initiate redo. |

**Consider allowing simultaneous recognition of multiple gestures if it enhances the experience.** Although simultaneous gestures are unlikely to be useful in nongame apps, a game might include multiple onscreen controls — such as a joystick and firing buttons — that people can operate at the same time.

### macOS

People primarily interact with macOS using a keyboard and mouse. In addition, they can make standard gestures on a Magic Trackpad, Magic Mouse, or a game controller that includes a touch surface.

### tvOS

People expect to use standard gestures to navigate tvOS apps and games with a compatible remote, Siri Remote, or game controller that includes a touch surface.

### visionOS

visionOS supports two categories of gestures: indirect and direct.

People use an **indirect gesture** by looking at an object to target it, and then manipulating that object from a distance — indirectly — with their hands. For example, a person can look at a button to focus it and select it by quickly tapping their finger and thumb together. Indirect gestures are comfortable to perform at any distance, and let people quickly change focus between different objects and select items with minimal movement.

People use a **direct gesture** to physically touch an interactive object. For example, people can directly type on the visionOS keyboard by tapping the virtual keys. Direct gestures work best when they are within reach. Because people may find it tiring to keep their arms raised for extended periods, direct gestures are best for infrequent use. visionOS also supports direct versions of all standard gestures, allowing people the choice to interact directly or indirectly with any standard component.

Standard direct gestures in visionOS:

| Direct gesture | Common use |
|---|---|
| Touch | Directly select or activate an object. |
| Touch and hold | Open a contextual menu. |
| Touch and drag | Move an object to a new location. |
| Double touch | Preview an object or file; select a word in an editing context. |
| Swipe | Reveal actions and controls; dismiss views; scroll. |
| With two hands, pinch and drag together or apart | Zoom in or out. |
| With two hands, pinch and drag in a circular motion | Rotate an object. |

**Support standard gestures everywhere you can.** For example, as soon as someone looks at an object in your app or game, tap is the first gesture they're likely to make when they want to select or activate it. Even if you also support custom gestures, supporting standard gestures such as tap helps people get comfortable with your app or game quickly.

**Offer both indirect and direct interactions when possible.** Prefer indirect gestures for UI and common components like buttons. Reserve direct gestures and custom gestures for objects that invite close-up interaction or specific motions in a game or interactive experience.

**Avoid requiring specific body movements or positions for input.** Not all people can perform specific body movements or position themselves in certain ways at all times, whether due to disability, spatial constraints, or other environmental factors. If your experience requires movement, consider supporting alternative inputs to let people choose the interaction method that works best for them.

#### Designing custom gestures in visionOS

If you want to offer a specific interaction for your experience that people can't perform using an existing system gesture, consider designing a custom gesture. To offer this type of interaction, your app needs to be running in a Full Space, and you must request people's permission to access information about their hands.

**Prioritize comfort.** Continually test ergonomics of all interactions that require custom gestures. A custom interaction that requires people to keep their arms raised for even a little while can be physically tiring, and repeating very similar movements many times in succession can stress people's muscles and joints.

**Carefully consider complex custom gestures that involve multiple fingers or both hands.** People may not always have both hands available when using your app or game. If you require a more complex gesture for your experience, consider also offering an alternative that requires less movement.

**Avoid custom gestures that require using a specific hand.** It can increase someone's cognitive load if they need to remember which hand to use to trigger a custom gesture. It may also make your experience less welcoming to people with strong hand-dominance or limb differences.

#### Working with system overlays in visionOS

In visionOS 2 and later, people can look at the palm of one hand and use gestures to quickly access system overlays for Home and Control Center. These interactions are available systemwide, and are reserved solely for accessing system overlays.

> **Note (Apple):** The system overlay is the default method of accessing Control Center in visionOS 2 and later. The visionOS 1 behavior (looking upward) remains available as an accessibility setting.

When designing apps and games that use custom gestures or anchor content to a person's hands, it's important to take interactions with the system overlays into consideration.

**Reserve the area around a person's hand for system overlays and their related gestures.** If possible, don't anchor content to a person's hands or wrists. If you're designing a game that involves hand-anchored content, place it outside of the immediate area of someone's hand to avoid colliding with the Home indicator.

> *Image caption:* The area reserved for interacting with system overlays. A person looks at their palm to reveal the Home indicator. A person turns their hand to reveal the status bar, and can tap to open Control Center.

**Consider deferring the system overlay behavior when designing an immersive app or game.** In certain circumstances, you may not want the Home indicator to appear when someone looks at the palm of their hand. For example, a game that uses virtual hands or gloves may want to keep someone within the world of the story, even if they happen to look at their hands from different angles. In such cases, when your app is running in a Full Space, you can choose to require a tap to reveal the Home indicator instead.

> *Image caption:* Default behavior in the Shared Space. Default behavior in a Full Space. Deferred behavior in a Full Space.

> **Note (Apple):** Apps and games that you built for visionOS 1 defer the system overlay behavior by default. When a person looks at their palm with your app running in a Full Space, the Home indicator won't appear unless they tap first.

**Use caution when designing custom gestures that involve a rolling motion of the hand, wrist, and forearm.** This specific motion is reserved for revealing system overlays. Since system overlays always display on top of app content and your app isn't aware of when they're visible, it's important to test any custom gestures or content that might conflict.

### watchOS

**Double tap.** In watchOS 11 and later, people can use the double-tap gesture to scroll through lists and scroll views, and to advance between vertical tab views. Additionally, you can specify a toggle or button as the primary action in your app, or in your widget or Live Activity when the system displays it in the Smart Stack. Double-tapping in a view with a primary action highlights the control and then performs the action. The system also supports double tap for custom actions that you offer in notifications, where it acts on the first nondestructive action in the notification.

**Avoid setting a primary action in views with lists, scroll views, or vertical tabs.** This conflicts with the default navigation behaviors that people expect when they double-tap.

**Choose the button that people use most commonly as the primary action in a view.** Double tap is helpful in a nonscrolling view when it performs the action that people use the most. For example, in a media controls view, you could assign the primary action to the play/pause button.

## Specifications

### Standard gestures

The system provides APIs that support the familiar gestures people use with their devices, whether they use a touchscreen, an indirect gesture in visionOS, or an input device like a trackpad, mouse, remote, or game controller.

| Gesture | Supported in | Common action |
|---|---|---|
| Tap | iOS, iPadOS, macOS, tvOS, visionOS, watchOS | Activate a control; select an item. |
| Swipe | iOS, iPadOS, macOS, tvOS, visionOS, watchOS | Reveal actions and controls; dismiss views; scroll. |
| Drag | iOS, iPadOS, macOS, tvOS, visionOS, watchOS | Move a UI element. |
| Touch (or pinch) and hold | iOS, iPadOS, tvOS, visionOS, watchOS | Reveal additional controls or functionality. |
| Double tap | iOS, iPadOS, macOS, tvOS, visionOS, watchOS | Zoom in; zoom out if already zoomed in; perform a primary action on Apple Watch Series 9 and Apple Watch Ultra 2. |
| Zoom | iOS, iPadOS, macOS, tvOS, visionOS | Zoom a view; magnify content. |
| Rotate | iOS, iPadOS, macOS, tvOS, visionOS | Rotate a selected item. |

For guidance on supporting additional gestures and button presses on specific input devices, see Pointing devices, Remotes, and Game controls.

## Native implementation

**Related**
- Feedback
- Eyes
- Playing haptics

**Developer documentation**
- Gestures — SwiftUI
- `UITouch` — UIKit
- Setting up access to ARKit data
- `persistentSystemOverlays(_:)`
- `handGestureShortcut(_:isEnabled:)` and `primaryAction`

**Videos:** Enhance your UI animations and transitions · Design for spatial input

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Every platform supports basic gestures" → the web has its own conflicting basics, and they're partly browser-owned.** Tap on the web is a click or a `pointerup`, and it already carries meaning the browser controls: a link click navigates, a form submit fires, and — critically — an unhandled single-finger swipe scrolls the page or triggers browser back/forward navigation. Apple's rule "avoid using a familiar gesture to perform an action that's unique to your app" translates directly: don't hijack scroll-feeling swipe gestures for custom app logic unless you are prepared to fully replace the browser's native scroll and edge-navigation behavior, because a half-replacement (say, a horizontal swipe carousel with no fallback) breaks the browser back gesture people rely on at a screen edge.

**Standard gesture table → Pointer Events, not touch-specific APIs.** Apple's table spans touchscreen, trackpad, mouse, remote, and game controller under one set of gesture names because the system abstracts the input device away. The Pointer Events API (`pointerdown`, `pointermove`, `pointerup`, `pointercancel`) is the closest web equivalent — a single event model that fires for mouse, touch, and pen alike, so you write one gesture handler rather than branching on `touchstart` versus `mousedown`. Where the web genuinely falls short is device *detection*: there's no clean signal for "is this a trackpad or a touchscreen," only pointer type (`mouse`, `touch`, `pen`) and coarse hover/pointer media queries, so some of Apple's per-device nuance (three-finger swipe, four-finger swipe) has no web equivalent at all — the browser doesn't expose finger-count gestures to page script.

**"Indicate when a gesture isn't available" → CSS `touch-action` and disabled-state affordances.** Apple's warning about ambiguous unavailable states maps to two separate web concerns: visually distinguishing a disabled interactive element (contrast, cursor, ARIA `aria-disabled`), and explicitly declaring which native gestures a region should or shouldn't handle via the `touch-action` CSS property, so the browser doesn't fight your custom handler mid-gesture.

**"Avoid conflicting with gestures that access system UI" → this is the sharpest edge on the web.** Apple's watchOS edge-swipe and visionOS palm-gesture examples are platform gestures a well-behaved app must not shadow. The web's equivalent conflicts are numerous and mostly invisible until a user hits them: an edge-swipe-to-go-back gesture on iOS Safari and in PWAs, pull-to-refresh on Chrome for Android, pinch-zoom, and double-tap-to-zoom. `touch-action: pan-y` or `none` can suppress these, but doing so removes an accessibility fallback for people who rely on native browser gestures, so the same caution Apple gives for visionOS hand-rolling motion applies with more force here — suppress only the exact gesture in the exact region you're replacing, not the whole viewport.

**Custom gesture discoverability → there's no HIG-equivalent muscle memory to lean on.** Apple's platforms teach people gestures over years of consistent system behavior. A web app gets none of that; a swipe-to-dismiss card in a browser is discoverable only if you build the affordance yourself (a visible edge, a drag handle, a hint animation). Apple's rule "make custom gestures easy to learn" is, if anything, a stricter requirement on the web than on a native platform.

**visionOS gaze-plus-pinch and hand-anchored content → no meaningful web analogue.** This is genuinely platform-specific: browsers running in visionOS's Safari get standard pointer/click events, not raw hand-tracking or gaze data, so the indirect/direct gesture distinction, hand-anchoring rules, and system-overlay collision-avoidance guidance don't have anything for a web developer to implement against today.

## Do / Don't

| Do | Don't |
|---|---|
| Use tap, swipe, and drag for their standard meanings | Repurpose a standard gesture for a unique app action |
| Provide immediate feedback as a gesture is performed | Leave people guessing whether a gesture registered |
| Clearly indicate when a gesture is unavailable | Let an unavailable control look identical to an available one |
| Offer a shortcut gesture alongside a standard control | Replace a standard control with a gesture-only path |
| Test custom gestures for ergonomics and real-world use | Require sustained raised-arm gestures without an alternative |
| Reserve the hand area around a person for system overlays in visionOS | Anchor content directly to a person's hand or wrist in visionOS |
| Design custom gestures usable with either hand | Require a specific hand to trigger a custom gesture |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
