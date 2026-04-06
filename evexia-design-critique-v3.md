# Evexia Primary Care — Expert Panel Design Critique v3

**Site:** https://evexia-spec.vercel.app
**Date:** April 6, 2026
**Context:** Spec pitch site built by Bar1 Digital for Nina Pliakos, FNP-C. v3 reflects updates from v2 critique implementation — column swap on About, offset frame, stats under photo, services font cleanup, and section spacing tightening.

---

## Site Overview

| Metric | Value |
|--------|-------|
| **Total page height** | ~8,800px |
| **Sections** | Hero, Etymology bar, Philosophy, About Nina, Services (7), Testimonials, Getting Started, Pricing & Coverage, CTA Band, Find Us, Footer |
| **Color palette** | Ink #1C1914, Ivory #F8F5F0, Sage #7A8C6E, Gold #B89A66, Ash #56534C, Parchment #EDEAE3, Blush #C08472, White #FFFFFF |
| **Fonts** | Cormorant Garamond (display headlines only) + Inter (body, UI, service names) |
| **CTAs** | 4 buttons: 3× "Schedule Your Visit / Book Your Appointment" (sage bg), 1× "Book Your First Visit" (white bg in CTA band) |
| **Schema markup** | MedicalBusiness JSON-LD ✓ |
| **Open Graph** | Title, description, image ✓ |
| **Skip nav** | Missing ✗ |
| **Image alt text** | Present on all images ✓ |
| **Real booking integration** | Missing ✗ |
| **Real map embed** | Missing (styled text placeholder) ✗ |

---

## Phase 1: Critique

### Jakob Nielsen — Usability Expert

**What works well**

The navigation is clean and minimal — five items with clear labels that map to the actual page sections. The sticky header with scroll-state background change solves the "Where am I?" heuristic competently. The service expand/collapse accordion pattern correctly applies progressive disclosure, showing only the service name and one-line description until the user opts to expand. This matches Nielsen's principle of matching the system to user need: people scanning services don't need all 8 bullet points — only those investigating a specific service do.

The three-step "Getting Started" section directly addresses the anxiety new patients feel. Numbered steps, short imperative titles (Schedule, Your Visit, Your Plan), and brief supporting copy deliver the procedural clarity that Nielsen's "Help users recognize, diagnose, and recover from errors" and "Help and documentation" heuristics call for.

**Concerns**

1. **No actual booking mechanism.** The primary CTA "Book Your Visit" scrolls to a contact section with a phone number and email address. Nielsen's "User control and freedom" heuristic demands the path from intent to action be as short as possible. A user who decides to book at 11pm, or who prefers not to call, has no option. The lack of an online booking link is the single biggest conversion leak on the site.

2. **Navigation omits two important sections.** "Pricing & Coverage" and "Find Us" are not in the top nav. A first-time visitor trying to confirm the practice accepts their insurance, or to find the address, must scroll through the entire page. These are decision-critical pages for healthcare consumers.

3. **Fake phone number and placeholder email.** `(480) 555-0147` is obviously fake to anyone who notices; `hello@evexiaprimarycare.com` doesn't exist. For a pitch site, this is acceptable, but the presentation would be markedly stronger with real contact details or clearly marked placeholder notes for the client review context.

4. **"Stories" nav label is ambiguous.** Users scan nav labels for familiar category words. "Stories" reads like a blog or social media feed — not patient reviews. "Reviews" or "Patients" would better set expectations and match the content behind the link.

5. **Location section has no real map.** The map placeholder is a styled text card with a "Get Directions" link. This violates the "Match between system and the real world" heuristic — users expect a visual map in a map slot. At minimum, an embedded Google Maps iframe would dramatically increase place familiarity and trust.

6. **No error states or form.** There's no contact form — only a button that routes to email or phone based on device detection. If that detection fails or the user doesn't have a mail client configured, the CTA silently fails with no fallback or error message.

---

### Don Norman — UX Pioneer

**What works well**

The three-level emotional design structure is working. At the visceral level, the botanical hero image and warm typographic palette create immediate calm and luxury — appropriate for a healthcare practice differentiating itself from clinical sterility. At the behavioral level, the service accordion reduces cognitive load cleanly. At the reflective level, Nina's personal story in the About section — "She spent years in high-volume healthcare settings watching something erode" — creates the narrative identification that makes a practice feel personally chosen, not just convenient.

The column swap in the About section (v3) is noticeably better. Content left, photo right follows the natural reading pattern in English. The reader finishes Nina's story and credentials before landing on her face — so the photo functions as confirmation of the person they've just read about rather than a mugshot at the start.

**Concerns**

1. **The hero image is disconnected from the human story.** A botanical plant in a glass is beautiful but anonymous. The site's entire emotional arc is built on Nina's personal story and the patient-provider relationship. The hero image could be a photograph of the actual practice interior, or Nina at her desk — something that gives visitors a conceptual model of what walking through that door actually feels like. Stock botanicals, however beautiful, signal "template."

2. **The stats (10+, 45, 5★) are under the photo but lack context.** "45 Min. Average Visit" is genuinely differentiating — most primary care visits are 15-20 minutes. But the number alone doesn't signal why it matters. A small contextual label like "vs. industry avg: 15 min" would transform a data point into an emotional reframe.

3. **The "Your Provider" badge overlaps the photo at `left: -2rem`.** On certain viewport widths, this will clip outside the content column or overlap the text column. The affordance suggests a floating credential card, but the positioning risks visual clipping that undermines the polish effect it's meant to create.

4. **Three testimonials is the minimum viable social proof.** Three quotes, all from 2024-2025, with no names beyond first name and last initial. Healthcare decisions are high-stakes. Norman's reflective level design asks: does this feel trustworthy? With no star count, no Google review badge, no photo of the patient (even illustrated avatars), and no link to a third-party review platform, the trust signals are thin. A "Read more on Google" link to a real Google Business profile would close this gap.

5. **The CTA band button style breaks consistency.** Three CTAs use sage background buttons, then the full-width CTA band uses a white button on a dark green background. The style divergence confuses the signifier system — the user has learned sage = book, but now white = book. Keeping all booking CTAs in one style would reinforce the learned pattern.

---

### Dieter Rams — 10 Principles of Good Design

**What works well**

Principle 4 — "Good design is unobtrusive" — is largely achieved. The navigation disappears into the content. The typography never competes with the message. The service rows respect the rhythm of the page. The section dividers (small sage asterisks) are appropriately modest. The palette is restrained: two neutrals, one accent (sage), one secondary accent (gold used sparingly). This is fundamentally the right design philosophy for a healthcare provider.

**Concerns**

1. **The etymology bar violates Principle 10: "As little design as possible."** The Greek pronunciation guide `εὐεξία · ev · ek · si · a · "The body in its naturally flourishing state"` is placed between the hero and the philosophy section. As a brand element, it's charming. But it creates a full-width interruption that stalls the emotional momentum of the hero. Consider integrating this etymology into the footer or as a subtle decorative element on the About section rather than a full section break.

2. **The offset photo frame (new in v3) adds ornamentation that competes with the photo.** The `::before` pseudo-element sage rectangle is a good editorial instinct, but the 1.5px border at 38% opacity adds visual noise without contributing information. Rams would ask: does this element serve a purpose, or is it decoration? If decoration, remove it. A stronger photographic framing approach — like a more distinctive image crop or a colored background behind the photo column — would serve the function without the fussy frame.

3. **The services section uses two featured rows (`svc-featured`) but the visual distinction is subtle.** Sage-colored numbers on otherwise identical rows don't adequately prioritize Wellness Exams and Preventive Medicine if those are truly the signature services. A more honest visual hierarchy would elevate these more decisively — or reconsider whether the "featured" distinction is meaningful enough to maintain.

4. **Principle 7 — "Good design is long-lasting."** The blush color (#C08472) appears in the footer links and is not used elsewhere on the page. Orphaned color variables signal unfinished design thinking. Either use blush consistently (for accent links throughout, or for a specific UI role) or remove it.

---

### Jony Ive — Simplicity and Elegance

**What works well**

The typography pairing is the best decision in this design. Cormorant Garamond at large display sizes (the hero headline, section h2s) has a knife-edge elegance — those hairline serifs read as precision and refinement, exactly what a discerning healthcare patient wants to feel. Inter for all functional text (body, service names, credentials, UI) is the right call; it disappears into legibility. The rule — Cormorant for display, Inter for everything else — is clear, consistent, and self-reinforcing.

The sticky photo column in the About section, with content scrolling past a fixed Nina portrait, is a subtle but powerful choice. The user reads her story while her face remains present — it's a digital equivalent of a face-to-face conversation.

**Concerns**

1. **The "Book Your Visit" hero button uses a slightly muted sage.** The hero CTA is the most important button on the page. At `background: var(--sage) = #7A8C6E`, it's quiet against the dark hero background — which is elegant, but potentially too quiet. A very slight saturation boost on the hover state, or a sharper contrast between the default and hover state, would give it more physical presence without compromising the palette.

2. **The credential grid (4 items, 2 columns) has disproportionate visual weight.** After tightening margin-top to 1.6rem (v3), it reads better. But the credential items have no visual separator between the institution label (0.74rem uppercase, low opacity) and the degree title (0.86rem, darker). A hair of additional spacing between cred-school and cred-degree — even 2px — would give each credential item a cleaner internal structure.

3. **Section-to-section rhythm breaks at the CTA band.** The page flows: parchment → ink → parchment → ivory → parchment → ivory → parchment → dark (CTA) → parchment → ink (footer). The dark CTA band is the only full-bleed dark element outside the hero and services. This contrast is powerful but the entry into it (from the ivory insurance section, with a thin section-divider asterisk before it) feels abrupt. A more gradual transition — perhaps the CTA band inheriting a slightly lighter dark tone, or a generous top padding — would smooth this moment.

4. **The about-badge (`Your Provider / Nina Pliakos / FNP-C`) at `left: -2rem` creates an awkward hang.** The badge is meant to feel like a floating credential overlay. But positioned at -2rem from the left edge of the photo frame, it extends into the content column's space, potentially sitting over body text on intermediate viewport widths. This needs either a `min-width` media query guard or a repositioning to `bottom: -1px; left: 0` to keep it safely within the photo column.

---

### Ethan Marcotte — Responsive Web Design

**What works well**

The responsive breakpoints (1024px, 768px, 600px, 480px) cover the critical device transitions. The `.hbr` span system for responsive heading breaks is a thoughtful progressive enhancement — it lets the display typography break elegantly at wider viewports without creating orphaned words on mobile. The service expand/collapse works identically on mobile (single-column grid) and desktop (4-column grid).

**Concerns**

1. **The `about-photo-col` is `position: sticky; top: 110px`.** At mobile breakpoints where the grid collapses to a single column (stacked), `sticky` has no effect — but the photo still has `height: 580px` applied. A 580px fixed-height image on a 390px wide iPhone 14 will be tall and dominating. The object-fit: cover is correct, but the height may need to reduce to 380-420px on mobile.

2. **The `svc-detail-content` grid (`grid-template-columns: 1fr 1fr`) collapses to single column via the `.svc-row { grid-template-columns: 1fr }` mobile override — but the detail panel's 2-column grid is not separately overridden.** The detail items inside an expanded service row may try to render in 2 columns on small screens where the row itself has gone single-column, creating a layout inconsistency.

3. **`grid-template-columns: 6fr 5fr` on the About section has no graceful collapse between 768px and 1024px.** At ~900px the content column will be quite wide and the photo column quite narrow, potentially causing the badge to run outside its container. The 768px breakpoint stacks to a single column, but the intermediate range is unguarded.

4. **The counter animation uses `threshold: 0.6`** — the element must be 60% visible before the counter starts. On shorter mobile viewports, large sections may never reach 60% viewport intersection, so counters (10+, 45, 5★) may never animate. Reducing to `threshold: 0.2` or `0.3` would increase reliability.

5. **No `loading="lazy"` on the philosophy section image.** The Nina photo (hero images) loads eagerly which is correct. But the eucalyptus philosophy image has `loading="lazy"` while the philosophy section appears quite early in the page. Given section order, this image will likely be in the user's first scroll — lazy loading it may cause a visible late load. Consider `loading="eager"` or removing the lazy attribute from the second image.

---

### Vitaly Friedman — Web Design Educator

**What works well**

The site successfully communicates its core conversion message: this practice is different because Nina gives you more time and genuinely listens. That message is threaded through every section — the hero subheadline, the philosophy quote, Nina's story, the 45-minute average visit stat, and every testimonial quote. Message consistency is harder to achieve than it looks, and this site does it without feeling like it's hitting you over the head.

The insurance/pricing section is commendably transparent. Many private practices bury pricing or omit it entirely. Displaying "$200 first visit, $125 follow-ups" alongside insurance acceptance signals confidence and removes a major hesitation for self-pay patients.

**Concerns**

1. **No online booking integration is the most significant business risk.** From a conversion perspective: a visitor who decides to book but can't do so immediately (phone line closed, no mail client configured, cognitive friction of composing an email from scratch) will often not return. The call-to-action chain ends at a phone number. Integrating a booking widget (Zocdoc, Jane App, Calendly, or a custom form) would dramatically increase conversion. Even a mailto link that pre-populates the subject line ("Appointment Request – [Your Name]") reduces friction.

2. **The testimonials section needs volume and verification.** Three anonymous pull-quotes with only first name + last initial carry minimal credibility in 2026. Healthcare consumers routinely check Google reviews, Healthgrades, and Zocdoc ratings before booking. A Google review badge ("4.9 ★ on Google · 47 reviews") or a link to the Google Business profile would anchor the qualitative testimonials in verifiable data.

3. **No calls to action in the navigation.** The "Book a Visit" nav button is the only action item. Adding "Insurance" or "Pricing" to the nav (even as a secondary item) would capture users who come to the site with a specific question — "does she take my insurance?" — and can't find the answer without scrolling.

4. **The services section doesn't communicate what a session actually includes.** The service descriptions list features ("Comprehensive annual physical exam, Age-appropriate cancer screenings...") but don't anchor to duration, included vs. add-on, or how they compare to a standard primary care visit. A short pricing note per service category, or a "What's Included in a Wellness Exam?" anchor, would reduce pre-booking uncertainty.

5. **No social media or external presence signals.** No Instagram, no Google Business link, no Healthgrades badge. For a spec site, this is fine. But for the real launch, social proof from external platforms (even a single Google review widget) is essential for a healthcare provider competing against established practices.

6. **SEO: the page title is well-formed** (`Evexia Primary Care | Nina Pliakos, FNP-C · Scottsdale, AZ`) but there is no meta description. The OG description is present but the `<meta name="description">` tag for standard search snippet display appears to be missing. This reduces search result click-through rates.

---

## Phase 2: Prioritized Recommendations

### 1. Add online booking integration or pre-populated contact form
**Problem:** Every CTA on the site ends at a phone number or email — there's no way to book outside business hours or without initiating a phone call.
**Fix:** At minimum, change the "Book Your Appointment" button to a pre-populated mailto:
```html
<button onclick="window.location.href='mailto:hello@evexiaprimarycare.com?subject=New%20Patient%20Appointment%20Request&body=Hi%20Nina%2C%0AI%27d%20like%20to%20schedule%20a%20new%20patient%20appointment.%0A%0AName%3A%0APhone%3A%0APreferred%20days%2Ftimes%3A'">Request Appointment</button>
```
Ideal: embed a Calendly widget or Zocdoc "Book Online" button as a secondary CTA alongside the phone number.
**Impact:** Direct conversion increase — removes the largest friction point in the booking funnel.
**Effort:** 15 minutes for mailto fix; 1-2 hours for Calendly integration
**Credit:** Nielsen, Friedman

---

### 2. Add "Pricing" and "Find Us" to the navigation
**Problem:** Two of the most decision-critical sections (insurance/pricing and location) are not accessible from the nav. Users looking to answer "does she take my insurance?" or "where is this practice?" must scroll the entire page.
**Fix:**
```html
<!-- Add to nav ul -->
<li><a href="#insurance">Pricing</a></li>
<li><a href="#location">Find Us</a></li>
```
Or replace "Stories" with a dropdown or expand to a 7-item nav with a visual divider before "Book a Visit."
**Impact:** Reduces drop-off from users with specific intent questions.
**Effort:** 10 minutes
**Credit:** Nielsen, Friedman

---

### 3. Add a real Google Maps embed to the Find Us section
**Problem:** The map placeholder is a styled text card. Users expect a visual map — it's a standard affordance for a location section.
**Fix:** Replace `.loc-map` content with an iframe:
```html
<iframe
  src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3328...ACTUAL_EMBED_URL"
  width="100%" height="100%" style="border:0; min-height:380px;"
  allowfullscreen="" loading="lazy"
  referrerpolicy="no-referrer-when-downgrade">
</iframe>
```
Keep the "Get Directions →" link as a fallback overlay.
**Impact:** Trust signal, place familiarity, navigation intent.
**Effort:** 15 minutes once the real address is confirmed
**Credit:** Nielsen, Norman

---

### 4. Add Google review count or Healthgrades badge to the testimonials section
**Problem:** Three anonymous pull-quotes carry minimal credibility as standalone trust signals.
**Fix:** Add a verifiable review anchor above the testimonials:
```html
<div class="review-anchor reveal" style="text-align:center; margin-bottom:2rem;">
  <span style="font-family:'Cormorant Garamond',serif; font-size:2rem; color:var(--ink);">4.9★</span>
  <span style="display:block; font-size:0.78rem; letter-spacing:1.5px; text-transform:uppercase; color:var(--ash); margin-top:4px;">
    <a href="[Google Business Profile URL]" target="_blank" rel="noopener" style="color:var(--sage);">47 Reviews on Google</a>
  </span>
</div>
```
**Impact:** Converts "nice quotes" into verified social proof — the #1 trust signal in healthcare.
**Effort:** 20 minutes
**Credit:** Norman, Friedman

---

### 5. Fix the About badge position for intermediate viewport widths
**Problem:** `.about-badge` at `left: -2rem; bottom: -1px; position: absolute` will extend into the content column on viewports between 768px and ~1024px, potentially overlapping body text.
**Fix:**
```css
.about-badge {
  left: 0;          /* safe within photo column */
  bottom: -1px;
  /* keep all other styles */
}

@media (min-width: 1100px) {
  .about-badge { left: -2rem; }  /* only overhang on wide screens */
}
```
**Impact:** Prevents layout breakage at intermediate viewport widths.
**Effort:** 5 minutes
**Credit:** Marcotte, Ive

---

### 6. Reduce testimonial item padding and add volume
**Problem:** `.test-item { padding: 2.5rem 0 }` creates generous white space between three short quotes, making the section feel padded rather than rich.
**Fix:**
```css
.test-item { padding: 1.8rem 0; }
```
Also increase from 3 to 5-6 testimonials. Three feels like minimum viable social proof.
**Impact:** Denser social proof section; less scrolling to reach the Getting Started CTA.
**Effort:** 5 minutes for CSS; content from client
**Credit:** Nielsen, Friedman

---

### 7. Add a meta description tag
**Problem:** The page is missing `<meta name="description">` — only OG description is present. Without it, Google generates its own search snippet from page content, which is often poorly targeted.
**Fix:** Add to `<head>`:
```html
<meta name="description" content="Evexia Primary Care — unhurried, personalized primary care in Scottsdale, AZ. Nina Pliakos, FNP-C. Same-week appointments. Insurance accepted. Self-pay from $200.">
```
**Impact:** Improved search result click-through rate and SEO control.
**Effort:** 2 minutes
**Credit:** Friedman

---

### 8. Unify CTA button style across the page
**Problem:** The large CTA band uses a white button on dark background, while all other CTAs use sage. This breaks the learned visual signifier system.
**Fix:**
```css
.btn-cta {
  background: var(--sage);
  color: white;
  border: 1.5px solid var(--sage);
}
.btn-cta:hover {
  background: transparent;
  color: white;
  border-color: white;
}
```
**Impact:** Consistent affordance system — users always know what a booking button looks like.
**Effort:** 5 minutes
**Credit:** Norman, Ive

---

### 9. Add a skip-to-content link for accessibility
**Problem:** The site has no `<a href="#main" class="skip-nav">Skip to content</a>` element. Screen reader and keyboard users must tab through the entire navigation on every page load.
**Fix:**
```html
<!-- First element inside <body> -->
<a href="#philosophy" class="skip-nav" style="position:absolute;left:-999px;top:auto;width:1px;height:1px;overflow:hidden;">Skip to main content</a>
```
```css
.skip-nav:focus { position:static; width:auto; height:auto; }
```
**Impact:** WCAG 2.1 AA compliance — "bypass blocks" success criterion 2.4.1.
**Effort:** 5 minutes
**Credit:** Marcotte

---

### 10. Guard the About grid intermediate breakpoint
**Problem:** `grid-template-columns: 6fr 5fr` has no override between 768px and 1024px. At ~900px the photo column becomes quite narrow, and the badge may overflow its bounds.
**Fix:**
```css
@media (max-width: 980px) and (min-width: 769px) {
  .about-grid { grid-template-columns: 1fr 1fr; gap: 3rem; }
  .about-photo-frame img { height: 460px; }
}
```
**Impact:** Smooth layout across all viewport widths.
**Effort:** 10 minutes
**Credit:** Marcotte

---

## Phase 3: Overall Vision

After applying these ten changes, Evexia's spec site stops being a beautiful brochure and becomes a functioning conversion machine. The most transformative single change is the booking integration: when a visitor who's just read Nina's story and felt that "this is the provider I've been looking for" moment can book directly — right there, without a phone call — the site's job is complete. Everything else is in service of that moment.

With the Google Maps embed in the Find Us section, the location stops feeling like a placeholder and starts feeling like a real place you could walk into next Tuesday. Paired with a Google review badge anchoring the testimonials — even just a star count and review number — the social proof section becomes a cascade of trust rather than three isolated quotes floating in white space. The site would carry the credibility of a practice that's been operating and earning genuine patient loyalty, not just launched.

The navigation additions (Pricing and Find Us) change the site's posture from "scroll and discover" to "I know what I'm looking for and I can find it." Healthcare consumers often arrive with a specific question: do you take my insurance? Where are you located? What does a first visit cost? Answering those questions in two clicks rather than requiring a full-page scroll converts hesitant visitors into booked patients.

The visual refinements — unifying the CTA button style, guarding the About section's intermediate breakpoint, fixing the badge position — are invisible to most visitors but are exactly the details that distinguish a polished pitch from a demo. When Nina's team or a potential investor looks at this site, the absence of layout glitches on a 13-inch MacBook at 900px sends a signal about the care and craft behind Bar1 Digital's work.

What this site already does exceptionally well — and should stay untouched — is its emotional architecture. The progression from botanical calm (hero) to personal philosophy (Approach) to human story (About Nina) to comprehensive capability (Services) to social proof (Stories) to clear path forward (Getting Started and Pricing) is exactly right. That's not a common skill in spec site design, and it's what will make this pitch compelling to Nina. The ten recommendations above are refinements to an already strong foundation. With them applied, this site would be ready to go live and start booking patients — not just pitching to them.

---

*Critique generated using the Bar1 Digital Expert Panel process. Previous critique: `evexia-design-critique-v2.md`.*
