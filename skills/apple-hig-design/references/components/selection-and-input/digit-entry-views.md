---
title: Digit entry views
url: https://developer.apple.com/design/human-interface-guidelines/digit-entry-views
platforms: [tvOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Digit entry views

A digit entry view fills the entire screen and prompts people to enter a series of digits, like a PIN, using a digit-specific keyboard.

## Core guidance

You can add an optional title and prompt above the line of digits.

### Best practices

**Use secure digit fields.** Secure digit fields display asterisks instead of the entered digit onscreen. Always use a secure digit field when your app asks for sensitive data.

**Clearly state the purpose of the digit entry view.** Use a title and prompt that explains why someone needs to enter digits.

## Platform considerations

Not supported in iOS, iPadOS, macOS, visionOS, or watchOS.

## Native implementation

**Related**
- Virtual keyboards

**Developer documentation**
- `TVDigitEntryViewController` — TVUIKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**This is a platform-specific, full-screen TV input pattern with no direct web analogue.** A digit entry view exists because tvOS input happens through a remote, not a keyboard: filling the whole screen with a single, unambiguous digit-specific keypad is a concession to that input method, not a general UI pattern. Nothing about a browser tab or a responsive layout calls for the same full-screen takeover, so porting the visual form of a digit entry view to the web would be copying the shape without the reason.

**The one principle that does transfer: secure digit fields.** Apple's instruction to mask entered digits with asterisks for sensitive data (PINs, codes) maps directly to the web's `<input type="password" inputmode="numeric" pattern="[0-9]*">`, which masks each character as it's typed and requests the numeric keypad on mobile. The `inputmode="numeric"` attribute is the web's equivalent of the "digit-specific keyboard" Apple describes: it asks the browser for a numeric input surface without changing the underlying value's type, the same way tvOS's digit keyboard is a numeric-only entry surface layered on top of a text value.

**"Clearly state the purpose" also transfers as a general form-design principle.** Any digit-only field, PIN, verification code, PIN-style confirmation, should be introduced by a visible label or prompt explaining why the digits are being collected, independent of platform. This is standard form-labeling practice on the web, not something specific to the tvOS pattern.

**Where segmented digit-box UIs (one box per digit) are popular on the web, treat them as a UX choice, not a platform requirement.** Nothing in Apple's guidance for this tvOS-only component recommends or implies a segmented-box pattern; that pattern is a common web/mobile convention for one-time codes, evaluated on its own accessibility merits (a single masked numeric input is usually easier for screen readers and password managers than several small boxes glued together with JavaScript).

## Do / Don't

| Do | Don't |
|---|---|
| Mask entered digits for sensitive data like PINs | Display entered PIN digits in plain text |
| Explain why digits are being requested with a title or prompt | Present a bare digit field with no stated purpose |
| Request a numeric-specific input surface for digit-only fields | Force a full alphanumeric keyboard for a PIN entry |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
