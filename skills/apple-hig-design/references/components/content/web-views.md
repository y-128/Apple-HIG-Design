---
title: Web views
url: https://developer.apple.com/design/human-interface-guidelines/web-views
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Web views

A web view loads and displays rich web content, such as embedded HTML and websites, directly within your app.

## Core guidance

For example, Mail uses a web view to show HTML content in messages.

### Best practices

**Support forward and back navigation when appropriate.** Web views support forward and back navigation, but this behavior isn't available by default. If people are likely to use your web view to visit multiple pages, allow forward and back navigation, and provide corresponding controls to initiate these features.

**Avoid using a web view to build a web browser.** Using a web view to let people briefly access a website without leaving the context of your app is fine, but Safari is the primary way people browse the web. Attempting to replicate the functionality of Safari in your app is unnecessary and discouraged.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, or visionOS. Not supported in tvOS or watchOS.

## Native implementation

**Related**
- Webkit.org

**Developer documentation**
- `WKWebView` — WebKit

**Key APIs**
- `WKWebView` — WebKit

**Videos:** Explore WKWebView additions

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and this topic inverts the usual exercise. Every other reference in this collection asks "what's the web equivalent of this native pattern?" Here, the native pattern *is* the web — a web view is a native app embedding a browser engine to show HTML content. There's no analogy to construct; the two sides of the mapping are the same technology viewed from opposite directions. What's worth carrying over instead are the two constraints Apple states, because they say something about how a *host* should treat embedded web content, which is directly useful for anyone who builds the pages that end up loaded inside one.

**"Support forward/back navigation when appropriate" → a page loaded in a web view should not assume it has a surrounding browser chrome.** If your web content is likely to be embedded (in Mail, in a third-party app's help viewer, in an in-app browser tab), don't rely on the user having visible browser back/forward buttons — the host app decides whether to expose that navigation, and Apple's own guidance says it isn't there by default. Pages that provide their own in-page navigation cues, or that avoid multi-step flows assuming free browser navigation, degrade more gracefully when embedded.

**"Avoid using a web view to build a web browser" → this is a statement about the host app, not about the web content itself, and has no meaningful web-side translation.** It's advice for the native developer choosing whether to reinvent Safari; a web page has no way to know or control whether it's being rendered inside a full browser or a constrained in-app web view, so there's nothing for web authors to act on here.

**If you are the web content being loaded, the transferable principle is: assume a reduced, unpredictable chrome.** An in-app web view may lack an address bar, may restrict pop-ups or new-tab behavior, and may not have all your book-marking or share affordances available. Building for graceful degradation — no dependency on `window.open` succeeding, no assumption that history state is user-visible — makes a page behave reasonably whether it loads in Safari or inside someone else's `WKWebView`.

## Do / Don't

| Do | Don't |
|---|---|
| Provide forward/back controls if people will visit multiple pages in your web view | Assume forward/back navigation is available by default |
| Use a web view to show web content briefly within your app's context | Try to replicate Safari's full browsing functionality in your app |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
