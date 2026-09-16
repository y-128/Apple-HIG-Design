---
title: Token fields
url: https://developer.apple.com/design/human-interface-guidelines/token-fields
platforms: [macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Token fields

A token field is a type of text field that can convert text into tokens that are easy to select and manipulate.

## Core guidance

For example, Mail uses token fields for the address fields in the compose window. As people enter recipients, Mail converts the text that represents each recipient's name into a token. People can select these recipient tokens and drag to reorder them or move them into a different field.

You can configure a token field to present people with a list of suggestions as they enter text into the field. For example, Mail suggests recipients as people type in an address field. When people select a suggested recipient, Mail inserts the recipient into the field as a token.

An individual token can also include a contextual menu that offers information about the token or editing options. For example, a recipient token in Mail includes a contextual menu with commands for editing the recipient name, marking the recipient as a VIP, and viewing the recipient's contact card, among others.

Tokens can also represent search terms in some situations; for guidance, see Search fields.

### Best practices

**Add value with a context menu.** People often benefit from a context menu with additional options or information about a token.

**Consider providing additional ways to convert text into tokens.** By default, text people enter turns into a token whenever they type a comma. You can specify additional shortcuts, such as pressing Return, that also invoke this action.

**Consider customizing the delay the system uses before showing suggested tokens.** By default, suggestions appear immediately. However, suggestions that appear too quickly may distract people while they're typing. If your app suggests tokens, consider adjusting the delay to a comfortable level.

## Platform considerations

Not supported in iOS, iPadOS, tvOS, visionOS, and watchOS. This is a macOS-only component with no cross-platform variant to compare against.

## Native implementation

**Related**
- Text fields
- Search fields
- Context menus

**Developer documentation**
- `NSTokenField` — AppKit

**Key APIs**
- `NSTokenField` — the sole API surface for this component, covering both the conversion behavior and the suggestion list

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mapping below applies the same principles to the web; it is inference, not Apple policy.

**A token field is what the web ecosystem usually calls a "tag input" or "multi-select combobox" — the closest standardized reference point is the WAI-ARIA combobox pattern with a listbox of selectable, removable values, since there is no native HTML element for it.** The reasoning behind Apple's control is the same reasoning that makes tag inputs useful anywhere: free text is ambiguous and hard to edit as a unit once several values sit in the same field, so converting each committed value into a discrete, selectable chip removes that ambiguity and lets someone reorder or delete one value without retyping the rest.

**"Text converts to a token on comma (configurably also on Return)" → the delimiter-commit pattern maps directly, but the web needs explicit `keydown` handling since there's no built-in equivalent.** The design principle worth keeping is Apple's default choice itself: commit on an unambiguous delimiter (comma) and optionally also on Return, rather than committing on every space or on blur, which would break multi-word values.

**Drag-to-reorder tokens → this is a solved, well-supported web interaction (native HTML5 drag-and-drop or a library-driven sortable list), but the accessibility gap is real and Apple's native control gets this for free through VoiceOver where a hand-rolled web widget does not.** A reorderable token list needs a keyboard-operable equivalent — typically arrow keys to move focus between tokens and a modifier or explicit "move" mode to reorder — because drag gestures alone exclude keyboard and switch-control users.

**Per-token contextual menu → each token needs its own accessible name and its own means of invoking a menu (a visible affordance, not only a right-click), since right-click-only interactions are invisible to touch and to many assistive technologies.** Mail's example — editing the name, marking VIP, viewing the contact card — illustrates that the menu is contextual to *that specific token's* underlying data, not a generic edit menu, so the web equivalent needs the same per-item data binding, not a single shared menu attached to the field.

**Suggestion delay → this is the same type-ahead accessibility tension documented in search-fields.md, and it applies with equal force here.** Apple's own guidance — that suggestions appearing too quickly can distract people while typing — is itself evidence that even Apple treats live-suggestion timing as a real UX cost, not just an accessibility afterthought; a debounce on the order of a couple hundred milliseconds before showing or announcing suggestions is a reasonable default on the web, tunable the same way `NSTokenField`'s delay is.

**Where the mapping is clean: token-as-filter (cross-referenced from Search fields) → this is exactly a faceted-search chip, a pattern the web already does well,** each chip representing one active filter term, removable independently, typically rendered above or beside the result set it constrains.

## Do / Don't

| Do | Don't |
|---|---|
| Convert committed text into a discrete, selectable token | Leave multiple values as one ambiguous run of free text |
| Support at least one clear delimiter (comma) to commit a token | Commit tokens on ambiguous triggers like spaces or blur |
| Give each token its own contextual menu tied to its own data | Attach one generic menu to the whole field regardless of which token is selected |
| Let people drag tokens to reorder, with a keyboard equivalent | Ship drag-to-reorder with no non-pointer alternative |
| Tune suggestion delay so it doesn't distract while typing | Fire suggestions on every keystroke with no debounce |
| Pair token suggestions with visible options people can discover | Expect people to guess which tokens the field will accept |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
