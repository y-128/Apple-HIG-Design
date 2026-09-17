---
title: Apple Pay
url: https://developer.apple.com/design/human-interface-guidelines/apple-pay
platforms: [iOS, iPadOS, macOS, visionOS, watchOS, Web]
last_updated: 2026-06-08
---

# Apple Pay

Apple Pay is a secure, easy way to make payments for physical goods and services, donations, and subscriptions in apps and in any browser.

## Core guidance

Use Apple Pay to sell physical goods like groceries, clothing, and appliances; for services such as club memberships, hotel reservations, and event tickets; and for donations. Apps and websites that accept Apple Pay display it as an available payment option and include an Apple Pay button in the purchasing flow that people use to bring up a payment sheet.

During checkout, the payment sheet can show the credit or debit card linked to Apple Pay, purchase amount (including tax and fees), shipping options, contact information, and other relevant details. People make any necessary adjustments and then authorize payment and complete the purchase using credentials stored securely on the device.

People pay using Face ID, Touch ID, or Optic ID on supported devices, or by double-clicking on Apple Watch. In browsers, they can also pay using a nearby iPhone or Apple Watch, or by scanning a code with an iPhone or iPad.

For developer guidance, see Apple Pay and Apple Pay on the Web. For a hands-on demo of Apple Pay on the web, see the Apple Pay on the web interactive demo.

> **Note (Apple):** Use In-app purchase to sell virtual goods in your app, such as premium content, and subscriptions for digital content.

### Offering Apple Pay

**Offer Apple Pay on all devices and browsers that support it.** If the device doesn't support Apple Pay, don't present Apple Pay as a payment option. For developer guidance, see `PKPaymentAuthorizationController` (iOS, watchOS) and `applePayCapabilities` (web).

**Make Apple Pay the primary payment option when credentials are available.** If you use Apple Pay APIs to find out whether someone has an active card in Wallet, you must make Apple Pay the primary — but not necessarily sole — payment option everywhere you use the APIs. Don't separate Apple Pay into a different step or flow. For example, you might pre-select Apple Pay when displaying it alongside other options. For developer guidance, see "Offering Apple Pay in Your App" (iOS, watchOS) and "Checking for Apple Pay availability" (web).

**Use Apple Pay buttons only to initiate payment or, when appropriate, the Apple Pay setup process.** When people choose an Apple Pay button to make a purchase, but their device doesn't have Apple Pay set up, they're given the opportunity to set up Apple Pay. Don't use Apple Pay buttons in any other way.

**If you use a custom button to start the Apple Pay payment process, make sure your custom button doesn't display "Apple Pay" or the Apple Pay logo.** In this scenario, you must let people know that you accept Apple Pay by displaying the Apple Pay mark graphic or referencing Apple Pay in text on the same page that displays your payment button.

**Use the Apple Pay mark graphic only to communicate that you accept Apple Pay.** The Apple Pay mark doesn't facilitate payment. Never use it as a payment button or position it as a button. When using the Apple Pay mark to indicate Apple Pay as the selected payment method, you can create a separate custom button that matches your app or website design to initiate the Apple Pay payment.

**Don't hide an Apple Pay button or make it appear unavailable.** If an Apple Pay button can't be used yet, such as when a product size or color hasn't been selected, gracefully point out the problem after someone taps or clicks the button.

**Inform search engines that Apple Pay is accepted on your website.** If your website uses semantic markup to provide product details to search engines, list Apple Pay as a payment option.

> **Important (Apple):** All websites that offer Apple Pay must include a privacy statement and adhere to the Acceptable Use Guidelines for Apple Pay on the web.

### Streamlining checkout

**Provide a cohesive checkout experience.** It's best when the entire checkout flow feels tightly integrated with your app or website. Use your branding throughout the checkout experience and avoid opening different pages or windows. For website checkout flows in particular, opening new windows during the process can cause confusion and may even lead people to think they've been handed off to a different website.

**If Apple Pay is available, assume people want to use it.** Consider presenting the Apple Pay button as the first payment option, displaying it larger than other options, or using a line to visually separate it from other choices.

**Accelerate single-item purchases with Apple Pay buttons on product detail pages.** In addition to a shopping cart, consider offering Apple Pay buttons on product detail pages so people can purchase an individual item quickly. Purchases initiated in this way need to be for an individual item only, excluding any items already in the cart. If the cart contains the purchased item, remove the item from the cart once the purchase is complete.

**Accelerate multi-item purchases with express checkout.** An express checkout feature immediately shows the payment sheet and lets someone purchase everything in their cart quickly using a single shipping method and destination.

**Support coupons and promotional codes in the payment sheet.** If you offer a coupon or promotional code, let people enter it directly on the payment sheet rather than requiring a separate step. This is especially important for express checkout flows, where people bypass the standard checkout experience.

**Collect necessary information, like color and size options, before people reach the Apple Pay button.** When information is missing at checkout time — perhaps because someone forgot to choose an option — gracefully point out the problem and help them correct it. Use highlighting or warning text to identify missing information, and automatically navigate to the problematic field so people can correct it quickly and complete their purchase.

**Collect optional information before checkout begins.** There's no way to input optional data — like gift messages or delivery instructions — on the payment sheet, so collect this information ahead of time or even after the purchase is complete.

**Gather multiple shipping methods and destinations before showing the payment sheet.** The payment sheet lets people select a single shipping method and destination for an entire order. If people can choose different shipping methods and destinations for individual items in an order, collect those details before Apple Pay checkout.

**For in-store pickup, help people choose a pickup location before displaying the payment sheet.** After someone chooses a pickup location, show the location's address on the payment sheet. For developer guidance, see "Displaying a Read-Only Pickup Address."

**Prefer checkout information from Apple Pay.** Assume that Apple Pay information is complete and up to date. Even if your app or website has existing contact, shipping, and payment information, consider fetching the latest from Apple Pay during checkout to reduce potential corrections.

**Avoid requiring account creation before purchase.** If you want people to register for an account, ask them to do so on the order confirmation page. Prepopulate as many registration fields as possible using information provided during checkout.

**Report transaction results in the payment sheet.** In failure cases, such as a bad address, provide error messages so people can take steps to fix the problem.

**Display an order confirmation or thank-you page.** After the payment sheet shows the result of the transaction, display an order confirmation page to thank people for their purchase, provide details about when the order will ship, and indicate how to check its status. Listing Apple Pay on the confirmation page isn't necessary, but if you do, show it after the last four digits of the account used to process the transaction or as a separate note — for example, "1234 (Apple Pay)" or "Paid with Apple Pay."

#### Customizing the payment sheet

**Only present and request essential information.** People may get confused or have privacy concerns if the payment sheet includes extraneous information. For example, it makes sense to see a contact email address but not a shipping address if the purchase is a gift card that's delivered electronically. Showing or asking for a shipping address in this scenario may give the false impression that something is physically delivered.

**Display the active coupon or promotional code, or let people enter one.** If people can enter a code before the payment sheet appears, show it on the sheet to reassure them that you applied the code. Consider allowing code entry on the payment sheet as well, particularly in an express checkout flow.

**Let people choose the shipping method in the payment sheet.** To the extent space permits, show a clear description, a cost, and, optionally, an estimated delivery or pickup date — or range of dates — for each available option. Leverage the shipping method's calendar and time-zone support to provide accurate delivery or pickup information, regardless of the person's current location. For developer guidance, see `PKDateComponentsRange`.

**For in-store pickup, consider letting people choose a pickup window that works for them.** You can use the shipping method to supply a range of dates and times from which people can choose.

**Use line items to explain additional charges, discounts, pending costs, add-on donations, recurring payments, and future payments.** A line item includes a label and cost; a line item for a recurring payment can also include a frequency. Don't use line items to show an itemized list of products that make up the purchase. For developer guidance, see `paymentSummaryItems`; for guidance on donations, see "Supporting donations" below.

**Keep line items short.** Make line items specific and easily understandable at a glance. Whenever possible, fit line items on a single line.

**Provide a business name after the word Pay on the same line as the total.** Use the same business name people will see when they look for the charge on their bank or credit card statement. This provides reassurance that payment is going to the right place — for example, "Pay [Business_Name]."

**If you're not the end merchant, identify both businesses in the payment sheet.** When your app, App Clip, or website acts as an intermediary, such as a marketplace where people buy from third-party sellers, people may not realize two businesses are involved. Clearly describe the relationship in the Pay line using something like "Pay [End_Merchant_Business_Name (via Your_Business_Name)]."

**Clearly disclose when people may incur additional costs after payment authorization.** In some cases, you may not know the total cost at checkout time. For example, the price of a car ride based on distance or time might change after checkout. Or, someone might want to add a tip after they receive their delivery. In situations like these, and when local regulations allow, you can provide a clear explanation in the payment sheet and a subtotal marked as **Amount Pending**. If you're preauthorizing a specific amount, be sure the payment sheet accurately reflects this information.

**Handle data entry and payment errors gracefully.** If an error occurs during checkout, help people resolve it quickly so they can complete their transaction. For related guidance, see "Data validation errors" below.

**Defer to the payment sheet for progress information during payment.** The payment sheet already presents loading states and progress clearly. Additional spinners or progress indicators can create confusion about the state of the transaction.

### Displaying a website icon

Many websites provide an icon that appears with bookmarks, in URL fields, and on a device's Home Screen. Websites that support Apple Pay can also use this icon during payment authorization — most notably during Handoff, when a person authorizes payment on a connected device — to provide visual reassurance that payment is going to the right place. For subscription payment flows, the icon can also appear in Wallet.

If your website supports Apple Pay, provide an icon in the following sizes: see Specifications.

### Handling problems

Provide clear, actionable guidance when problems occur during checkout or payment processing, so people can resolve them quickly and complete their transaction.

#### Data validation errors

Your app or website can respond to user input when the payment sheet appears, when people change certain field values on the payment sheet, and after they authenticate the transaction. Use these opportunities to check for data entry problems and to provide clear and consistent messaging. For developer guidance, see `PKPaymentAuthorizationViewControllerDelegate` (iOS, watchOS) and Apple Pay on the Web (web).

> **Note (Apple):** For privacy reasons, your app or website has limited access to data until people attempt to authorize a transaction. Before authorization, only the card type and a redacted shipping address are accessible. It's critical to display errors when authorization fails, but to the extent possible, you also need to attempt to validate available information and report problems before authorization.

**Avoid forcing compliance with your business logic.** Design a data validation process that's intelligent enough to ignore irrelevant data and infer missing data whenever possible. For example, if your app requires a five-digit zip code but someone enters a Zip+4 code, ignore the additional digits rather than asking for a correction. Let people enter phone numbers in multiple formats — such as with and without dashes, and with and without a country code — without producing an error.

**Accurately report problems to the system.** When a problem occurs, provide a custom error message and the correct status code so the system can show the most relevant error on the payment sheet. For developer guidance, see `PKPaymentError` (iOS, watchOS) and Apple Pay Status Codes (web).

**Explain the problem clearly and succinctly when data is invalid or incorrectly formatted.** Reference the relevant field and indicate exactly what's expected. For example, if people enter an invalid zip code, instead of showing "Address is invalid," show a specific message like "Zip code doesn't match city." If the shipping address is unserviceable, indicate why with a message like "Shipping not available for this state." Use noun phrases with sentence-style capitalization and no ending punctuation. Aim to keep messages at 128 characters or fewer to avoid truncation.

#### Payment processing problems

**Handle interruptions correctly.** An event like a cancellation or timeout might interrupt the payment flow, causing the payment sheet to dismiss. When such an event occurs, you must cancel any in-progress payment. After the payment sheet dismisses, people can restart the process by choosing the Apple Pay button again. For developer guidance, see `PKPaymentAuthorizationViewControllerDelegate` (iOS, watchOS) and `oncancel` (web).

### Supporting subscriptions

Your app or website can use Apple Pay to request authorization for recurring payments. A recurring payment can be a fixed amount, such as a monthly movie ticket subscription, or — when local regulations allow — a variable amount like a weekly grocery order. The initial authorization can also include discounts and additional fees.

**Clarify subscription details before showing the payment sheet.** Before asking people to authorize a recurring payment, make sure they fully understand the billing frequency and any other terms of service. You can show the billing frequency on the payment sheet.

**Include line items that reiterate billing frequency, discounts, and additional upfront fees.** Use these line items to remind people what they're authorizing. If no payment is required at authorization time, clearly disclose when billing will occur.

**Clearly communicate trial period terms.** For subscriptions with a trial period, use line items to display the trial amount (including $0 if free), the regular amount after the trial, and the date regular billing begins.

**Clarify the current payment amount in the total line.** Make sure people know the amount they're being billed at the time of authorization.

**Only show the payment sheet when a subscription change results in additional fees.** When someone changes a subscription, authorization isn't necessary if the cost decreases or remains the same.

> **Important (Apple):** Treat the billing agreement field as a plain-language summary, not a substitute for formal terms. If you use this field, be concise and avoid duplicating information shown elsewhere in your app, website, or line items. When in doubt, leave this field blank to maintain a clean, simple payment sheet.

### Supporting donations

Approved nonprofits can use Apple Pay to accept donations.

**Use a line item to identify a donation.** Display a line item on the payment sheet that reminds people they're authorizing a donation — for example, display "Donation $50.00."

**Streamline checkout by offering predefined donation amounts.** You can reduce steps in the donation process by offering recommended donations, like $25, $50, $100. Include an Other Amount option too, so people can customize the donation if they prefer.

### Using Apple Pay buttons

Apple Pay buttons come in several types and styles to fit different contexts and purchase flows. Use the Apple-provided APIs to create them. Doing so gives you:

- Buttons with Apple-approved captions, fonts, colors, and styles.
- Content that scales proportionally at any size.
- Automatic localization into the device's language.
- Corner radius customization to match your interface.
- Built-in VoiceOver support with automatic alternative text.

**Always use the Apple-provided API to display Apple Pay buttons.** Unlike button graphics, API-generated buttons always have the correct appearance and are localized automatically. Don't create custom Apple Pay button designs or try to replicate the Apple-provided ones. For developer guidance, see `PKPaymentButtonType` and `PKPaymentButtonStyle` (iOS and macOS), `WKInterfacePaymentButton` (watchOS), and Apple Pay on the Web (web).

> **Tip (Apple):** Use the Apple Pay mark graphic to communicate the availability of Apple Pay wherever you highlight payment options.

#### Button types

##### Apple Pay button

Choose a button type that best fits the terminology and flow of your purchase or payment experience. In some contexts, the system automatically displays an image of the default card on payment buttons, letting people know Apple Pay is set up and ready to use.

| Payment button term | Example usage |
|---|---|
| Apple Pay (plain) | An area in an app or website where people can make a purchase, such as a product detail page or shopping cart page. |
| Pay | An app or website that lets people pay bills or invoices, such as those for a utility — like cable or electricity — or a service like plumbing or car repair. |
| Check Out | An app or website offering a shopping cart or purchase experience that includes other payment buttons that start with the text "Check Out." |
| Continue | An app or website offering a shopping cart or purchase experience that includes other payment buttons that start with the text "Continue." |
| Book | An app or website that helps people book flights, trips, or other experiences. |
| Donate | An app or website for an approved nonprofit that lets people make donations. |
| Subscribe | An app or website that lets people purchase a subscription, such as a gym membership or a meal-kit delivery service. |
| Reload | An app or website that uses the term Reload to help people add money to a card, account, or payment system associated with a service, such as transit or a prepaid phone plan. |
| Add Money | An app or website that uses the term Add Money for the same kind of top-up service. |
| Top Up | An app or website that uses the term Top Up for the same kind of top-up service. |
| Order | An app or website that lets people place orders for items like meals or flowers. |
| Rent | An app or website that lets people rent items like cars or scooters. |
| Support | An app or website that uses the term Support to help people give money to projects, causes, organizations, and other entities. |
| Contribute | An app or website that uses the term Contribute for the same kind of giving. |
| Tip | An app or website that lets people tip for goods or services. |
| Apple Pay (fallback) | An app or website that has stylistic reasons to use a button that can have a smaller minimum width or that doesn't specify a call to action. If you choose a payment button type that isn't supported on the version of the operating system your app or website is running in, the system may replace it with this button. |

> **Source limitation:** The button-type artwork itself (the visual glyphs and exact on-button typography for each type) is presented as images in the source and doesn't survive PDF text extraction. The table above reproduces every button term and usage description Apple states in prose; it does not show the artwork. Cross-referencing against the minimum-size table later in the source confirms named buttons "Apple Pay," "Book with Apple Pay," "Buy with Apple Pay," "Check Out with Apple Pay," "Donate with Apple Pay," "Set Up Apple Pay," and "Subscribe with Apple Pay" — the remaining terms (Reload, Add Money, Top Up, Order, Rent, Support, Contribute, Tip, Continue) are named in prose but not independently confirmed against a sizing row.

##### Set Up Apple Pay button

When a device supports Apple Pay but the person hasn't set it up yet, you can use the Set Up Apple Pay button to show that you accept Apple Pay, and to give the person an explicit opportunity to set it up. Display the Set Up Apple Pay button in Settings, a user profile, or an interstitial page.

#### Button styles

**Use the automatic style to let the current system appearance determine the appearance of Apple Pay buttons.** For developer guidance, see `PKPaymentButtonStyle.automatic` (apps) and `ApplePayButtonStyle` (web). To control button appearance yourself, choose from the following options.

**Black.** Use on white or light-color backgrounds that provide sufficient contrast. Don't use on black or dark backgrounds.

**White with outline.** Use on white or light-color backgrounds that don't provide sufficient contrast. Don't place on dark or saturated backgrounds.

**White.** Use on dark-color backgrounds that provide sufficient contrast.

#### Button size and position

**Prominently display the Apple Pay button.** Make the Apple Pay button no smaller than other payment buttons, and avoid making people scroll to see it.

**Position the Apple Pay button correctly in relation to an Add to Cart button.** In a side-by-side layout, place the Apple Pay button to the right of an Add to Cart button. In a stacked layout, place the Apple Pay button above an Add to Cart button.

**Adjust the corner radius to match the appearance of other buttons.** By default, an Apple Pay button has rounded corners. You can change the corner radius to produce a button with square corners or a capsule-shape button. For developer guidance, see `cornerRadius`.

> **Note (Apple):** If the size you specify doesn't accommodate the translated title for the type of payment button you're using, the system automatically replaces it with the plain Apple Pay button. There is no automatic replacement for the Set Up Apple Pay button.

**Maintain the minimum button size and margins around the button.** Be mindful that the button title may vary in length depending on the locale. See Specifications for the values.

#### Apple Pay mark

Use the Apple Pay mark graphic to show that Apple Pay is an available payment option when showing other available payment options. The Apple Pay mark isn't a button; if you need an Apple Pay button, choose one of the buttons described in "Button types." For design guidance related to showing Apple Pay as a payment option, see "Offering Apple Pay" above.

**Use only the artwork provided by Apple, with no alterations other than height.** You can specify a height for the Apple Pay mark, but make sure that the height you use is equal to or larger than other payment brand marks in your payment flow. Don't adjust the width, corner radius, or aspect ratio of the artwork; don't add a trademark symbol or any other content; don't remove the border; don't add visual effects to the mark, such as shadows, glows, or reflections; and don't flip, rotate, or animate the Apple Pay mark.

**Maintain a minimum clear space around the mark of 1/10 of its height.** Don't let the Apple Pay mark share its surrounding border with another graphic or button.

Download the Apple Pay mark graphic and full usage guidelines from the Apple Pay Marketing Guidelines page.

### Referring to Apple Pay

You can use plain text to promote Apple Pay and indicate that Apple Pay is a payment option. As with all Apple product names, use Apple Pay exactly as shown in the Apple Trademark List — never make it plural or possessive — and adhere to the Guidelines for Using Apple Trademarks.

**Capitalize Apple Pay in text as it appears in the Apple Trademark List.** Use two words with an uppercase A, an uppercase P, and lowercase for all other letters. Display Apple Pay entirely in uppercase only when doing so is necessary for conforming to an established typographic style that capitalizes all letters.

**Never use the Apple logo to represent the name Apple in text.** In the United States, use the registered trademark symbol (®) the first time Apple Pay appears in body text. Don't include a registered trademark symbol when Apple Pay appears as a selection option during checkout.

| Example text | Correct? |
|---|---|
| Purchase with Apple Pay | Correct |
| Purchase with Apple Pay® | Correct (first use in US body text) |
| Purchase with ApplePay | Incorrect — must be two words |
| Purchase with [Apple logo] Pay | Incorrect — never use the Apple logo to stand in for the word "Apple" |
| Purchase with APPLE PAY | Correct only when conforming to an interface style that uses only capital letters |

**Coordinate the font face and size with your app or website.** Don't mimic Apple typography. Instead, use text attributes that are consistent with the rest of your app or website.

**Don't translate Apple Pay or any other Apple trademark.** Always use Apple trademarks in English, even when they appear within non-English text.

**In a payment selection context, you can display a text-only description of Apple Pay only when all payment options have text-only descriptions.** If any other payment option description includes an icon or logo, you must use the Apple Pay mark graphic as described in "Offering Apple Pay."

**When promoting Apple Pay in an app, follow App Store guidelines.** For specific guidance, see the App Store marketing guidelines.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, visionOS, or watchOS. **Not supported in tvOS.**

## Specifications

**Website icon sizes**

| Resolution | Size |
|---|---|
| @2x | 60×60 pt (120×120 px @2x) |
| @3x | 60×60 pt (180×180 px @3x) |

**Apple Pay button minimum size and margins**

| Button | Minimum width | Minimum height | Minimum margins |
|---|---|---|---|
| Apple Pay (plain) | 100 pt (100 px @1x, 200 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |
| Book with Apple Pay | 140 pt (140 px @1x, 280 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |
| Buy with Apple Pay | 140 pt (140 px @1x, 280 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |
| Check Out with Apple Pay | 140 pt (140 px @1x, 280 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |
| Donate with Apple Pay | 140 pt (140 px @1x, 280 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |
| Set Up Apple Pay | 140 pt (140 px @1x, 280 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |
| Subscribe with Apple Pay | 140 pt (140 px @1x, 280 px @2x) | 30 pt (30 px @1x, 60 px @2x) | 1/10 of the button's height |

**Apple Pay mark**

| Property | Value |
|---|---|
| Minimum clear space | 1/10 of the mark's height |
| Adjustable dimension | Height only (width, corner radius, and aspect ratio are fixed) |

**Data-validation error messages**

| Property | Value |
|---|---|
| Recommended maximum length | 128 characters (to avoid truncation) |
| Format | Noun phrases, sentence-style capitalization, no ending punctuation |

## Native implementation

**Related**
- Apple Pay Marketing Guidelines

**Developer documentation**
- Apple Pay — PassKit
- Apple Pay on the Web
- `WKInterfacePaymentButton` — WatchKit

**Key APIs**
- `PKPaymentAuthorizationController` — iOS, watchOS payment authorization
- `applePayCapabilities` — web availability check
- `PKDateComponentsRange` — shipping method date/time-zone support
- `paymentSummaryItems` — line items on the payment sheet
- `PKPaymentAuthorizationViewControllerDelegate` — iOS, watchOS error and interruption handling
- `PKPaymentError` — iOS, watchOS custom error reporting
- Apple Pay Status Codes — web equivalent of `PKPaymentError`
- `oncancel` — web interruption handling
- `PKPaymentButtonType` / `PKPaymentButtonStyle` — iOS, macOS button configuration
- `PKPaymentButtonStyle.automatic` — apps; `ApplePayButtonStyle` — web
- `cornerRadius` — button corner-radius configuration

**Videos:** What's new in Apple Pay

## Web translation *(derived — not from Apple)*

Apple Pay on the web is a real, first-party integration — via the Payment Request API and Apple's `ApplePaySession` JavaScript object — not an inference from native guidance, so most of the rules above already apply to the web exactly as written. The reasoning below explains *why* those rules exist and where the web genuinely diverges.

**Why button and mark rules are locked down: this is a financial trust surface, stricter than a login button.** A fake "Sign in with Apple" button is a phishing risk; a fake Apple Pay button is a direct path to payment fraud. That's why the rules here go further than the sign-in button rules — no custom Apple Pay button designs at all, ever, only the Apple-provided API output. A web team cannot recreate an Apple Pay button from CSS the way it might restyle a generic "pay" button; the API is the only sanctioned path, and this is not negotiable the way corner radius or bezel styling is for Sign in with Apple.

**The payment sheet is Apple's, not yours, and that boundary matters more on the web.** Native and web integrations both hand control to a system-rendered payment sheet rather than a page-rendered checkout form. On the web this is a meaningful trust signal: the person is authorizing payment inside a surface the browser (or connected device, during Handoff) controls, not inside arbitrary page JavaScript that could log card data. This is the same reasoning behind the Payment Request API as a general web standard — moving payment collection out of page-controlled DOM and into a browser-mediated UI reduces the attack surface for card-skimming scripts, regardless of which wallet backs it.

**Merchant validation replaces the native entitlement model.** A native app proves it's allowed to accept Apple Pay through code signing and an entitlement Apple grants. A website proves the same thing through domain verification — hosting a merchant identity file at a well-known path and validating the merchant session with Apple's servers on your backend before the sheet can display a real transaction. This is web-specific plumbing the HIG doesn't cover (it lives in the developer documentation), but it exists for the identical reason the entitlement does: Apple must be able to trust which merchant is asking to be paid.

**Where the web gives you less: browser and platform reach.** Apple Pay on the web works in Safari, and Apple has extended support to other browsers on Apple platforms through the Payment Request API bridge, but it is fundamentally bound to Apple hardware and an Apple Account with a provisioned card — there's no way to accept an "Apple Pay" payment from a Windows desktop Chrome session the way you can accept a card payment through a generic processor. Where a native iOS app can assume Apple Pay is *available* if the device supports it, a website must treat Apple Pay as one option among several and gracefully fall back — the "assume people want to use it" guidance is conditional on `applePayCapabilities` actually resolving true for that visitor.

**Website icon during Handoff → this is a web-specific mechanism with no native parallel.** The requirement to supply a bookmark/Home-Screen icon so it can appear during Handoff-based authorization on a connected device is unique to the web integration; there's no equivalent "which icon represents this app" question for a native app that already has an icon on the Home Screen by definition.

**The trademark and referral rules (capitalization, no logo substitution, no translation) transfer without modification.** These are legal/brand requirements, not rendering requirements, so a marketing page, a checkout page, and a native settings screen are all bound by the same Apple Trademark List rules for the string "Apple Pay."

**Amount Pending and variable-price authorization → maps to a broader web pattern of deferred-total checkout, but "when local regulations allow" is doing real work.** Ride-hailing and tip-adjustable checkouts on the web already use a similar pattern — authorize an estimate, settle the actual amount later — through card-network mechanisms like pre-authorization holds. Apple Pay's Amount Pending line item is a payment-sheet-level expression of the same idea; regulatory variance across regions is the actual constraint, not a web/native technical difference.

## Do / Don't

| Do | Don't |
|---|---|
| Make Apple Pay the primary payment option when a person has an active card | Separate Apple Pay into a different step or flow when credentials are available |
| Use Apple Pay buttons only to start payment or the setup process | Use an Apple Pay button for anything other than initiating payment or setup |
| Show the Apple Pay mark or text reference next to a custom payment button | Let a custom button display "Apple Pay" text or the Apple Pay logo itself |
| Gracefully explain why an Apple Pay button can't be used yet | Hide an Apple Pay button or make it appear unavailable |
| Request only essential information on the payment sheet | Ask for a shipping address on a purely digital, electronically delivered purchase |
| Keep data-validation error messages to 128 characters or fewer, specific and actionable | Show generic messages like "Address is invalid" |
| Cancel any in-progress payment when the sheet is dismissed by cancellation or timeout | Leave a payment in an ambiguous state after an interruption |
| Use only the Apple-provided API to render Apple Pay buttons | Create a custom Apple Pay button design or replicate the Apple-provided appearance |
| Adjust only the height of the Apple Pay mark | Change the mark's width, corner radius, aspect ratio, or add effects, borders, or animation |
| Write "Apple Pay" as two words with correct capitalization, never plural or possessive | Translate "Apple Pay" or substitute the Apple logo for the word "Apple" in text |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
