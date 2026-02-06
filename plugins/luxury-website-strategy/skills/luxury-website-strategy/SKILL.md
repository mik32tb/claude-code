---
name: luxury-website-strategy
description: Master visual and interaction strategy for premium, conversion-driven luxury websites. Use this skill when the user asks to build a high-ticket landing page, luxury agency website, or conversion-focused premium page. Generates production-ready code with dark luxury aesthetics, glassmorphic elements, and conversion-optimized CTA hierarchy.
license: Complete terms in LICENSE.txt
---

This skill provides a complete design system for building luxury, conversion-driven websites for high-ticket businesses. Every visual choice must increase trust, authority, and conversion without distracting from the offer.

The user provides website requirements: a landing page, multi-section site, or conversion-focused interface for a premium or high-ticket business. They may include context about the business, audience, or specific sections needed.

## Primary Positioning Goal

The website must instantly communicate:
"This company understands growth, systems, and money. They are not cheap — and that's a good thing."

This is NOT a design-for-design's-sake brief. Every visual choice must increase trust, authority, and conversion without distracting from the offer.

## Core Design Philosophy

- **Visual polish amplifies trust** — it never competes with the offer
- **Minimalism with intent**, not emptiness
- **Luxury through restraint**, not decoration
- **Systems over services**
- **Authority over hype**

## Global Visual System

### Color Palette (Premium-safe, dark luxury)

| Token           | Value                                        |
|-----------------|----------------------------------------------|
| Base background | Near-black graphite `#0B0D10`                |
| Surface cards   | Charcoal / glass panels `#12151B` with subtle blur |
| Accent          | Burnt orange → soft neon amber gradient      |
| Primary text    | Off-white `#EDEFF2`                          |
| Secondary text  | Muted gray (reduced contrast)                |

**Strict accent rules:**
- Accent color is used ONLY for CTAs, highlights, and progress cues
- No decorative gradients in body sections
- No accent color in long-form copy

### Typography

Use Webflow-safe font stacks:
- **Headlines:** Inter, Satoshi, or General Sans at weight 600–700
- **Body:** Inter at weight 400–500

Hero headline must use `clamp()` scaling:

```css
h1 {
  font-size: clamp(2.2rem, 5vw, 4rem);
}
```

## Page Structure & Visual Direction

### 1. Hero Section (Most Important)

**Purpose:**
- Immediate authority
- Signal systems + results
- Drive a single primary action (Strategy Call or Free Audit)

**Visual style:**
- Dark luxury background
- Very subtle radial glow behind headline
- Glassmorphic CTA container (not full-width)

**Copy hierarchy:**
- Outcome-driven headline
- Clear qualifier subhead (who it's for)
- ONE primary CTA only

**Mandatory 3D element (Hero):**
- Abstract floating funnel or dashboard UI (not literal tools)
- Purpose: visual explanation + authority
- Desktop: right side of hero
- Mobile: below copy

**3D interaction rules:**
- Idle float loop (6–8s, slow)
- Subtle mouse parallax (desktop only)
- No overlap with headline or CTA

**Tooling:**
- Spline embed OR lightweight Lottie
- Mobile fallback: static PNG
- No autoplay animation on mobile

### 2. Who This Is For (Qualification Section)

**Purpose:**
- Pre-qualify serious buyers
- Repel bad fits

**Visual direction:**
- Glass card grid
- Soft inner shadow, subtle depth
- Abstract minimal icons only

**Motion:**
- Fade + slight Y reveal
- Stagger: 80–120ms
- Trigger via `IntersectionObserver`

**Strict rule:** No hover gimmicks. Clarity over delight.

### 3. Systems Over Services (Authority Section)

**Purpose:**
- Differentiate from generic agencies

**Visual style:**
- Horizontal process layout
- Subtle glowing divider lines
- One-time muted accent pulse on scroll

**Optional micro-3D (only if performance allows):**
- Animated data flow or system lines (SVG or canvas)
- Purpose: reinforce systems thinking
- Hard fallback to static SVG

**Performance rule:** If it impacts load, remove immediately.

### 4. Proof & Trust (Critical Section)

**Purpose:**
- Reduce skepticism
- Build credibility without noise

**Visual direction:**
- Clean, high-contrast layout
- Static testimonials (no motion on text)
- Optional logo placeholders if testimonials are unavailable

**Motion rules:**
- Fade-in only
- No scaling
- No hover effects

**Rule:** Never animate trust aggressively.

### 5. Primary CTA (High Impact Section)

**Purpose:**
- Convert ready users

**Visual style:**
- Isolated section
- Dark → accent gradient background
- Floating glass CTA card

**CTA button behavior (mandatory):**
- Magnetic hover (desktop only)
- Soft glow on hover
- Press depth on click

```css
button:hover {
  box-shadow: 0 0 40px rgba(255, 140, 0, 0.35);
}
```

**Rule:** CTA must visually dominate the entire page.

## Motion & Micro-Interaction System

### Allowed

- Fade + slide
- Scale ≤ 1.04
- Very subtle parallax
- Button glow + magnetic pull

### Forbidden

- Bounce
- Fast loops
- Text scrambling
- Continuous background motion

### Luxury Timing

```css
/* Duration: 0.6–1.2s */
/* Easing: */
transition-timing-function: cubic-bezier(0.25, 0.1, 0.25, 1);
```

### Accessibility

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

## Implementation Rules

**Webflow-first stack:**
- Webflow interactions (basic reveals)
- Lottie for lightweight visuals
- ONE Spline embed max (hero only)
- Custom JS loaded in footer

**Performance:**
- No GSAP site-wide
- No heavy libraries above the fold
- Lazy-load embeds
- Defer JS

## Do Not Add Effects To

- Long-form copy
- Pricing
- FAQs
- Forms
- Legal / footer

If it slows reading, remove it.

## QA Checklist

Before finalizing, score each category as PASS or FAIL:

| Category             | Criteria                                                         |
|----------------------|------------------------------------------------------------------|
| Performance safety   | No heavy JS above fold, lazy-loaded embeds, deferred scripts     |
| Mobile degradation   | Static PNG fallback for 3D, no autoplay animation on mobile      |
| Accessibility        | `prefers-reduced-motion` respected, sufficient text contrast      |
| Visual restraint     | No decorative gradients in body, no accent in long-form copy     |
| CTA dominance        | CTA visually dominates page, magnetic hover, glow on hover       |
| Premium feel         | Dark luxury palette, glassmorphic surfaces, restrained typography |
| Conversion confidence| Single primary CTA per section, clear qualification, trust proof |
