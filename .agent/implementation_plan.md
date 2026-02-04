# Implementation Plan - Website Redesign (Martin Nowak Style)

## Goal
Transform the design of `bohuecon.github.io` to match the aesthetic of `https://sites.harvard.edu/martin-nowak/`.
Key characteristics: Minimalist, "Harvard" red/black/white or Blue academic theme (Nowak's is Blue), detailed typography (Inter), large hero image with dark overlay, two-tier navigation.

## Design Specs
- **Font**: 'Inter', sans-serif.
- **Colors**:
  - Primary Brand: `#205B92` (Harvard/Nowak Blue)
  - Dark Accent: `#1D2124` (Overlay background)
  - Text: `#000000` (Body), `#FFFFFF` (Hero Text)
  - Background: `#FFFFFF`
  - Footer: `#EEEEEC`
- **Layout**:
  - **Global Bar**: Dark bar at the top (University/School Name).
  - **Navbar**: Clean white, text links (no pills), logo on left.
  - **Hero**: Full-width background image. Dark translucent overlay box (`rgba(29, 33, 36, 0.85)`) on the right (or left).
  - **Content**: Single column, centered, max-width ~1170px.

## Steps

1.  **Generate Assets**:
    - Generate a "university campus blurred background" image for the hero section.
2.  **Update HTML (`index.html`)**:
    - Add Google Fonts link.
    - Add "Global Header" div (Fudan University color/style).
    - Restructure Navbar (remove `container` limits if full width is needed, or keep centered).
    - Restructure Hero to be full-width with an inner container for the overlay.
    - Move Profile Image inside the overlay or to a new "About" section if it doesn't fit the "text-heavy hero" vibe (but usually it's fine to keep it).
3.  **Update CSS (`css/main.css`)**:
    - Reset changes.
    - Implement the new color palette and typography.
    - Style the Global Bar and Navbar.
    - Style the Hero (background image + overlay).
    - Style Cards (remove "pill" aesthetic, make them clean, minimal borders/shadows).
    - Update Footer.
4.  **Verify**:
    - Check responsiveness.

## Asset Generation
- `images/hero-bg.png`: Blurred academic background.
