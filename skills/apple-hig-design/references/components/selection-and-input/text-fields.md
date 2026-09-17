---
title: Text fields
url: https://developer.apple.com/design/human-interface-guidelines/text-fields
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-06-05
---

# Text fields

A text field is a rectangular area in which people enter or edit small, specific pieces of text.

## Core guidance

### Best practices

**Use a text field to request a small amount of information, such as a name or an email address.** To let people input larger amounts of text, use a text view instead.

**Show a hint in a text field to help communicate its purpose.** A text field can contain placeholder text — such as "Email" or "Password" — when there's no other text in the field. Because placeholder text disappears when people start typing, it can also be useful to include a separate label describing the field to remind people of its purpose.

**Use secure text fields to hide private data.** Always use a secure text field when your app asks for sensitive data, such as a password. For developer guidance, see `SecureField`.

**To the extent possible, match the size of a text field to the quantity of anticipated text.** The size of a text field helps people visually gauge the amount of information to provide.

**Evenly space multiple text fields.** If your layout includes multiple text fields, leave enough space between them so people can easily see which input field belongs with each introductory label. Stack multiple text fields vertically when possible, and use consistent widths to create a more organized layout. For example, the first and last name fields on an address form might be one width, while the address and city fields might be a different width.

**Ensure that tabbing between multiple fields flows as people expect.** When tabbing between fields, move focus in a logical sequence. The system attempts to achieve this result automatically, so you won't need to customize this too often.

**Validate fields when it makes sense.** For example, if the only legitimate value for a field is a string of digits, your app needs to alert people if they've entered characters other than digits. The appropriate time to check the data depends on the context: when entering an email address, it's best to validate when people switch to another field; when creating a user name or password, validation needs to happen before people switch to another field.

**Use a number formatter to help with numeric data.** A number formatter automatically configures the text field to accept only numeric values. It can also display the value in a specific way, such as with a certain number of decimal places, as a percentage, or as currency. Don't assume the actual presentation of data, however, as formatting can vary significantly based on people's locale.

> *Image caption:* Formatted text.

**Adjust line breaks according to the needs of the field.** By default, the system clips any text extending beyond the bounds of a text field. Alternatively, you can set up a text field to wrap text to a new line at the character or word level, or to truncate (indicated by an ellipsis) at the beginning, middle, or end.

> *Image caption:* Clipped text, wrapped text, and truncated text.

**Consider using an expansion tooltip to show the full version of clipped or truncated text.** An expansion tooltip behaves like a regular tooltip and appears when someone places the pointer over the field.

**In iOS, iPadOS, tvOS, and visionOS apps, show the appropriate keyboard type.** Several different keyboard types are available, each designed to facilitate a different type of input, such as numbers or URLs. To streamline data entry, display the keyboard that's appropriate for the type of content people are entering. For guidance, see Virtual keyboards.

**Minimize text entry in your tvOS and watchOS apps.** Entering long passages of text or filling out numerous text fields is time-consuming on Apple TV and Apple Watch. Minimize text input and consider gathering information more efficiently, such as with buttons.

## Platform considerations

No additional considerations for tvOS or visionOS.

### iOS, iPadOS

**Display a Clear button in the trailing end of a text field to help people erase their input.** When this element is present, people can tap it to clear the text field's contents, without having to keep tapping the Delete key.

**Use images and buttons to provide clarity and functionality in text fields.** You can display custom images in both ends of a text field, or you can add a system-provided button, such as the Bookmarks button. In general, use the leading end of a text field to indicate a field's purpose and the trailing end to offer additional features, such as bookmarking.

### macOS

**Consider using a combo box if you need to pair text input with a list of choices.** For related guidance, see Combo boxes.

### watchOS

**Present a text field only when necessary.** Whenever possible, prefer displaying a list of options rather than requiring text entry.

## Native implementation

**Related**
- Text views
- Combo boxes
- Entering data

**Developer documentation**
- `TextField` — SwiftUI
- `SecureField` — SwiftUI
- `UITextField` — UIKit
- `NSTextField` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Text field vs. text view → `<input type="text">` vs. `<textarea>`.** Apple's split — small specific pieces of text versus larger passages — is the same split HTML already draws. The reasoning transfers directly: a single-line input communicates "short answer expected" the same way a compact text field does, and forcing a long answer into an `<input>` (via JavaScript auto-resize hacks) fights the same expectation Apple is describing, just on the web instead of native.

**Secure text field → `type="password"`, with one real gap.** `type="password"` masks input by default, matching `SecureField`. Where the platforms diverge: iOS and macOS give people a system-level, consistent way to reveal masked text (and offer to save it to a password manager) with guaranteed behavior; on the web, the reveal toggle is something you build yourself (a button that flips the `type` attribute between `password` and `text`), and if you skip it you've removed a capability iOS gives people for free. Always pair `type="password"` with `autocomplete="current-password"` or `autocomplete="new-password"` — this is the direct web analogue of the platform's built-in credential-manager integration, and skipping it is a bigger loss on the web than the equivalent omission would be natively, because there's no OS-level fallback to catch it.

**Placeholder text → the HTML `placeholder` attribute, but Apple's own caveat is stronger on the web than it sounds.** Apple already warns that placeholder text disappears once typing starts and recommends a separate persistent label for that reason. On the web this isn't just a usability nicety — a `placeholder` attribute is not a substitute for a `<label>` in any accessibility standard, has historically poor default contrast, and many screen readers announce it inconsistently or not at all depending on how the field is otherwise labeled. Treat Apple's "it can also be useful to include a separate label" as a hard requirement on the web, not an enhancement: every text input needs a real `<label>` (visually hidden if the design calls for placeholder-only appearance), with `placeholder` layered on top purely as a supplementary hint.

**Number formatter → `inputmode`, not `type="number"`.** This is a place the mapping genuinely breaks down if you reach for the obvious HTML5 type. `type="number"` adds a spinner UI most designs don't want, silently strips leading zeros and thousands separators, blocks locale-appropriate formatting like Apple warns about, and lets people type `e`, `+`, and `-` in ways that don't match "a string of digits." The closer match to Apple's number formatter — accept and *display* numeric data correctly per locale, without constraining the underlying input type — is a plain `<input type="text">` with `inputmode="numeric"` or `inputmode="decimal"` for soft-keyboard hinting, paired with your own formatting/validation logic (or the `Intl.NumberFormat` API) that respects the user's locale the way Apple explicitly warns you must.

**Validation timing → the `blur` vs. `input`/`change` distinction is the same judgment call Apple describes.** Apple's rule — validate email fields on field-switch, validate username/password before allowing field-switch — maps to choosing between the `blur` event (validate once focus leaves, non-blocking) and intercepting `blur` or `keydown` to conditionally prevent focus from moving (blocking, matches the "must happen before people switch fields" case). Pair either with `aria-invalid` and an `aria-describedby`-linked error message; the constraint validation API (`required`, `pattern`, `:invalid` styling) gives you some of this natively but its default error UI is inconsistent enough across browsers that most teams still hand-roll the messaging layer.

**Line-break handling (clip / wrap / truncate) → this is a text-input-value concern, not a display-only CSS concern, and the mapping is incomplete.** For single-line `<input>` elements, the value never wraps — visually clipping overflow text is the closest native behavior, and `text-overflow: ellipsis` combined with `overflow: hidden` and `white-space: nowrap` reproduces Apple's truncated-at-the-end case. But CSS truncation only ever cuts from the end; truncating at the beginning or middle the way Apple's macOS text fields can requires manual string manipulation in JavaScript, since there's no CSS equivalent. `<textarea>` wraps by default at the word level, matching Apple's word-wrap case; character-level wrapping needs `word-break: break-all` explicitly.

**Expansion tooltip for clipped text → the native `title` attribute is a weak substitute.** The browser's built-in `title` tooltip technically shows full text on hover, but it's slow to appear, not keyboard-accessible, and invisible on touch — none of which matches Apple's tooltip behavior. A custom tooltip component (shown on focus as well as hover, dismissible, and exposed via `aria-describedby`) is closer to what Apple describes, at the cost of building it yourself.

**Keyboard type selection → covered in depth under Virtual keyboards' web translation** (`inputmode`, `type`, and `autocomplete` together are the web equivalent of `UIKeyboardType` and `UITextContentType`).

**Focus order across fields → the DOM's default tab order already does this, matching Apple's "system attempts this automatically."** Source-order DOM markup produces a correct tab sequence without a `tabindex` on every field; reaching for explicit `tabindex` values to reorder fields is the web equivalent of overriding a behavior the platform already gets right, and is exactly the kind of customization Apple says you "won't need to do too often."

## Do / Don't

| Do | Don't |
|---|---|
| Use a text field for short, specific input | Use a text field for large passages of text — use a text view |
| Pair placeholder text with a separate persistent label | Rely on placeholder text alone to identify a field's purpose |
| Use a secure text field for passwords and sensitive data | Show sensitive input in plain text |
| Size the field to match anticipated text length | Use a uniform field size regardless of expected content |
| Space and align multiple fields consistently | Crowd fields together without clear label association |
| Validate at a moment appropriate to the field's context | Validate every field at the same trigger regardless of context |
| Show the keyboard type appropriate to the content (iOS, iPadOS, tvOS, visionOS) | Show the default keyboard for numeric, email, or URL entry |
| Minimize text entry on tvOS and watchOS | Require long-form typing on Apple TV or Apple Watch |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
