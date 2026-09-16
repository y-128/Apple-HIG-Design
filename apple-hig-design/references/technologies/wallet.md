---
title: Wallet
url: https://developer.apple.com/design/human-interface-guidelines/wallet
platforms: [iOS, iPadOS, macOS, visionOS, watchOS]
last_updated: 2026-06-08
---

# Wallet

Wallet helps people securely store their credit and debit cards, driver's license or state ID, transit cards, event tickets, keys, and more on iPhone and Apple Watch.

## Core guidance

People use their cards and passes in Wallet to make Apple Pay purchases, track their orders, confirm their identity, and streamline activities like boarding a plane, attending a concert, or receiving a discount.

When you integrate Apple Wallet into your app, you can create custom passes and present them the moment people need them, securely verify an individual's identity so they can access personal content, and offer detailed receipts and tracking information where it's most convenient. For developer guidance, see Wallet.

### Passes

Passes are digital representations of information that people can add to Wallet, like event tickets, boarding passes, membership reward cards, and coupons.

**Offer to add new passes to Wallet.** When an action results in a new pass, like purchasing an event ticket or registering for a store reward program, you can present system UI that adds the pass to Wallet with one tap. For frequent, predictable actions like checking in for a flight, you can add passes in the background after a person grants a one-time authorization, so they don't need to tap an Add to Apple Wallet button each time. Wallet notifies the person whenever a pass is added. If someone wants to review a pass first, you can show a custom view with an Add to Apple Wallet button. For developer guidance, see `addPasses(_:withCompletionHandler:)`, `PKPassLibrary.Capability.backgroundAddPasses`, and `PKAddPassesViewController`.

**Help people add a pass created outside your app.** If someone creates a pass using your website or another device, suggest adding it to Wallet the next time they open your app. If people decline your suggestion, don't ask them again.

**Add related passes as a group.** If your app generates multiple passes, like boarding passes for a multi-connection flight, add all passes at once so people don't have to add each one individually. If your website distributes a group of passes, such as a set of event tickets, bundle them together so people can download them all at once. For developer guidance, see "Distributing and updating a pass."

**Display an Add to Apple Wallet button to let people add an existing pass not already in Wallet.** If someone previously declined your suggestion to add a pass to Wallet — or if they removed the pass — a button makes it easy to add the pass if they change their mind. You can display an Add to Apple Wallet button wherever corresponding pass information appears in your app. For developer guidance, see `PKAddPassButton`. An Add to Apple Wallet badge is also available for emails and webpages; for guidance, see the Add to Apple Wallet guidelines.

**Let people jump from your app to their pass in Wallet.** Wherever your app displays information about a pass that exists in Wallet, you can offer a link that opens it directly. Label the link something like "View in Wallet."

**Tell the system when your passes expire.** Wallet automatically hides expired passes to reduce crowding, and provides a button that lets people revisit them. To help ensure the system hides passes appropriately, set the expiration date, relevant date, and voided properties of each pass correctly; for developer guidance, see `Pass`.

**Always get permission before deleting passes from Wallet.** For example, you could include an in-app setting that lets people specify whether they want to delete passes manually or allow automatic removal. If necessary, you can show an alert before deleting a pass.

**Help the system suggest a pass when relevant.** Ideally, passes automatically appear when they're needed so people don't have to manually locate them. When you provide information about when and where your pass is relevant, the system can display a link to it on the Lock Screen when people are most likely to want it. For example, a gym membership card could appear on the Lock Screen as people enter the gym. For certain types of passes, like event tickets, the system can also start a Live Activity. For developer guidance, see "Showing a Pass on the Lock Screen."

> *Image caption:* A pass surfaced as a Lock Screen banner, and the same pass driving a Live Activity.

**Keep passes up to date.** Physical passes don't typically change, but a digital pass can reflect changes as they happen. An airline boarding pass, for example, can automatically update to display flight delays and gate changes.

**Use change messages only for updates to time-critical information.** A change message interrupts people, so send one only for updates they need to know about. For example, people need to know when there's a gate change for a flight, but they don't need to know when a customer service phone number changes. Never use a change message for marketing or other noncritical communication. Change messages are available per-field; for developer guidance, see "Adding a Web Service to Update Passes."

### Pass anatomy

You define the content and structure of a pass using a combination of pass fields and semantic tags. Pass fields define what information appears on a pass and how it's arranged. Semantic tags describe pass content to the system, enabling features like surfacing a pass when it's needed, and featured actions, which are quick links to related content like venue directions or event guides. For poster event and semantic boarding passes, semantic tags are required and enable automatic layout. Include pass fields alongside semantic tags for these pass types too, so the passes display correctly on devices running older versions of iOS.

In some cases, you can provide supplemental information that people can access via sheets linked from the front of the pass. The back of the pass holds settings and information people rarely need to access, like legal text.

For developer guidance, see Wallet Passes.

#### Pass field types

Pass fields are organized into the following areas:

- **Logo and logo text fields** — show the brand icon and name; they remain visible when the pass is collapsed in Wallet.
- **Header fields** — show critical information that remains visible when the pass is collapsed.
- **Primary field** — shows the most important information people need.
- **Secondary and auxiliary fields** — show useful, but less critical information.
- **Footer fields** — show supplemental information, such as pass category (for example, "Family" or "Annual").
- **Back fields** — show supplemental details that appear in pass details in Wallet.

Layout varies by pass style. For developer guidance, see "Defining the metadata of your Wallet Pass."

### Designing passes

Wallet uses a consistent visual style to build familiarity and trust. Instead of merely replicating the appearance of its physical counterpart, design a clean, simple pass that feels at home in Wallet.

**Use Pass Designer to design and preview passes for Apple Wallet.** Starting from Apple-provided templates or a blank pass, you can create boarding passes, coupons, event tickets, store cards, generic passes, and poster generic passes. For more information, see "Creating a pass with Pass Designer."

**Design a pass that looks great and works well on all devices.** Passes can look different depending on the device. For example, a pass on Apple Watch shows less information and fewer images than on iPhone. Don't put essential information in elements that might be unavailable on certain devices, and avoid adding padding to images — for example, watchOS crops white space from some images. For guidance, see the watchOS section below.

**Keep the pass front uncluttered.** Show essential information, like an event date or account balance, in the header so people can see it when the pass is collapsed in Wallet. Use the rest of the pass front for information people need quick access to. Place details people don't need often on the additional pass information sheet.

**Make your pass instantly identifiable.** Use brand colors and visual elements like images, icons, and full-art backgrounds to help people recognize your pass at a glance.

**Ensure sufficient contrast between background and text colors.** Pick label colors that keep text legible against both solid backgrounds and background images.

> *Image caption:* Sufficient contrast between a solid background and label text, contrasted with insufficient contrast between a solid background and label text.
> *Image caption:* Sufficient contrast between an image background and label text, contrasted with insufficient contrast between an image background and label text.

**Use language that works on any device.** Passes can appear on multiple devices, so use text that makes sense everywhere. For example, "Slide to view" is meaningful on iPhone but doesn't apply on Apple Watch.

### Pass styles

You can choose from a variety of pass styles. Each one defines the appearance and layout of your pass.

**Boarding passes.** The boarding pass style is for travel tickets: airline boarding passes, train tickets, bus tickets, boat tickets, and generic transit passes. Typically, each pass corresponds to a single trip with a specific starting and ending point. Use semantic tags for airline boarding passes; use pass fields for all other transit types. For developer guidance, see "Creating an airline boarding pass using semantic tags."

**Coupons.** The coupon style is for coupons, special offers, and other discounts. For developer guidance, see "Creating a coupon pass."

**Event tickets.** The event ticket pass style is for entry into events like sporting events, concerts, movies, and plays. Typically each pass corresponds to a specific event, but you can also use a single pass for multiple events, as with a season ticket. An event ticket supports a full-art background to evoke the look and feel of your event. For developer guidance, see "Creating a poster event pass using semantic tags." Non-poster style event tickets use standard pass fields and can use a background image and thumbnail.

> *Image caption:* An event ticket with background and thumbnail, alongside an event ticket with thumbnail only.

**Store cards.** The store card style is for store loyalty cards, discount cards, points cards, and gift cards. If an account carries a balance, the pass usually displays it. For developer guidance, see "Creating a store card pass."

**Poster generic passes.** The poster generic pass style features a full background image and a pass field layout distinct from other pass styles, offering a flexible option that supports a wide range of use cases. It's not tied to a specific category, so you can use it whenever another pass style doesn't fit.

**Generic passes.** The generic style is for passes that don't fit the other categories, such as a gym membership card or coat-check claim ticket. For developer guidance, see "Creating a generic pass."

### Pass images

Passes support a variety of image types. Create pass images in PNG format in @2x and @3x format.

**Reserve pass images for visual content.** Embedded text isn't accessible and may not be visible if images don't display on all devices. For text information, use text fields and semantic tags instead. Use Pass Designer or corresponding APIs to add barcodes rather than embedding them in pass images.

**Keep image file sizes small.** People can receive passes via email or a webpage. To make downloads as fast as possible, use the smallest image files that still look great.

**Provide a pass icon.** The system uses it to represent your pass on the Lock Screen, in Mail, and on passes in Wallet. You can use your app icon or design a separate one.

**Logo.** The logo appears in the top leading corner of passes with pass fields. It's typically a horizontal text logo representing your brand, optionally combined with a graphic element. **Avoid inner drop shadows on logo artwork** — they can reduce legibility when the logo renders on the pass. See Specifications for exact file dimensions.

**Primary logo.** Like the logo, the primary logo appears in the top-leading corner of your pass, but is used exclusively for semantic passes. See Specifications for exact file dimensions.

> *Image caption:* A square primary logo with logo text, alongside a rectangular primary logo with no logo text.

**Secondary logo.** The secondary logo displays an additional logo for a ticket issuer or event organizer. It appears in the bottom-trailing corner of a poster event ticket. See Specifications for exact file dimensions.

**Icon.** Icons are square and represent your company or brand when your pass appears on the Lock Screen, in Mail, and on passes in Wallet. The system automatically applies rounded corners, so you don't need to round them. See Specifications for exact file dimensions.

> *Image caption:* An icon shown in a Lock Screen banner, alongside the same icon displayed on a pass in Wallet.

**Strip image.** Strip images appear on coupons and store cards to reinforce your brand or offer. Because text can appear over strip images, ensure sufficient contrast between your text and the image. Keep areas behind text uncluttered, and place important visual elements toward the bottom or trailing edge. Avoid embedding text in the strip image. See Specifications for exact file dimensions.

**Thumbnail.** Thumbnails are small images, such as a movie poster, that appear on event tickets and generic passes. Thumbnails are square — use rounded corners on your artwork and export as a transparent PNG. See Specifications for exact file dimensions.

**Background.** The background image is the visual centerpiece of a pass. Backgrounds appear blurred behind content on older event tickets; backgrounds appear unblurred on poster event tickets and poster generic passes. See Specifications for the separate non-poster and poster background dimensions.

**Position content within the safe area** — on poster generic passes and poster event tickets, a material strip covers the bottom edge of the image. If your pass includes a barcode, account for it in your background design. You can preview your pass layout in Pass Designer to verify placement. For developer guidance, see `footerBackgroundColor` in `Pass`.

> *Image caption:* Pass layout and corresponding safe areas, shown for both the standard pass layout and the poster layout.

**Footer.** The footer is only available for airline boarding passes. See Specifications for exact file dimensions.

### Order tracking

When you support order tracking, Wallet can display information about an order a customer placed through your app or website, updating the information whenever the status of the order changes. In iOS 17 and later, you can help people start tracking their order right from your app or website and offer additional ways to add their order to Wallet.

Wallet presents a dashboard that displays a customer's active and completed orders. People can choose an order to view details about it, like the items they ordered and fulfillment information for shipping and pickup.

> *Image caption:* The Wallet order dashboard, showing a customer's active and completed orders.

The Wallet Orders schema defines the properties you use to provide order data like product descriptions, order status, contact information, and shipping and pickup details, including estimated arrival dates, addresses, tracking numbers, and pickup instructions. Wallet displays the information you supply within consistent, system-defined interfaces. To help people get the information they need quickly and conveniently, supply as much information as you can, using the properties that match your order processes.

**Make it easy for people to add an order to Wallet.** For example, when a customer completes an Apple Pay transaction in your app or website, use `PKPaymentOrderDetails` (app) or `ApplePayPaymentOrderDetails` (web) to automatically add the order to Wallet. In iOS 17 and later, you can use `AddOrderToWalletButton` to display the system-provided Track with Apple Wallet button in relevant areas of your app or website — such as in pages for order confirmation, status, or tracking — or in emails to customers. If a person already added an order to Wallet, trying to add it again opens Wallet and displays the order.

**Make information about an order available immediately after people place it.** People need to confirm that their order was received, even when payment, processing, and fulfillment are still pending. If you won't have details until a later time, provide the data you have at the time of the order and supply a status description like "Check back later for full order details."

**Provide fulfillment information as soon as it's available, and keep the status up to date.** When you supply fulfillment data or you change the status of an order, the system updates the order information and can automatically send a notification to customers. The system uses the fulfillment status you report to update the order's current status to a value like Order Placed, Processing, Ready for Pickup, Picked Up, Out for Delivery, Delivered, or — if something goes wrong — Issue or Canceled. For guidance on describing a status, see "Displaying order and fulfillment details" below.

**Supply a high-resolution logo image that uses a nontransparent background.** The system displays your logo image in the dashboard and detail view, so you want to make sure that people can instantly recognize it at various sizes. Use the PNG or JPEG format to create a logo image that measures 300×300 pixels. To help ensure that your logo image renders correctly, be sure to use a nontransparent background. For developer guidance, see `logo`.

**Supply distinct, high-resolution product images that use nontransparent backgrounds.** The system displays a product's image — along with descriptive information you supply — in the detail views, order dashboard, and notifications for an order or a fulfillment. When creating a product image, use a straightforward depiction and a solid, nontransparent background. Showing a product in a "lifestyle" context or against a busy background can make the item hard to distinguish at small sizes. For each product, use the PNG or JPEG format to create an image that measures 300×300 pixels.

**In general, keep text brief.** People appreciate being able to read text at a glance, and the system can truncate text that's too long.

**Use clear, approachable language, and localize the text you provide.** You want to make sure that all your customers can read the information in an order. Also, make sure the price you show matches the final price the customer confirmed.

#### Displaying order and fulfillment details

An order gives people ways to contact the merchant and displays details about their Apple Pay purchase, including fulfillment status and per-item information.

**Provide a link to an area where people manage their order.** When you provide a universal link, people can open your order management area even if they don't have your app installed. To learn more about universal links, see "Allowing apps and websites to link to your content"; for developer guidance, see `Order`.

**Clearly describe each item so people can verify that their order contains everything they expect.** You can use the `LineItem` property to provide information like a product's price, name, and image. An order lists the line items for every item the customer ordered; a fulfillment lists only the line items that fulfillment includes. When appropriate, you can also attach a PDF receipt to an individual transaction related to an order.

**Supply a prioritized list of your apps that might be installed on the device.** The system uses this list when it needs to display a link to your app within the order details view. For example, if you provide multiple apps and more than one of them is installed on the device, the system displays a link to the installed app that's highest on your list. If none of your apps are installed on the device, the system displays a link to the first app on your list. For developer guidance, see `Order`.

**Avoid sending duplicate notifications.** For example, you can tell the system to avoid sending order-related notifications through Wallet when the customer has one of your associated apps installed.

**Make it easy for customers to contact the merchant.** Provide multiple contact methods, so people can choose the one that works best for them. At minimum, you need to provide a link to the merchant's website or landing page, but you can also provide a Messages for Business link, a phone number, an email address, and a link to a support page. When people choose the Contact button in an order, the system displays a menu of the contact methods you supply. For developer guidance, see `Merchant`.

**Help people track their order.** A multi-item order can have multiple fulfillments, where each fulfillment is either shipping or pickup. For example, if a customer orders a pair of shoes and a T-shirt, the customer might want to have one item shipped, while picking up the other. Regardless of fulfillment type, you need to supply enough information for people to know where their items are and when to expect them at the destination they specified. In addition to an estimated time of arrival, here's some information that people particularly appreciate:

- A link that opens the carrier's website to a page with information about a shipping fulfillment. When possible, provide a direct link — in addition to a tracking number — so people can easily view the most up-to-date shipping information. If necessary, display this link on any intermediate order-tracking page you open.
- A scannable barcode when one is required to pick up the order in a pickup fulfillment. It's convenient when people can offer the barcode from within Wallet instead of finding it in an email or webpage.
- Clear, detailed instructions that can help people receive or pick up their order.

**Keep the fulfillment screen centered on order tracking.** For example, if you recommend your app or other services to customers, be sure to prioritize order-tracking information over other content in the screen.

**Choose shipping-fulfillment values that match the details you have about the shipping process.** If you know the carrier, enter its name in the `carrier` property; otherwise, leave the default "Track Shipment" value. If you can access details about a carrier's interim shipping steps — such as when a fulfillment is on the way or out for delivery — indicate each step by using specific status values like `onTheWay`, `outForDelivery`, or `delivered`. In contrast, if you don't have access to a carrier's shipping details, use the `shipped` status. In both cases, provide a tracking link (when one is available) so people can track their order on their own. For developer guidance, see `ShippingFulfillment`.

**Keep customers informed through relevant fulfillment status descriptions.** A great status message is approachable, accurate, and clearly related to the status it describes. In addition to supplying information that helps people understand the status of their order, a status message also gives you an opportunity to use your brand's communication style.

**Be direct and thorough when describing an Issue or Canceled status.** People generally need to know why there's a problem and what they can do about it.

### Identity verification

On iPhone running iOS 16 and later, people can store an ID card in Wallet, and later allow an app or App Clip to access information on the card to verify their identity without leaving their current context. For example, a person might need to confirm their identity when they apply for a credit card within their banking app. To learn how to support in-person mobile ID verification, see ID Verifier.

> **Developer note (Apple):** Apple doesn't create or see the ID documents that people add to Wallet, and when people agree to share identifying information with your app, you receive only encrypted data that isn't readable on the device. For developer guidance, see "Requesting identity data from a Wallet pass."

To help you offer a consistent experience that people can trust, Apple provides a Verify with Wallet button you can use in your app when you need to ask for identity verification. The button reveals a sheet that describes your request and lets people agree to share their information or cancel.

**Present a Wallet verification option only when the device supports it.** If the current device can't return the identity information you request, don't display a Verify with Apple Wallet button. Be prepared to present a fallback view that offers a different verification method if Verify with Apple Wallet isn't available; for developer guidance, see `VerifyIdentityWithWalletButton`.

**Ask for identity information only at the precise moment you need it.** People can be suspicious of a request for personal information if it doesn't seem to be related to their current action. If your app needs identity verification, for example, wait to ask for this information until people are completing the process or transaction that requires it; don't request verification before people are ready to start the process or when they're simply creating an account.

**Clearly and succinctly describe the reason you need the information you're requesting.** You must write text that explains why people need to share identity information with your app (this text is called a purpose string or usage description string). The system displays your purpose string in the verification sheet so people can make an informed decision.

| To verify… | To support… | Example purpose string |
|---|---|---|
| Identity | Opening an account for which proof of identity is legally required to prevent fraud | "Federal law requires this information to verify your identity and also to help [App Name] prevent fraud." |
| Driving privilege | Renting a vehicle that requires legal driving privileges | "Applicable state law requires [App Name] to verify your driving privileges." |

**For each purpose string, aim for a brief, complete sentence that's direct, specific, and easy for everyone to understand.** Use sentence case, avoid passive voice, and include a period at the end.

**Ask only for the data you actually need.** People may lose trust in your app if you ask for more data than you need to complete the current task or action. For example, if you need to ensure that a customer is at least a certain age, use a request that specifies an age threshold; avoid requesting the customer's current age or birth date. For developer guidance, see `age(atLeast:)`.

**Clearly indicate whether you will keep the data and — if you need to keep it — specify how long you'll do so.** To help people trust your app, it's essential to explain how long you might need to keep the personal information they agree to share with you. When you use PassKit APIs to specify a duration — such as a particular period, indefinitely, or only as long as it takes to complete the current verification — the system automatically displays explanatory content in the verification sheet. For developer guidance, see `PKIdentityIntentToStore`.

**Choose the system-provided verification button that matches your use case and the visual design of your app.** The system provides the following button labels to support various use cases:

| Button label | Consider using when… |
|---|---|
| Verify Age | Your app can complete the current transaction after you verify a person's age. An example transaction is making a car available to lease. |
| Verify Identity | Your app can complete the current transaction after you verify a person's identity. An example transaction is a car rental. |
| Continue | Verify with Wallet forms one part of a verification process that also requires people to supply additional information not provided by Verify with Wallet, such as a Social Security number or phone number. Examples include opening a financial account or performing a background check. |
| (Custom label) | Your app can complete the current verification flow without additional steps, but the "Verify Age," "Verify Identity," and "Continue" button labels aren't appropriate for your use case. An example is an app that helps people sign up for a government service. |

All button labels are also available in a multiline variant that the system automatically uses when horizontal space is constrained. For developer guidance, see `PKIdentityButton.Label`.

**The verification button always uses white letters on a black background.** You can choose the style that includes a light outline if you need to ensure that the button contrasts well with a dark background in your app. In addition, you can use the `cornerRadius` property to adjust the verification button's corners to match other related buttons in your interface. For developer guidance, see `PKIdentityButton.Style.blackOutline`.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, or visionOS. **Not supported in tvOS.**

### watchOS

On Apple Watch, Wallet displays passes in a scrolling carousel of cards. People can add your pass to their Apple Watch even if you don't create a watch-specific app, so it's important to understand how your pass can look on the device.

People can tap a pass on their Apple Watch to reveal a details screen that displays additional information in a scroll view. In some cases, people can also tap a specific transaction to get more information.

Each pass style specifies the fields and images that can appear in the basic layout areas of the watchOS card. If some information doesn't fit within the layout areas, the system displays it in the scrolling details screen.

> **Important (Apple):** In every style, watchOS crops the strip image to fit the aspect ratio of the card interface and may crop white space from other images. This applies to boarding, coupon, store, event, and generic pass styles alike.

## Specifications

**Logo**

| Property | Value |
|---|---|
| Supported pass styles | Non-semantic airline boarding passes, non-airline boarding pass styles, coupons, non-poster event tickets, generic passes, store cards |
| Filename | `logo.png` |
| Minimum width | 50 pt |
| Maximum width | 160 pt |
| Height | 50 pt |

**Primary logo**

| Property | Value |
|---|---|
| Supported pass styles | Airline boarding passes, poster event tickets, and poster generic passes |
| Filename | `primaryLogo.png` |
| Minimum width | 30 pt |
| Maximum width | 126 pt |
| Height | 30 pt |

**Secondary logo**

| Property | Value |
|---|---|
| Supported pass styles | Poster event ticket |
| Filename | `secondaryLogo.png` |
| Minimum width | 12 pt |
| Maximum width | 135 pt |
| Height | 12 pt |

**Icon**

| Property | Value |
|---|---|
| Supported pass styles | All |
| Filename | `icon.png` |
| Width | 38 pt |
| Height | 38 pt |

**Strip image**

| Property | Value |
|---|---|
| Supported pass styles | Coupon, store card |
| Filename | `strip.png` |
| Width | 375 pt |
| Height | 144 pt |

**Thumbnail**

| Property | Value |
|---|---|
| Supported pass styles | Event ticket, generic pass |
| Filename | `thumbnail.png` |
| Minimum width | 60 pt |
| Maximum width | 90 pt |
| Height | 90 pt |

**Background — non-poster passes**

| Property | Value |
|---|---|
| Supported pass styles | Event tickets |
| Filename | `background.png` |
| Width | 343 pt |
| Height | 503 pt |

**Background — poster passes**

| Property | Value |
|---|---|
| Supported pass styles | Poster event tickets, poster generic passes |
| Filename | `artwork.png` |
| Width | 358 pt |
| Height | 448 pt |

**Footer**

| Property | Value |
|---|---|
| Supported pass styles | Airline boarding passes |
| Filename | `footer.png` |
| Width | 268 pt |
| Height | 15 pt |

**Order tracking images**

| Image | Format | Dimensions | Background |
|---|---|---|---|
| Merchant logo | PNG or JPEG | 300×300 px | Nontransparent |
| Product image (per product) | PNG or JPEG | 300×300 px | Nontransparent |

All pass image formats use PNG, exported at @2x and @3x.

## Native implementation

**Related**
- Apple Pay
- ID Verifier

**Developer documentation**
- FinanceKitUI
- FinanceKit
- PassKit (Apple Pay and Wallet)
- Wallet Passes
- Wallet Orders

**Key APIs**
- `addPasses(_:withCompletionHandler:)` — add one or more passes with system UI
- `PKPassLibrary.Capability.backgroundAddPasses` — add passes in the background after one-time authorization
- `PKAddPassesViewController` — custom review view before adding a pass
- `PKAddPassButton` — button for adding an existing pass not yet in Wallet
- `Pass` — expiration date, relevant date, and voided properties that control automatic hiding
- `footerBackgroundColor` (in `Pass`) — safe-area-aware background styling
- `PKPaymentOrderDetails` (app) / `ApplePayPaymentOrderDetails` (web) — auto-add an order after an Apple Pay transaction
- `AddOrderToWalletButton` — system-provided Track with Apple Wallet button (iOS 17+)
- `Order` / `Merchant` / `LineItem` / `ShippingFulfillment` — order and fulfillment data model
- `age(atLeast:)` — request an age threshold instead of a birth date
- `PKIdentityIntentToStore` — declare how long identity data will be retained
- `PKIdentityButton.Label` / `PKIdentityButton.Style.blackOutline` — system-provided verification button
- `VerifyIdentityWithWalletButton` — Verify with Wallet entry point

**Videos:** What's new in Wallet

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance for this page. Most of Wallet is genuinely platform-bound — pass rendering, order dashboards, and identity verification all happen inside Wallet itself, which has no web counterpart — but one real web integration point exists, and a few narrower principles transfer even where the mechanism doesn't.

**The one real web touchpoint: Add to Apple Wallet on a webpage.** Apple explicitly documents an Add to Apple Wallet badge for emails and webpages, alongside the native `PKAddPassButton`. This works because a `.pkpass` file is just a signed bundle a browser can link to or download — a website can trigger the same "add to Wallet" system action a native app does, without needing Wallet's rendering engine itself. Beyond linking to a `.pkpass` file (or triggering the equivalent JavaScript on supported browsers), a website has no way to draw, preview, or otherwise interact with pass content — Wallet is the only renderer, on-device, full stop.

**Why pass design itself can't move to the web: the platform *is* the rendering guarantee.** Apple's insistence on a consistent visual style, exact image dimensions per pass style, and system-controlled layout areas (header/primary/secondary/back fields) exists because Wallet — not your code — ultimately lays out the pass on a Lock Screen banner, a Live Activity, an Apple Watch card, and the Wallet app itself, across screen sizes you don't control. A web team cannot approximate this by building an HTML page that "looks like a pass," because the actual value of a pass — showing up on the Lock Screen at a gate, surfacing automatically near a venue, syncing across a person's devices — comes entirely from being real Wallet data, not from visual resemblance.

**Order tracking → the general principle (structured status, not free text) transfers; the constraints don't.** Apple's Wallet Orders schema and the emphasis on brief, truncation-safe status text exist because Wallet renders your order data inside *its* fixed dashboard and detail views. The nearest web equivalent is structured order/tracking data — for example, `schema.org/Order` and `schema.org/ParcelDelivery` markup, or a merchant's own order-status page — driving a UI you fully control. The reasoning behind "keep text brief" (a shared, space-constrained system surface) doesn't apply once you're building your own status page; you can be as verbose as good UX allows. What does transfer is the underlying discipline: define statuses as an explicit, finite set (placed, processing, shipped, delivered, issue) rather than freeform strings, because that's what lets any consuming system — Wallet's or your own — reason about state reliably.

**Identity verification → no web equivalent exists, but the privacy discipline is a general principle worth adopting anyway.** Verify with Wallet is bound to a physical ID stored on-device and a native verification ceremony; there is no "Verify with Wallet" for a browser tab. But the specific obligations Apple lists — ask for a threshold (`age(atLeast:)`) rather than a birth date, state up front how long you'll retain what's shared, ask only at the exact moment you need it — are good privacy engineering regardless of platform, and increasingly map onto what web-based age- and identity-verification regimes require by law in some jurisdictions. If a web team is building its own identity-verification flow (through a third-party KYC vendor, for instance), Apple's purpose-string discipline — a short, specific, sentence-case explanation of why the data is needed — is a reasonable bar to hold that flow to, even without any shared technology.

**Change messages → the "interrupt only for what matters" principle applies to any push-notification-backed status update.** Whether it's a Wallet pass field update or a web push notification about a shipment, the same judgment call recurs: reserve an interruption for information someone needs to act on (a gate change), and use a quieter channel (an in-app or in-page update, checked passively) for everything else.

## Do / Don't

| Do | Don't |
|---|---|
| Add related passes as a group, such as all boarding passes for a connecting flight | Make people add each related pass one at a time |
| Ask permission before deleting a pass from Wallet | Remove a pass without the person's consent |
| Set expiration date, relevant date, and voided correctly so Wallet can hide passes appropriately | Leave stale, expired passes cluttering Wallet |
| Reserve change messages for time-critical updates, like a gate change | Send a change message for marketing or noncritical information |
| Keep the pass front uncluttered, with essential info in the header | Cram every detail onto the pass front instead of the information sheet |
| Ensure sufficient contrast between label text and both solid and image backgrounds | Ship a pass where text is illegible against its background |
| Present a Verify with Apple Wallet button only when the device supports it | Show the button on a device that can't return the requested identity information |
| Ask only for the data you need, using an age threshold instead of a birth date when possible | Request a birth date when an age threshold would do |
| State clearly how long you'll retain identity data, or that you won't | Leave people uncertain about how long their shared data will be kept |
| Keep the fulfillment screen centered on order tracking | Let app promotion or unrelated content crowd out tracking information |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
