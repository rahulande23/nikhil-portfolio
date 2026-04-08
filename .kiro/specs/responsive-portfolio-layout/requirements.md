# Requirements Document

## Introduction

This feature makes the video editor portfolio website fully responsive across four breakpoints: desktop (>1024px), tablet (768px–1024px), mobile (≤768px), and small mobile (≤480px). The current site has an incomplete media query that hides the nav links on tablet without providing a replacement, portrait video cards break on mobile, the hero section clips on small screens, the custom cursor appears on touch devices, and the contact email overflows its container. The goal is a polished, cinematic experience on every screen size while preserving the dark film-editor aesthetic.

## Glossary

- **Portfolio**: The video editor portfolio website (index.html + styles.css + links.js)
- **Nav**: The top navigation bar containing the logo, nav links, CTA button, and hamburger button
- **Hamburger_Menu**: The full-screen mobile overlay that replaces the desktop nav links on small screens
- **Hero**: The two-column opening section containing the title, description, stats, and video mockup
- **Work_Grid**: The CSS grid of project cards in the Work section
- **Portrait_Card**: A project card displaying a 9:16 aspect-ratio video
- **Landscape_Card**: A project card displaying a 16:9 aspect-ratio video
- **Reel_Player**: The full-width iframe embed in the Showreel section
- **Process_Grid**: The four-step workflow grid in the Process section
- **Contact_Section**: The bottom section containing the large title, email link, and social links
- **Custom_Cursor**: The dot-and-ring cursor overlay driven by mousemove events
- **Floating_Tags**: The decorative "4K / 120fps", "Color Grade", and "VFX · Motion" badges overlaid on the hero video mockup
- **Touch_Device**: Any device that reports `(hover: none) and (pointer: coarse)` via CSS media query or has touch events
- **Breakpoint_Desktop**: Viewport width greater than 1024px
- **Breakpoint_Tablet**: Viewport width between 768px and 1024px (inclusive)
- **Breakpoint_Mobile**: Viewport width 768px or less
- **Breakpoint_Small_Mobile**: Viewport width 480px or less
- **Touch_Target**: Any interactive element (link, button) that a user taps on a touch device

---

## Requirements

### Requirement 1: Hamburger Menu Navigation

**User Story:** As a mobile visitor, I want a hamburger menu that opens a full-screen overlay, so that I can navigate the site without the nav links being hidden with no replacement.

#### Acceptance Criteria

1. WHILE the viewport is at Breakpoint_Mobile, THE Nav SHALL display the hamburger button and hide the desktop nav links and CTA button.
2. WHEN the hamburger button is tapped, THE Hamburger_Menu SHALL animate open as a full-screen overlay covering the viewport.
3. WHEN the Hamburger_Menu is open, THE Hamburger_Menu SHALL display all five section links and a "Hire me" CTA link in a vertically stacked layout.
4. WHEN a navigation link inside the Hamburger_Menu is tapped, THE Hamburger_Menu SHALL close and scroll to the target section.
5. WHEN the Hamburger_Menu is open, THE Portfolio SHALL prevent body scroll.
6. THE hamburger button icon SHALL animate from three horizontal bars to an X shape when the menu is open, and back to three bars when closed.
7. THE Hamburger_Menu open and close transitions SHALL complete within 350ms using a CSS transform or opacity animation.
8. WHILE the viewport is at Breakpoint_Desktop, THE Nav SHALL hide the hamburger button and display the desktop nav links and CTA button.

---

### Requirement 2: Responsive Hero Section

**User Story:** As a visitor on any device, I want the hero section to display fully without clipping or overflow, so that I can read the title, description, and stats clearly.

#### Acceptance Criteria

1. WHILE the viewport is at Breakpoint_Tablet, THE Hero SHALL switch from a two-column grid to a single-column stacked layout with the text content above the video mockup.
2. WHILE the viewport is at Breakpoint_Mobile, THE Hero SHALL reduce the title font size to no larger than 72px and the description font size to no larger than 15px.
3. WHILE the viewport is at Breakpoint_Small_Mobile, THE Hero SHALL reduce the title font size to no larger than 56px.
4. WHILE the viewport is at Breakpoint_Mobile, THE Hero SHALL hide the Floating_Tags decorative elements.
5. WHILE the viewport is at Breakpoint_Mobile, THE Hero stats row SHALL wrap into a two-column grid rather than a single horizontal row.
6. IF the hero content overflows the viewport height on any breakpoint, THEN THE Hero SHALL allow vertical scrolling without horizontal overflow.

---

### Requirement 3: Responsive Work Grid and Video Cards

**User Story:** As a mobile visitor, I want the project cards to stack into readable columns, so that I can browse the portfolio without cards overflowing or becoming too small to view.

#### Acceptance Criteria

1. WHILE the viewport is at Breakpoint_Tablet, THE Work_Grid SHALL display Portrait_Cards in a two-column grid.
2. WHILE the viewport is at Breakpoint_Mobile, THE Work_Grid SHALL display Portrait_Cards in a single-column layout, each card spanning the full container width.
3. WHILE the viewport is at Breakpoint_Mobile, THE Portrait_Card height SHALL be calculated using a 9:16 aspect ratio relative to the card's width so the video fills the card without distortion.
4. WHILE the viewport is at Breakpoint_Mobile, THE Landscape_Card SHALL maintain a 16:9 aspect ratio and span the full container width.
5. THE card iframe SHALL fill its parent card-visual container at 100% width and 100% height on all breakpoints.

---

### Requirement 4: Responsive Reel Section

**User Story:** As a mobile visitor, I want the showreel player to scale to my screen width, so that I can watch the reel without horizontal scrolling.

#### Acceptance Criteria

1. THE Reel_Player SHALL maintain a 16:9 aspect ratio at all breakpoints using a padding-top percentage or aspect-ratio CSS property.
2. WHILE the viewport is at Breakpoint_Mobile, THE Reel_Player SHALL span the full container width with a maximum width of 100%.
3. WHILE the viewport is at Breakpoint_Mobile, THE section title above the Reel_Player SHALL reduce font size to no larger than 56px.

---

### Requirement 5: Responsive Process Grid

**User Story:** As a mobile visitor, I want the process steps to stack vertically, so that I can read each step without the text being cramped.

#### Acceptance Criteria

1. WHILE the viewport is at Breakpoint_Tablet, THE Process_Grid SHALL display in a two-column layout.
2. WHILE the viewport is at Breakpoint_Mobile, THE Process_Grid SHALL display in a single-column layout with each step spanning full width.
3. WHILE the viewport is at Breakpoint_Mobile, THE step description text SHALL be at least 14px.

---

### Requirement 6: Responsive About Section

**User Story:** As a mobile visitor, I want the about section to stack the portrait and content vertically, so that both are fully readable without overlap.

#### Acceptance Criteria

1. WHILE the viewport is at Breakpoint_Tablet, THE about section SHALL switch from a two-column layout to a single-column stacked layout with the portrait above the content.
2. WHILE the viewport is at Breakpoint_Mobile, THE skills grid chips SHALL wrap freely and each chip SHALL have a minimum height of 44px to meet touch target requirements.
3. WHILE the viewport is at Breakpoint_Mobile, THE awards row SHALL stack vertically rather than display horizontally.

---

### Requirement 7: Responsive Contact Section

**User Story:** As a mobile visitor, I want the contact email and title to fit within the screen width, so that the layout does not break or require horizontal scrolling.

#### Acceptance Criteria

1. WHILE the viewport is at Breakpoint_Mobile, THE contact email link SHALL use `word-break: break-all` or `overflow-wrap: break-word` so it wraps within the container.
2. WHILE the viewport is at Breakpoint_Mobile, THE Contact_Section title font size SHALL scale down to no larger than 48px per line.
3. WHILE the viewport is at Breakpoint_Mobile, THE social links row SHALL wrap into a two-column grid or stack vertically.
4. THE contact email link SHALL remain a tappable anchor tag with a minimum touch target height of 44px on Touch_Devices.

---

### Requirement 8: Hide Custom Cursor on Touch Devices

**User Story:** As a touch device user, I want the custom cursor elements hidden, so that the floating dot and ring do not appear as stale artifacts on my screen.

#### Acceptance Criteria

1. WHILE the device matches `(hover: none) and (pointer: coarse)`, THE Custom_Cursor dot and ring elements SHALL have `display: none`.
2. WHILE the device matches `(hover: none) and (pointer: coarse)`, THE Portfolio JavaScript cursor animation loop SHALL not attach mousemove listeners or SHALL exit early without updating cursor positions.
3. WHILE the viewport is at Breakpoint_Desktop on a non-touch device, THE Custom_Cursor SHALL remain visible and functional.

---

### Requirement 9: Touch-Friendly Tap Targets

**User Story:** As a mobile visitor, I want all interactive elements to be large enough to tap accurately, so that I don't accidentally trigger the wrong action.

#### Acceptance Criteria

1. THE Nav hamburger button SHALL have a minimum width of 44px and minimum height of 44px on Touch_Devices.
2. THE Hamburger_Menu navigation links SHALL each have a minimum height of 44px and padding sufficient to meet that height.
3. THE btn-primary and btn-secondary call-to-action buttons SHALL have a minimum height of 44px on Touch_Devices.
4. THE social links in the Contact_Section SHALL each have a minimum height of 44px on Touch_Devices.

---

### Requirement 10: Typography Scale Across Breakpoints

**User Story:** As a visitor on any device, I want headings and body text to scale proportionally, so that the cinematic aesthetic is preserved without text overflowing or becoming unreadably small.

#### Acceptance Criteria

1. WHILE the viewport is at Breakpoint_Tablet, THE section-title headings SHALL be no larger than 80px.
2. WHILE the viewport is at Breakpoint_Mobile, THE section-title headings SHALL be no larger than 56px.
3. WHILE the viewport is at Breakpoint_Small_Mobile, THE section-title headings SHALL be no larger than 44px.
4. WHILE the viewport is at Breakpoint_Mobile, THE body paragraph text SHALL be no smaller than 14px.
5. THE Portfolio SHALL not produce horizontal scroll at any breakpoint due to text overflow.

---

### Requirement 11: Section Spacing and Padding Adjustments

**User Story:** As a mobile visitor, I want sections to have tighter but comfortable spacing, so that the page doesn't feel either cramped or wastefully padded.

#### Acceptance Criteria

1. WHILE the viewport is at Breakpoint_Mobile, each full-width section SHALL have horizontal padding of no less than 20px and no more than 32px.
2. WHILE the viewport is at Breakpoint_Mobile, the vertical padding between sections SHALL be reduced to no more than 80px from the desktop value.
3. WHILE the viewport is at Breakpoint_Small_Mobile, the vertical padding between sections SHALL be reduced to no more than 60px.

---

### Requirement 12: Smooth Animations Across Devices

**User Story:** As a visitor on any device, I want scroll-triggered animations and transitions to run smoothly, so that the cinematic feel is maintained without jank.

#### Acceptance Criteria

1. THE fade-up, fade-left, and fade-right IntersectionObserver animations SHALL function on all breakpoints.
2. WHILE the device matches `(prefers-reduced-motion: reduce)`, THE Portfolio SHALL disable or minimise all CSS transitions and animations.
3. THE marquee scroll animation SHALL continue to run on all breakpoints without causing layout overflow.
4. WHILE the viewport is at Breakpoint_Mobile, THE film progress bar SHALL remain visible and update correctly on scroll.
