---
title: ID Verifier
url: https://developer.apple.com/design/human-interface-guidelines/id-verifier
platforms: [iOS]
last_updated: 2023-09-12
---

# ID Verifier

ID Verifier lets your iPhone app read mobile IDs in person without requiring external hardware.

## Core guidance

Beginning in iOS 17, you can integrate ID Verifier into your app, letting iPhone read ISO18013-5 compliant mobile IDs and helping you support in-person ID verification. For example, personnel at a concert venue can use your app on iPhone to verify customers' ages.

Using ID Verifier has advantages for both customers and organizations.

- Customers only present the minimum data needed to prove their age or identity, without handing over their ID card or showing their device.
- Apple provides the key components of the certificate issuance, management, and validation process, simplifying app development and enabling a consistent and trusted ID verification experience.

Depending on the needs of your app, you can use ID Verifier to make the following types of requests:

**Display Only request.** Use a Display Only request to display data — such as a person's name or age alongside their photo portrait — within system-provided UI on the requester's iPhone, so the requester can visually confirm the person's identity. When you make a Display Only request, the customer's data remains within the system-provided UI and isn't transmitted to your app. For developer guidance, see `MobileDriversLicenseDisplayRequest`.

**Data Transfer request.** Use a Data Transfer request only when you have a legal verification requirement and you need to store or process information like a person's address or date of birth. You must request an additional entitlement to make a Data Transfer request. To learn more, see Get started with ID Verifier; for developer guidance, see `MobileDriversLicenseDataRequest` and `MobileDriversLicenseRawDataRequest`.

### Best practices

**Ask only for the data you need.** People may lose trust in the experience if you ask for more data than you need to complete the current verification. For example, if you need to ensure that a customer is at least a minimum age, use a request that specifies an age threshold; avoid requesting the customer's current age or birth date. For developer guidance, see `ageAtLeast(_:)`.

**If your app qualifies for Apple Business Register, register for ID Verifier** to ensure that people can view essential information about your organization when you make a request. Registering for ID Verifier with Apple Business Register lets you provide your official organization name and logo for the system to display on customers' devices as part of the ID verification UI. To learn if your app qualifies and how to register, see Apple Business Register.

**Provide a button that initiates the verification process.** Use a label like *Verify Age* in a button that performs a simple age check or *Verify Identity* for a more detailed identity data request. **Avoid including a symbol that specifies a particular type of communication**, like NFC or QR codes. **Never include the Apple logo in any button label.**

| Button type | Example usage |
|---|---|
| Verify Age | An app that checks whether people are old enough to attend an event or access a venue, like a concert hall. |
| Verify Identity | An app that verifies whether specific identity information matches expected values, such as name and birth date when picking up a rental car. |

> **Source limitation:** the source PDF's "Button type" column rendered as empty for both rows — only the "Example usage" text was captured. The button labels shown above (*Verify Age*, *Verify Identity*) are reconstructed from the immediately preceding body text, which names exactly these two labels for exactly these two use cases, so the row-to-label pairing follows the source's own ordering rather than being invented.

**In a Display Only request, help the person using your app provide feedback on the visual confirmation they perform.** For example, when the reader displays the customer's portrait, you might provide buttons labeled *Matches Person* and *Doesn't Match Person* so your app can receive an approved or rejected value as part of the response.

## Platform considerations

No additional considerations for iOS. Not supported in iPadOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Apple Business Register
- IDs in Wallet
- Identity verification

**Developer documentation**
- Adopting the Verifier API in your iPhone app — ProximityReader

**Key APIs**
- `MobileDriversLicenseDisplayRequest` — makes a Display Only request; customer data stays in system UI and is never transmitted to your app
- `MobileDriversLicenseDataRequest` / `MobileDriversLicenseRawDataRequest` — make a Data Transfer request; requires an additional entitlement
- `ageAtLeast(_:)` — request an age threshold instead of a birth date or current age

**Videos:** What's new in Wallet and Apple Pay

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

ID Verifier has no web analogue and none is plausible. It depends on ISO 18013-5's proximity protocol (a Bluetooth Low Energy / NFC session between two devices, cryptographically authenticated against issuer-signed credentials), on iPhone-specific secure hardware to hold and present that session, and on Apple's own certificate issuance and validation infrastructure sitting between the requester and the credential. No browser API reaches into device-to-device BLE/NFC credential exchange, and no web standard defines an equivalent trust chain for mobile driver's licenses. A web page cannot originate this kind of request, cannot receive the response, and has no substitute protocol to fall back to — this is squarely platform- and hardware-bound.

The one piece of reasoning that generalizes, and is worth carrying into any web verification flow, is the minimum-disclosure principle stated in "ask only for the data you need": request a yes/no age threshold rather than a birth date, request a match/no-match rather than a full identity record, whenever the underlying question is binary. That's a privacy-by-design argument independent of ID Verifier's mechanics, and it applies equally to a web form that only needs to confirm someone is over 18 — such a form should ask for confirmation of a threshold, not collect and store a birth date it doesn't need. Likewise, "never include the Apple logo in a button label" generalizes to a rule against a page implying platform or vendor endorsement it doesn't have: a web verification button shouldn't borrow a third-party brand mark to appear more trustworthy than the underlying check actually is.

Everything else here — the Display Only vs. Data Transfer request types, the entitlement gate, Apple Business Register, the system-provided confirmation UI — is specific to ID Verifier's device-to-device protocol and does not translate to a client-server web request.

## Do / Don't

| Do | Don't |
|---|---|
| Request only the minimum data needed, such as an age threshold | Request a full birth date or current age when a yes/no check would do |
| Register for Apple Business Register if your app qualifies | Leave your organization unidentified in the verification UI |
| Label the verification button with a plain action, like Verify Age or Verify Identity | Include a symbol naming the underlying communication method, like NFC or QR |
| — | Include the Apple logo in any button label |
| Let people confirm a Display Only visual match with clear Matches / Doesn't Match feedback | Leave people with no way to record the outcome of a visual identity check |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
