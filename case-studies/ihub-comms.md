# iHub Comms — one communication platform built for iHub, in place of paid subscriptions

**Client:** iHub Africa (internal use) · **Team:** CTRL + Create
**My role:** Product engineer — I came up with the idea, owned the product and all of the UI/UX design and mockups, put the team together, built features alongside them, and pitched the app to iHub
**Stack:** React + Vite · Supabase (PostgreSQL, Auth, Row Level Security, Realtime, Storage, Edge Functions) · Vercel
**Status:** Pitched to iHub for internal use; source is private (client work)

---

## The problem

iHub runs its learner cohorts across several separate platforms: one for courses, one for classes, an attendance app, chat groups for announcements, and spreadsheets for tasks and submissions. Two things were going wrong:

- **Cost.** iHub was paying subscriptions for platforms that each covered only one slice of what a cohort needs.
- **Communication gaps.** Information was spread across all of them, so learners missed deadlines and announcements, and mentors had no single place to see who was falling behind.

## My approach

**1. Spotted the gap and defined the product.** I saw iHub struggling with its communication platforms and paying for subscriptions that didn't close the gap, so I scoped one platform that covers what a cohort actually uses day to day, so iHub could stop paying for overlapping tools.

**2. Designed the whole experience.** I owned all of the UI/UX: the information architecture, the sidebar workspace layout, every screen's mockups and the interaction details. The aim was a tool learners would open every day without training.

**3. Built a team to deliver it.** I put together **CTRL + Create** so we could show we can collaborate the way real product teams do: feature branches, pull requests and reviews, with work split across frontend, backend and integration. I worked on features alongside the team.

**4. Pitched it to iHub** as a platform for internal use.

## What the product does

- **Announcements** mentors can pin, with live notifications
- **Channels and direct messages** — cohort channels, mentor-only rooms, private 1:1 chats
- **Task board** — drag between columns, assignees, due dates, overdue flags, comments, share a task into chat
- **Submissions** with file upload and mentor feedback; learners see only their own
- **Schedule** — a month calendar showing sessions and task deadlines together
- **Attendance** — learners report late or absent with a reason; mentors mark the day
- **Courses** with per-learner module progress
- **Notes** — Notion-style pages with a block editor
- **One search box** across everything, plus an Inbox
- **"My day" dashboard** — the mentor view flags anyone under 80% attendance
- **Admin** — invite people, manage cohorts, channels and integrations

## Product decisions worth explaining

- **Invite-only, so the platform stays iHub's.** There is no public sign-up. An admin invites each person, and their role and cohort are set by the database, not by the browser.
- **Permissions enforced in the database, not just hidden in the UI.** Learner, mentor and admin access is checked by Row Level Security, so tampering with the page can't grant access it shouldn't.
- **Honest about what isn't connected yet.** Course, class and attendance platforms without API access show "not set up yet" instead of made-up numbers.
- **Designed to replace, not add.** Every feature maps to a tool iHub was already paying for or a gap they were covering by hand.

## Under the hood

- Permissions enforced in PostgreSQL with Row Level Security for learner, mentor and admin, not just hidden in the UI.
- Invite-only accounts: a security-definer accept_invite() function sets role and cohort, and a trigger stops non-admins changing their own role.
- Live updates for announcements, messages, task comments and notifications through Supabase Realtime subscriptions.
- Submissions and profile photos in Supabase Storage, with photos visible only to the learner's own cohort.
- One Postgres search function across tasks, announcements, messages, submissions, schedule and notes, still filtered by RLS.
- Edge Functions for invite emails (Resend), integration sync behind one adapter per platform, and an assistant that queries with the user's own token.

## Outcome

- One platform covering announcements, chat, tasks, submissions, schedule, attendance, courses and notes
- Designed end to end by me and built as a team by CTRL + Create
- Pitched to iHub for internal use

## What I'd do next

Pilot it with one cohort and measure which paid platforms they actually stop opening. That is the real test of whether it closes the gap.
