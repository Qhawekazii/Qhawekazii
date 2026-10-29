# St Frusquin Sporting — a club website that's fast on mobile data and never makes things up

**Client:** St Frusquin Sporting Football Club ("The Stallions") · **Solo project**
**Live:** [st-frusquin-sporting.vercel.app](https://st-frusquin-sporting.vercel.app)
**Stack:** React 19 + Vite · CSS Modules with design tokens · Formspree · GitHub Actions / Vercel
**Status:** Live; source is private (client work)

---

## The problem

A community football club with five teams (Seniors, U15, U13 Boys, U13 Girls, U11) had no website. Parents, players and sponsors relied on social media to find fixtures, contact details and photos. The club had over 100 match photos and almost no fixed fixture or roster information yet.

Two constraints shaped everything: most visitors are parents on phones with limited data, and the club needed something they could trust and keep updated.

## What I did

**Cut the first load from 32 MB to 3.9 MB.** The gallery originally loaded 101 full-size photos. I generated small thumbnails for the grid and load the full image only when someone opens it — an 88% reduction in initial page weight.

**Organised the site around the five divisions.** Tabs filter fixtures, team and gallery by division, each with a live link to that team's official league page. Photos are tagged by division so parents find their child's team quickly.

**Refused to fill gaps with fake content.** Fixtures, roster and news show an honest "coming soon" state instead of invented names and results. A club site with wrong fixtures is worse than one that says "not yet".

**Made it accessible.** Fixed button contrast to WCAG AA, added visible focus states and larger touch targets, gave the photo lightbox proper dialog semantics with a focus trap, and switched off animation for anyone who has reduced motion turned on.

**Made the contact form real.** It submits through Formspree with loading, success and error states, so messages reach the club.

**Rebuilt it as it grew.** I started with plain HTML/CSS/JS, then migrated to React + Vite with a bolder sports-brand redesign once the content structure was clear. I also fixed a deployment issue so the same build works on both GitHub Pages and Vercel.

## Outcome

- 88% lighter first load (32 MB → 3.9 MB)
- Five divisions, 100+ photos, real coach portraits and league links in one place
- A README written for client handoff, so the next person can update it
