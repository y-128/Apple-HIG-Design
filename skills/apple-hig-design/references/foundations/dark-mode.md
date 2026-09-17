---
title: Dark Mode
url: https://developer.apple.com/design/human-interface-guidelines/dark-mode
platforms: [iOS, iPadOS, macOS, tvOS]
last_updated: 2024-08-06
---

# Dark Mode

Dark Mode is a systemwide appearance setting that uses a dark color palette to provide a comfortable viewing experience tailored for low-light environments.

## Core guidance

In iOS, iPadOS, macOS, and tvOS, people often choose Dark Mode as their default interface style, and they generally expect all apps and games to respect their preference. In Dark Mode, the system uses a dark color palette for all screens, views, menus, and controls, and may also use greater perceptual contrast to make foreground content stand out against the darker backgrounds.

### Best practices

**Avoid offering an app-specific appearance setting.** An app-specific appearance mode option creates more work for people because they have to adjust more than one setting to get the appearance they want. Worse, they may think your app is broken because it doesn't respond to their systemwide appearance choice.

**Ensure that your app looks good in both appearance modes.** In addition to using one mode or the other, people can choose the Auto appearance setting, which switches between the light and dark appearances as conditions change throughout the day, potentially while your app is running.

**Test your content to make sure that it remains comfortably legible in both appearance modes.** For example, in Dark Mode with Increase Contrast and Reduce Transparency turned on (both separately and together), you may find places where dark text is less legible when it's on a dark background. You might also find that turning on Increase Contrast in Dark Mode can result in reduced visual contrast between dark text and a dark background. Although people with strong vision might still be able to read lower contrast text, such text could be illegible for many. For guidance, see Accessibility.

**In rare cases, consider using only a dark appearance in the interface.** For example, it can make sense for an app that supports immersive media viewing to use a permanently dark appearance that lets the UI recede and helps people focus on the media.

> *Image caption:* The Stocks app uses a dark-only appearance.

### Dark Mode colors

The color palette in Dark Mode includes dimmer background colors and brighter foreground colors. It's important to realize that these colors aren't necessarily inversions of their light counterparts: while many colors are inverted, some are not.

**Embrace colors that adapt to the current appearance.** Semantic colors (like `labelColor` and `controlColor` in macOS or `separator` in iOS and iPadOS) automatically adapt to the current appearance. When you need a custom color, add a Color Set asset to your app's asset catalog in Xcode, and specify the bright and dim variants of the color. Avoid using hard-coded color values or colors that don't adapt.

> *Image caption:* System colors in the light appearance, and system colors in the dark appearance.

**Aim for sufficient color contrast in all appearances.** Using system-defined colors can help you achieve a good contrast ratio between your foreground and background content. At a minimum, make sure the contrast ratio between colors is no lower than **4.5:1**. For custom foreground and background colors, strive for a contrast ratio of **7:1**, especially in small text. This ratio ensures that your foreground content stands out from the background, and helps your content meet recommended accessibility guidelines.

**Soften the color of white backgrounds.** If you display a content image that includes a white background, consider slightly darkening the image to prevent the background from glowing in the surrounding Dark Mode context.

#### Icons and images

The system uses SF Symbols (which automatically adapt to Dark Mode) and full-color images that are optimized for both the light and dark appearances.

**Use SF Symbols wherever possible.** Symbols work well in both appearance modes when you use dynamic colors to tint them or when you add vibrancy. For guidance, see Color.

**Design separate interface icons for the light and dark appearances if necessary.** For example, an icon that depicts a full moon might need a subtle dark outline to contrast well with a light background, but need no outline when it displays on a dark background. Similarly, an icon that represents a drop of oil might need a slight border to make the edge visible against a dark background.

> *Image caption:* Icon in the light appearance with no border, and icon in the dark appearance with border for better contrast.

**Make sure full-color images and icons look good in both appearances.** Use the same asset if it looks good in both the light and dark appearances. If an asset looks good in only one mode, modify the asset or create separate light and dark assets. Use asset catalogs to combine your assets into a single named image.

> *Image caption:* Illustration on a light background; on a dark background, the same illustration has poor contrast and many details are lost; illustration adjusted for better contrast on a dark background.

#### Text

The system uses vibrancy and increased contrast to maintain the legibility of text on darker backgrounds.

**Use the system-provided label colors for labels.** The primary, secondary, tertiary, and quaternary label colors adapt automatically to the light and dark appearances.

> *Image caption:* Primary label in the light appearance, and secondary label in the dark appearance.

**Use system views to draw text fields and text views.** System views and controls make your app's text look good on all backgrounds, adjusting automatically for the presence or absence of vibrancy. When possible, use a system-provided view to display text instead of drawing the text yourself.

## Platform considerations

No additional considerations for tvOS. Dark Mode isn't supported in visionOS or watchOS.

### iOS, iPadOS

In Dark Mode, the system uses two sets of background colors — called base and elevated — to enhance the perception of depth when one dark interface is layered above another. The base colors are dimmer, making background interfaces appear to recede, and the elevated colors are brighter, making foreground interfaces appear to advance.

> *Image caption:* Base, Elevated, and Light background colors shown side by side.

**Prefer the system background colors.** Dark Mode is dynamic, which means that the background color automatically changes from base to elevated when an interface is in the foreground, such as a popover or modal sheet. The system also uses the elevated background color to provide visual separation between apps in a multitasking environment and between windows in a multiple-window context. Using a custom background color can make it harder for people to perceive these system-provided visual distinctions.

### macOS

When people choose the graphite accent color in General settings, macOS causes window backgrounds to pick up color from the current desktop picture. The result — called desktop tinting — is a subtle effect that helps windows blend more harmoniously with their surrounding content.

**Include some transparency in custom component backgrounds when appropriate.** Transparency lets your components pick up color from the window background when desktop tinting is active, creating a visual harmony that can persist even when the desktop picture changes. To help achieve this harmony, add transparency only to a custom component that has a visible background or bezel, and only when the component is in a neutral state, such as a state that doesn't use color. You don't want to add transparency when the component is in a state that uses color, because doing so can cause the component's color to fluctuate when the window background adjusts to a different location on the desktop or when the desktop picture changes.

## Native implementation

**Related**
- Color
- Materials
- Typography

**Developer documentation**
- Asset catalogs — Xcode (Color Set assets for light/dark variants)

**Key APIs**
- `labelColor`, `controlColor` — macOS semantic colors that adapt automatically to the current appearance
- `separator` — iOS, iPadOS semantic color that adapts automatically to the current appearance

**Videos:** Meet Liquid Glass · Implementing Dark Mode on iOS

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Systemwide appearance, not an app-specific toggle → respect `prefers-color-scheme`, and default any manual override to "System."** Apple's reasoning is explicit: a separate in-app light/dark setting duplicates a decision the person already made at the OS level, and a site that ignores that decision reads as broken, not merely unstyled. The direct web equivalent is the `prefers-color-scheme` media feature — style both palettes from it by default rather than shipping only a light theme and letting dark-mode users see an unstyled or manually-inverted page. If a product still wants an in-app toggle (a legitimate want — not every OS exposes the setting as prominently as Apple's own), give it three states, not two: Light, Dark, and System, where System defers to `prefers-color-scheme` exactly the way Apple's Auto setting defers to the OS.

**Semantic colors that adapt automatically → design tokens keyed by role, not by hex value.** `labelColor`, `controlColor`, and `separator` are not colors so much as named roles that resolve to different concrete values per appearance; a component that references the role never has to know which mode is active. The web analogue is a token layer — CSS custom properties or a design-token system — where components consume `--color-text-primary` or `--color-separator` and the token's resolved value flips per appearance, rather than components branching on a theme class internally. This is also why hard-coded hex values scattered through component code are the thing to avoid on both platforms: the failure mode Apple names ("colors that don't adapt") is identical to a web codebase with inline `color: #111` values that nobody remembers to pair with a dark variant.

**"These colors aren't necessarily inversions of their light counterparts" → don't build dark mode with a filter.** This is the load-bearing sentence in the source, and it rules out the cheapest web implementation: applying `filter: invert()` (or a CSS `color-scheme: dark` blanket switch with no custom palette) to a light design and calling it done. A mathematical inversion also inverts photographs, brand colors, and anything that was already dark-on-light for a *reason* — a red error color inverts to a cyan that no longer reads as "error." Apple hand-tunes a dark palette where some values invert and some deliberately don't; the web equivalent is the same discipline — a designed dark palette with its own contrast decisions, not a computed transform of the light one.

**Base and elevated backgrounds → lightness carries elevation on dark surfaces, because shadow stops working.** This is the clearest and most underused mapping. On a light background, a drop shadow reads as elevation because it darkens the area behind a raised surface relative to a bright backdrop — the mechanism depends on there being room to go darker. On a dark background that room mostly doesn't exist: a shadow cast onto near-black is barely perceptible, so a modal or popover that only gets a `box-shadow` in dark mode can look like it's floating at the same depth as the page behind it. Apple's fix is to make the elevated surface itself *lighter* than the base surface — depth is encoded as a lightness step, not a shadow. The web equivalent is a small ordered scale of surface lightness values (base, raised, overlay, modal) that get *lighter* as content moves toward the viewer in dark mode, used alongside or instead of shadow — the same idea Material Design calls "elevation overlays." Where the mapping is incomplete: Apple's base/elevated pair is wired into system-provided views and switches automatically when content enters the foreground (a popover, a multitasking window); the web has no automatic foreground-detection to key off, so the elevation step has to be applied deliberately per component role rather than inherited for free.

**Contrast ratios → this is not an analogy, it's the same standard.** Apple's 4.5:1 minimum and 7:1 target for small text are, respectively, WCAG 2.x's AA and AAA thresholds for normal text contrast. There is no translation gap here at all — a web dark theme should be checked against the same two numbers, with the same emphasis Apple places on re-testing once Increase Contrast–equivalent settings (`prefers-contrast: more`) are layered on top, since a palette that clears 4.5:1 in isolation can fall under it once a semi-transparent surface sits between text and background.

**SF Symbols adapting automatically → icons that inherit `currentColor` instead of shipping as fixed-color assets.** Apple's symbols adapt because they're rendered, not baked as bitmaps, and can be tinted or given vibrancy at draw time. The web equivalent is using an icon font or inline SVG with `fill: currentColor` (or no explicit fill) so an icon inherits whatever the surrounding text color resolves to per appearance, instead of maintaining separate light and dark PNG icon exports the way Apple explicitly recommends only "if necessary." Where this breaks down: true vibrancy — where content translucently blends with whatever sits behind it — has a partial web analogue in `backdrop-filter`, but browser support, performance cost, and the lack of any system-level compositing mean it's a much heavier, less reliable effect than what Apple gets from the OS compositor for free.

**Desktop tinting (macOS) → genuinely platform-specific, with no clean web equivalent.** Desktop tinting depends on the system reading the actual desktop picture behind a window and bleeding its color into translucent surfaces — there's no meaningful web parallel, since a browser tab has no access to "what's behind the OS window" and no reason to reach for it. `backdrop-filter: blur()` over a page's own background can create a loosely similar feeling of surfaces picking up ambient color, but it's sampling the page's own content, not the desktop's, so treat this one as platform-bound rather than force an analogy.

**Softening white backgrounds in images → the same fix, same reason, on the web.** Apple's rationale — an image with a pure-white background will visually "glow" against a dark surrounding UI — applies unchanged to any web page with a dark theme. The fix transfers directly: pre-process image assets intended for dark contexts (slightly darken or add a subtle tint), or apply a CSS treatment (a subtle background-color behind transparent-background images, or a slight `filter: brightness()` reduction) so a bright image doesn't sit at a jarringly different luminance than the page around it.

## Do / Don't

| Do | Don't |
|---|---|
| Respect the systemwide (or `prefers-color-scheme`) appearance choice | Offer an app-specific appearance setting that ignores the system choice |
| Support the Auto/System option so appearance can switch while running | Assume the appearance is fixed for the life of a session |
| Use semantic/token-based colors that adapt automatically | Hard-code color values that don't adapt to the current appearance |
| Hand-tune a distinct dark palette | Generate the dark palette by mathematically inverting the light one |
| Make elevated surfaces lighter to signal depth in dark contexts | Rely on shadow alone to convey elevation on dark backgrounds |
| Meet at least 4.5:1 contrast, and 7:1 for small custom text | Ship a palette that only "looks fine" without checking contrast ratios |
| Use adaptive symbols/icons (`currentColor`, dynamic tint) | Ship a single fixed-color icon asset for both appearances without checking it |
| Soften or tint image assets with white backgrounds for dark contexts | Let a bright image glow against a dark surrounding interface |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
