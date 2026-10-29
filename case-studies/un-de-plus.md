# Un De Plus Tours & Transfers — from a broken template to a site that takes bookings

**Client:** Un De Plus Tours & Transfers, an existing South African tour operator · **Solo project**
**Live:** [unde-plus.co.za](https://unde-plus.co.za)
**Stack:** Next.js 14 · TypeScript · Tailwind CSS · Supabase (Auth, PostgreSQL, Row Level Security) · jsPDF · Vercel
**Status:** Live; source is private (client work)

---

## The problem

The client had a site generated with an AI site builder. It looked finished, but it didn't work as a business tool:

- Booking, contact, donation and volunteer forms didn't submit anywhere — enquiries were silently lost
- Many buttons did nothing, and several hero images were broken
- The contact details were placeholders, not the real phone numbers
- Broken structured data in the homepage crashed the build
- The "translate" option didn't actually translate
- Every page had its own copy-pasted navigation, so fixing one link meant fixing it everywhere

For a tour operator selling to international visitors, a form that quietly drops an enquiry is lost revenue.

## What I did

**Made every enquiry land somewhere.** Wired the booking form, contact form and charity (Little Rose) forms to Supabase, with real loading, success and error states. Staff can see every enquiry and saved itinerary in an `/admin` dashboard.

**Built a trip planner customers can keep.** Visitors pick experiences, then save the itinerary to an account, download it as a PDF, email it to themselves, or export it to Google Docs — so the plan follows them back to their travel group.

**Opened the site to international visitors.** A working language switcher translates the whole site into 19 languages, and an accessibility widget offers read-aloud, adjustable text size and high-contrast mode.

**Fixed the foundations.** One shared navbar in the root layout, real contact details everywhere, a page per service (safari, Johannesburg, Soweto, Cape Town, Durban, Mpumalanga, custom tours, transfers, shuttles), real photos, a social share image, sitemap and metadata, and patched dependency vulnerabilities.

**Took it live.** Deployed on Vercel and connected the client's own domain.

## Decisions worth explaining

- **Security in the database.** Row Level Security means customers can only read their own itineraries, anyone can submit an enquiry, and only admins can read them all.
- **The client owns his hosting.** He pays Vercel directly on his own card, so the site doesn't depend on me to stay online.

## Outcome

- Booking and contact enquiries are captured instead of lost
- The build passes and the site is live on the client's domain
- Staff have one dashboard for every itinerary and enquiry
