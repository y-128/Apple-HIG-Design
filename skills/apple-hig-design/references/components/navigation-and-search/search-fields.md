---
title: Search fields
url: https://developer.apple.com/design/human-interface-guidelines/search-fields
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2026-06-08
---

# Search fields

A search field lets people search a collection of content for specific terms they enter.

## Core guidance

A search field is an editable text field that displays a Search icon, a Clear button, and placeholder text where people can enter what they are searching for. Search fields can use a scope bar as well as tokens to help filter and refine the scope of their search. Across each platform, there are different patterns for accessing search based on the goals and design of your app.

For developer guidance, see Adding a search interface to your app; for guidance related to systemwide search, see Searching.

### Best practices

**Use placeholder text to help people know what they can search for.** Placeholder text can be helpful when you need to reinforce the scope of your search or to educate people about the type of content that search has access to.

**If possible, start search immediately when a person types.** Searching while someone types makes the search experience feel more responsive because it provides results that are continuously refined as the text becomes more specific. This single sentence is Apple's entire position on type-ahead search — start on keystroke, not on submit — and it is also the source of the hardest accessibility problem in this document (see Web translation below).

**Consider showing suggested search terms.** For example, you can display recent searches before search begins, or predictive search suggestions as a person types. This can help someone search faster, even when the search itself doesn't begin immediately.

**Simplify search results.** Provide the most relevant search results first to minimize the need for someone to scroll to find what they're looking for. In addition to prioritizing the most likely results, consider categorizing them to help people find what they want.

**Consider letting people filter search results.** For example, you can include a scope bar in the search results content area to help people quickly and easily filter search results.

### Scope bars and tokens

Scope bars and tokens are components you can use to let someone narrow the parameters of a search either before or after they make it.

- A **scope bar** is a control for filtering and adjusting the scope of a search.
- A **token** is a visual representation of a search term that someone can select and edit, and acts as a filter for any additional terms in the search.

**Use a scope bar to filter among clearly defined search categories.** A scope bar can help someone move from a broader scope to a narrower one. For example, in Mail on iPhone, a scope bar helps people move from searching their entire mailbox to just the specific mailbox they're viewing. For developer guidance, see Scoping a search operation.

**Default to a broader scope and let people refine it as they need.** A broader scope provides context for the full set of available results, which helps guide people in a useful direction when they choose to narrow the scope.

**Use tokens to filter by common search terms or items.** When you define a token, the term it represents gains a visual treatment that encapsulates it, indicating that people can select and edit it as a single item. Tokens can clarify a search term, like filtering by a specific contact in Mail, or focus a search to a specific set of attributes, like filtering by photos in Messages. For the related macOS component, see Token fields.

**Consider pairing tokens with search suggestions.** People may not know which tokens are available, so pairing them with search suggestions can help people learn how to use them.

## Platform considerations

No additional considerations for visionOS.

### iOS

There are three main places you can position the entry point for search:

- As a tab in a tab bar
- In a toolbar at the bottom or top of the screen
- Directly inline with content

Where search makes the most sense depends on the layout, content, and navigation of your app.

**Search as a tab.** You can place search as a tab in a tab bar, which keeps search visible and always available as people switch between the sections of your app. There are two styles of search tabs:

- **Standard tab.** This style displays the search tab uniformly with the rest of the tab bar. Tapping the search tab navigates people to a search landing page with a search field at the top.
- **Button appearance.** This style displays the search tab as a separate button and allows people to start searching immediately. Tapping the search tab brings focus to the search field and displays the keyboard.

> *Image caption:* Standard tab and Button appearance styles of a search tab, side by side.

**Choose the standard tab style to provide suggestions, promote discovery, and encourage exploration.** This style of search tab creates a dedicated landing page for search, providing an opportunity to reveal any content or suggestions that might be helpful before someone taps the field to begin the search. This approach is great for an app with a variety of rich content that people might want to explore. For example, Apple TV uses this search tab style to present its various genres and categories, helping ground people in what's available before they search.

**Choose the button appearance to help people quickly find what they need.** When someone interacts with this style of search tab, the keyboard immediately appears with the search field above it, ready to begin the search. This approach provides a more transient experience that brings people directly back to their previous tab after they exit search, and is ideal when you want search to resolve quickly and seamlessly.

**Search in a toolbar.** As an alternative to search in a tab bar, you can also place search in a toolbar either at the bottom or top of the screen.

- You can include search in a bottom toolbar either as an expanded field or as a toolbar button, depending on how much space is available. When someone taps it, it animates into a search field above the keyboard so they can begin typing.
- You can include search in a top toolbar, also called a navigation bar, where it appears as a toolbar button. When someone taps it, it animates into a search field that appears either above the keyboard or at the top if there isn't space at the bottom.

> *Image caption:* Search in a bottom toolbar and Search in a top toolbar, side by side.

**Place search at the bottom if there's room.** You can either add a search field to an existing toolbar, or as a new toolbar where search is the only item. Search at the bottom is useful in any situation where search is a priority, since it keeps the search experience easy to reach. Examples of apps with search at the bottom in various toolbar layouts include Settings, where it's the only item, and Mail and Notes, where it fits alongside other important controls.

**Place search at the top when it's important to defer to content at the bottom of the screen, or there's no bottom toolbar.** Use search at the top in cases where covering the content might interfere with a primary function of the app. The Wallet app, for example, includes event passes in a stack at the bottom of the screen for easy access and viewing at a glance.

**Search as an inline field.** In some cases you might want your app to include a search field inline with content.

**Place search as an inline field when its position alongside the content it searches strengthens that relationship.** When you need to filter or search within a single view, it can be helpful to have search appear directly next to content to illustrate that the search applies to it, rather than globally. This pattern is useful if your app has more than one search field and if location plays a critical role in the scope of your search. For example, although the main search in the Music app is a tab, people can navigate to their library and use an inline search field to filter their songs and albums.

**When at the top, position an inline search field above the list it searches, and consider pinning it to the top toolbar when scrolling.** This helps keep it distinct from search that appears in other locations.

### iPadOS, macOS

The placement and behavior of the search field in iPadOS and macOS is similar. If your app is available on both iPad and Mac, try to keep the search experience as consistent as possible across both platforms.

> *Image caption:* Search field placement compared side by side between iPadOS and macOS.

**Put a search field at the trailing side of the toolbar for many common uses.** Many apps benefit from the familiar pattern of search in the toolbar, particularly apps with split views that need to search across multiple columns of information, like Mail, Notes, and Voice Memos. This placement makes great use of space because it lets people navigate results while keeping their selection visible in the detail view. Additionally, consider placing search in the toolbar if results appear in the detail view of your app, like in Freeform, where search in the toolbar filters the boards in the detail view below.

**Include search at the top of the sidebar when filtering content or navigation there.** Apps such as Settings take advantage of search to quickly filter the sidebar and expose sections that may be multiple levels deep, providing a simple way for people to search, preview, and navigate to the section or setting they're looking for. This approach is useful if your app has a rich detail view and you need to create a distinct separation between the sidebar you're filtering and the adjacent view.

**Include search as an item in the sidebar or tab bar when you want an area dedicated to discovery.** If your search is paired with rich suggestions, categories, or content that needs more space, it can be helpful to have a dedicated area for it. This is particularly useful for apps where browsing and search go hand in hand, like Music and TV, where it provides a unified location to highlight suggested content, categories, and recent searches. A dedicated area also ensures search is always available as people navigate and switch sections of your app.

**In a search field in a dedicated area, consider immediately focusing the field when a person navigates to the area** to help them search faster and locate the field more easily. An exception to this is on iPad when only a virtual keyboard is available, in which case it's better to leave the field unfocused to prevent the keyboard from unexpectedly covering the view.

**Account for window resizing with the placement of the search field.** On iPad, the search field fluidly resizes with the app window like it does on Mac. However, for compact views on iPad, it's important to ensure that search is available where it's most contextually useful. For example, Notes and Mail place search above the column for the content list when they resize down to a compact view.

### tvOS

A search screen is a specialized keyboard screen that helps people enter search text, displaying search results beneath the keyboard in a fully customizable view. For developer guidance, see `UISearchController`.

**Provide suggestions to make searching easier.** People typically don't want to do a lot of typing in tvOS. To improve the search experience, provide popular and context-specific search suggestions, including recent searches when available. For developer guidance, see Using suggested searches with a search controller.

### watchOS

When someone taps the search field, the system displays a text-input control that covers the entire screen. The app only returns to the search field after they tap the Cancel or Search button.

## Native implementation

**Related**
- Searching
- Token fields

**Developer documentation**
- Adding a search interface to your app — SwiftUI
- `searchable(text:placement:prompt:)` — SwiftUI
- `UISearchBar` — UIKit
- `UISearchTextField` — UIKit
- `NSSearchField` — AppKit
- `UISearchController` — UIKit (tvOS search screen)

**Key APIs**
- `searchable(text:placement:prompt:)` — attach a search field to a SwiftUI view with placement control
- `UISearchBar` / `UISearchTextField` — UIKit search field components
- `NSSearchField` — AppKit search field component
- Scoping a search operation — developer guidance for implementing scope bars

**Videos:** Design intuitive search experiences · Get to know the new design system · Discoverable design

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A search field is `role="searchbox"` (or a native `<input type="search">`), not a generic textbox.** The semantic distinction matters because assistive technology announces it differently and browsers attach native behavior (an `x` clear affordance in most engines) that mirrors Apple's built-in Clear button. Wrapping the field in a `<form role="search">` or a `search` landmark element gives screen reader users a way to jump straight to it, the web equivalent of search having a guaranteed, discoverable position on every Apple platform.

**"Start search immediately when a person types" → this is where the web's accessibility model and Apple's UX goal genuinely conflict, and it's worth stating plainly.** Live, on-keystroke result updates are exactly the pattern that ARIA live regions handle badly by default: a naive `aria-live="polite"` region re-announces on every keystroke, which for a screen reader user produces a torrent of interruption rather than help, and `aria-live="assertive"` is worse. There is no clean out-of-the-box fix — the practical mitigations are debouncing announcements (announce the result *count* after typing pauses, not after every character), using `aria-live="polite"` sparingly and only for the summary line rather than the full result list, and pairing it with `aria-describedby` or an `aria-activedescendant` pattern for suggestion navigation via arrow keys rather than relying on live-region narration alone. This is a case where Apple's platform-level type-ahead (built into `UISearchBar`/`NSSearchField` with mature VoiceOver integration already solved) gives Apple a head start that the open web has to hand-build every time.

**Scope bar → a `role="tablist"` or a button group scoped to the search results region, not global navigation.** This is the one place in this component family where ARIA tabs *are* the right pattern, because a scope bar genuinely behaves like Apple describes browser tabs: mutually exclusive, all filtering the same content region, with only one active at a time. Don't confuse this with the tab-bars document's warning against using `tablist` for primary navigation — the difference is that a scope bar's "tabs" don't change the page or the URL, they filter a result set in place.

**Tokens → see the token-fields document for the shared pattern**, since Apple explicitly cross-references the two. The type-ahead accessibility problem described above compounds when token suggestions are also live-updating; treat suggestion lists and result lists as separate live regions so a screen reader user isn't narrated both at once.

**Placement flexibility (tab, toolbar, inline, sidebar) → this maps to responsive layout decisions, not to a single canonical web search-bar position.** Apple's own guidance is explicitly that placement depends on app structure — there is no universal "put search here" rule even within Apple's platforms, so don't treat a persistent top-right search icon as more authoritative than it is. The more load-bearing principle to port is Apple's placement logic itself: search that's central to the product deserves a permanent, low-friction slot (Apple's bottom-toolbar or dedicated-tab treatment); search that's secondary or scoped to one view can appear inline and load on demand.

**Full-screen search takeover (watchOS) → the mobile web equivalent is a focus-trapped search overlay**, and the accessibility requirement is the same regardless of platform: trap focus within the overlay while it's open, return focus to the triggering control on close, and make the exit action (Cancel/Escape) unambiguous and keyboard-reachable.

## Do / Don't

| Do | Don't |
|---|---|
| Show placeholder text that reinforces the scope of the search | Leave the field with no hint about what it searches |
| Start returning results as a person types, when feasible | Require an explicit submit for every search |
| Surface recent or predictive suggestions before typing begins | Present a blank field with zero starting guidance |
| Default to a broad scope and let people narrow it | Default to an overly narrow scope that hides relevant results |
| Use a scope bar for clearly defined, mutually exclusive categories | Use a scope bar for open-ended or overlapping filters |
| Pair tokens with search suggestions so people learn what's available | Introduce tokens with no way to discover them |
| On iPad, leave the field unfocused when only a virtual keyboard is available | Auto-focus search and cover the view with the keyboard unexpectedly |
| Keep the iPad and Mac search experience consistent for cross-platform apps | Diverge search placement between iPad and Mac without reason |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
