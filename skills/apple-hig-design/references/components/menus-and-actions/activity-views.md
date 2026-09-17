---
title: Activity views
url: https://developer.apple.com/design/human-interface-guidelines/activity-views
platforms: [iOS, iPadOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Activity views

An activity view — often called a share sheet — presents a range of tasks that people can perform in the current context.

## Core guidance

Activity views present sharing activities like messaging and actions like Copy and Print, in addition to quick access to frequently used apps. People typically reveal a share sheet by choosing an Action button while viewing a page or document, or after they've selected an item. An activity view can appear as a sheet or a popover, depending on the device and orientation.

You can provide app-specific activities that can appear in a share sheet when people open it within your app or game. For example, Photos provides app-specific actions like Copy Photo, Add to Album, and Adjust Location. By default, the system lists app-specific actions before actions — such as Add to Files or AirPlay — that are available in multiple apps or throughout the system. People can edit the list of actions to ensure that it displays the ones they use most and to add new ones.

You can also create app extensions to provide custom share and action activities that people can use in other apps. (An app extension is code you provide that people can install and use outside of your app.) For example, you might create a custom share activity that people can install to help them share a webpage with a specific social media service. Even though macOS doesn't provide an activity view, you can create share and action app extensions that people can use on a Mac. For guidance, see Share and action extensions below.

### Best practices

**Avoid creating duplicate versions of common actions that are already available in the activity view.** For example, providing a duplicate Print action is unnecessary and confusing because people wouldn't know how to distinguish your action from the system-provided one. If you need to provide app-specific functionality that's similar to an existing action, give it a custom title. For example, if you let people use custom formatting to print a bank transaction, use a title that helps people understand what your print activity does, like "Print Transaction."

**Consider using a symbol to represent your custom activity.** SF Symbols provides a comprehensive set of configurable symbols you can use to communicate items and concepts in an activity view. If you need to create a custom interface icon, center it in an area measuring about **70x70 pixels**. For guidance, see Icons.

**Write a succinct, descriptive title for each custom action you provide.** If a title is too long, the system wraps it and may truncate it. Prefer a single verb or a brief verb phrase that clearly communicates what the action does. Avoid including your company or product name in an action title. In contrast, the share sheet displays the title of a share activity — typically a company name — below the icon that represents it.

**Make sure activities are appropriate for the current context.** Although you can't reorder system-provided tasks in an activity view, you can exclude tasks that aren't applicable to your app. For example, if it doesn't make sense to print from within your app, you can exclude the Print activity. You can also identify which custom tasks to show at any given time.

**Use the Share button to display an activity view.** People are accustomed to accessing system-provided activities when they choose the Share button. Avoid confusing people by providing an alternative way to do the same thing.

### Share and action extensions

Share extensions give people a convenient way to share information from the current context with apps, social media accounts, and other services. Action extensions let people initiate content-specific tasks — like adding a bookmark, copying a link, editing an inline image, or displaying selected text in another language — without leaving the current context.

The system presents share and action extensions differently depending on the platform:

- In iOS and iPadOS, share and action extensions are displayed in the share sheet that appears when people choose an Action button.
- In macOS, people access share extensions by clicking a Share button in the toolbar or choosing Share in a context menu. People can access an action extension by holding the pointer over certain types of embedded content — like an image they add to a Mail compose window — clicking a toolbar button, or choosing a quick action in a Finder window.

**If necessary, create a custom interface that feels familiar to people.** For a share extension, prefer the system-provided composition view because it provides a consistent sharing experience that people already know. For an action extension, include your app name. If you need to present an interface, include elements of your app's interface to help people understand that your extension and your app are related.

**Streamline and limit interaction.** People appreciate extensions that let them perform a task in just a few steps. For example, a share extension might immediately post an image to a social media account with a single tap or click.

**Avoid placing a modal view above your extension.** By default, the system displays an extension within a modal view. While it might be necessary to display an alert above an extension, avoid displaying additional modal views.

**If necessary, provide an image that communicates the purpose of your extension.** A share extension automatically uses your app icon, helping give people confidence that your app provided the extension. For an action extension, prefer using a symbol or creating an interface icon that clearly identifies the task.

**Use your main app to denote the progress of a lengthy operation.** An activity view dismisses immediately after people complete the task in your share or action extension. If a task is time-consuming, continue it in the background, and give people a way to check the status in your main app. Although you can use a notification to tell people about a problem, don't notify them simply because the task completes.

## Platform considerations

No additional considerations for iOS, iPadOS, or visionOS. The activity view (share sheet) itself is not supported in macOS, tvOS, or watchOS — however, macOS does support share and action app extensions, accessed through a Share button in the toolbar, a context menu, or a Finder quick action, rather than through an activity view.

## Specifications

| Item | Value |
|---|---|
| Custom activity interface icon | Centered in an area of about 70x70 pixels |

## Native implementation

**Related**
- Sheets
- Popovers

**Developer documentation**
- UIActivityViewController — UIKit
- UIActivity — UIKit
- App Extension Support — Foundation

**Key APIs**
- `UIActivityViewController` — UIKit, presents the activity view (share sheet)
- `UIActivity` — UIKit, defines a custom app-specific activity
- App Extension Support (Foundation) — underlies share and action extensions

**Videos:** Design for Collaboration with Messages

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**The activity view itself has a real, if thinner, web equivalent: the Web Share API.** Calling the browser's native share sheet hands off to the OS-level share surface — on a phone, this can be the exact same system share sheet Apple describes, including installed apps and system actions. This is the one part of this page that maps almost one-to-one: use the platform's native share trigger rather than building a custom "share" dropdown, for the same reason Apple gives — people already know how the system share surface works and trust it.

**Where the web falls short: app-specific activities and installable extensions have no equivalent.** Apple's model lets an app both consume the share sheet (offering it to others) and extend it (installing new items into other apps' share sheets) system-wide. A website can trigger the OS share sheet, but it cannot register a persistent "share target" the way a native app extension can, and it has no way to add an item to other apps' menus. Progressive Web Apps can register as a Web Share Target once installed, which is the closest analogue, but it requires installation and platform support that isn't universal.

**"Avoid duplicating actions already available" → still holds, but the failure mode differs.** On the web the more common mistake is building a full custom share modal (icons for Twitter, Facebook, email, copy-link) that duplicates what `navigator.share()` already offers for free on supporting browsers, and that looks visually stale the moment a platform adds or removes a service. Feature-detect Web Share support and fall back to a custom list only where it's unavailable (mainly desktop browsers), rather than defaulting to a custom UI everywhere.

**Custom icon sizing → doesn't transfer; there is no equivalent surface to size for.** The 70x70-pixel guidance is specific to the native activity view's icon grid, which a web page never renders into.

**"Use your main app to denote progress" → applies to any web share flow that kicks off a background task.** If sharing triggers a slow server-side operation (uploading a file to a linked service, for instance), don't block the share affordance itself; surface progress or completion somewhere persistent in the app rather than only in a transient toast tied to the share action.

## Do / Don't

| Do | Don't |
|---|---|
| Use the Share button to trigger the activity view | Provide a separate custom way to do the same thing |
| Give custom activities succinct, verb-based titles | Include your company or product name in an action title |
| Give a custom activity a distinct title if similar to a system action | Duplicate a system-provided action like Print without differentiating it |
| Exclude activities that don't make sense in context | Show every system-provided task regardless of relevance |
| Prefer the system-provided composition view for share extensions | Build a custom composition interface without good reason |
| Streamline an extension to a few steps | Add unnecessary modal views on top of an extension |
| Track long-running tasks in your main app | Notify people just because a task finished |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
