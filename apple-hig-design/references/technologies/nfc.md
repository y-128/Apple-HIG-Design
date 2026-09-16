---
title: NFC
url: https://developer.apple.com/design/human-interface-guidelines/nfc
platforms: [iOS, iPadOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# NFC

Near-field communication (NFC) allows devices within a few centimeters of each other to exchange information wirelessly.

## Core guidance

iOS apps running on supported devices can use NFC scanning to read data from electronic tags attached to real-world objects. For example, a person can scan a toy to connect it with a video game, a shopper can scan an in-store sign to access coupons, or a retail employee can scan products to track inventory.

### In-app tag reading

An app can support single- or multiple-object scanning when the app is active, and display a scanning sheet whenever people are about to scan something.

**Don't encourage people to make contact with physical objects.** To scan a tag, an iOS device must simply be within close proximity of the tag. It doesn't need to actually touch the tag. Use terms like *scan* and *hold near* instead of *tap* and *touch* when asking people to scan objects.

**Use approachable terminology.** Near-field communication may be unfamiliar to some people. To make it approachable, avoid referring to technical, developer-oriented terms like NFC, Core NFC, Near-field communication, and tag. Instead, use friendly, conversational terms that most people will understand.

| Use | Don't use |
|---|---|
| Scan the [object name]. | Scan the NFC tag. |
| Hold your iPhone near the [object name] to learn more about it. | To use NFC scanning, tap your phone to the [object]. |

**Provide succinct instructional text for the scanning sheet.** Provide a complete sentence, in sentence case, with ending punctuation. Identify the object to scan, and revise the text appropriately for subsequent scans. Keep the text short to avoid truncation.

| First scan | Subsequent scans |
|---|---|
| Hold your iPhone near the [object name] to learn more about it. | Now hold your iPhone near another [object name]. |

### Background tag reading

Background tag reading lets people scan tags quickly any time, without needing to first open your app and initiate scanning. On devices that support background tag reading, the system automatically looks for nearby compatible tags whenever the screen is illuminated. After detecting and matching a tag with an app, the system shows a notification that the people can tap to send the tag data to the app for processing.

Note that background reading isn't available when an NFC scanning sheet is visible, Wallet or Apple Pay are in use, cameras are in use, the device is in Airplane Mode, and the device is locked after a restart.

**Support both background and in-app tag reading.** Your app must still provide an in-app way to scan tags, for people with devices that don't support background tag reading.

## Platform considerations

No additional considerations for iOS or iPadOS. Not supported in macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Developer documentation**
- Core NFC

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

NFC has a real but narrow web analogue: the **Web NFC API**, which lets a page read and write NFC tags through `NDEFReader`. It is not a general substitute for Core NFC. Web NFC ships only in Chromium-based browsers on Android, requires a secure (HTTPS) context and a user gesture to start a scan, and is not implemented in Safari on any platform — so the one device family this whole HIG page is written for (iPhone, iPadOS) has no Web NFC support at all, and no other browser engine (Firefox, non-Chromium Edge) has shipped it either. Any web-based NFC feature is consequently Android-Chrome-only in practice, which is a materially smaller reach than Core NFC's iOS/iPadOS coverage.

Where the platforms do overlap — a Chromium/Android page actually running Web NFC — Apple's terminology reasoning transfers directly, because it isn't really about NFC, it's about not making users learn acronyms to complete a task. **"Don't encourage contact with physical objects"** and **"use approachable terminology"** apply exactly as written: prompt text should say "hold your phone near the tag," not "tap to scan the NFC chip," regardless of which OS or browser is reading the tag. **"Provide succinct instructional text, in sentence case, with ending punctuation, revised for subsequent scans"** is a general prompt-writing rule that a Web NFC-based scanning flow should follow the same way a native app does.

**Background tag reading has no web equivalent and cannot have one.** It depends on the OS scanning for tags continuously whenever the screen is on, independent of any app being open or a page being loaded — a capability that requires system-level access no browser exposes or plausibly ever will, since it would mean a page (or a background service) getting hardware access without any active user session. Every Web NFC scan must be explicitly started by an in-page user gesture while that page is open; there is no background-reading counterpart to design for.

## Do / Don't

| Do | Don't |
|---|---|
| Ask people to scan or hold near an object | Ask people to tap or touch an object to scan it |
| Use friendly, conversational terms for the object being scanned | Expose technical terms like NFC, Core NFC, or tag in your UI text |
| Write scanning-sheet instructions as a complete sentence in sentence case with ending punctuation | Leave scanning-sheet text long enough to risk truncation |
| Revise instructional text for subsequent scans | Repeat the exact first-scan text for every subsequent scan |
| Support in-app scanning even when background tag reading is available | Rely on background tag reading alone and drop in-app scanning |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
