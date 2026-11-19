SafeGarden on Wheels — v8 header, wordmark and booking CTAs

Based on v5 (v6 = lettering, v7 = crayon companions, v8 = animation + booking CTAs). Only the header was redesigned; photos, slider, body copy, SEO metadata, JSON-LD,
contact placeholders and services are unchanged.

WORDMARK
- Real HTML text (selectable, readable by search engines and screen readers), not an image.
- Lettering follows the owner's crayon reference: bold rounded Fredoka 700, both lines in one rust colour
  (#A3430D), "SafeGarden" leads and "on Wheels" follows at 60% size; "EVENT CHILDCARE · VANCOUVER, BC"
  stays in the HTML for search engines and screen readers but is not shown (the hero badge says it).
- Crayon grain: a tiny inline SVG noise texture is clipped to the letters (no extra file or request),
  with a soft light halo. Browsers without text clipping, and high-contrast mode, show solid text.
- Sizes scale from one value on .logo (em-based), so the balance stays the same at every width:
  50px desktop, 44px tablet, 28–36px mobile.
- Fredoka is self-hosted as a 2.4 KB subset (weight 700 only) (fonts/fredoka-brand.woff2, letters of the brand name only)
  and preloaded. A size-adjusted Arial fallback keeps the layout steady while it loads.
  Licence: fonts/Fredoka-OFL.txt (SIL Open Font License 1.1). If the brand name ever changes,
  the subset must be regenerated.

LAYOUT
- Desktop (1001px+): wordmark on the left, six compact navigation items on the right.
- Desktop also has a "Inquire now" button at the right end of the navigation. From 1200px down the
  small grey sub-labels under the navigation items are hidden to make room.
- Tablet (701–1000px): wordmark, "Inquire now" and Menu.
- Mobile (700px and below): wordmark and a single 44×44 Menu button only, so the wordmark gets the room.
  The menu's bottom tile is "Inquire now".
- Wide-screen crayon clouds and sun show only from 1440px, where they cannot touch the wordmark.

CRAYON COMPANIONS
- Cloud behind "Safe", sun after "Garden", pink flower before "on Wheels", and an orange road with a
  brown wheel and speed lines under "on Wheels", following the owner's reference drawing.
- All are sized in em, so they scale with the wordmark at every width.
- Cloud, sun and flower are small WebP copies made for the header (images/brand-cloud.webp,
  brand-sun.webp, brand-flower.webp, about 24 KB together) instead of the 90–180 KB PNGs.
  The road and wheel are inline SVG with a crayon-edge filter (no file).
- The old wide-screen header cloud and sun (shown from 1440px) were removed, because the logo now
  carries its own.
- v8 motion (slow and small): wheel rolls (3s), speed lines pulse, road draws in once on load,
  sun turns (40s), cloud drifts, flower sways. All motion stops for visitors who ask their device
  for reduced motion (the road is then shown fully drawn).

REMOVED
- v5's thin wheel and road line, the small sun beside the wordmark, and the thin "continuity" curve
  above the Approach section.

CSS
- All header rules now live in one block at the top of the stylesheet. Scattered header/menu rules
  and dead selectors (old utility row, .lsun, .em, wig, --bw, continuity-mark) were deleted, not
  overridden. The stylesheet is about 3 KB smaller.
- Inline styles on <header> and the main <nav> were moved into that block.
- Script: the mobile menu now also closes when a tile's icon or label is tapped.

CHECKED
1920, 1440, 1366, 1280, 1100, 1024, 1001, 1000, 768, 700, 480, 390, 360 and 320px:
no horizontal scroll, no overlap between the wordmark, navigation, buttons and decorations,
menu opens inside the screen. Animations for the wordmark are intentionally not added yet.

STILL REQUIRED BEFORE PUBLISHING (unchanged from v4)
- Real contact email or form URL, production domain for canonical/OG/sitemap, owner confirmation
  of qualification and service statements.

INQUIRY CTAs (v8)
- Visitors compare several providers and check prices before committing, so the main button is a plain,
  low-commitment inquiry: "Inquire now" with a chat icon, linking to #contact. Under Packages (#flow) it
  reads "Get a quote", for people comparing prices.
- Placed in: desktop/tablet header, a band right under the first view ("Comparing options? Ask us about
  pricing, dates and ages. No commitment." + "Already have a date? Check availability"), the end of
  Our Goal, Events and Packages (these replaced buttons that only scrolled to their own section),
  and the mobile menu. "Join a pilot" and the hiring buttons are unchanged.
- Look: every inquiry CTA shares one style (class .go) that differs from the regular brown buttons
  (About Us, View all news, Join a pilot…): a sunny yellow-to-orange gradient with dark text (contrast
  above 6:1), a raised 3D edge, a soft light sweep every ~5 seconds, a gently nudging arrow on the menu
  and sticky-bar buttons, and a press-down effect on hover/tap. Motion stops under reduced-motion.
- CSS tidy-up: the regular button no longer needs !important for its text colour; the CTA rules sit right
  after the regular button rules so they win by order, not by overrides.
- Mobile sticky bar: appears once the first-view CTA has scrolled away, hides at the contact section,
  the footer and while the menu is open. Remove the <a class="sbar"> element to switch it off.
- The inquiry form / availability calendar is not built yet; all CTAs point to #contact until it exists.
  When it is, "Inquire now" opens the question tab and "Check availability" the date-request tab.
