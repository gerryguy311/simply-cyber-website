# Design System Document

## 1. Overview & Creative North Star

### Creative North Star: "The Architectural Sentinel"
This design system moves beyond the standard "SaaS Blue" template to create a high-end, editorial experience for Simply Cyber. The visual strategy is anchored in **Architectural Sentinel** aesthetics: a blend of rigid, authoritative structure and ethereal, high-tech transparency. 

To break the "standard website" look, we utilize **intentional asymmetry**. Layouts should not feel like a repeating grid; instead, use large, offset typography and overlapping containers to create a sense of motion and technical sophistication. We replace structural lines with **tonal depth**, creating a digital environment that feels curated, premium, and inherently trustworthy.

---

## 2. Colors

The palette is rooted in a deep, authoritative navy and a high-energy "Cyber Blue," balanced by surgical white surfaces.

### Surface Hierarchy & Nesting
We reject the "flat" web. Depth is built through a strictly defined hierarchy of surfaces:
- **Base Layer:** `surface` (#f7f9ff) – The primary canvas.
- **Sectional Shifts:** Use `surface_container_low` (#edf4ff) to define broad content areas.
- **Interactive Layers:** Use `surface_container_highest` (#dbe3ee) for cards or elevated UI modules.

### The "No-Line" Rule
**Explicit Instruction:** Prohibit the use of 1px solid borders to separate sections. Boundaries must be defined solely through background color shifts. A `surface_container_low` section sitting on a `surface` background provides all the definition needed.

### The "Glass & Gradient" Rule
To add "soul" to the tech-focused aesthetic:
- **Glassmorphism:** Use `surface_container_lowest` (#ffffff) at 70% opacity with a `backdrop-blur` of 20px for floating navigation or overlay elements.
- **Signature Gradients:** For Hero backgrounds and Primary CTAs, use a subtle linear gradient from `primary` (#005796) to `primary_container` (#1d70b8) at a 135-degree angle.

---

## 3. Typography

The typography strategy leverages the cleanliness of **Montserrat** (substituted via the user's request, supported by **Plus Jakarta Sans** and **Inter** for technical precision) to create a hierarchy that feels both modern and editorial.

*   **Display Scales (`plusJakartaSans`):** Used for "Impact Statements." Large, bold, and tightly tracked. This is the "voice" of authority.
*   **Headline & Title (`plusJakartaSans`):** These define the structure. Use `headline-lg` (2rem) to introduce sections with confidence.
*   **Body & Label (`inter`):** Chosen for its extreme legibility in technical contexts. `body-md` (0.875rem) is our workhorse for educational content.

**Identity Conveyance:** The contrast between the expansive, airy Display type and the dense, functional Body type mimics a high-end cybersecurity report—professional, detailed, yet accessible.

---

## 4. Elevation & Depth

We achieve hierarchy through **Tonal Layering** rather than traditional drop shadows or lines.

### The Layering Principle
Stack containers to create a "soft lift."
*   **Level 0:** `surface` (Background)
*   **Level 1:** `surface_container_low` (Section)
*   **Level 2:** `surface_container_lowest` (Card/Form)

### Ambient Shadows
When an element must float (e.g., a Modal or a primary Action Card):
*   **Blur:** 40px to 60px.
*   **Opacity:** 4%–8%.
*   **Color:** Use a tinted version of `on_surface` (#141c24) to create a natural "ambient occlusion" look rather than a grey smudge.

### The "Ghost Border" Fallback
If a container requires a border for accessibility, use the `outline_variant` token (#c1c7d2) at **15% opacity**. High-contrast, 100% opaque borders are strictly forbidden.

---

## 5. Components

### Buttons
*   **Primary:** Gradient of `primary` to `primary_container`. Text: `on_primary`. Radius: `md` (0.375rem).
*   **Secondary:** Ghost style. Transparent background with a "Ghost Border" and `primary` text.
*   **Tertiary:** No background or border. `primary` text with a 2px underline appearing only on hover.

### Cards & Lists
*   **Card Style:** No borders. Background: `surface_container_lowest`. Use `spacing-8` (2rem) for internal padding.
*   **List Items:** Forbid divider lines. Separate items using `spacing-4` (1rem) of vertical white space and a subtle background shift to `surface_container_low` on hover.

### Input Fields
*   **Styling:** `surface_container_low` background with a bottom-only "Ghost Border."
*   **Focus State:** Border transitions to 2px `primary_container` with a subtle `surface_tint` outer glow.

### Signature Component: The "Security Pulse" Chip
*   **Purpose:** For status indicators or live updates.
*   **Style:** `surface_container_highest` background, `label-sm` typography, and a small 8px circle using `tertiary` (#ae0002) for alerts or `primary_container` for "Active" states.

---

## 6. Do's and Don'ts

### Do:
*   **DO** use whitespace as a functional tool. Use `spacing-20` (5rem) between major sections to let the tech aesthetic "breathe."
*   **DO** align text to a rigorous grid, but allow imagery and decorative "Cyber" elements to break the container edges.
*   **DO** use `surface_container_high` for nested content like "Code Snippets" or "Technical Specs."

### Don't:
*   **DON'T** use pure black (#000000). Always use `on_surface` (#141c24) for text to maintain a premium, ink-like feel.
*   **DON'T** use default "Drop Shadows." If it looks like a standard shadow, it's too heavy.
*   **DON'T** use 1px solid dividers. If you need to separate content, use a background color change or a large `spacing` jump.