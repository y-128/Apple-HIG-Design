---
title: Photo editing
url: https://developer.apple.com/design/human-interface-guidelines/photo-editing
platforms: [iOS, iPadOS, macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Photo editing

Photo-editing extensions let people modify photos and videos within the Photos app by applying filters or making other changes.

## Core guidance

Edits are always saved in the Photos app as new files, safely preserving the original versions.

To access a photo editing extension, a photo must be in edit mode. While in edit mode, tapping the extension icon in the toolbar displays an action menu of available editing extensions. Selecting one displays the extension's interface in a modal view containing a top toolbar. Dismissing this view confirms and saves the edit, or cancels it and returns to the Photos app.

### Best practices

**Confirm cancellation of edits.** Editing a photo or video can be time consuming. If someone taps the Cancel button, don't immediately discard their changes. Ask them to confirm that they really want to cancel, and inform them that any edits will be lost after cancellation. There's no need to show this confirmation if no edits have been made yet.

**Don't provide a custom top toolbar.** Your extension loads within a modal view that already includes a toolbar. Providing a second toolbar is confusing and takes space away from the content being edited.

**Let people preview edits.** It's hard to approve an edit if you can't see what it looks like. Let people see the result of their work before closing your extension and returning to the Photos app.

**Use your app icon for your photo editing extension icon.** This instills confidence that the extension is in fact provided by your app.

## Platform considerations

No additional considerations for iOS, iPadOS, or macOS. Not supported in tvOS, visionOS, or watchOS.

## Native implementation

**Developer documentation**
- App extensions
- PhotoKit

**Videos:** Introducing Photo Segmentation Mattes

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

The photo-editing *extension* mechanism does not transfer: it depends on the Photos app hosting third-party code in a modal view with a system-provided toolbar, and on a system-managed non-destructive edit stack that always preserves the original file. The web has no equivalent host app to extend, and a web page editing an image has no OS-level guarantee that an "original" is preserved anywhere unless the application itself builds that guarantee.

What does transfer is the underlying image-editing UI principle, independent of the hosting platform. "Don't provide a custom top toolbar" generalizes to a rule about nested chrome: any web editor embedded inside another surface (an image editor inside a CMS, a cropping tool inside a modal) should not duplicate the host's toolbar — one set of controls, in one place, at one time, is the reasoning, and it applies whether the host is Photos or a web app shell. "Let people preview edits before committing" and "confirm cancellation when unsaved edits exist" are general destructive-action patterns that hold for any web editing surface with unsaved state: don't let a Cancel or navigate-away action silently discard work, and don't ask for confirmation when there's nothing to lose. "Use your app icon for the extension icon" maps to the general principle that an embedded tool should visually identify its source — a web equivalent is showing the provider's branding or icon on an embedded editing widget so users know which service is doing the editing.

Where the mapping breaks down: Apple's guarantee that edits are non-destructive and always saved as new files is a system-level property of Photos' storage model. On the web, "non-destructive" and "original preserved" are promises the application itself must implement and cannot borrow from the platform — there's no browser-level equivalent to Photos' edit history.

## Do / Don't

| Do | Don't |
|---|---|
| Ask for confirmation before discarding unsaved edits | Discard changes immediately when someone taps Cancel |
| Skip the cancellation prompt if no edits have been made | Show a confirmation dialog when there's nothing to lose |
| Rely on the host's existing top toolbar | Add a second, custom top toolbar inside the extension |
| Let people preview the result before closing the extension | Force people to accept an edit without seeing it applied |
| Use your app's own icon for the extension | Use a generic or unrelated icon for the extension |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
