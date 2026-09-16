---
title: Sign in with Apple
url: https://developer.apple.com/design/human-interface-guidelines/sign-in-with-apple
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2022-09-14
---

# Sign in with Apple

Sign in with Apple provides a fast, private way to sign into apps and websites, giving people a consistent experience they can trust and the convenience of not having to remember multiple accounts and passwords.

## Core guidance

Supporting Sign in with Apple lets people use the Apple Account they already have to sign in or sign up, and skip filling out forms, verifying email addresses, and choosing passwords. In cases where you choose to ask for a name and email address, people have the option to share a unique, random email address that automatically relays messages to their personal email address. For developer guidance, see Authentication Services.

You can offer Sign in with Apple in every version of your app or website across all platforms — including non-Apple platforms.

Sign in with Apple makes it easy for people to authenticate with Face ID, Touch ID, or Optic ID and has two-factor authentication built in for an added layer of security. Apple doesn't use Sign in with Apple to profile people or their activity in apps.

### Offering Sign in with Apple

Follow these guidelines to offer Sign in with Apple when it's most convenient for people.

**Ask people to sign in only in exchange for value.** People need to understand why you're asking them to sign in, so it can work well to display a brief, approachable description of sign-in benefits. For example, you might want to tell people that signing in lets them personalize the app experience, access additional features, or synchronize data.

**Delay sign-in as long as possible.** People often abandon apps when they're forced to sign in before doing anything useful. Give them a chance to familiarize themselves with your app before making a commitment. For example, a live-streaming app could let people explore available content before signing in to stream something.

**If you require an account, ask people to set it up before offering any sign-in options.** Start by explaining the reasons for requiring an account. Then, after people complete account setup, let them choose a convenient way to sign in to their new account by offering Sign in with Apple and any other sign-in methods you support.

**Consider letting people link an existing account to Sign in with Apple.** When you support this type of linking, people can get the convenience of using Sign in with Apple while maintaining access to the information in an account they've already set up. You can offer account linking before or after people sign in to their existing account. For example:

- If people share an email address through Sign in with Apple and it matches the address in an existing account, you can suggest that they link Sign in with Apple to that account.
- If people used an existing user name and password to sign in, you can display an account-linking suggestion in their account's settings view or another logical place.

**In a commerce app, wait until after people make a purchase before asking them to create an account.** If you support a guest checkout system, give people a quick way to create an account after the transaction completes. For example, if you support Apple Pay, let people create an account on the order confirmation page. In cases where people have already provided their name and email address during the Apple Pay transaction, you don't need to ask for this information.

**As soon as Sign in with Apple completes, welcome people to their new account.** Help people use their new account right away; don't delay the experience by asking for information that isn't required.

**Indicate when people are currently signed in.** You can help people confirm their sign-in method by displaying a phrase like "Using Sign in with Apple" in places like a settings or account interface.

### Collecting data

People appreciate Sign in with Apple for its privacy and convenience. Although some apps or websites may require additional information — such as a date of birth or a region of residence — it's essential to minimize your requests for data as people set up an account. Build on the trust that people have in Sign in with Apple by describing why you need additional data and clearly displaying the data you receive.

**Clarify whether the additional data you request is required or just recommended.** If the data is legally or contractually required — such as an agreement to terms of service, country or region of residence, birth date, or information required by a region's real-identity laws — make sure people understand that they must supply the additional information to complete the setup of their account. If additional data isn't required but can improve the user experience, make sure people know the request is optional and help them understand the benefits of providing the information.

**Don't ask people to supply a password.** A key benefit of Sign in with Apple is that people don't have to create and memorize additional passwords. Unless people have stopped using Sign in with Apple with your app or website, don't ask for a password.

**Avoid asking for a personal email address when people supply a private relay address.** Using Sign in with Apple, people can choose to share a private relay address that automatically forwards messages to their verified personal email account. It's essential to respect this choice and avoid overriding it by asking for a personal email address. If you present customer service, retail, or other experiences that request identification via email address, you can:

- Make sure that people can view their private relay address in your app or website.
- Direct people to Settings > Apple Account > Password & Security > Apps using Apple Account to retrieve their private relay address.
- Use other identifying values, like an order number or phone number collected as part of a purchase.

**Give people a chance to engage with your app before asking for optional data.** As people use your app, you can help them discover places where they can benefit from sharing more information with you. For example, you might suggest that they provide a contact phone number if they want real-time text updates, or social network information if they want to play games with friends. If people choose not to provide optional information, don't prevent them from accessing their account or using all the features of your app.

**Be transparent about the data you collect.** People value knowing how you use the data that they share with you. One way you can be transparent is to welcome people by using the name or email address they shared. Doing this helps establish how you use this information and, for a relay address, shows people where to find it in the future. If you don't display all the data that people provide, they are likely to wonder why you asked for it.

### Displaying buttons

Apple provides several Sign in with Apple buttons you can use to let people set up an account and sign in. If necessary, you can create a custom button to offer Sign in with Apple.

**Prominently display a Sign in with Apple button.** Make a Sign in with Apple button no smaller than other sign-in buttons, and avoid making people scroll to see the button.

#### Using the system-provided buttons

When you use the system-provided APIs to create a Sign in with Apple button, you get the following advantages:

- A button that's guaranteed to use an Apple-approved appearance.
- Assurance that the button's contents maintain ideal proportions as you change its style.
- Automatic translation of the button's title into the language specified by the device.
- Support for configuring the button's corner radius to match the style of your UI (iOS, macOS, and web).
- A system-provided alternative text label that lets VoiceOver describe the button.

For developer guidance, see `ASAuthorizationAppleIDButton` (iOS, macOS, and tvOS), `WKInterfaceAuthorizationAppleIDButton` (watchOS), and Displaying Sign in with Apple buttons on the web. You can also visit the Sign in with Apple button page to view and adjust live previews of web-based buttons and get the code.

The system provides several variants of the button title. Depending on the platform on which your content runs, choose the variant that fits the terminology of your sign-in experience and use it consistently throughout your interfaces.

The button titles Sign in with Apple, Sign up with Apple, and Continue with Apple are available for iOS, macOS, tvOS, and the web. For watchOS, the system provides one title: Sign in.

Depending on the platform, the system provides up to three options for the appearance of the Sign in with Apple button: white, white with an outline, and black. Choose the appearance that works best with the background on which the button displays.

**White.** The white style is available on all platforms and the web. Use this style on dark backgrounds that provide sufficient contrast.

**White with outline.** The white outlined style is available in iOS, macOS, and the web. Use this style on white or light-color backgrounds that don't provide sufficient contrast with the white button fill. Avoid using this style on a dark or saturated background, because the black outline can add visual clutter; instead, use the white style to contrast with a dark background.

**Black.** The black style is available on all platforms and the web. Use this style on white or light-color backgrounds that provide sufficient contrast; don't use it on black or dark backgrounds.

Unlike the black Sign in with Apple button for other platforms, the watchOS button uses a fill color that's not fully black. To contrast with the pure black background of Apple Watch, the watchOS button uses the system-defined dark gray appearance.

#### Button size and corner radius

**Adjust the corner radius to match the appearance of other buttons in your app.** By default, the Sign in with Apple button has rounded corners. In iOS, macOS, and the web, you can change the corner radius to produce a button with square corners or a capsule-shape button. For developer guidance, see `cornerRadius` (iOS and macOS) and Displaying Sign in with Apple buttons on the web.

**Maintain the minimum button size and margin around the button in iOS, macOS, and the web.** Be mindful that the button title may vary in length depending on the locale.

| Minimum width | Minimum height | Minimum margin |
|---|---|---|
| 140 pt (140 px @1x, 280 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |

#### Creating a custom Sign in with Apple button

If your interface requires it, you can create a custom Sign in with Apple button for iOS, macOS, or the web. For example, you may want to align logos across multiple sign-in buttons, use buttons that display only a logo, or adjust the button's font, bezel, or background appearance to coordinate with your UI.

**Always make sure that people can instantly identify your custom button as a Sign in with Apple button.** If your custom button differs too much from the standard one, people may not feel comfortable using it to set up an account or sign in.

> **Note (Apple):** App Review evaluates all custom Sign in with Apple buttons.

Apple Design Resources provides downloadable Apple logo artwork you can use to create custom Sign in with Apple buttons that display either a logo only or a logo and text. The logo files are available in PNG, SVG, and PDF formats, and the artwork for both types of buttons includes both black and white versions.

All downloadable logo files include padding that simplifies positioning the logo in a button. Logo-only logo files include horizontal and vertical padding that ensures the correct proportion of the logo relative to the button. In addition to padding that keeps the logo and button correctly proportioned, logo files for buttons with text also include horizontal padding that provides a minimum margin between the logo and the button's leading edge and title.

**Use only the logo artwork downloaded from Apple Design Resources; never create a custom Apple logo.** As you create a custom Sign in with Apple button, follow these guidelines for using the downloadable logo file:

- Use the logo file to position the Apple logo in a button; never use the Apple logo as a button.
- Match the height of the logo file to the height of the button.
- Don't crop the logo file.
- Don't add vertical padding.

**To make sure that your custom button is visually consistent with the system-provided Sign in with Apple button, don't change the following attributes:**

- **Titles.** Use only Sign in with Apple, Sign up with Apple, or Continue with Apple.
- **General shape.** Buttons that combine the logo with text are always rectangular; logo-only buttons can be circular or rectangular.
- **Logo and title colors.** Within a button, both items must be either black or white; don't use custom colors.

**To coordinate with your app design, you can change:**

- **Title font.** You can also adjust the font's weight and size.
- **Title case.** You can capitalize every letter in the title.
- **Background appearance.** The overall color needs to remain black or white. If necessary, you can include a subtle texture or gradient to help the button harmonize with your interface.
- **Button corner radius.** You can use a corner radius value that matches the other buttons in your UI.
- **Button bezel and shadow.** For example, you can use a stroke to emphasize the button bezel or add a drop shadow.

#### Custom buttons with a logo and text

Choose the format of the logo file based on the height of your button. Because SVG and PDF are vector-based formats, you can use these files in buttons of any height. Use the PNG files only in buttons that are 44 points tall, which is the default (and recommended) button height in iOS. Logos are available in small, medium, and large sizes, so you can match logo sizes in all the sign-up buttons you display.

**Prefer the system font for the title** — that is, Sign in with Apple, Sign up with Apple, or Continue with Apple. Regardless of the font you choose, the title and button height of your custom button need to use the same proportions that the system uses. Using the system font as an example, the title's font size would be 43% of the button's height — in other words, the button's height would be 233% of the title's font size, rounded to the nearest integer.

**In general, preserve the capitalization style of the title.** By default, all variants of the button title capitalize the first word — that is, Sign or Continue — and Apple; all other letters are lowercase. Avoid changing this style unless your interface uses only uppercase.

**Keep the title and logo vertically aligned within the button.** To do this, vertically align the title to the middle of the button, then add the logo image, making sure its height matches the height of the button. Because the logo image includes top and bottom padding, vertically aligning the title in the button ensures that the title, the logo, and the button stay properly aligned.

**Inset the logo if necessary.** If you need to horizontally align the Apple logo with other authentication logos, you can adjust the space between the logo and the button's leading edge.

**Maintain a minimum margin between the title and the right edge of the button.** Ensure the margin measures at least 8% of the button's width.

**Maintain the minimum button size and margin around the button.** Be mindful that the button title may vary in length depending on the locale.

| Minimum width | Minimum height | Minimum margin |
|---|---|---|
| 140 pt (140 px @1x, 280 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |

#### Custom logo-only buttons

Choose the format of the logo file based on the size of your button. The downloadable artwork for logo-only buttons is available in SVG, PDF, and PNG formats. Use the vector-based SVG and PDF formats for buttons of any size; use the PNG format only in buttons that measure 44x44 pt.

**Don't add horizontal padding to a logo-only image.** A logo-only Sign in with Apple button always has a 1:1 aspect ratio, and the artwork already includes the correct padding on all sides.

**Use a mask to change the default square shape of the logo-only image.** For example, you might want to use a circular or rounded rectangular shape to present all logo-only sign-in buttons. Never crop the Apple-provided artwork to decrease its built-in padding or use the logo by itself, and avoid including additional padding. Apple shows examples of a rounded rectangle mask, no mask, and a circular mask as acceptable treatments.

**Maintain a minimum margin around the button.** Ensure the margin measures at least 1/10 of the button's height.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

## Specifications

### System-provided button sizing

| Property | Value |
|---|---|
| Minimum width | 140 pt (140 px @1x, 280 px @2x) |
| Minimum height | 30 pt (30 px @1x, 60 px @2x) |
| Minimum margin | 1/10 of the button's height |
| Default recommended button height (iOS) | 44 pt |
| Title font size (system font) | 43% of button height |
| Button height relative to title font size | 233% of title font size, rounded to the nearest integer |
| Minimum margin between title and right edge | 8% of button's width |
| Logo-only button aspect ratio | 1:1 |
| Logo-only button minimum margin | 1/10 of button's height |

> **Source limitation:** the source PDF references several illustrations that don't render as text — the button-title variant list, the black/white/outline appearance swatches, the corner-radius range diagram, and the proportion diagrams for custom buttons. The specification values above (sizes, margins, ratios) are captured in the source text and reproduced in full; the visual examples themselves are not reproducible here.

## Native implementation

**Related**
- Sign in with Apple button (live preview and code generator for web buttons)

**Developer documentation**
- Authentication Services
- Displaying Sign in with Apple buttons on the web — Sign in with Apple

**Key APIs**
- `ASAuthorizationAppleIDButton` — system-provided button for iOS, macOS, and tvOS
- `WKInterfaceAuthorizationAppleIDButton` — system-provided button for watchOS
- `cornerRadius` — adjusts corner radius on iOS and macOS buttons

**Videos:** Move beyond passwords · Simplify sign in for your tvOS apps · Introducing Sign In with Apple

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance beyond the button-display page it links to. The mappings below extend the same principles to general web authentication design; they are inference, not Apple policy.

**Sign in with Apple JS is the actual web surface, and it is closer to native than most "sign in with X" web SDKs.** Apple ships a real JavaScript library (`AppleIDSignInOnSuccess` / `AppleIDSignInOnFailure` event handlers, a REST token endpoint) plus the button-generator page the source explicitly links to. This isn't a stretched analogy — Apple designs for the web here, so the button-appearance rules (white / white-outline / black, minimum size, corner-radius range) apply on the web exactly as documented, not as an inference.

**"Ask only in exchange for value" and "delay sign-in" → this is the core anti-pattern the web has been fighting under other names.** The HIG's guidance to defer authentication until a person has experienced enough value to want an account maps directly onto the web usability principle against forced early registration. Nothing about the reasoning is platform-specific: an unmotivated sign-in wall increases abandonment on a website exactly as it does in an app. Where the platforms differ is enforcement — Apple's App Review can reject an app for violating this; no equivalent gate exists for a website.

**The private relay email is where the web genuinely has less than Apple gives you.** Sign in with Apple's relay address is backed by Apple's mail infrastructure and is revocable per-app from the person's Apple Account settings — a website receiving that address has no way to know, at signup time, whether it's real or relayed, and must simply treat it as an opaque, working email address like any other. The rule "don't ask for a personal email when they gave you a relay one" transfers as a UX principle (don't second-guess the identity value a login provider hands you), but the technical guarantee behind it — Apple silently forwarding mail — is not something a generic web OAuth flow can replicate; it is unique to Sign in with Apple regardless of surface.

**Button branding rules map without modification because they're really trademark and App Review rules, not platform rules.** The forbidden and permitted attributes — never recolor the logo or title away from black/white, never crop the logo artwork, only the three approved title strings, minimum size and margin — apply identically whether the button renders in a native view or a `<div>` on a webpage. A web team implementing a custom Sign in with Apple button is bound by the exact same "always make sure people can instantly identify it" requirement as an iOS team, and Apple's own web button-generator tool exists specifically so web developers don't have to hand-roll compliance.

**Where this reasons into WebAuthn / passkeys: the underlying trust model, not the specific rules.** Sign in with Apple's appeal — Face ID/Touch ID/Optic ID-backed authentication, no password to create or leak, built-in two-factor — is the same value proposition WebAuthn and platform passkeys offer natively in a browser without routing through any particular vendor's SDK. If a web team's actual goal is "the account-security benefits Sign in with Apple gives native apps," a first-party passkey flow using the WebAuthn API achieves the same properties without a third-party identity provider in the loop. Sign in with Apple JS and WebAuthn passkeys are not the same mechanism, but they answer the same underlying user need — memorize nothing, prove identity locally — and a web team should decide between "add Apple as a federated login option" and "add first-party passkey login" based on that need, not assume one subsumes the other.

**"Indicate when people are currently signed in" has no platform-specific translation — it's just good account-UI practice, web or native.** Displaying "Using Sign in with Apple" in a settings screen is exactly the kind of session-source transparency any web account page should already provide regardless of the identity provider used.

## Do / Don't

| Do | Don't |
|---|---|
| Offer Sign in with Apple across every version of your app or website, including non-Apple platforms | Require sign-in before people have experienced any value in your app |
| Ask for a password only if someone has stopped using Sign in with Apple | Ask people to supply a password when they use Sign in with Apple |
| Respect a private relay address people share | Ask for a personal email address when someone has already shared a relay address |
| Use the system-provided button APIs whenever possible | Recreate the Apple logo or use it as a standalone button |
| Keep custom buttons instantly identifiable as Sign in with Apple | Change the logo or title color away from black/white on a custom button |
| Use only "Sign in with Apple," "Sign up with Apple," or "Continue with Apple" as titles | Invent alternate button titles |
| Match the minimum size and margin values for custom buttons | Crop the downloaded logo artwork or add extra padding to it |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
