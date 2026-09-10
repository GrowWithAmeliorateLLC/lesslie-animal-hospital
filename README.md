# lesslie-animal-hospital (production site)

Static production website for **lesslieanimalhospital.vet**, served by its own dedicated Netlify site connected to this repo.

## Publish setup (one-time)
1. In Netlify, create a new site from **this** repo (`GrowWithAmeliorateLLC/lesslie-animal-hospital`).
2. No base directory needed — the repo root is the site root. **Publish directory** = `.` (already in `netlify.toml`).
3. Deploys are automatic on every push to `main`.

## Notes
- Pages are **root-relative directory-index URLs** (`/about-us/`, `/book/`) — never repo-relative.
- `_redirects` — the 301 map (old Weebly `.html` → new URLs). Preserves the homepage rankings and boarding/appointments/contact equity from the July 2026 SEO baseline.
- **Booking** is the client's existing **Vello** scheduler (Direct Booking, synced to ezyVet). The `/book/` page and the "Book Now" buttons point to the Vello booking URL — **replace the `VELLO_BOOKING_URL` placeholder** once Eric/IDEXX provide it.
- **Analytics:** add the **GA4** tag site-wide at build (replaces the dead Universal Analytics).
- `/mockup/` — the client-facing design mockup (full-bleed redesign). Not part of the final site nav; remove or leave noindex at launch.
- Stack preserved (not touched): ezyVet (PIMS), Vello (booking/comms), phone/AI receptionist, Vetco, Vet Direct, Tiger World.

## Before go-live
- **Remove the `<meta name="robots" content="noindex">` tag from every page** (each page carries it until launch).
- DNS cutover: apex `A` → Netlify, `www` CNAME → Netlify; leave MX/email records untouched.
- Verify all `_redirects` resolve, SSL is live, the Vello Book Now works on mobile, and GA4 is firing.

## Pages (core 8)
`/` · `/about-us/` · `/services/` · `/book/` · `/boarding/` · `/exotics/` · `/emergency/` · `/contact/`
Additional pages (Dentistry, Grooming, Surgical, Vaccinations, Resources, Forms, blog) are $199 add-ons and currently 301 to `/services/` or the homepage.

## Migration note
Migrated Sept 2026 from `found-reports/lesslie-animal-hospital-prod/` into this dedicated repo. Once the Netlify production site is repointed here, the old folder in `found-reports` can be removed. The client's scope/ITEX pages remain in `found-reports` because they serve the shared `scope.` / `itex.` subdomains.
