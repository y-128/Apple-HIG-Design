---
title: Entering data
url: https://developer.apple.com/design/human-interface-guidelines/entering-data
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-06-21
---

# Entering data

When you need information from people, design ways that make it easy for them to provide it without making mistakes.

## Core guidance

Entering information can be a tedious process regardless of the interaction methods people use. Improve the experience by pre-gathering as much information as possible to minimize the amount of data that people need to supply, and by supporting all available input methods so people can choose the method that works for them.

### Best practices

**Get information from the system whenever possible.** Don't ask people to enter information that you can gather automatically — such as from settings — or by getting their permission, such as their location or calendar information.

**Be clear about the data you need.** For example, you might display a prompt in a text field — like "username@company.com" — or provide an introductory label that describes the information, like "Email." You can also prefill fields with reasonable default values, which can minimize decision making and speed data entry.

**Use a secure text-entry field when appropriate.** If your app or game needs sensitive data, use a field that obscures people's input as they enter it, typically by displaying a small filled circle symbol for each character. For developer guidance, see `SecureField`. In tvOS, you can also configure a digit entry view to obscure the numerals people enter (for developer guidance, see `isSecureDigitEntry`). When you use the system-provided text field in visionOS, the system shows the entered data to the wearer, but not to anyone else; for example, a secure text field automatically blurs when people use AirPlay to stream their content.

**Never prepopulate a password field.** Always ask people to enter their password or use biometric or keychain authentication. For guidance, see Managing accounts.

**When possible, offer choices instead of requiring text entry.** It's usually easier and more efficient to choose from lists of options than to type information, even when a keyboard is conveniently available. When it makes sense, consider using a picker, menu, or other selection component to give people an easy way to provide the information you need.

**As much as possible, let people provide data by dragging and dropping it or by pasting it.** Supporting these interactions can ease data entry and make your experience feel more integrated with the rest of the system.

**Dynamically validate field values.** People can get frustrated when they have to go back and correct mistakes after filling out a lengthy form. When you verify values as soon as people enter them — and provide feedback as soon as you detect a problem — you give them the opportunity to correct errors right away. For numeric data in particular, consider using a number formatter, which automatically configures a text field to accept only numeric values. You can also configure a formatter to display the value in a specific way, such as with a certain number of decimal places, as a percentage, or as currency.

**When data entry is necessary, make sure people understand that they must provide the required data before they can proceed.** For example, if you include a Next or Continue button after a set of text fields, make the button available only after people enter the data you require.

## Platform considerations

No additional considerations for iOS, iPadOS, tvOS, visionOS, or watchOS.

### macOS

**Consider using an expansion tooltip to show the full version of clipped or truncated text in a field.** An expansion tooltip behaves like a regular tooltip, appearing when the pointer rests on top of a field. Apps running in macOS — including iOS and iPadOS apps running on a Mac — can use an expansion tooltip to help people view the complete data they entered when a text field is too small to display it. For guidance, see Offering help > macOS, visionOS.

## Native implementation

**Related**
- Text fields
- Virtual keyboards
- Keyboards

**Developer documentation**
- Input events — SwiftUI

**Key APIs**
- `SecureField` — obscured text-entry field
- `isSecureDigitEntry` — obscures numeral entry in a tvOS digit entry view

**Videos:** What's new in UIKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Get information from the system whenever possible" → autofill and autocomplete attributes.** Apple's rule against re-asking for data the system already has maps directly to the `autocomplete` attribute and correctly typed `input` elements. A field that isn't labeled `autocomplete="email"`, `"tel"`, `"street-address"`, and so on forces the browser's autofill to guess, which reproduces exactly the friction Apple is warning against — the difference is the web's equivalent of "asking the system" is declarative markup, not an API call.

**"Never prepopulate a password field" → don't set a `value` on password inputs, and don't fight the password manager.** The reasoning is the same on both platforms: a plausible-looking prefilled password invites people to trust and submit a value they didn't choose. On the web this extends further — `autocomplete="new-password"` versus `"current-password"` materially changes whether a browser's password manager offers to generate or fill a value, so getting that attribute wrong breaks the exact convenience Apple is describing.

**"Offer choices instead of requiring text entry" → prefer `select`, radio groups, and native pickers over free text.** The web has an advantage here Apple doesn't need to argue for: native form controls are cheap, accessible by default, and don't require a design decision each time. The failure mode to avoid is reimplementing a picker as a styled `div` that loses keyboard and screen-reader support a native `<select>` would have given for free.

**"Let people provide data by dragging and dropping it or by pasting it" → don't block the `paste` event, and support the Drag and Drop API on file and text inputs.** Apple frames this as making the experience feel integrated with the system; on the web, the equivalent failure is a form that silently swallows pasted content (common in over-eager input masking) or a file-upload zone that only accepts a click, not a dropped file. Supporting `ondrop` alongside a visible click target covers both interaction styles.

**"Dynamically validate field values" → the Constraint Validation API plus real-time feedback, not just `required`.** Apple's point is that catching an error at entry time is kinder than catching it at submit time. On the web this means validating on `input` or `blur` rather than waiting for form submission, and surfacing the message next to the field rather than in a alert dialog. A native `<input type="number">` or `type="email">` gets you partway there for free; anything more specific (a phone number format, a currency amount) needs explicit script-driven validation, same as Apple's number-formatter advice.

**"Make required data explicit before people can proceed" → disable (or clearly gate) the submit control, and mark required fields both visually and with `aria-required`.** The visual cue (an asterisk, a label) and the programmatic cue (`required` or `aria-required="true"`) need to agree, or assistive technology and sighted users get different information about the same form.

**Secure text-entry field → `input type="password"` is the floor, not the ceiling.** The browser gives you masked characters for free, which covers Apple's baseline. What the web doesn't give you automatically is Apple's visionOS behavior of hiding entered data from anyone but the person typing during screen sharing or streaming — there's no direct web equivalent, so an app that must guard against a shared screen or a projector needs its own masking logic beyond the input type.

## Do / Don't

| Do | Don't |
|---|---|
| Pull information from the system or settings when it's available | Ask people to re-enter information your app can already access |
| Use a prompt or label to describe the data a field needs | Leave a field's purpose ambiguous |
| Obscure sensitive input with a secure text field | Prepopulate a password field with a guessed or default value |
| Offer a picker, menu, or selection control when options are known | Require typing when a list of choices would do |
| Support drag-and-drop and paste into data-entry fields | Restrict entry to typing alone |
| Validate values as people enter them and surface errors immediately | Wait until submission to reveal every mistake at once |
| Disable Next or Continue until required data is present | Let people advance past incomplete required fields |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
