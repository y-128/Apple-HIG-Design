---
title: Virtual keyboards
url: https://developer.apple.com/design/human-interface-guidelines/virtual-keyboards
platforms: [iOS, iPadOS, tvOS, visionOS, watchOS]
last_updated: 2025-06-09
---

# Virtual keyboards

On devices without physical keyboards, the system offers various types of virtual keyboards people can use to enter data.

## Core guidance

A virtual keyboard can provide a specific set of keys that are optimized for the current task; for example, a keyboard that supports entering email addresses can include the "@" character and a period or even ".com". A virtual keyboard doesn't support keyboard shortcuts.

When it makes sense in your app, you can replace the system-provided keyboard with a custom view that supports app-specific data entry. In iOS, iPadOS, and tvOS, you can also create an app extension that offers a custom keyboard people can install and use in place of the standard keyboard.

### Best practices

**Choose a keyboard that matches the type of content people are editing.** For example, you can help people enter numeric data by providing the numbers and punctuation keyboard. When you specify a semantic meaning for a text input area, the system can automatically provide a keyboard that matches the type of input you expect, potentially using this information to refine the keyboard corrections it offers. For developer guidance, see `keyboardType(_:)` (SwiftUI), `textContentType(_:)` (SwiftUI), `UIKeyboardType` (UIKit), and `UITextContentType` (UIKit).

> *Image caption:* Standard virtual keyboard types include ASCII capable, ASCII capable number pad, Decimal pad, Default, Email address, Name phone pad, Number pad, Numbers and punctuation, Phone pad, Twitter, and URL.

**Consider customizing the Return key type if it helps clarify the text-entry experience.** The Return key type is based on the keyboard type you choose, but you can change this if it makes sense in your app. For example, if your app initiates a search, you can use a search Return key type rather than the standard one so the experience is consistent with other places people initiate search. For developer guidance, see `submitLabel(_:)` (SwiftUI) and `UIReturnKeyType` (UIKit).

### Custom input views

In some cases, you can create an input view if you want to provide custom functionality that enhances data-entry tasks in your app. For example, Numbers provides a custom input view for entering numeric values while editing a spreadsheet. A custom input view replaces the system-provided keyboard while people are in your app. For developer guidance, see `ToolbarItemPlacement` (SwiftUI) and `inputViewController` (UIKit).

**Make sure your custom input view makes sense in the context of your app.** In addition to making data entry simple and intuitive, you want people to understand the benefits of using your custom input view. Otherwise, they may wonder why they can't regain the system keyboard while in your app.

**Play the standard keyboard sound while people type.** The keyboard sound provides familiar feedback when people tap a key on the system keyboard, so they're likely to expect the same sound when they tap keys in your custom input view. People can turn keyboard sounds off for all keyboard interactions in Settings > Sounds. For developer guidance, see `playInputClick()` (UIKit).

### Custom keyboards

In iOS, iPadOS, and tvOS, you can provide a custom keyboard that replaces the system keyboard by creating an app extension. An app extension is code you provide that people can install and use to extend the functionality of a specific area of the system; to learn more, see App extensions.

After people choose your custom keyboard in Settings, they can use it for text entry within any app, except when editing secure text fields and phone number fields. People can choose multiple custom keyboards and switch between them at any time. For developer guidance, see Creating a custom keyboard.

**Custom keyboards make sense when you want to expose unique keyboard functionality systemwide**, such as a novel way of inputting text or the ability to type in a language the system doesn't support. If you want to provide a custom keyboard for people to use only while they're in your app, consider creating a custom input view instead.

**Provide an obvious and easy way to switch between keyboards.** People know that the Globe key on the standard keyboard — which replaces the dedicated Emoji key when multiple keyboards are available — quickly switches to other keyboards, and they expect a similarly intuitive experience in your keyboard.

**Avoid duplicating system-provided keyboard features.** On some devices, the Emoji/Globe key and Dictation key automatically appear beneath the keyboard, even when people are using custom keyboards. Your app can't affect these keys, and it's likely to be confusing if you repeat them in your keyboard.

**Consider providing a keyboard tutorial in your app.** People are used to the standard keyboard, and learning how to use a new keyboard can take time. You can help make the process easier by providing usage instructions in your app — for example, you might tell people how to choose your keyboard, activate it during text entry, use it, and switch back to the standard keyboard. Avoid displaying help content within the keyboard itself.

## Platform considerations

Not supported in macOS.

### iOS, iPadOS

**Use the keyboard layout guide to make the keyboard feel like an integrated part of your interface.** Using the layout guide also helps you keep important parts of your interface visible while the virtual keyboard is onscreen. For developer guidance, see Adjusting your layout with keyboard layout guide.

> *Image caption:* The keyboard layout guide helps ensure that app UI and the keyboard work well together. Without the layout guide, the keyboard could make entering text more difficult, or make tapping a button more difficult.

**Place custom controls above the keyboard thoughtfully.** Some apps position an input accessory view containing custom controls above the keyboard to offer app-specific functionality related to the data people are working with. For example, Numbers displays controls that help people apply standard or custom calculations to spreadsheet data. If your app offers custom controls that augment the keyboard, make sure they're relevant to the current task. If other views in your app use Liquid Glass, or if your view looks out of place above the keyboard, apply Liquid Glass to the view that contains your controls to maintain consistency. If you use a standard toolbar to contain your controls, it automatically adopts Liquid Glass. Use the keyboard layout guide and standard padding to ensure the system positions your controls as expected within the view. For developer guidance, see `ToolbarItemPlacement` (SwiftUI), `inputAccessoryView` (UIKit), and `UIKeyboardLayoutGuide` (UIKit).

### tvOS

tvOS displays a linear virtual keyboard when people select a text field using the Siri Remote.

> **Note (Apple):** A grid keyboard screen appears when people use devices other than the Siri Remote, and the layout of content automatically adapts to the keyboard.

When people activate a digit entry view, tvOS displays a digit-specific keyboard. For guidance, see Digit entry views.

### visionOS

In visionOS, the system-provided virtual keyboard supports both direct and indirect gestures and appears in a separate window that people can move where they want. You don't need to account for the location of the keyboard in your layouts.

### watchOS

On Apple Watch, a text field can show a keyboard if the device screen is large enough. Otherwise, the system lets people use dictation or Scribble to enter information. You can't change the keyboard type in watchOS, but you can set the content type of the text field. The system uses this information to make text entry easier, such as by offering suggestions. For developer guidance, see `textContentType(_:)` (SwiftUI).

People can also use a nearby paired iPhone to enter text on Apple Watch.

## Native implementation

**Related**
- Entering data
- Keyboards
- Layout

**Developer documentation**
- keyboardType(_:) — SwiftUI
- textContentType(_:) — SwiftUI
- UIKeyboardType — UIKit

**Key APIs**
- `keyboardType(_:)` (SwiftUI) / `UIKeyboardType` (UIKit) — choose which virtual keyboard type appears for a text field
- `textContentType(_:)` (SwiftUI) / `UITextContentType` (UIKit) — specify the semantic meaning of a text field so the system can refine the keyboard and its suggestions
- `submitLabel(_:)` (SwiftUI) / `UIReturnKeyType` (UIKit) — customize the Return key
- `ToolbarItemPlacement` (SwiftUI) / `inputViewController` (UIKit) — build a custom input view that replaces the system keyboard
- `playInputClick()` (UIKit) — play the standard keyboard sound from a custom input view
- `inputAccessoryView` / `UIKeyboardLayoutGuide` (UIKit) — position custom controls above the keyboard

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Choosing a keyboard type maps to the `type` attribute and, more precisely, to `inputmode`.** Apple's `keyboardType(_:)` picks a purpose-built keyboard — email, phone pad, decimal pad, URL — so people only see the keys relevant to what they're entering. On the web the closest native tool is the `inputmode` attribute (`email`, `tel`, `numeric`, `decimal`, `url`, `search`), which asks the on-screen keyboard to show the matching layout without changing how the value is validated or submitted. The numeric-input type attribute looks like the obvious match for Apple's number pad, but it isn't: it adds a spinner control, mishandles decimals in some locales, and is a poor substitute for a true numeric keypad. The better practice, and the one that actually reproduces Apple's number-pad/decimal-pad distinction, is a text input with `inputmode="numeric"` or `inputmode="decimal"` plus a `pattern` for validation.

**`textContentType` doesn't map to one web attribute — it splits into two.** Apple's content type does double duty: it picks the keyboard layout and it tells the system what kind of data to expect for autofill and correction. The web splits this into `inputmode` (which keys appear) and `autocomplete` (semantic meaning like `email`, `tel`, `name`, `one-time-code`, which drives autofill and can influence keyboard suggestions). Setting only one of the two is a common web gap that Apple's single API doesn't have room for — treat them as a pair, not alternatives.

**The Return key type maps directly to the `enterkeyhint` attribute.** Apple's example — using a search Return key type when your app initiates a search, so the experience matches other search entry points — is precisely what `enterkeyhint` (`search`, `go`, `send`, `done`, `next`, `previous`) is for. This is one of the cleanest one-to-one mappings on this page.

**Custom keyboards have no web equivalent, and that's a hard boundary, not a gap to work around.** A browser page cannot install a systemwide input method the way an iOS, iPadOS, or tvOS app extension can. Don't attempt to simulate this; it's a native-platform capability the web deliberately doesn't expose, for the same security reasons no page can intercept keystrokes typed into other sites.

**Custom input views translate only partially, and what's lost is worth naming.** You can build an on-screen control — a calculator-style keypad drawn from buttons, for instance — that avoids triggering the native virtual keyboard entirely, which gets you Apple's "replace the keyboard with app-specific input" outcome for a narrow case. What you can't do is suppress the OS keyboard for a real text field and substitute your own drawing surface the way `inputViewController` allows; the browser owns that keyboard, and any workaround (like using `readonly` plus a synthetic caret) forfeits the OS keyboard's autofill, dictation, and accessibility integration in exchange for a UI you fully own and fully have to maintain.

**The keyboard layout guide's job — keep important content visible above the keyboard — has no equally reliable web counterpart.** An emerging API exposes the on-screen keyboard's height so a page can react to it, but support isn't universal. The common fallback is listening for the visual viewport to shrink and scrolling the focused field into view, which is a reasonable approximation but not a guarantee the way Apple's layout guide is; test on-device rather than trusting any single technique.

**The standard keyboard sound has no browser-provided equivalent at all.** There's no system typing sound to opt into on the web the way there is on iOS. If you want auditory feedback for a custom on-screen control, you own the entire implementation, and you should weigh whether adding it actually matches user expectation on a platform where typing has never made a sound.

## Do / Don't

| Do | Don't |
|---|---|
| Match the keyboard type to the kind of data being entered | Show the default alphanumeric keyboard for numeric or email fields |
| Set a semantic content type so the system can refine keyboard suggestions | Leave text fields without a specified content type when one applies |
| Customize the Return key type when it clarifies the action | Leave a generic Return key on a field that triggers search or submission |
| Use the keyboard layout guide to keep key UI visible above the keyboard | Let the keyboard cover fields or controls people still need |
| Make a custom keyboard's switching gesture obvious and consistent with the system's | Duplicate the system's Emoji/Globe or Dictation keys in a custom keyboard |
| Build a custom input view only when it adds real, app-specific value | Replace the system keyboard without explaining the benefit |
| Offer a tutorial in the app for a custom keyboard | Put help content inside the keyboard itself |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
