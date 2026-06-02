# The Mum Bridge & Care Foundation - Website Knowledge Base

## Overview
This document captures the comprehensive UI structure, design system, and user experience of The Mum Bridge & Care Foundation website (themumbridge.org). Created: February 25, 2026 | Last Updated: June 2, 2026

## June 2, 2026 — Major Restructure (Developer Brief, May 2026)
The homepage was restructured per the May 2026 "Website Restructure Brief + Copy" with ~40% copy reduction and a new scroll order. Key changes:

### New scroll order (replaces previous)
1. Hero — new headline + Donate as primary CTA (deep plum #4A2545)
2. The Problem — "The Weight She Carries Alone" — dark plum bg, image on right
3. Impact So Far (NEW) — 6 stat cards (70+, 100+, 5–6, Mum Bridge Circle, 3, 100%)
4. What We Do — reduced from 6 cards to 5; removed all emoji icons; bottom row centered
5. Community Photos Gallery — moved up (was between Board and Partners)
6. Who We Are — About section cut by ~60%; 3 videos retained with per-card hook lines
7. Our Partners
8. Our Team — board bios cut to one sentence each; View More expandables removed
9. Donate (NEW structure) — intro copy + 4 donation tiers BEFORE Flutterwave/bank details
10. Join / Volunteer — combined into a single two-card section
11. Contact + Footer — newsletter signup now consolidated into footer only

### Sections removed entirely
- Vision & Mission (Our Purpose)
- Core Values
- SDG Alignment
- Mid-page CTA section
- Standalone Join Community / newsletter section (consolidated to footer)

### New / changed brand colour usage
- `#4A2545` (deep plum) introduced for: Problem section background, primary Donate button, donate-tier titles, donate-pay border, modal "feature" tier
- `#C9A84C` (warm gold) used for Impact So Far stat numbers and card top borders
- Existing `--color-primary` (#7B5E7B) retained as global primary for nav/headings

### Donation modal (existing modal updated)
- Added intro copy and a 4-tier summary block BEFORE the Flutterwave button + bank details
- Tier summary uses `.donation-tiers-summary` with `role="list"`; feature tier (Gathering 2026) is full-width with deep-plum left border

### Hero & video updates (June 2, 2026 — later same day)
- **Hero background image** changed from the Unsplash hands stock photo to an authentic TMB community photo: `assets/hero/community-hero.jpg` (sourced from `assets/impact/may-2026/TMB-215.jpg`, resized to 2400×1600, quality 82, ~400KB). Chosen for wide composition, visible wheelchair user, TMB foundation banner in-frame, and B&W tonality that supports text legibility. Overlay updated to a deep-plum→warm-brown diagonal gradient (#4A2545 78% → 62% → warm brown 65%) plus a soft radial vignette.
- **Open Graph / Twitter Card images** updated to point at the new hero image (was YouTube thumbnail of gxrBAENtICA).
- **Mobile hero**: `background-attachment` switches from `fixed` to `scroll` below 768px (iOS perf + visual quality).
- **Video order + label remap** (request June 2, 2026): cards now display, in order:
  1. `za7F0wHYMPc` — label "Our Story" — hook "How The Mum Bridge began, and why it had to."
  2. `gxrBAENtICA` — label "Our Community" — hook "Meet the mothers we exist for."
  3. `EGRzyEBu5Hk` — label "Our Impact" — hook "What changes when a mother with a disability finds her community."

  Note: labels/hooks no longer follow the YouTube IDs they originally rode with — they were remapped to align with the new card positions on June 2, 2026.

### Polish (June 2, 2026)
- Transition curves upgraded to `cubic-bezier(0.25, 1, 0.5, 1)` (ease-out-quart)
- Staggered card reveals (impact, services, donate tiers, jv-cards, partners, board) — 80ms increments
- Impact card hover: gold gradient sweep on top border
- Donate tier hover: lifted shadow + 1px plum ring
- All staggered animations are disabled under `prefers-reduced-motion`

## Website Purpose
Supporting mothers with disabilities through community, resources, and empowerment.

## Website Pages
The website consists of three main pages:
1. **index.html** - Main homepage with all sections and information
2. **privacy-policy.html** - Privacy Policy page (legal compliance)
3. **terms-of-use.html** - Terms of Use page (legal compliance)

---

## Design System & Brand Identity

### Color Palette
The website uses a warm, accessible, and dignified color scheme:
- **Primary**: `#7B5E7B` (Muted purple - represents strength & community)
- **Primary Light**: `#9D7E9D`
- **Primary Dark**: `#5A445A`
- **Accent**: `#D4A574` (Warm gold - represents hope & warmth)
- **Accent Light**: `#E8C9A0`
- **Background**: `#FDFBF9` (Warm off-white)
- **Background Alt**: `#F5F1ED`
- **Text Primary**: `#2C2C2C` (Near-black for readability)
- **Text Secondary**: `#5F5F5F`

### Typography
- **Primary Font**: System fonts (-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell)
- **Display Font**: Georgia, 'Times New Roman', serif (used for headings and emphasis)
- **Base Font Size**: 18px (1.125rem)
- **Line Height**: 1.7 (excellent readability)

### Spacing System
8px base grid system:
- XS: 8px
- SM: 16px
- MD: 24px
- LG: 40px
- XL: 64px
- 2XL: 96px

### Visual Effects
- **Shadows**: Soft, layered shadows (sm, md, lg variants)
- **Border Radius**: Rounded corners (0.375rem to 1.25rem)
- **Transitions**: Smooth animations (200ms - 800ms)
- **Hover States**: Subtle lifts (translateY) and scale transforms

---

## Page Structure & Sections

### 1. Fixed Header & Navigation
- **Position**: Fixed at top with solid warm off-white background
- **Height**: 82px desktop / 70px mobile (body has padding-top to account for this)
- **Components**:
  - Logo (50px height) with icon and text variants
  - Desktop navigation links with elegant underline animation on hover
  - "Donate Now" button (accent gold gradient, prominent CTA) — in nav on desktop
  - Mobile hamburger menu (white lines on mobile, transforms to X when open)
- **Mobile Behavior**: Hamburger menu, body scroll lock when open
- **Accessibility**: ARIA labels, keyboard navigation, focus indicators

### 2. Hero Section
- **Height**: 85vh minimum
- **Background**: High-quality Unsplash image with gradient overlay (purple to warm gold)
  - URL: `https://images.unsplash.com/photo-1531206715517-5c0ba140b2b8`
  - Overlay: rgba(92, 64, 92, 0.80) to rgba(139, 101, 76, 0.75)
  - Background attachment: Fixed (parallax effect)
- **Content**:
  - Hero title with responsive font sizing (clamp function)
  - Hero subtitle with opacity for depth
  - `.hero-buttons` flex container with two CTAs:
    1. "Join Our Community" link (primary gradient)
    2. "❤️ Donate Now" button (`#heroTopDonateBtn`, class `hero-donate-btn btn-donate`) — opens donation modal; stacks below "Join Our Community" on mobile
- **Animation**: Smooth fade-in with translateY entrance
- **Typography**: White text with layered text-shadow for contrast and readability

### 3. Impact & Statistics Section
- **Background**: Linear gradient (primary-dark to primary)
- **Color**: White text on dark purple gradient
- **Layout**: CSS Grid with auto-fit (minmax 240px)
- **Components**:
  - Stat cards with glassmorphism effect (backdrop-filter blur)
  - Large numbers in accent-light color with display font
  - Hover effect: Slight lift and background lightening
  - Impact statement at top (max-width 900px, centered)

### 4. What We Do Section
- **Background**: Main warm off-white
- **Layout**: 3-column grid (auto-fit, minmax 280px)
- **Components**:
  - Service cards with white background
  - Gradient icon boxes (purple to gold)
  - Clean shadows with hover lift
  - Service title and description

### 5. Vision & Mission Section
- **Background**: Alternate warm background
- **Layout**: 2-column grid (responsive)
- **Components**:
  - VM cards with top gradient border (4px)
  - Uppercase labels in accent color
  - Card hover: Slight lift effect

### 6. About Section
- **Background**: Main background
- **Layout**: Centered content (max-width 800px)
- **Components**:
  - Body text with generous line-height (1.9)
  - Highlight box with gradient background and left accent border
  - **3-video gallery** (`.videos-section` > `.videos-grid`) — added May 4, 2026
    - Desktop: 3-column CSS Grid; Tablet: 3-column; Mobile: 1-column stacked
    - Video 1 (`gxrBAENtICA`) — label "Our Story"
    - Video 2 (`EGRzyEBu5Hk`) — label "Our Impact"
    - Video 3 (`za7F0wHYMPc`) — label "Our Community"
    - Each card: YouTube thumbnail image, white play button overlay, gradient label bar
    - Hover/focus: lift (translateY -3px), accent outline, thumbnail dim, play button scale
    - Accessibility: `aria-label` on each link, `aria-hidden` on decorative elements, `prefers-reduced-motion` respected
    - Previously: single `.about-video` card (replaced)

### 7. Core Values Section
- **Background**: Main background
- **Layout**: 6-column grid (clever 2-column spans with last 2 centered)
- **Responsive**: 1 column mobile, 2 columns tablet, 3x2 desktop
- **Components**:
  - Value cards with left accent border
  - Circular gradient icon (48px)
  - Hover: Lift + shadow + border color change
  - Quote section at bottom with gradient background

### 8. Board of Trustees Section
- **Background**: Alternate background
- **Layout**: 3-column grid (6 visible members as of April 16, 2026; 7th member Adeoye Yetunde Adeyita commented out pending photo)
- **Responsive**: 1 column mobile, 2 columns tablet
- **Components**:
  - Member cards with image (340px height)
  - Image hover: Scale 1.05 with gradient overlay
  - Member info with name, role, bio
  - Social links (clean icon design, no boxes)
  - Expandable "View More" for full bio
- **Image Handling**: object-fit: cover with specific positioning for each member

### 9. Partners Section
- **Background**: Main background
- **Purpose**: Showcase partner organizations
- **Partners (3 as of April 17, 2026)**: MatchBox, LASODA, NNGO
- **Partner descriptions**:
  - MatchBox: "Supporting our mission to create accessible and inclusive opportunities for mothers with disabilities."
  - LASODA: "The Mum Bridge is a registered member of the Lagos State Office for Disability Affairs (LASODA), working to strengthen access, visibility, and support for mothers with disabilities within Lagos State."
  - NNGO: "The Mum Bridge is a member of the Nigeria Network of NGOs, part of a national community committed to strengthening civil society and advancing inclusive, impact-driven work."
- **Components**: Logo grid with partner-card articles — logo image, name, description, badge

### 10. Community Gallery Section
- **Background**: Main warm off-white (`--color-background`)
- **Placement**: Between Board of Trustees and Partners sections
- **Added**: May 22, 2026
- **Layout**: 3-column CSS Grid on desktop, 2-column tablet, 1-column mobile
- **Initial state**: First 9 photos visible; remaining 11 hidden with `gallery-item--hidden` class
- **"Show more" toggle**: `#gallery-toggle` button reveals/hides hidden items; text updates dynamically
- **Photo source**: `assets/impact/may-2026/` — 20 JPG files (TMB-16, TMB-21, TMB-35, TMB-49, TMB-57, TMB-73, TMB-74, TMB-76, TMB-90, TMB-126, TMB-129, TMB-131, TMB-135, TMB-137, TMB-147, TMB-199, TMB-201, TMB-212, TMB-215, TMB-217)
- **Asset version**: `?v=20260522`
- **Lightbox**: `#gallery-lightbox` — `role="dialog" aria-modal="true"`, triggered by any `.gallery-thumb-btn` click
  - Prev/next buttons + keyboard arrow navigation
  - Touch swipe left/right on mobile
  - ESC key or backdrop click to close
  - Focus trap (Tab stays inside lightbox)
  - Focus restoration to triggering thumbnail on close
  - `aria-live="polite"` counter announces "X of 20" on each change
- **Adding new photos**: Add `<figure class="gallery-item gallery-item--hidden">` block with `data-index` incremented; update total in button text
- **Each thumbnail**: `<button class="gallery-thumb-btn">` (keyboard-accessible), `loading="lazy"`, descriptive `alt` text, expand icon overlay on hover/focus
- **Accessibility**: `prefers-reduced-motion` respected (transitions disabled), min 44px tap targets, all interactive elements are native buttons

### 11. SDG (Sustainable Development Goals) Section
- **Background**: Alternate background
- **Layout**: 2-column grid (max-width 1000px)
- **Responsive**: 1 column mobile
- **Components**:
  - SDG cards with top 4px colored border
  - SDG number badge (primary background)
  - Focus label (uppercase, accent color)
  - Contribution description
  - Hover: Lift effect

### 11. CTA (Call-to-Action) Section
- **Purpose**: Drive engagement and donations
- **Styling**: Prominent with accent colors

### 12. Join Community Section
- **Purpose**: Newsletter subscription
- **Components**: Form with input and submit button

### 13. Volunteer Section
- **Purpose**: Recruit volunteers
- **Components**: Information and application CTA

### 14. Support Section
- **Purpose**: Encourage financial support
- **Components**: Donation information and button

### 15. Contact Section
- **Purpose**: Provide contact information
- **Components**: Email, location, contact form or details

### 16. Footer
- **Background**: Linear gradient (dark gray #2C2C2C to #3D3D3D)
- **Color**: White text
- **Pattern**: Subtle radial gradients with brand colors (purple & gold)
- **Components**:
  - **Brand Section**: Organization name, tagline, email link
  - **Social Media Section**: "Connect With Us" heading
    - Instagram (@themumbridge)
    - LinkedIn (https://www.linkedin.com/company/the-mum-bridge/)
    - Twitter (@themumbridge)
    - Large tap-friendly icons (48x48px desktop, 56x56px mobile)
    - Hover: Accent color + lift + drop shadow
    - Animated entrance (staggered delays)
  - **Divider**: Gradient horizontal line
  - **Copyright**: "© 2025 The Mum Bridge & Care Foundation. All rights reserved."
  - **Registration**: "Registered in Nigeria - CAC: 9112955"
- **Note**: Facebook icon removed as of February 27, 2026

---

## Privacy Policy & Terms of Use Pages

Both pages share a consistent design system with the main site while being optimized for readability and legal compliance.

### Privacy Policy Page (privacy-policy.html)

**Purpose**: Legal compliance document explaining data collection, use, and protection practices. Required for Google Ad Grants and GDPR/privacy law compliance.

**Structure**:
- **Header**: Simplified header with logo, "The Mum Bridge" text, and "Back to Home" link
- **Hero Section**: Page title and subtitle with gradient background
- **Content Sections**:
  1. Introduction & Effective Date
  2. Information We Collect (contact forms, newsletter, donations, cookies/analytics)
  3. How We Use Your Information
  4. Third-Party Services (Google Analytics, payment processors)
  5. Cookies & Tracking (with opt-out instructions)
  6. Data Security
  7. International Data Transfers
  8. Children's Privacy
  9. Changes to This Policy
  10. Contact Information
- **Footer**: Simplified footer with navigation links (Home, Privacy Policy, Terms of Use, Contact), copyright, and CAC registration number

**Design Elements**:
- Same color palette and design system as main site
- Policy sections with white background cards
- Highlighted boxes for important information
- Contact box with gradient background
- Max-width 900px for optimal readability
- Generous line-height (1.8) for easy reading

### Terms of Use Page (terms-of-use.html)

**Purpose**: Legal document outlining the terms and conditions for using the website. Establishes user responsibilities and limitations of liability.

**Structure**:
- **Header**: Identical to Privacy Policy page
- **Hero Section**: Page title and subtitle
- **Content Sections**:
  1. Introduction & Acceptance of Terms
  2. Use of Website (intended use, prohibited activities)
  3. Intellectual Property Rights
  4. External Links
  5. Disclaimer
  6. Limitation of Liability
  7. Governing Law (Nigerian jurisdiction)
  8. Changes to These Terms
  9. Contact Information
- **Footer**: Identical to Privacy Policy page

**Design Elements**:
- Consistent with Privacy Policy page styling
- Clean, professional layout
- Easy navigation between legal pages
- Mobile-responsive design

### Key Features (Both Pages)
- **Accessibility**: WCAG compliant, keyboard navigable, screen reader friendly
- **Responsive**: Mobile-first design with breakpoints matching main site
- **Navigation**: Easy return to main site via header link and footer
- **Readability**: Optimized typography, spacing, and contrast
- **Legal Compliance**: Covers data protection, cookies, GDPR, and Nigerian law
- **Last Updated Date**: Both pages show "Last Updated: February 23, 2025"

---

## Special Features & Components

### Donation Modal
- **Trigger**: "Donate Now" buttons throughout site
- **Design**: Clean, focused modal with glassmorphism
- **Overlay**: Dark background with blur
- **Components** (top to bottom order):
  - Header with gradient background
  - Close button (X) with rotation animation
  - **Flutterwave button** (added April 17, 2026) — orange gradient button linking to https://flutterwave.com/donate/0dbi6mww4nxu, opens in new tab; moved to top of modal body April 17, 2026
  - "Or pay by bank transfer" divider
  - Bank details in elegant field layout
  - Multi-currency accounts with copy buttons (USD, NGN, EUR, GBP)
  - Currency badges with gradient
  - Hover states on all interactive elements
  - Thank you note at bottom
- **Responsive**: Adjusts padding and font sizes for mobile
- **Accessibility**: Focus trap, ESC to close, ARIA labels, rel="noopener noreferrer" on external link

### Mobile Menu
- **Trigger**: Hamburger button (visible < 768px)
- **Animation**: Hamburger transforms to X
- **Behavior**: Full-screen overlay, prevents body scroll
- **Colors**: White hamburger lines on mobile

### Intersection Observer
- **Purpose**: Trigger animations when sections enter viewport
- **Effect**: Sections start with opacity 0 and translateY(30px)
- **Trigger**: `.visible` class added when in viewport
- **Transition**: 800ms cubic-bezier easing

---

## Accessibility Features (WCAG Compliant)

### 1. Semantic HTML5
- Proper use of header, nav, main, section, article, footer elements
- ARIA labels and roles throughout
- Landmark regions for screen readers

### 2. Keyboard Navigation
- All interactive elements keyboard accessible
- Visible focus indicators (3px accent outline with 2px offset)
- Focus trap in modals
- Skip links available

### 3. Color Contrast
- 4.5:1 minimum contrast ratio (WCAG AA)
- Text shadows on hero for readability
- High contrast on all text

### 4. Motion Preferences
- Respects `prefers-reduced-motion` media query
- Animations disabled if user prefers reduced motion

### 5. Touch Targets
- Minimum 44x44px tap targets on mobile
- Larger social icons on mobile (56px)
- Adequate spacing between interactive elements

---

## Responsive Design Breakpoints

### Mobile (< 768px)
- Single column layouts
- Stacked navigation (hamburger menu)
- Larger touch targets
- Adjusted font sizes
- Full-width components

### Tablet (769px - 1024px)
- 2-column grids where appropriate
- Maintained readability
- Optimized spacing

### Desktop (> 1024px)
- Full multi-column grids
- Hover effects activated
- Optimal spacing and typography
- Fixed background attachment (parallax)

---

## Performance Optimizations

### Images
- High-quality Unsplash images
- `image-rendering: crisp-edges` for sharpness
- Lazy loading for board member images
- Proper sizing and compression

### CSS
- CSS variables for consistency and easy theming
- Single stylesheet (no external CSS files)
- Efficient selectors
- Hardware-accelerated transforms

### Asset Versioning (Cache Busting)
- All local asset `src`/`href` attributes carry a `?v=YYYYMMDD` query string (e.g. `?v=20260413`)
- A `<meta name="asset-version" content="YYYYMMDD">` tag in each page's `<head>` records the current version
- **Scope**: favicon, logo images, board member photos, partner logos — across all 3 HTML files
- **On every deployment**: find-and-replace the old date string with the new one across all files:
  ```bash
  sed -i '' 's/v=OLD_DATE/v=NEW_DATE/g' index.html privacy-policy.html terms-of-use.html
  sed -i '' 's/content="OLD_DATE"/content="NEW_DATE"/g' index.html privacy-policy.html terms-of-use.html
  ```
- Current version: `20260602` (bumped June 2, 2026 for May 2026 restructure)

### JavaScript
- Vanilla JS (no framework overhead)
- Event delegation where possible
- Intersection Observer for scroll animations
- Efficient DOM manipulation

---

## User Experience (UX) Philosophy

### 1. Warmth & Dignity
- Warm color palette (purple + gold)
- Serif fonts for elegance
- Generous spacing and breathing room
- Soft shadows and rounded corners

### 2. Accessibility First
- Clear hierarchy and structure
- High contrast and readable fonts
- Keyboard and screen reader support
- Respect for user preferences

### 3. Trust & Credibility
- Professional design with personality
- Real board member photos and bios
- Clear organizational information
- Transparent donation process
- Registration number prominently displayed

### 4. Community Focus
- Inclusive language and imagery
- Multiple ways to engage (donate, volunteer, join)
- Social proof (stats, SDG alignment, partners)
- Easy contact and connection

### 5. Smooth Interactions
- Subtle animations enhance, don't distract
- Hover states provide feedback
- Clear CTAs guide users
- Mobile-friendly interactions

---

## Technical Architecture

### Structure
- **Single-page application** style (all content on index.html)
- **Inline CSS** in `<style>` tag (11,000+ lines)
- **Inline JavaScript** in `<script>` tag (end of body)
- **No external dependencies** (no jQuery, no frameworks)

### Assets
- **Logo**: `assets/logo/the-mum-bridge-icon.png` (favicon & mobile)
- **Hero Image**: External Unsplash URL
- **Board Images**: Local assets or data URIs
- **Icons**: SVG inline in HTML

### Browser Support
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Graceful degradation for older browsers
- Progressive enhancement approach

### Analytics
- **Platform**: Google Analytics 4
- **Tracking ID**: G-RT75M8FH5G
- **Implemented on**: index.html, privacy-policy.html, terms-of-use.html
- **Date Added**: March 5, 2026
- **Tag type**: `gtag.js` script in `<head>` of each page

---

## Content Strategy

### Voice & Tone
- **Warm**: Welcoming and inclusive
- **Dignified**: Respectful and professional
- **Hopeful**: Optimistic and empowering
- **Clear**: Straightforward and accessible

### Key Messages
1. Supporting mothers with disabilities
2. Community-driven approach
3. Practical resources and empowerment
4. Professional and registered organization (CAC: 9112955)
5. Aligned with UN Sustainable Development Goals

---

## Future Enhancements Noted in Code
(From developer comments at end of file)

1. Connect form submissions to backend/email service
2. Add actual newsletter integration (Mailchimp, etc.)
3. ✅ COMPLETED (Mar 5, 2026) — Google Analytics 4 (G-RT75M8FH5G) implemented on all pages
4. Add Cookie consent banner
5. Add structured data (Schema.org) for SEO
6. ✅ COMPLETED (Feb 25, 2026) — Privacy Policy page added
7. ✅ COMPLETED (Feb 25, 2026) — Terms of Use page added
8. ✅ COMPLETED (May 4, 2026) — Open Graph + Twitter Card meta tags added to index.html (og:image uses YouTube thumbnail of gxrBAENtICA)
9. Add loading states for forms
10. Consider A/B testing for CTAs

---

## Known Issues & Fixes Applied

### Fixed Issues
1. ✅ Hero background sharpness improved
2. ✅ Board member image cropping optimized
3. ✅ Mobile menu hamburger visibility fixed (white lines)
4. ✅ Horizontal scroll prevented (overflow-x: hidden)
5. ✅ Focus indicators for accessibility
6. ✅ Touch targets sized appropriately

### To Be Addressed
1. ✅ Privacy Policy and Terms of Use pages — COMPLETED (Feb 25, 2026)
2. ⚠️ HTTPS enforcement on all pages
3. ⚠️ Cookie banner implementation
4. ⚠️ Broken links check
5. ⚠️ Form backend integration

---

## SEO Considerations

### Current Implementation
- ✅ Meta description
- ✅ Semantic HTML
- ✅ Descriptive title tag
- ✅ Alt text on images (ARIA labels)
- ✅ Fast load times
- ✅ Mobile-friendly

### To Add
- ✅ Privacy Policy page — Added (Feb 25, 2026)
- ✅ Terms of Use page — Added (Feb 25, 2026)
- ⏳ Sitemap.xml
- ⏳ Robots.txt
- ✅ Open Graph tags — Added May 4, 2026
- ⏳ Schema.org structured data

---

## Deployment Information

### Registration
- **Organization**: The Mum Bridge & Care Foundation
- **Country**: Nigeria
- **CAC Number**: 9112955
- **Domain**: themumbridge.org
- **Email**: info@themumbridge.org
- **Location**: Lagos State, Nigeria

### Social Media Presence
- Instagram: @themumbridge
- LinkedIn: /company/the-mum-bridge/ (corrected Feb 27, 2026)
- Twitter: @themumbridge
- **Note**: Facebook removed from footer as of February 27, 2026

---

## Summary

The Mum Bridge & Care Foundation website is a beautifully designed, accessible, and user-friendly single-page website that effectively communicates the organization's mission of supporting mothers with disabilities. The design system prioritizes warmth, dignity, and accessibility while maintaining professional credibility. The site features:

- **Sophisticated design system** with CSS variables and consistent spacing
- **Accessibility-first approach** (WCAG compliant)
- **Responsive design** that works seamlessly across all devices
- **Smooth animations** that enhance without distracting
- **Clear CTAs** guiding users to donate, volunteer, or join the community
- **Professional credibility** through board member bios, SDG alignment, and registration info

The website is fully operational with legal compliance pages (Privacy Policy and Terms of Use) in place and Google Analytics 4 tracking active across all three pages. Social media presence has been updated: Facebook removed, LinkedIn URL corrected. The site is ready for Google Ad Grants eligibility review.

---

---

## Knowledge Maintenance Protocol

This document MUST be updated whenever changes are made to the codebase. Before considering any development task complete:

1. Update the relevant section(s) in this document
2. Mark any completed TODO items with ✅ and the completion date
3. Add new features/components to the appropriate sections
4. Update the "Last Updated" date at the top and bottom of this file
5. Document any new third-party integrations (tracking, forms, APIs)

---

**Last Updated**: June 2, 2026
**Document Maintainer**: Development Team
**Purpose**: Onboarding, reference, and continuity across development sessions
