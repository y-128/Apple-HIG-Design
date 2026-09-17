---
title: Snippets
url: https://developer.apple.com/design/human-interface-guidelines/snippets
platforms: [iOS, iPadOS, macOS]
last_updated: 2026-06-08
---

# Snippets

When someone performs a task with Siri or an App Shortcut, a snippet shows the result or asks for confirmation.

## Core guidance

Snippets are compact views that appear in response to an action that someone takes using Siri, Spotlight, or the Shortcuts app.

You can present a snippet related to one of your app's actions by including it with an app intent that you design to meet the specific needs of a task. For example, you might design a snippet for checking the weather forecast or updating progress toward a daily goal.

There are two snippet types: confirmation and result. A confirmation snippet lets people confirm or cancel an action, and may include options that affect the result. By contrast, a result snippet provides information — possibly as the outcome of a confirmation — that doesn't require further action. An app intent that displays a snippet always shows a result, while the confirmation step is optional.

> *Image caption:* A confirmation snippet requires additional input to proceed.
> *Image caption:* A result snippet provides information without requiring further action.

### Anatomy

A snippet consists of the following elements:

- **Dialogue.** The app intent dialogue that Siri speaks to communicate the snippet's information. The system includes the dialogue text by default and places it above the custom view.
- **Custom view.** A view that visually communicates the snippet's information. A custom view can include one or more buttons for modifying the content of the snippet, getting more information, or taking another action.
- **System-provided button(s).** A confirmation snippet includes two system-provided buttons under the custom view: a secondary Cancel button and a primary button with a customizable label. A result snippet includes a single Done button that dismisses the view.

### Best practices

**Ensure legibility.** Check for sufficient contrast between the snippet's custom content and the system-provided background in both light and dark appearances, and keep consistent margins for the content within the view. This clarifies the layout and helps people interpret the snippet quickly and reliably.

**Keep content concise.** Snippets exist to facilitate lightweight, quick interactions, so it's important to keep their content short and easily legible. To ensure all content is visible, create custom views that are **no taller than the 400-point maximum height**. When considering the amount of text to include, be mindful that fonts draw at various sizes based on a person's preferred text size setting. For a result snippet, if you need to provide more detail, deep-link to the content in your app instead of including it in the custom view.

**Choose a descriptive label for a confirmation snippet's primary button.** You can choose an appropriate label from among those that the system provides, or you can supply a custom label. For example, when designing a snippet to order coffee, labeling the primary button Order is clearer than labeling it OK or Proceed. If you don't specify a label, the system default is Continue.

**Communicate a snippet's purpose visually.** Don't rely on showing the dialogue text to convey a snippet's purpose. While the spoken app intent dialogue is essential for interactions when someone isn't looking at the screen, prefer to omit it from a snippet's visual representation and use the custom view to convey its information instead.

## Platform considerations

No additional considerations for iOS, iPadOS, or macOS. Not supported in tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Siri
- App Shortcuts
- Live Activities

**Developer documentation**
- App Intents
- Displaying static and interactive snippets

**Videos:** Design interactive snippets

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. Snippets are a system-composited view — the app intent dialogue, the custom view, and the button chrome all render inside a Siri/Spotlight/Shortcuts surface the app doesn't own — so there is no direct web equivalent; a web page never renders inside another app's shell this way.

The narrow principle that transfers is the **confirmation-versus-result distinction** itself. It maps cleanly onto the difference between a web confirmation dialog (which blocks on a decision, offers Cancel plus a labeled primary action) and a toast or inline status message (which reports an outcome and needs only a dismiss). Apple's insistence on a *descriptive* primary-button label over generic OK/Proceed, and its 400-point height ceiling to force concision, both restate general dialog and toast UX principles that already apply on the web: name the action, not the mechanism, and keep confirmation and result surfaces short enough to scan at a glance. The requirement to duplicate a snippet's meaning visually rather than lean on spoken dialogue has no web parallel, since the web has no equivalent voice-first delivery path to design around.

## Do / Don't

| Do | Don't |
|---|---|
| Keep custom views concise and within 400 points tall | Cram excessive detail into a snippet's custom view |
| Deep-link to your app for more detail in a result snippet | Try to fit everything into the snippet itself |
| Choose a descriptive primary button label (e.g. Order) | Use a generic label like OK or Proceed when a clearer one fits |
| Convey the snippet's purpose through its custom view | Rely on the spoken dialogue text to convey visual purpose |
| Check contrast in both light and dark appearances | Assume system background contrast is automatically sufficient |
| Keep consistent margins within the view | Let content crowd the edges of the snippet |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
