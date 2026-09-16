---
title: Right to left
url: https://developer.apple.com/design/human-interface-guidelines/right-to-left
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: unknown
---

# Right to left

Support right-to-left languages like Arabic and Hebrew by reversing your interface as needed to match the reading direction of the related scripts.

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

When people choose a language for their device — or just your app or game — they expect the interface to adapt in various ways (to learn more, see Localization).

System-provided UI frameworks support right-to-left (RTL) by default, allowing system-provided UI components to flip automatically in the RTL context. If you use system-provided elements and standard layouts, you might not need to make any changes to your app's automatically reversed interface.

If you want to fine-tune your layout or enhance specific localizations to adapt to different currencies, numerals, or mathematical symbols that can occur in various locales in countries that use RTL languages, follow these guidelines.

## Core guidance

### Text alignment

**Adjust text alignment to match the interface direction, if the system doesn't do so automatically.** For example, if you left-align text with content in the left-to-right (LTR) context, right-align the text to match the content's mirrored position in the RTL context.

> *Image caption:* Left-aligned text in the LTR context.
> *Image caption:* Right-aligned content in the RTL context.

**Align a paragraph based on its language, not on the current context.** When the alignment of a paragraph — defined as three or more lines of text — doesn't match its language, it can be difficult to read. For example, right-aligning a paragraph that consists of LTR text can make the beginning of each line difficult to see. To improve readability, continue aligning one- and two-line text blocks to match the reading direction of the current context, but align a paragraph to match its language.

> *Image caption:* A left-aligned paragraph in the RTL context.
> *Image caption:* A right-aligned paragraph in the RTL context.

**Use a consistent alignment for all text items in a list.** To ensure a comfortable reading and scanning experience, reverse the alignment of all items in a list, including items that are displayed in a different script.

> *Image caption:* Right-aligned content in the RTL context.
> *Image caption:* Mixed alignment in the RTL content.

### Numbers and characters

Different RTL languages can use different number systems. For example, Hebrew text uses Western Arabic numerals, whereas Arabic text might use either Western or Eastern Arabic numerals. The use of Western and Eastern Arabic numerals varies among countries and regions and even among areas within the same country or region.

If your app covers mathematical concepts or other number-centric topics, it's a good idea to identify the appropriate way to display such information in each locale you support. In contrast, apps that don't address number-related topics can generally rely on system-provided number representations.

> *Image caption:* Western Arabic numerals.
> *Image caption:* Eastern Arabic numerals.

**Don't reverse the order of numerals in a specific number.** Regardless of the current language or the surrounding content, the digits in a specific number — such as "541," a phone number, or a credit card number — always appear in the same order.

> *Image caption:* Latin.
> *Image caption:* Hebrew.
> *Image caption:* Arabic (Western Arabic numerals).
> *Image caption:* Arabic (Eastern Arabic numerals).

**Reverse the order of numerals that show progress or a counting direction; never flip the numerals themselves.** Controls like progress bars, sliders, and rating controls often include numerals to clarify their meaning. If you use numerals in this way, be sure to reverse the order of the numerals to match the direction of the flipped control. Also reverse a sequence of numerals if you use the sequence to communicate a specific order.

> *Image caption:* Latin.
> *Image caption:* Arabic (Eastern Arabic numerals).
> *Image caption:* Hebrew.
> *Image caption:* Arabic (Western Arabic numerals).

### Controls

**Flip controls that show progress from one value to another.** Because people tend to view forward progress as moving in the same direction as the language they read, it makes sense to flip controls like sliders and progress indicators in the RTL context. When you do this, also be sure to reverse the positions of the accompanying glyphs or images that depict the beginning and ending values of the control.

> *Image caption:* A directional control in the LTR context.
> *Image caption:* A directional control in the RTL context.

**Flip controls that help people navigate or access items in a fixed order.** For example, in the RTL context, a back button must point to the right so the flow of screens matches the reading order of the RTL language. Similarly, next or previous buttons that let people access items in an ordered list need to flip in the RTL context to match the reading order.

**Preserve the direction of a control that refers to an actual direction or points to an onscreen area.** For example, if you provide a control that means "to the right," it must always point right, regardless of the current context.

**Visually balance adjacent Latin and RTL scripts when necessary.** In buttons, labels, and titles, Arabic or Hebrew text can appear too small when next to uppercased Latin text, because Arabic and Hebrew don't include uppercase letters. To visually balance Arabic or Hebrew text with Latin text that uses all capitals, it often works well to increase the RTL font size by about **2 points**.

> *Image caption:* Arabic and Hebrew text can look too small next to uppercased Latin text of the same font size.
> *Image caption:* You can slightly increase the font size of Arabic and Hebrew text to visually balance uppercased Latin text.

### Images

**Avoid flipping images like photographs, illustrations, and general artwork.** Flipping an image often changes the image's meaning; flipping a copyrighted image could be a violation. If an image's content is strongly connected to reading direction, consider creating a new version of the image instead of flipping the original.

**Reverse the positions of images when their order is meaningful.** For example, if you display multiple images in a specific order like chronological, alphabetical, or favorite, reverse their positions to preserve the order's meaning in the RTL context.

> *Image caption:* Items with meaningful positions in the LTR context.
> *Image caption:* Items with meaningful positions in the RTL context.

### Interface icons

When you use SF Symbols to supply interface icons for your app, you get variants for the RTL context and localized symbols for Arabic and Hebrew, among other languages. If you create custom symbols, you can specify their directionality. For developer guidance, see Creating custom symbol images for your app.

> *Image caption:* LTR variants of directional symbols.
> *Image caption:* RTL variants of directional symbols.

**Flip interface icons that represent text or reading direction.** For example, if an interface icon uses left-aligned bars to represent text in the LTR context, right-align the bars in the RTL context.

> *Image caption:* LTR variant of a symbol that represents text.
> *Image caption:* RTL variant of a symbol that represents text.

**Consider creating a localized version of an interface icon that displays text.** Some interface icons include letters or words to help communicate a script-related concept, like font-size choice or a signature. If you have a custom interface icon that needs to display actual text, consider creating a localized version. For example, SF Symbols offers different versions of the signature, rich-text, and I-beam pointer symbols for use with Latin, Hebrew, and Arabic text, among others.

> *Image caption:* Latin.
> *Image caption:* Hebrew.
> *Image caption:* Arabic.

**If you have a custom interface icon that uses letters or words to communicate a concept unrelated to reading or writing, consider designing an alternative image that doesn't use text.**

**Flip an interface icon that shows forward or backward motion.** When something moves in the same direction that people read, they typically interpret that direction as forward; when something moves in the opposite direction, people tend to interpret the direction as backward. An interface icon that depicts an object moving forward or backward needs to flip in the RTL context to preserve the meaning of the motion. For example, an icon that represents a speaker typically shows sound waves emanating forward from the speaker. In the LTR context, the sound waves come from the left, so in the RTL context, the icon needs to flip to show the waves coming from the right.

> *Image caption:* LTR variant of a symbol that depicts forward motion.
> *Image caption:* RTL variant of a symbol that depicts forward motion.

**Don't flip logos or universal signs and marks.** Displaying a flipped logo confuses people and can have legal repercussions. Always display a logo in its original form, even if it includes text. People expect universal symbols and marks like the checkmark to have a consistent appearance, so avoid flipping them.

> *Image caption:* A logo.
> *Image caption:* A universal symbol or mark.

**In general, avoid flipping interface icons that depict real-world objects.** Unless you use the object to indicate directionality, it's best to avoid flipping an icon that represents a familiar item. For example, clocks work the same everywhere, so a traditional clock interface icon needs to look the same regardless of language direction. Some interface icons might seem to reference language or reading direction because they represent items that are slanted for right-handed use. However, most people are right-handed, so flipping an icon that shows a right-handed tool isn't necessary and might be confusing.

**Before merely flipping a complex custom interface icon, consider its individual components and the overall visual balance.** In some cases, a component — like a badge, slash, or magnifying glass — needs to adhere to a visual design language regardless of localization. For example, SF Symbols maintains visual consistency by using the same backslash to represent the prohibition or negation of a symbol's meaning in both LTR and RTL versions.

> *Image caption:* LTR variant of a symbol that includes a backslash.
> *Image caption:* RTL variant of a symbol that includes a backslash.

In other cases, you might need to flip a component (or its position) to ensure the localized version of the icon still makes sense. For example, if a badge represents the actual UI that people see in your app, it needs to flip if your UI flips. Alternatively, if a badge modifies the meaning of an interface icon, consider whether flipping the badge preserves both the modified meaning and the overall visual balance of the icon. In one of Apple's examples, the badge doesn't depict an object in the UI, but keeping it in the top-right corner visually unbalances the cart it decorates.

**If your custom interface icon includes a component that can imply handedness, like a tool, consider preserving the orientation of the tool while flipping the base image if necessary.**

> *Image caption:* LTR variant of a symbol that depicts a tool.
> *Image caption:* RTL variant of a symbol that depicts a tool.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS. The guidance above applies uniformly across all six platforms.

## Native implementation

**Related**
- Layout
- Inclusion
- SF Symbols

**Developer documentation**
- Localization
- Preparing views for localization — SwiftUI
- Creating custom symbol images for your app

**Videos:** Enhance your app's multilingual experience · Design for Arabic

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy. Right-to-left support is one of the areas where the web's native mechanisms map unusually closely to what Apple describes for its platforms, because both are built on the same underlying foundation: the Unicode Bidirectional Algorithm.

**"System-provided UI frameworks support RTL by default" → `dir="rtl"` and the browser's own bidi engine.** Setting `dir="rtl"` on `html` (or on a subtree) is the web's equivalent of choosing an RTL language on an Apple device: it flips the box model, text alignment, and native form controls automatically, the same way Apple's system frameworks flip system-provided components without extra work from the developer. Just as Apple says you "might not need to make any changes" if you stick to system-provided elements and standard layouts, a page built entirely from native HTML elements and logical CSS properties often needs no additional RTL-specific code beyond the `dir` attribute.

**"Adjust text alignment to match the interface direction" → CSS logical properties instead of physical ones.** Apple's underlying point is that a hardcoded left/right choice breaks the moment the reading direction flips. The web's answer is logical properties: `text-align: start` / `end` instead of `left` / `right`, and `margin-inline-start`, `padding-inline-end`, `border-inline-start`, `inset-inline-start`, and so on instead of their physical equivalents. These resolve automatically based on `dir` and `writing-mode`, so a layout written entirely in logical properties mirrors itself the same way Apple's system-provided layouts do — with zero conditional logic. Any hardcoded `left`/`right` value is a spot that will not flip, which is the direct web analogue of a hand-placed layout that Apple warns needs manual attention.

**"Align a paragraph based on its language, not the current context" → per-element `dir`, not just a page-level attribute.** The `dir` attribute is not limited to `html`; it can be set on any element, including a `blockquote` or a `span` wrapping a quoted passage in a different script. This is the direct equivalent of Apple's instruction to align a paragraph to match its own language even when the surrounding interface reads the other way. The `unicode-bidi` CSS property and the `bdi` element exist specifically to isolate a run of text so its own directionality doesn't leak into or get overridden by its container — a finer-grained tool than Apple's platforms expose, because the web more often mixes scripts within a single flow of prose.

**"Don't reverse the order of numerals in a specific number" → mostly automatic, because of how the bidi algorithm treats digits.** The Unicode Bidirectional Algorithm treats digits as their own directional category and keeps them in their original left-to-right internal order even when embedded in an RTL run, which is exactly the behavior Apple is asking developers to preserve by hand. This mapping mostly holds without extra work as long as numbers are kept as ordinary Unicode text; it breaks down only if a developer manually reverses the character order of a numeric string before rendering it, which defeats the algorithm and reproduces the bug Apple is warning against.

**"Reverse the order of numerals that show progress" → application logic, not something the browser infers.** Unlike plain numeral order, the meaning of "step 3 of 5" reversing to read right-to-left when a progress control flips is domain logic, not text layout. There's no CSS property that knows a numeral sequence represents progress; the same manual reversal Apple describes has to happen in the app's own rendering logic, gated on `dir` or the `:dir(rtl)` pseudo-class.

**"Flip controls that show progress" and "flip controls that help people navigate" → the `:dir()` pseudo-class and logical transforms, with no automatic icon flipping.** Native form controls like `<input type="range">` and `<progress>` inherit some mirroring from `dir` automatically, but custom-built sliders, carousels, and back/next affordances do not — the developer has to detect direction (via `:dir(rtl)` in CSS, or the resolved `dir` in script) and apply the flip deliberately, exactly as Apple describes for custom controls. This is a real gap relative to native platforms: SF Symbols ships curated RTL variants of directional icons out of the box, and there is no equivalent shared, curated icon set on the web. Mirroring an icon on the web is a manual `transform: scaleX(-1)`-class operation applied per icon, conditioned on direction, with no system-level curation deciding which icons should and shouldn't flip.

**"Preserve the direction of a control that refers to an actual direction" and "don't flip logos or universal signs" → the same selective-mirroring judgment, now the developer's to make.** The reasoning Apple gives — mirror things whose meaning is tied to reading-direction semantics (progress, forward motion, navigation order), and never mirror things whose meaning is fixed regardless of script (logos, universal marks, real-world objects like clocks, numerals themselves) — carries over to the web unchanged, but nothing in CSS enforces the distinction. A common, well-documented instance of this on the web is media transport controls: a play button, a video scrubber's time display, and volume icons conventionally do not mirror in RTL interfaces even though the surrounding chrome does, because their meaning is anchored to universal media conventions rather than to reading direction — the same logic Apple applies to clocks and checkmarks.

**"Visually balance adjacent Latin and RTL scripts" → per-script font-size and metrics adjustment via `:lang()` or `:dir()`.** Apple's "+2pt" guidance exists because Arabic and Hebrew have no uppercase letters and so read smaller next to all-caps Latin at the same nominal size. The web equivalent is scoping a slightly larger `font-size` (or adjusting `line-height`) to Arabic/Hebrew runs using a `:lang(ar)`, `:lang(he)`, or `:dir(rtl)` selector. Some web fonts bake compensating metrics into the font file itself, which reduces but doesn't eliminate the need for this manual adjustment, particularly when Latin and RTL runs are set in different typefaces with different cap-heights.

**Where the mapping genuinely breaks down.** The biggest structural gap is the absence of a system-curated, RTL-aware icon library on the web — Apple's SF Symbols does this centrally with LTR/RTL variant pairs and localized text-bearing symbols; on the web this curation work is either left to the individual site, delegated to a third-party icon set, or (most commonly) not done at all, which is why icon mirroring is one of the most frequently botched parts of RTL web support in practice.

## Do / Don't

| Do | Don't |
|---|---|
| Adjust text alignment to match the interface direction when the system doesn't do it automatically | Leave hardcoded left/right alignment that ignores the RTL context |
| Align a paragraph to match its own language, even inside a differently-directed interface | Right-align an LTR paragraph (or left-align an RTL one) just because the surrounding context is flipped |
| Use one consistent alignment for every item in a list, including mixed-script items | Mix alignment across list items in the same list |
| Reverse the order of numerals that show progress or a counting direction | Flip the numerals themselves when reversing a sequence's order |
| Keep the digits within a specific number (phone numbers, "541," credit card numbers) in their original order | Reverse the order of digits inside a specific number |
| Flip controls that show progress or help people navigate a fixed order | Leave a back button or progress control unflipped in the RTL context |
| Preserve the direction of a control that refers to an actual onscreen direction | Flip a control whose meaning is a literal direction (e.g. "point right") |
| Increase RTL font size by about 2 points to balance adjacent uppercase Latin text | Leave Arabic or Hebrew text looking undersized next to all-caps Latin |
| Reverse the positions of images when their order is meaningful (chronological, alphabetical, favorite) | Flip photographs, illustrations, or general artwork |
| Flip interface icons that represent text, reading direction, or forward/backward motion | Flip logos, universal signs and marks, or icons that depict real-world objects |
| Consider preserving a tool's orientation while flipping the base image, when handedness is implied | Flip an icon's core visual-language components (badge, slash, magnifying glass) without considering visual balance |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
