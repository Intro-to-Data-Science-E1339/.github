# Intro to Data Science - course control panel

This is the **`.github` repo** for the `Intro-to-Data-Science-E1339` course org - the control panel faculty & instructors use to run
the course. **You never need a CLI or to write code: every action is a clickable UI button.**

## Run an action

Open the **[Actions tab](https://github.com/Intro-to-Data-Science-E1339/.github/actions)**, pick a workflow, and click
**Run workflow**. Buttons only show if you have write access - you're in this org's
`course-admin` team (declared here, course-wide), or a cohort's `instructors-<tag>` team
(declared in that cohort's own `classroom-config/people.yml`). The full, annotated list of
actions is on the **[org home page](https://github.com/Intro-to-Data-Science-E1339)**.

## Typical flow

1. **New materials repo** / **New assignment** - scaffold your content repos, then fill them in.
2. Create an empty **cohort org** for the year, add the bot as an Owner, then run **Bootstrap cohort**.
3. Each session: **Release materials** / **Release assignment**. Students self-onboard via the cohort's
   **welcome** "Join" issue.
4. Grading: **Grade assignment** -> **Sync gradebooks** -> **Render grades** -> **Distribute grades**.

## What's in here

- `.github/workflows/` - the action buttons (seeded from the central toolkit; refreshed by **Refresh actions**).
- `dsl-course.yml` - this course's identity (name/code) and `course_admins` (the
  course-wide admin SSOT, kept in sync into every cohort by **Sync membership**).
  Instructors/TAs and the schedule are both declared per cohort instead, in that
  cohort's own `classroom-config`.
- `profile/README.md` - the public org landing page (auto-generated repo index).

Built and kept in sync by the [DSL teaching toolkit](https://github.com/hertie-data-science-lab/dsl-teaching-course-setup).
