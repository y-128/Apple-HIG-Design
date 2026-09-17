---
title: Undo and redo
url: https://developer.apple.com/design/human-interface-guidelines/undo-and-redo
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Undo and redo

Undo and redo gives people easy ways to reverse many types of actions, which can also help people explore and experiment safely as they learn a new interface or task.

## Core guidance

People expect undo and redo to let them reverse their recent actions, so they're likely to try undoing — often multiple times — until something changes. In a situation like this, people might not remember which of their previous actions an undo is targeting, which can lead to unintended changes and frustration. To help people remain in control, it's essential to help people predict the outcome of undoing and redoing and to highlight the results.

### Best practices

**Help people predict the results of undo and redo as much as possible.** On iPhone, for example, you can describe the result in the alert that displays when people shake the device, giving them the option of performing the undo or canceling it. If you provide undo and redo menu items, you can modify the menu item labels to identify the result. For example, a document-based app might use menu item labels like Undo Typing or Redo Bold.

**Show the results of an undo or redo.** Sometimes, the most recent action that people want to undo affects content or an area that's no longer visible. In cases like this, it's crucial to highlight the result of each undo and redo to keep people from thinking that the action had no effect, which can lead them to perform it repeatedly. For example, if people undo after deleting a paragraph in a document area that's no longer onscreen, you might scroll the document to show the restored paragraph.

**Let people undo multiple times.** Avoid placing unnecessary limits on the number of times people can undo or redo. People generally expect to undo every action they've performed since taking a logical step like opening a document or saving their work.

**Consider giving people the option to revert multiple changes at once.** In some scenarios, people might appreciate the ability to undo a batch of discrete but related actions — like incremental adjustments to a single property or attribute — so they don't have to undo each individual adjustment. In other cases, it can make sense to give people a convenient way to undo all the changes they made since opening a document or saving their work.

**Provide undo and redo buttons only when necessary.** People generally expect to initiate undo and redo in system-supported ways, such as choosing the items in a macOS app's Edit menu, using keyboard shortcuts on a Mac or iPad, or shaking their iPhone. If it's important to provide dedicated undo and redo buttons in your app, use the standard system-provided symbols and put the buttons in a toolbar.

## Platform considerations

No additional considerations for visionOS. Not supported in tvOS or watchOS.

### iOS, iPadOS

**Avoid redefining standard gestures for undo and redo.** For example, people can use a three-finger swipe to initiate an undo or redo, or shake their iPhone. As with all standard gestures, redefining them in your interface runs the risk of confusing people and making your experience unpredictable.

**Briefly and precisely describe the operation to be undone or redone.** The undo and redo alert title automatically includes a prefix of "Undo " or "Redo " (including the trailing space). You need to provide an additional word or two that describes what's being undone or redone, to appear after this prefix. For example, you might create alert titles such as "Undo Name" or "Redo Address Change."

### macOS

**Place undo and redo commands in the Edit menu and support the standard keyboard shortcuts.** Mac users expect to find undo and redo at the top of the Edit menu; they also expect to use Command-Z and Shift-Command-Z to perform undo and redo, respectively.

## Native implementation

**Related**
- Feedback
- Pointing devices
- Standard keyboard shortcuts
- Edit menu

**Developer documentation**
- `UndoManager` — Foundation

**Key APIs**
- `UndoManager` — Foundation class that registers and coordinates undo and redo operations

**Videos:** Essential Design Principles

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**There is no platform-level undo stack on the web, so the whole burden Apple hands to `UndoManager` falls on the app.** This is the central gap: native platforms give every app a shared, system-integrated undo mechanism triggered by a standard gesture or shortcut. The browser gives you `document.execCommand('undo')` inside `contenteditable` regions (deprecated and unreliable) and native undo inside plain `<input>`/`<textarea>` elements, but nothing that spans a whole application's state. A web app with meaningful undo has to build and maintain its own command history, typically as a stack of applied and reversible state changes.

**"Help people predict the results of undo and redo" → label the action, don't just expose Ctrl/Cmd-Z.** Apple's guidance to render "Undo Typing" or "Redo Bold" rather than a bare "Undo" applies just as strongly on the web, arguably more so, because the browser gives you no equivalent system-level hint at all. If your app implements custom undo, surface what's about to be reversed — in a toast, a menu item label, or a status region — before or as the action fires.

**"Let people undo multiple times" → keep a real history stack, not a single-step revert.** A common web shortcut-code smell is snapshotting only the previous state and calling it undo; Apple's expectation (undo back through an entire editing session) means the stack needs real depth, and redo needs to survive at least until the next new action invalidates it — the same branching-history problem native undo managers solve.

**Ctrl/Cmd-Z as a keyboard shortcut → intercept it deliberately, and don't collide with the browser's native undo.** Where your app owns a `contenteditable` or canvas-like surface, you can bind `keydown` for Ctrl-Z / Cmd-Shift-Z and route it into your own history stack, mirroring Apple's macOS Command-Z / Shift-Command-Z convention. Inside a plain text `<input>`, the browser already owns undo natively — trying to override it usually produces a worse experience than leaving it alone.

**"Show the results of an undo or redo" → scroll or focus the affected region after the action fires.** This maps without modification: if a reversed action touched content outside the current viewport, move the viewport (or focus) to it, exactly as Apple describes scrolling a document to reveal a restored paragraph. Silent undo — where the DOM changes off-screen — reproduces the exact confusion Apple is warning about.

**"Provide undo and redo buttons only when necessary" → the same restraint applies, for a different reason.** Apple's reasoning is that people expect system-supported ways first; on the web there's no system convention to lean on, so the case for a visible button is often stronger, not weaker, especially for people who don't know the keyboard shortcut. Where you do add one, an icon consistent with the platform convention (a curved arrow) keeps it recognizable rather than novel.

## Do / Don't

| Do | Don't |
|---|---|
| Label undo and redo actions with what they'll affect | Present a bare "Undo" with no indication of the result |
| Scroll or highlight the area an undo or redo changes | Let an undo appear to do nothing when its effect is off-screen |
| Let people undo back through an entire session | Cap the number of available undo steps arbitrarily |
| Support standard shortcuts (Cmd-Z, Shift-Cmd-Z) and gestures | Redefine the three-finger swipe or shake-to-undo gesture |
| Add dedicated undo/redo buttons only when system-supported methods aren't enough | Add undo/redo buttons as the sole way to trigger the action |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
