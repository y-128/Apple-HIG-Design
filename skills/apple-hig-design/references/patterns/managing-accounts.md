---
title: Managing accounts
url: https://developer.apple.com/design/human-interface-guidelines/managing-accounts
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Managing accounts

When it doesn't create an unnecessary barrier to your experience, an account can be a convenient way for people to access their content and track personal details.

## Core guidance

Ask people to create an account only if your core functionality requires it; otherwise, let people enjoy your app or game without one. If you require an account, consider using Sign in with Apple to give people a consistent sign-in experience they can trust and the convenience of not having to remember multiple accounts and authentication methods.

### Best practices

**Explain the benefits of creating an account and how to sign up.** If your app or game requires an account, write a brief, friendly description of the reasons for the requirement and its benefits. Display this message in your sign-in view.

**Delay sign-in for as long as possible.** People often abandon apps when they're forced to sign in before they can do anything useful. To help avoid this situation, give people a chance to get a sense of what your app or game does before asking them to make a commitment to it. For example, a shopping app might let people browse as much as they want, requiring sign-in only when they're ready to make a purchase.

**If you don't use Sign in with Apple in your iOS, iPadOS, macOS, or visionOS app, prefer using a passkey.** Passkeys simplify account creation and authentication, eliminating the need for people to create or enter passwords. When an app supports passkeys, people simply provide their user name when creating a new account or signing in to an existing one. For developer guidance, see Supporting passkeys. If you need to continue using passwords for authentication, augment security by requiring two-factor authentication (for developer guidance, see Securing Logins with iCloud Keychain Verification Codes).

**Always identify the authentication method you offer.** For example, if you display a button for signing in to your app with Face ID, title it using a phrase like "Sign In with Face ID" instead of a generic phrase like "Sign In."

**Refer only to authentication methods that are available in the current context.** For example, don't reference Face ID on a device that doesn't offer it. Check the device's capabilities and use the appropriate terminology. For developer guidance, see `LABiometryType`.

**In general, avoid offering an app-specific setting for opting in to biometric authentication.** People turn on biometric authentication at the system level, so presenting an in-app setting is redundant and could be confusing.

**Avoid using the term passcode to refer to account authentication.** People create a passcode to unlock their device or authenticate for Apple services. If you use the term in your interface, people might think you're asking them to reuse their passcode in your app or game.

### Deleting accounts

If you help people create an account within your app or game, you must also help them delete it, not just deactivate it. In addition to following the guidelines below, be sure to understand and comply with your region's legal requirements related to account deletion and the right to be forgotten.

> **Note (Apple):** If legal requirements compel your app to maintain accounts or information — such as digital health records — or to follow a specific account-deletion process, clearly describe the situation so people can understand the information or accounts you must maintain and the process you must follow.

**Provide a clear way to initiate account deletion within your app or game.** If people can't perform account deletion within your app, you must provide a direct link to the webpage on which people can do so. Make the link easy to discover — for example, don't bury it in your Privacy Policy or Terms of Service pages.

> **Developer note (Apple):** If people used Sign in with Apple to create an account within your app, you revoke the associated tokens when they delete their account. See Token revocation.

**Provide a consistent account-deletion experience whether people perform it within your app or game or on the website.** For example, avoid making one version of the deletion flow longer or more complicated than the other.

**Consider letting people schedule account deletion to occur in the future.** People can appreciate the opportunity to use their remaining services or wait until their subscription auto-renews before deleting their account. If you offer a way to schedule account deletion, offer an option for immediate deletion as well.

**Tell people when account deletion will complete, and notify them when it's finished.** Because it can sometimes take a while to fully delete an account, it's essential to keep people informed about the status of the deletion process so they know what to expect.

**If you support in-app purchases, help people understand how billing and cancellation work when they delete their account.** For example, you might need to help people understand the following scenarios:

- Billing for an auto-renewable subscription continues through Apple until people cancel the subscription, regardless of whether they delete their account.
- After they delete their account, people need to cancel their subscription or request a refund.

In addition to helping people understand these scenarios, provide information that describes how to cancel subscriptions and manage purchases. For guidance, see Helping people manage their subscriptions and Providing help with in-app purchases.

> **Note (Apple):** Even if people didn't use your app to purchase the subscription, you still need to support account deletion.

### TV provider accounts

Many popular TV providers let people sign in to their accounts at the system level, eliminating the need to authenticate on an app-by-app basis. If your TV provider app requires people to sign in, use TV Provider Authentication to provide the most efficient onboarding experience.

**Avoid displaying a sign-out option when people are signed in at the system level.** If your app must include a sign-out option, invoking it needs to prompt people to navigate to Settings > TV Provider to sign out of their account.

**Never instruct people to sign out by adjusting privacy controls.** The TV provider controls in Settings > Privacy aren't a sign-out mechanism. These settings help people manage the apps that can access their TV provider account.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, or visionOS.

### tvOS

Most people interact with Apple TV using a remote, not a keyboard, so ask for the minimum amount of information necessary.

**Prefer letting people use another device to sign up or authenticate.** When you configure your app's associated domains, Apple TV can work with other devices to safely suggest sign-in credentials, including Sign in with Apple. For developer guidance, see Configuring an associated domain.

**When people are signed in to a shared account, avoid asking them to choose their profile every time they become the current user.** In tvOS 16 and later, your app can share its credentials with all users while storing each individual's profile and user data separately. When you support this type of sharing, your app can automatically use the current user's profile without asking each person to sign in separately to a shared account. For developer guidance, see `kSecUseUserIndependentKeychain` and User Management Entitlement.

**Minimize data entry.** If you need to gather more than a small amount of information, ask people to visit a website from another device. If you need an email address, show the email keyboard screen, which includes a list of recently entered addresses.

### watchOS

Use iCloud synchronization to provide access to the Keychain, letting people autofill user names and passwords and preserve app settings.

## Native implementation

**Related**
- Onboarding
- Sign in with Apple

**Developer documentation**
- Supporting passkeys — Authentication Services

**Key APIs**
- `LABiometryType` — reports which biometric authentication method, if any, is available on the current device
- `kSecUseUserIndependentKeychain` — tvOS keychain option supporting per-user credentials under a shared sign-in
- Token revocation — revoke Sign in with Apple tokens when an account is deleted

**Videos:** What's new in passkeys · What's new in device management

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Ask for an account only if core functionality requires it" and "delay sign-in as long as possible" → these transfer unchanged, and the web has fewer excuses for violating them.** A native app at least has an install step as a commitment signal before it asks for sign-in; a web page has none — someone can leave in one click. That makes Apple's delay-sign-in advice, if anything, more important on the web: gate authentication behind the specific action that needs it (checkout, saving, publishing) rather than at the front door.

**Sign in with Apple → available on the web too, and the same "consistent, trusted" reasoning applies.** Apple's Sign in with Apple JS SDK lets a website offer the same button and flow as a native app. The broader principle — prefer a federated or passwordless option over yet another username/password pair — maps to offering Sign in with Apple, Google, or similar OAuth providers alongside (or instead of) a bespoke credential system, for the same reason Apple gives: fewer accounts and passwords for people to manage.

**Passkeys → the WebAuthn API is the direct web equivalent, not just an analogy.** Passkeys are a cross-platform standard; a website can register and authenticate passkeys via `navigator.credentials.create()`/`.get()`, and a passkey created on one platform can often be used to sign in on the web too. Apple's preference ordering (passkey over password, two-factor if you must keep passwords) is sound, unmodified, web guidance — this is one of the rare cases where the native rule and the web rule are close to identical because the underlying standard is shared.

**Biometric authentication → Face ID/Touch ID show up on the web only as the platform authenticator behind WebAuthn, never as a named, brandable button.** You cannot title a web button "Sign In with Face ID" the way a native app can, because the browser — not your page — decides which authenticator (Face ID, Touch ID, a security key, a PIN) actually gets invoked, and it doesn't tell your page which one the person used beforehand. The transferable instruction becomes generic: offer "Sign in with a passkey" rather than naming a specific biometric your page can't actually guarantee.

**Account deletion — right to be forgotten, consistent in-app/web flows, billing clarity → applies to the web with no platform-specific gap.** Every point in Apple's Deleting accounts section (a discoverable deletion path, no burying it in legal pages, consistent flow across surfaces, clear subscription-cancellation guidance) is jurisdiction-driven (GDPR, CCPA, and similar) rather than platform-driven, so it applies to a web app exactly as written. If your product also has a native app, Apple's "consistent regardless of which surface" instruction becomes a concrete requirement: the web deletion flow and the app deletion flow need to match.

**TV provider accounts and tvOS-specific remote-based sign-in → platform-specific, no web analogue.** System-level TV provider authentication, associated-domain credential suggestion for Apple TV, and shared-account profile switching are tvOS platform integrations with no meaning outside that ecosystem. The one narrow principle that generalizes is "minimize data entry when the input method is poor" — the web equivalent shows up in similarly constrained contexts (a smart-TV browser, a kiosk) where the same instruction to keep forms short and offer a QR-code hand-off to a phone applies for the identical reason.

## Do / Don't

| Do | Don't |
|---|---|
| Require an account only when core functionality needs one | Force sign-in before people can evaluate your app |
| Offer Sign in with Apple or a passkey as the preferred path | Make a username/password pair the only option |
| Name the specific authentication method you offer | Use a generic "Sign In" label when a specific method is used |
| Provide an easy-to-find, in-app account-deletion path | Bury deletion inside Privacy Policy or Terms of Service text |
| Keep the deletion flow consistent across app and web | Make one deletion surface slower or more complex than the other |
| Explain subscription billing and cancellation clearly on deletion | Leave people unsure whether deleting their account also cancels billing |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
