---
title: Apple Pencil and Scribble
url: https://developer.apple.com/design/human-interface-guidelines/apple-pencil-and-scribble
platforms: [iPadOS]
last_updated: 2024-05-07
---

# Apple Pencil and Scribble

Apple Pencil helps make drawing, handwriting, and marking effortless and natural, in addition to performing well as a pointer and UI interaction tool.

## Core guidance

Apple Pencil is a versatile, intuitive tool for iPad apps that offers pixel-level precision when jotting notes, sketching, painting, marking up documents, and more. Scribble lets people use Apple Pencil to enter text in any text field through fast, private, on-device handwriting recognition. For details on Apple Pencil features and compatibility, see Apple Pencil.

### Best practices

**Support behaviors people intuitively expect when using a marking instrument.** Most people have a lot of experience with real-world marking tools, and this knowledge informs their expectations when they use Apple Pencil with your app. To provide a delightful experience, think about the ways people interact with nondigital pencils, pens, and other marking instruments, and proactively support actions that people may naturally attempt. For example, people often want to write in the margins of documents or books.

**Let people choose when to switch between Apple Pencil and finger input.** For example, if your app supports Apple Pencil for marking, also ensure that your app's controls respond to Apple Pencil so people don't have to switch to using their finger to activate them. In this scenario, a control that doesn't support Apple Pencil input might seem to be unresponsive, giving the impression of a malfunction or low battery. (Scribble only supports Apple Pencil input.)

**Let people make a mark the moment Apple Pencil touches the screen.** You want the experience of putting Apple Pencil to screen to mirror the experience of putting a classic pencil to paper, so it's essential to avoid requiring people to tap a button or enter a special mode before they can make a mark.

**Help people express themselves by responding to the way they use Apple Pencil.** Apple Pencil may sense tilt (altitude), force (pressure), orientation (azimuth), and barrel roll. Use this information to affect the strokes Apple Pencil makes, such as by varying thickness and intensity. When responding to pressure, keep things simple and intuitive. For example, it feels natural to affect continuous properties — such as ink opacity or brush size — by varying the pressure.

**Provide visual feedback to indicate a direct connection with content.** Make sure Apple Pencil appears to directly and immediately manipulate content it touches onscreen. Avoid letting Apple Pencil appear to initiate seemingly disconnected actions, or affect content on other parts of the screen.

**Design a great left- and right-handed experience.** Avoid placing controls in locations that may be obscured by either hand. If there's a chance controls may become obscured, consider letting people reposition them.

### Hover

**Use hover to help people predict what will happen when Apple Pencil touches the screen.** For example, as people hold Apple Pencil above the screen, a hover preview can show the dimensions and color of the mark that the current tool can make. As much as possible, avoid continuously modifying the preview as people move Apple Pencil closer or farther from the screen. A preview that changes according to height is unlikely to clarify the mark Apple Pencil will make, and frequent visual variations can be very distracting to people.

**Avoid using hover to initiate an action.** Unlike tapping a button or marking the screen, hovering is a relatively imprecise motion that doesn't require people to think about the actual distance between Apple Pencil and the display. You don't want people to inadvertently perform an action — especially a destructive action that they might want to undo — just because they hold Apple Pencil near the screen.

**Prefer showing a preview value that's near the middle in a range of dynamic values.** Dynamic properties like opacity or flow can be difficult to depict at the highest or lowest ends of the spectrum. For example, previewing the appearance of a brush mark made with the maximum pressure could occlude the area in which people are marking; in contrast, depicting a mark made with the minimum pressure could be hard for people to detect, making the preview an inaccurate representation of an actual mark or even invisible.

**Consider using hover to support relevant interactions close to where people are marking.** For example, you might respond to hover by displaying a contextual menu of tool sizes when people perform a gesture like squeeze or press a modifier key on an attached keyboard. Revealing a menu near where people are marking lets them make choices without moving Apple Pencil or their hands to another part of the screen.

**Prefer showing hover previews for Apple Pencil, not for a pointing device.** Although a pointing device can also respond to hover gestures, it might be confusing to provide the same visual feedback for both devices. If it makes sense in your app, you can restrict your hover preview to Apple Pencil only. For developer guidance, see Adopting hover support for Apple Pencil.

### Double tap

**Respect people's settings for the double-tap gesture when they make sense in your app.** By default, models of Apple Pencil that support the double-tap gesture respond by toggling between the current tool and the eraser, but people can set the gesture to toggle between the current and previous tool, show and hide the color picker, or do nothing at all. If your app supports these behaviors, let people use their preferred gestures to perform them. If the systemwide double-tap settings don't make sense in your app, you can still use the gesture to change the interaction mode. For example, a 3D app that offers a mesh-editing tool could use double tap to toggle between the tool's raise and lower modes.

**Give people a way to specify custom double-tap behavior if necessary.** If you offer custom double-tap behavior in addition to some or all of the default behaviors, provide a control that lets people choose the custom behavior mode. People need to know which mode they're in; otherwise, they may get confused when your app responds differently to their interactions. In this scenario, make sure it's easy for people to discover the custom behavior your app supports, but don't turn it on by default.

**Avoid using the double-tap gesture to perform an action that modifies content.** In rare cases, it's possible for people to double-tap accidentally, which means that they may not even be aware that your app has performed the action. Prefer using double tap to perform actions that are easy for people to undo. In particular, avoid using double tap to perform a potentially destructive action that might result in data loss.

### Squeeze

Using Apple Pencil Pro, people can squeeze to perform an action. You can design a custom behavior that responds to squeeze, but recognize that people may choose to configure the squeeze gesture to run an App Shortcut instead of app-specific actions.

> **Note (Apple):** The squeeze gesture is available only when the paired iPad screen is on and while the Apple Pencil Pro is not directly contacting it. Because squeeze works when there's distance between Apple Pencil Pro and iPad, people might not always be visually aware of the gesture's onscreen result.

**Treat squeeze as a single, quick gesture that performs a discrete — not continuous — action.** People sometimes squeeze with a lot of force, so holding a squeeze or squeezing several times quickly can be tiring. Help people remain comfortable by responding to a single squeeze and promptly displaying the result.

**If you use squeeze to reveal app UI, like a contextual menu, display it close to Apple Pencil Pro.** Displaying the result of a squeeze near the tip of Apple Pencil Pro strengthens the connection between the device and the gesture, and can help people stay engaged with their task.

**Define squeeze actions that are nondestructive and easy to undo.** As with the double-tap gesture, people can make the squeeze gesture without meaning to, so it's essential to avoid using squeeze to perform an action that could result in data loss.

### Barrel roll

While marking with Apple Pencil Pro, people can use a barrel-roll gesture to change the type of mark they're making. For example, while using Apple Pencil Pro to highlight content in Notes, people can barrel-roll to rotate the angle of the mark.

**Use barrel roll only to modify marking behavior, not to enable navigation or display other controls.** In contrast to double tap and squeeze, barrel roll is naturally related to marking and doesn't make sense for performing an interface action.

### Scribble

With Scribble and Apple Pencil, people can simply write wherever text is accepted in your app — they don't have to tap or switch modes first. Because Scribble is fully integrated into iPadOS, it's available to all apps by default.

**Make text entry feel fluid and effortless.** By default, Scribble works in all standard text components — such as text fields, text views, search fields, and editable fields in web content — except password fields. If you use a custom text field in your app, avoid making people tap or select it before they can begin writing.

**Make Scribble available everywhere people might want to enter text.** Unlike using the keyboard, using Apple Pencil encourages people to treat the screen the way they treat a sheet of paper. Help strengthen this perception in your app by making Scribble consistently available in places where text entry seems natural. For example, in Reminders, it's natural for people to create a new reminder by writing it in the blank space below the last item, even though the area doesn't contain a text field. For developer guidance, see UIIndirectScribbleInteraction.

**Avoid distracting people while they write.** Some text field behaviors work well for keyboard input, but can disrupt the natural writing experience that Apple Pencil provides. For example, it's best to avoid displaying autocompletion text as people write in a text field because the suggestions can visually interfere with their writing. It's also a good idea to hide a field's placeholder text the moment people begin to write so that their input doesn't appear to overlap it.

**While people are writing in a text field, make sure it remains stationary.** In some cases, it can make sense to move a text field when it becomes focused: for example, a search field might move to make more room to display results. Such a movement is fine when people are using the keyboard, but when they're writing it can make them feel like they've lost control of where their input is going. If you can't prevent a text field from moving or resizing, consider delaying the change until people pause their writing.

**Prevent autoscrolling text while people are writing and editing in a text field.** When transcribed text autoscrolls, people might try to avoid writing on top of it. Worse, if text scrolls while people are using Apple Pencil to select it, they might select a different range of text than they want.

**Give people enough space to write.** A small text field can feel uncomfortable to write in. When you know that Apple Pencil input is likely, improve the writing experience in your app by increasing the size of the text field before people begin to write in it or when they pause writing; avoid resizing a text field while people are writing. For developer guidance, see UIScribbleInteraction.

### Custom drawing

Using PencilKit, you can let people take notes, annotate documents and images, and draw with the same low-latency experience that iOS provides. PencilKit also makes it easy to create a custom drawing canvas in your app and offer a state-of-the-art tool picker and ink palette.

**Help people draw on top of existing content.** By default, the colors on your PencilKit canvas dynamically adjust to Dark Mode, so people can create content in either mode and the results will look great in both. However, when people draw on top of existing content like a PDF or a photo, you want to prevent the dynamic adjustment of colors so that the markup remains sharp and visible.

**Consider displaying custom undo and redo buttons when your app runs in a compact environment.** In a regular environment, the tool picker includes undo and redo buttons, but in a compact environment it doesn't. In a compact environment, you could display undo and redo buttons in a toolbar. You might also consider supporting the standard 3-finger undo/redo gesture, so people can use it in any environment. For guidance, see Undo and redo.

## Platform considerations

Apple Pencil and Scribble are supported only in iPadOS. Not supported in iOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Entering data

**Developer documentation**
- PencilKit
- PaperKit
- Adopting hover support for Apple Pencil
- `UIIndirectScribbleInteraction`
- `UIScribbleInteraction`

**Key APIs**
- `UIIndirectScribbleInteraction` — enable Scribble in custom text-entry regions that aren't standard text fields
- `UIScribbleInteraction` — respond to writing focus, including resizing a text field before or between writing
- PencilKit — canvas, tool picker, and ink palette for custom drawing
- PaperKit — document markup and annotation surface

**Videos:** Read between the strokes with PencilKit · Unwrap PaperKit · Meet PaperKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Pressure, tilt, and orientation → the Pointer Events API.** This is one of the rare hardware topics with a genuine, if partial, web analogue. The Pointer Events specification exposes `pressure`, `tiltX`/`tiltY`, `twist` (roughly analogous to barrel roll), and `pointerType` on `PointerEvent`, so a web canvas can read force and angle from a stylus in much the same shape Apple describes for Apple Pencil. The gap is hardware and browser coverage: `pressure` and tilt values are only meaningful when the input device and browser actually report them, support is inconsistent across styluses and platforms, and there's no reliable way to detect "this is Apple Pencil on iPad Safari" versus a generic stylus with partial reporting. Apple's rule to keep pressure response "simple and intuitive" — mapping it to one continuous property like opacity or size — transfers directly, since guessing wrong is cheap to fix but overcomplicating multi-axis input is not.

**"Make a mark the moment the pencil touches the screen" → avoid a first-touch delay.** The general web principle is the same one behind avoiding a 300ms tap-delay: input should have zero perceptible activation latency. On the web this means responding to `pointerdown` immediately rather than requiring a mode switch, and being wary of touch-action or scroll-locking configurations that introduce a delay before a stroke starts registering.

**Hover for preview, not for triggering actions → `pointerType` gating plus no hover-as-click.** The Pointer Events API lets you detect `pointerType === 'pen'` and read `hovering` state distinct from an actual `pointerdown`, so a web app can show a preview cursor without treating proximity as intent — mirroring Apple's warning against using hover to fire destructive actions. This maps cleanly because the underlying hazard (accidental triggering from an imprecise, ambient signal) is identical on both platforms.

**Scribble (handwriting-to-text) → no analogue.** Scribble is on-device, OS-integrated handwriting recognition wired into every native text field automatically. Nothing in the web platform provides this: there is no browser API that converts pen strokes to text in an arbitrary `<input>` or `contenteditable` element. A web app that wants handwriting input must build or embed its own recognition pipeline and its own custom writing surface — it cannot inherit the behavior the way a native iPadOS text field does. This is a genuine capability gap, not a naming difference.

**Squeeze and barrel roll → no analogue.** These are physical gestures specific to Apple Pencil Pro hardware, detected by the pencil itself and delivered through iPadOS system APIs. There is no web equivalent signal — Pointer Events doesn't expose a squeeze sensor or barrel rotation beyond `twist`, and no stylus vendor exposes anything comparable through a browser API. Don't invent a mapping here.

**PencilKit / dynamic Dark Mode inks → no analogue.** The specific behavior of a drawing canvas's stroke colors adapting to light/dark mode unless drawing over existing content is a PencilKit-specific rendering detail with no web equivalent beyond the general `prefers-color-scheme` media query, which addresses UI chrome, not ink color logic for a canvas application.

## Do / Don't

| Do | Don't |
|---|---|
| Let a mark begin the instant Apple Pencil touches the screen | Require a tap or mode switch before marking |
| Support both Apple Pencil and finger input on the same controls | Leave controls that only respond to finger touch |
| Vary a single continuous property (opacity, size) with pressure | Map pressure to multiple properties at once |
| Use hover only for preview | Use hover to trigger an action, especially a destructive one |
| Show preview values near the middle of a dynamic range | Preview at the extreme ends of opacity or flow |
| Treat squeeze as a single discrete, undoable action | Use squeeze or double tap for destructive, hard-to-undo actions |
| Keep a writing text field stationary while people write | Move, resize, or autoscroll a text field mid-stroke |
| Hide placeholder text and suppress autocomplete while writing | Let autocompletion suggestions visually overlap handwriting |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
