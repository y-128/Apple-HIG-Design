---
title: Text views
url: https://developer.apple.com/design/human-interface-guidelines/text-views
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-06-05
---

# Text views

A text view displays multiline, styled text content, which can optionally be editable.

## Core guidance

Text views can be any height and allow scrolling when the content extends outside of the view. By default, content within a text view is aligned to the leading edge and uses the system label color. In iOS, iPadOS, and visionOS, if a text view is editable, a keyboard appears when people select the view.

### Best practices

**Use a text view when you need to display text that's long, editable, or in a special format.** Text views differ from text fields and labels in that they provide the most options for displaying specialized text and receiving text input. If you need to display a small amount of text, it's simpler to use a label or — if the text is editable — a text field.

**Keep text legible.** Although you can use multiple fonts, colors, and alignments in creative ways, it's essential to maintain the readability of your content. It's a good idea to adopt Dynamic Type so your text still looks good if people change text size on their device. Be sure to test your content with accessibility options turned on, such as bold text. For guidance, see Accessibility and Typography.

**Make useful text selectable.** If a text view contains useful information such as an error message, a serial number, or an IP address, consider letting people select and copy it for pasting elsewhere.

## Platform considerations

No additional considerations for macOS, visionOS, or watchOS.

### iOS, iPadOS

**Show the appropriate keyboard type.** Several different keyboard types are available, each designed to facilitate a different type of input. To streamline data entry, the keyboard you display when editing a text view needs to be appropriate for the type of content. For guidance, see Virtual keyboards.

### tvOS

You can display text in tvOS using a text view. Because text input in tvOS is minimal by design, tvOS uses text fields for editable text instead.

## Native implementation

**Related**
- Labels
- Text fields
- Combo boxes

**Developer documentation**
- Text — SwiftUI
- `UITextView` — UIKit
- `NSTextView` — AppKit

**Key APIs**
- `Text` — SwiftUI
- `UITextView` — UIKit
- `NSTextView` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Text view vs. label/text field → `<textarea>`/`contenteditable` region vs. a plain text node or single-line `<input>`.** Apple's reason for reaching for a text view — long, editable, or specially formatted content — is the same reason to reach for a `<textarea>` or a `contenteditable` block on the web instead of rendering static text or using a single-line `<input>`. The "use a label for a small amount of text" half of the rule maps directly too: don't reach for a heavyweight editable region to display a sentence of static copy.

**Keep text legible / adopt Dynamic Type → respect the user's root font size, same as Apple's platform-wide Dynamic Type guidance.** A scrollable, potentially long block of text is exactly where an author is most tempted to fix a pixel size and stop thinking about it. The web equivalent of "adopt Dynamic Type" is sizing the text view's font in `rem` so it follows the user's browser font-size preference, and verifying line length and line-height stay comfortable at both the default and an enlarged size — the same test Apple asks for under Accessibility settings.

**Make useful text selectable → this is the web's default behavior, so the risk runs the other way.** Apple has to state this as a positive instruction because native platforms sometimes require deliberate opt-in for selectable text. On the web, plain text is selectable unless an author actively disables it (`user-select: none`) or renders it as an image or canvas output. The practical translation of Apple's rule here is a warning: don't disable selection on error messages, serial numbers, IDs, or other copyable data for cosmetic reasons — the default the browser already gives you is the correct behavior.

**Editable region → track the input-mode/keyboard-type mapping deliberately.** Apple's "show the appropriate keyboard type" for iOS/iPadOS text views has a real web parallel: `inputmode` and `type` attributes (or their equivalents for a `contenteditable` region built as a rich editor) steer mobile virtual keyboards toward numeric, email, or URL layouts. It's a smaller lever on the web than Apple's platform-level keyboard system, but the underlying obligation — don't make someone hunt for a key your input clearly needs — is the same.

## Do / Don't

| Do | Don't |
|---|---|
| Use a text view for long, editable, or specially formatted text | Use a text view to display a short, static string |
| Use a label (or text field, if editable) for small amounts of text | Reach for a heavyweight text view when a label would do |
| Adopt Dynamic Type so text scales with the user's preference | Fix text size and ignore accessibility text-size settings |
| Test content with accessibility options like bold text turned on | Ship without testing under accessibility settings |
| Let people select and copy useful text (error messages, serial numbers, IPs) | Block selection of copyable, useful information |
| On iOS/iPadOS, show the keyboard type appropriate to the content | Show a generic keyboard regardless of expected input |
| On tvOS, use text fields for editable text | Rely on tvOS text views for text input |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
