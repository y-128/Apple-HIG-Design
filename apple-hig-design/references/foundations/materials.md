---
title: Materials
url: https://developer.apple.com/design/human-interface-guidelines/materials
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-09-09
---

# Materials

A material is a visual effect that creates a sense of depth, layering, and hierarchy between foreground and background elements.

## Core guidance

Materials help visually separate foreground elements, such as text and controls, from background elements, such as content and solid colors. By allowing color to pass through from background to foreground, a material establishes visual hierarchy to help people more easily retain a sense of place.

Apple platforms feature two types of materials: Liquid Glass, and standard materials. Liquid Glass is a dynamic material that unifies the design language across Apple platforms, allowing you to present controls and navigation without obscuring underlying content. In contrast to Liquid Glass, the standard materials help with visual differentiation within the content layer.

### Liquid Glass

Liquid Glass forms a distinct functional layer for controls and navigation elements — like tab bars and sidebars — that floats above the content layer, establishing a clear visual hierarchy between functional elements and content. Liquid Glass allows content to scroll and peek through from beneath these elements to give the interface a sense of dynamism and depth, all while maintaining legibility for controls and navigation.

**Don't use Liquid Glass in the content layer.** Liquid Glass works best when it provides a clear distinction between interactive elements and content, and including it in the content layer can result in unnecessary complexity and a confusing visual hierarchy. Instead, use standard materials for elements in the content layer, such as app backgrounds. An exception to this is for controls in the content layer with a transient interactive element like sliders and toggles; in these cases, the element takes on a Liquid Glass appearance to emphasize its interactivity when a person activates it.

**Use Liquid Glass effects sparingly.** Standard components from system frameworks pick up the appearance and behavior of this material automatically. If you apply Liquid Glass effects to a custom control, do so sparingly. Liquid Glass seeks to bring attention to the underlying content, and overusing this material in multiple custom controls can provide a subpar user experience by distracting from that content. Limit these effects to the most important functional elements in your app. For developer guidance, see Applying Liquid Glass to custom views.

**Only use clear Liquid Glass for components that appear over visually rich backgrounds.** Liquid Glass provides two variants — regular and clear — that you can choose when building custom components or styling some system components. The appearance of these variants can differ in response to certain system settings, like if people choose a preferred look for Liquid Glass in their device's settings, or turn on accessibility settings that reduce transparency or increase contrast in the interface.

The regular variant blurs and adjusts the luminosity of background content to maintain legibility of text and other foreground elements. Scroll edge effects further enhance legibility by blurring and reducing the opacity of background content. Most system components use this variant. Use the regular variant when background content might create legibility issues, or when components have a significant amount of text, such as alerts, sidebars, or popovers.

> *Image caption:* On dark background
> *Image caption:* On light background

The clear variant is highly translucent, which is ideal for prioritizing the visibility of the underlying content and ensuring visually rich background elements remain prominent. Use this variant for components that float above media backgrounds — such as photos and videos — to create a more immersive content experience.

For optimal contrast and legibility, determine whether to add a dimming layer behind components with clear Liquid Glass:

- If the underlying content is bright, consider adding a dark dimming layer of 35% opacity. For developer guidance, see `clear`.
- If the underlying content is sufficiently dark, or if you use standard media playback controls from AVKit that provide their own dimming layer, you don't need to apply a dimming layer.

For guidance about the use of color, see Liquid Glass color.

### Standard materials

Use standard materials and effects — such as blur, vibrancy, and blending modes — to convey a sense of structure in the content beneath Liquid Glass.

**Choose materials and effects based on semantic meaning and recommended usage.** Avoid selecting a material or effect based on the apparent color it imparts to your interface, because system settings can change its appearance and behavior. Instead, match the material or vibrancy style to your specific use case.

**Help ensure legibility by using vibrant colors on top of materials.** When you use system-defined vibrant colors, you don't need to worry about colors seeming too dark, bright, saturated, or low contrast in different contexts. Regardless of the material you choose, use vibrant colors on top of it. For guidance, see System colors.

> *Image caption:* Poor contrast between the material and systemGray3 label
> *Image caption:* Good contrast between the material and vibrant color label

**Consider contrast and visual separation when choosing a material to combine with blur and vibrancy effects.** For example, consider that:

- Thicker materials, which are more opaque, can provide better contrast for text and other elements with fine features.
- Thinner materials, which are more translucent, can help people retain their context by providing a visible reminder of the content that's in the background.

For developer guidance, see Material.

## Platform considerations

The Liquid Glass and standard-material guidance above applies across Apple platforms, but each platform adds its own material set, vibrancy values, and behaviors.

### iOS, iPadOS

In addition to Liquid Glass, iOS and iPadOS continue to provide four standard materials — ultra-thin, thin, regular (default), and thick — which you can use in the content layer to help create visual distinction.

> *Image caption:* ultraThin
> *Image caption:* thin
> *Image caption:* regular
> *Image caption:* thick

iOS and iPadOS also define vibrant colors for labels, fills, and separators that are specifically designed to work with each material. Labels and fills both have several levels of vibrancy; separators have one level. The name of a level indicates the relative amount of contrast between an element and the background: The default level has the highest contrast, whereas quaternary (when it exists) has the lowest contrast.

Except for quaternary, you can use the following vibrancy values for labels on any material. In general, avoid using quaternary on top of the `thin` and `ultraThin` materials, because the contrast is too low.

- `UIVibrancyEffectStyle.label` (default)
- `UIVibrancyEffectStyle.secondaryLabel`
- `UIVibrancyEffectStyle.tertiaryLabel`
- `UIVibrancyEffectStyle.quaternaryLabel`

You can use the following vibrancy values for fills on all materials.

- `UIVibrancyEffectStyle.fill` (default)
- `UIVibrancyEffectStyle.secondaryFill`
- `UIVibrancyEffectStyle.tertiaryFill`

The system provides a single, default vibrancy value for a separator, which works well on all materials.

### macOS

macOS provides several standard materials with designated purposes, and vibrant versions of all system colors. For developer guidance, see `NSVisualEffectView.Material`.

**Choose when to allow vibrancy in custom views and controls.** Depending on configuration and system settings, system views and controls use vibrancy to make foreground content stand out against any background. Test your interface in a variety of contexts to discover when vibrancy enhances the appearance and improves communication.

**Choose a background blending mode that complements your interface design.** macOS defines two modes that blend background content: behind window and within window. For developer guidance, see `NSVisualEffectView.BlendingMode`.

### tvOS

In tvOS, Liquid Glass appears throughout navigation elements and system experiences such as Top Shelf and Control Center. Certain interface elements, like image views and buttons, adopt Liquid Glass when they gain focus.

In addition to Liquid Glass, tvOS continues to provide standard materials, which you can use to help define structure in the content layer. The thickness of a standard material affects how prominently the underlying content shows through. For example, consider using standard materials in the following ways:

| Material | Recommended for |
|---|---|
| ultraThin | Full-screen views that require a light color scheme |
| thin | Overlay views that partially obscure onscreen content and require a light color scheme |
| regular | Overlay views that partially obscure onscreen content |
| thick | Overlay views that partially obscure onscreen content and require a dark color scheme |

### visionOS

In visionOS, windows generally use an unmodifiable system-defined material called glass that helps people stay grounded by letting light, the current Environment, virtual content, and objects in people's surroundings show through. Glass is an adaptive material that limits the range of background color information so a window can continue to provide contrast for app content while becoming brighter or darker depending on people's physical surroundings and other virtual content.

> **Note (Apple):** visionOS doesn't have a distinct Dark Mode setting. Instead, glass automatically adapts to the luminance of the objects and colors behind it.

**Prefer translucency to opaque colors in windows.** Areas of opacity can block people's view, making them feel constricted and reducing their awareness of the virtual and physical objects around them.

**If necessary, choose materials that help you create visual separations or indicate interactivity in your app.** If you need to create a custom component, you may need to specify a system material for it. Use the following examples for guidance.

- The `thin` material brings attention to interactive elements like buttons and selected items.
- The `regular` material can help you visually separate sections of your app, like a sidebar or a grouped table view.
- The `thick` material lets you create a dark element that remains visually distinct when it's on top of an area that uses a regular background.

To ensure foreground content remains legible when it displays on top of a material, visionOS applies vibrancy to text, symbols, and fills. Vibrancy enhances the sense of depth by pulling light and color forward from both virtual and physical surroundings.

visionOS defines three vibrancy values that help you communicate a hierarchy of text, symbols, and fills.

- Use `UIVibrancyEffectStyle.label` for standard text.
- Use `UIVibrancyEffectStyle.secondaryLabel` for descriptive text like footnotes and subtitles.
- Use `UIVibrancyEffectStyle.tertiaryLabel` for inactive elements, and only when text doesn't need high legibility.

> *Image caption:* label
> *Image caption:* secondaryLabel
> *Image caption:* tertiaryLabel

### watchOS

**Use materials to provide context in a full-screen modal view.** Because full-screen modal views are common in watchOS, the contrast provided by material layers can help orient people in your app and distinguish controls and system elements from other content. Avoid removing or replacing material backgrounds for modal sheets when they're provided by default.

## Native implementation

**Related**
- Color
- Accessibility
- Dark Mode

**Developer documentation**
- Adopting Liquid Glass
- `glassEffect(_:in:)` — SwiftUI
- `Material` — SwiftUI
- `UIVisualEffectView` — UIKit
- `NSVisualEffectView` — AppKit

**Key APIs**
- `glassEffect(_:in:)` — SwiftUI modifier for applying Liquid Glass to custom views
- `clear` — the clear Liquid Glass variant (see Apple's developer guidance when deciding on a dimming layer)
- `Material` — SwiftUI standard materials (`ultraThin`, `thin`, `regular`, `thick`)
- `UIVisualEffectView` — UIKit view that hosts blur and vibrancy effects
- `UIVibrancyEffectStyle.label` / `.secondaryLabel` / `.tertiaryLabel` / `.quaternaryLabel` — label vibrancy levels
- `UIVibrancyEffectStyle.fill` / `.secondaryFill` / `.tertiaryFill` — fill vibrancy levels
- `NSVisualEffectView` — AppKit equivalent
- `NSVisualEffectView.Material` — macOS standard materials with designated purposes
- `NSVisualEffectView.BlendingMode` — behind window and within window blending
- AVKit standard media playback controls — provide their own dimming layer

**Videos:** Meet Liquid Glass · Get to know the new design system

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Two material types → separate your chrome layer from your content layer before choosing any visual effect.** The load-bearing idea in Apple's document is not blur — it is that a translucent material marks a *functional* layer (navigation, controls) floating above a *content* layer, so people always know which parts of the screen act on the content and which parts are the content. On the web the analogous discipline is deciding up front that sticky headers, floating toolbars, tab bars, and command palettes belong to one layer, and that cards, tables, and article bodies belong to another. Applying a `backdrop-filter` to both flattens exactly the distinction the effect exists to create. Apple's "don't use Liquid Glass in the content layer" rule translates directly: glassy surfaces on your content cards buy you nothing and cost you legibility.

**Regular vs clear variants → choose translucency strength by what is underneath, not by taste.** Apple's split is functional. The regular variant blurs *and* adjusts luminosity, so it is the safe choice when text sits on it or when the background is unpredictable. The clear variant is nearly transparent and is reserved for surfaces floating over deliberately rich media. The web equivalent is that a blur radius alone is not a material: `backdrop-filter` combined only with `blur()` does not correct luminance, so bright background imagery still bleeds through and destroys text contrast. To approximate the regular variant you need blur plus a semi-opaque background color plus, often, a saturation or brightness adjustment. To approximate the clear variant you use minimal blur and let the media dominate — and then Apple's dimming rule applies: over bright content, a dark scrim (Apple specifies 35% opacity for its clear variant) is what restores contrast. That number is Apple's, tuned to their material; treat it as a starting point on the web and verify contrast ratios against your actual imagery rather than assuming it transfers.

**Content-adaptive behavior → the mapping breaks down here.** Liquid Glass reads the luminance of what is behind it and shifts to keep foreground elements legible; visionOS glass goes further and adapts to the user's physical surroundings. The web has no equivalent. `backdrop-filter` samples the backdrop but applies a fixed transform to it — it cannot decide "this backdrop is too bright, darken myself." Anything adaptive on the web has to be built by hand: sampling image brightness in script, or shipping two prepared treatments and switching between them. Because that is fragile, the practical web rule is stricter than Apple's — assume your translucent surface will at some point sit over the worst-case background, and make it legible in that case rather than in the average case.

**Vibrancy → no true analogue; use solid, contrast-checked foreground colors instead.** Apple's vibrancy is a compositing behavior that pulls color forward from behind the material, which is why Apple can say "use vibrant colors and stop worrying about contrast." Nothing in CSS does this. Applying opacity to text over a blurred surface produces a superficially similar look but the opposite result: it lowers contrast exactly where Apple's vibrancy would preserve it. The honest translation of Apple's vibrancy hierarchy (label, secondary, tertiary, quaternary) is a hierarchy of fully opaque foreground colors whose contrast you have measured against the composited surface. Apple's own caution — avoid quaternary on thin and ultraThin materials because contrast is too low — is the same warning in their vocabulary: the thinner the material, the fewer hierarchy levels you can afford.

**Material thickness → an opacity scale, and a reminder that thickness is a legibility decision.** Apple's four-step scale (ultraThin, thin, regular, thick) maps cleanly onto the alpha of your surface color: thicker means more opaque, better contrast for fine features and small text; thinner means more of the background reads through, preserving context. tvOS makes the reasoning explicit by tying thickness to intent — the lightest material for full-screen light-scheme views, the heaviest when the overlay must read as dark. On the web the same logic holds, with the extra constraint that you should pick a thickness that still works when `backdrop-filter` is unsupported or disabled, because your fallback is whatever background color you set underneath.

**System settings → honor the user's transparency, contrast, and color-scheme preferences.** Apple notes that Liquid Glass changes appearance when someone reduces transparency or increases contrast. The web exposes the same intent through `prefers-reduced-transparency`, `prefers-contrast`, and `prefers-color-scheme`. Reduced transparency should not merely soften the blur; it should replace the material with an opaque surface, since the point of the preference is to remove the visual noise of see-through layers entirely. Treating these as optional polish inverts Apple's model, where the material is defined partly by how it degrades.

**Performance → a real web-specific constraint Apple doesn't have.** `backdrop-filter` forces the browser to composite and re-filter the region behind an element on every frame it or its backdrop moves, which is expensive on large surfaces, on scroll, and on low-end hardware. Apple's platform materials are implemented far below the app layer and carry no comparable cost to the developer. This gives the web an independent reason to follow Apple's "use sparingly" rule: on Apple platforms overuse is a taste problem, on the web it is also a frame-rate problem. Full-viewport glass and glass on every card in a scrolling list are the two patterns that reliably cause it.

**Optical refraction and specular highlights → no web analogue; say so rather than fake it.** Liquid Glass bends and reflects light at its edges, which is what makes it read as a physical material rather than a blurred rectangle. CSS filters cannot refract, and imitating the edge highlight with borders and gradients produces a static approximation that looks wrong the moment the surface moves. It is better to build a clean, well-contrasted translucent surface than a poor imitation of a material the browser cannot render. Related: there is no system-wide glass on the web, so your material will not match anything the user sees elsewhere in the browser — consistency has to come from within your own product.

## Do / Don't

| Do | Don't |
|---|---|
| Reserve Liquid Glass for the functional layer — controls and navigation floating above content | Use Liquid Glass in the content layer, such as app backgrounds |
| Let system components pick up Liquid Glass automatically | Apply Liquid Glass effects to many custom controls |
| Limit Liquid Glass effects to the most important functional elements in your app | Overuse the material and distract from the underlying content |
| Use the regular variant when background content might hurt legibility, or when a component has a lot of text (alerts, sidebars, popovers) | Use the clear variant on text-heavy components or over unpredictable backgrounds |
| Use the clear variant for components floating over visually rich media such as photos and videos | Assume clear Liquid Glass stays legible over bright content without a dimming layer |
| Add a dark dimming layer of 35% opacity behind clear Liquid Glass when the underlying content is bright | Add a redundant dimming layer over already-dark content or over AVKit controls that provide their own |
| Use standard materials to convey structure in the content layer beneath Liquid Glass | Use Liquid Glass where a standard material belongs |
| Choose materials and effects by semantic meaning and recommended usage | Choose a material based on the apparent color it imparts to your interface |
| Use system-defined vibrant colors on top of materials | Place non-vibrant labels such as systemGray3 on a material |
| Use thicker, more opaque materials for better contrast with fine features and small text | Use quaternary vibrancy on top of the thin and ultraThin materials |
| Use thinner, more translucent materials when people benefit from seeing the background context | Ignore how system settings change a material's appearance and behavior |
| Test where vibrancy improves communication in custom macOS views and controls | Assume vibrancy is always the right choice for custom views |
| Prefer translucency to opaque colors in visionOS windows | Fill visionOS windows with opacity that blocks people's view of their surroundings |
| Use materials to provide context and orientation in watchOS full-screen modal views | Remove or replace the default material backgrounds of watchOS modal sheets |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
