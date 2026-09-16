---
title: Controls
url: https://developer.apple.com/design/human-interface-guidelines/controls
platforms: [iOS, iPadOS, macOS]
last_updated: 2024-06-10
---

# Controls

A control provides quick access to a feature of your app from Control Center, the Lock Screen, or the Action button.

## Core guidance

A control is a button or toggle that provides quick access to your app's features from other areas of the system. Control buttons perform an action, link to a specific area of your app, or launch a camera experience on a locked device. Control toggles switch between two states, such as on and off.

People can add controls to Control Center by pressing and holding in an empty area of Control Center, to the Lock Screen by customizing their Lock Screen, and to the Action button by configuring the Action button in the Settings app.

### Anatomy

Controls contain a symbol image, a title, and, optionally, a value. The symbol visually represents what the control does and can be a symbol from SF Symbols or a custom symbol. The title describes what the control relates to, and the value represents the state of the control. For example, the title can display the name of a light in a room, while the value can display whether it's on or off.

Controls display their information differently depending on where they appear:

- In Control Center, a control displays its symbol and, at larger sizes, its title and value.
- On the Lock Screen, a control displays its symbol.
- On iPhone devices with a control assigned to the Action button, pressing and holding it displays the control's symbol in the Dynamic Island, as well as its value (if present).

### Best practices

**Offer controls for actions that provide the most benefit without having to launch your app.** For example, launching a Live Activity from a control creates an easy and seamless experience that informs someone about progress without having to navigate to your app to stay up to date.

**Update controls when someone interacts with them, when an action completes, or remotely with a push notification.** Update the contents of a control to accurately reflect the state and show if an action is still in progress.

**Choose a descriptive symbol that suggests the behavior of the control.** Depending on where a person adds a control, it may not display the title and value, so the symbol needs to convey enough information about the control's action. For control toggles, provide a symbol for both the on and off states. For example, use the SF Symbols `door.garage.open` and `door.garage.closed` to represent a control that opens and closes a garage door.

**Use symbol animations to highlight state changes.** For control toggles, animate the transition between both on and off states. For control buttons with actions that have a duration, animate indefinitely while the action performs and stop animating when the action is complete.

**Select a tint color that works with your app's brand.** The system applies this tint color to a control toggle's symbol in its on state. When a person performs the action of a control from the Action button, the system also uses this tint color to display the value and symbol in the Dynamic Island.

**Help people provide additional information the system needs to perform an action.** A person may need to configure a control to perform a desired action — for example, select a specific light in a house to turn on and off. If a control requires configuration, prompt people to complete this step when they first add it. People can reconfigure the control at any time.

**Provide hint text for the Action button.** When a person presses the Action button, the system displays hint text to help them understand what happens when they press and hold. When someone presses and holds the Action button, the system performs the action configured to it. Use verbs to construct the hint text.

**If your control title or value can vary, include a placeholder.** Placeholder information tells people what your control does when the title and value are situational. The system displays this information when someone brings up the controls gallery in Control Center or the Lock Screen and chooses your control, or before they assign it to the Action button.

**Hide sensitive information when the device is locked.** When the device is locked, consider having the system redact the title and value to hide personal or security-related information. Specify if the system needs to redact the symbol state as well. If specified, the system redacts the title and value, and displays the symbol in its off state.

**Require authentication for actions that affect security.** For example, require people to unlock their device to access controls to lock or unlock the door to their house or start their car.

### Camera experiences on a locked device

If your app supports camera capture, starting with iOS 18 you can create a control that launches directly to your app's camera experience while the device is locked. For any task beyond capture, a person must authenticate and unlock their device to complete the task in your app.

**Use the same camera UI in your app and your camera experience.** Sharing UI leverages people's familiarity with the app. By using the same UI, the transition to the app is seamless when someone captures content and taps a button to perform additional tasks, such as posting to a social network or editing a photo.

**Provide instructions for adding the control.** Help people understand how to add the control that launches this camera experience.

## Platform considerations

No additional considerations for iOS, iPadOS, or macOS. Not supported in watchOS, tvOS, or visionOS.

## Native implementation

**Related**
- Widgets
- Action button

**Developer documentation**
- LockedCameraCapture
- WidgetKit

**Key APIs**
- `promptsForUserConfiguration()` — indicates a control needs configuration when first added
- `controlWidgetActionHint(_:)` — supplies the Action button's press-and-hold hint text
- `IntentAuthenticationPolicy` — requires device authentication before a control's action runs
- `LockedCameraCapture` — builds a camera control that launches directly to a capture experience on a locked device
- SF Symbols with paired on/off states (for example, `door.garage.open` / `door.garage.closed`) and `SymbolEffect` for animated state transitions

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mapping below applies the same principles to the web; it is inference, not Apple policy, and it breaks down more than it holds up.

**Control Center, the Lock Screen, and the Action button are OS-owned surfaces the web cannot reach, so most of this page is platform-bound.** A control lives in system chrome the app doesn't render and doesn't control the placement of — a person adds it themselves, from a system gallery, to a location the app never draws. No web API grants a page or an installed PWA a slot in the OS's own quick-settings panel, lock screen, or a hardware button's press-and-hold action. State this plainly rather than forcing a comparison.

**The nearest web analogue is the Web App Manifest's `shortcuts` member, and the gap between it and a Control is instructive.** Manifest shortcuts let an installed PWA expose a small set of quick actions from a long-press (or right-click) on its home-screen or taskbar icon — structurally, this is the same idea as a control that "provides quick access to a feature of your app... or link[s] to a specific area of your app." But a manifest shortcut is static: a name, an icon, and a URL, resolved at install time. It cannot toggle between two live states, cannot animate a symbol to show progress, cannot display a dynamic value, and cannot be updated remotely the way Apple describes updating a control's contents when an action completes or a push notification arrives. Treat manifest shortcuts as covering only the "quick link to a specific screen" half of what a Control does, not the toggle-with-live-state half.

**"Choose a descriptive symbol that suggests the behavior" transfers directly to any icon-only web surface.** The reasoning is identical regardless of platform: wherever a title and value might not render — a manifest shortcut icon, a browser-extension toolbar button, a PWA's badge — the icon alone has to carry the meaning, so it needs to be legible and unambiguous at a glance, exactly as Apple requires for a control's Lock Screen appearance where only the symbol shows.

**"Hide sensitive information when the device is locked" has no clean web equivalent, because the web has no concept of "the device is locked" that a page or manifest shortcut can query or respond to.** A PWA's manifest shortcuts and any OS-level quick-action surface render the same way regardless of the device's lock state, because the browser (not the site) owns that boundary and doesn't expose redaction hooks to installed web apps. If a web product surfaces potentially sensitive content through any OS-adjacent affordance — a notification, a badge, a shortcut label — the safer default is to never put sensitive detail there at all, since there's no mechanism to conditionally redact it the way Apple's system-level redaction does.

**"Require authentication for actions that affect security" is a principle worth carrying over even without an OS-level unlock gate to depend on.** Where a manifest shortcut or a similarly quick web affordance triggers something consequential — unlocking a smart-home device, moving money, deleting data — the app itself has to enforce a confirmation or re-authentication step, since the web has no equivalent of "require the device to be unlocked" that a shortcut can declare and have the OS enforce on its behalf.

## Do / Don't

| Do | Don't |
|---|---|
| Offer controls only for actions genuinely useful without opening the app | Turn a control into a launcher that just opens the app |
| Provide distinct symbols for a toggle's on and off states | Reuse one symbol and rely on color alone to show state |
| Keep control content updated after actions complete or push notifications arrive | Let a control's displayed state go stale |
| Prompt for required configuration when a control is first added | Let people add an unconfigured control with no way to complete it |
| Redact sensitive titles, values, and symbol state on a locked device | Show personal or security-related information on the Lock Screen |
| Require authentication for security-affecting actions | Let a control unlock a door or start a car with no authentication step |
| Reuse your app's camera UI in a locked-device camera control | Design a separate, unfamiliar camera interface for the control |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
