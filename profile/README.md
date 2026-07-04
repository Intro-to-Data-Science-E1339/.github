# Intro to Data Science

**Intro to Data Science** - managed by the Hertie Data Science Lab.
_This page is auto-generated; edits will be overwritten on the next refresh._

## Cohorts

List of cohort orgs registered to receive releases from this course org. _Auto-discovered from the
`cohort-courses-pages.yml` registry_:

- [Intro-to-Data-Science-f2025](https://github.com/Intro-to-Data-Science-f2025)

## Repositories

List of all repositories associated with the course org; a centralised registry and historical
record of course-related content. _Add new course-related content here, then push to the relevant
cohort org using the GitHub Actions below_.

| Repo | Visibility | Description |
| --- | --- | --- |
| [course-materials-f2025](https://github.com/Intro-to-Data-Science-E1339/course-materials-f2025) | private | Course materials (lectures/readings by session) |

## Available actions for faculty & admin

All actions live in the [`.github` repo's Actions tab](https://github.com/Intro-to-Data-Science-E1339/.github/actions)
_(automatically bootstrapped from the central
[dsl-teaching-course-setup repo](https://github.com/hertie-data-science-lab/dsl-teaching-course-setup))_:

### One-time setup actions:
- [**Bootstrap cohort**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/bootstrap-cohort.yml) - configure a freshly-created cohort org (sets up scaffold repos), register it with the course org, refresh dropdowns.
- [**Send enrolment codes**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/send-codes.yml) - generate a random non-PII enrolment code per student and email each their code (to their university inbox). Students paste the code into the welcome Join issue - no personal data in the public repo. `dry_run` previews codes + emails. Needs the `GRAPH_*` (or `SMTP_*`) secrets.
- [**Sync membership**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/sync-membership.yml) - one consolidated, fully-automatic reconcile of org + `students`-team access (from `students.csv`), project teams (from `teams.csv`), `course_admins` (from this org's declared `people:` block, mirrored into every cohort's own `course-admin` team), and each cohort's own `instructors`/`teaching_assistants` (from its `classroom-config/people.yml`, reconciled into that cohort's `instructors` team AND a course-org `instructors-<tag>` team). Triggers on push (editing any of those files takes effect immediately, including removals - there's no prune toggle, the file is the live truth) and on a daily cron (catches a faculty entry's `start`/`end` rotation with no edit that day); `workflow_dispatch` is a manual escape hatch.
- [**New materials repo**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/new-materials.yml) - scaffold a correctly-structured `course-materials-<year>` repo (session folders + the Release buttons).
- [**New assignment**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/new-assignment.yml) - scaffold an `assignment-N-<year>` template repo (starter on `main`; the `solution` branch carries the model solution, `grading.yml`, and the hidden tests).
- [**Refresh actions**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/refresh-actions.yml) - repopulate the cohort/session/assignment dropdowns, re-equip content repos, and rebuild this index.
- [**Show status**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/status.yml) - a per-cohort checklist of everything configured (identity, people, manifest, schedule, roster, teams, grades, session calendar) with direct edit links for anything missing. Read-only.

### Optional: public course website (open courseware)
- [**Publish course website**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/publish-site.yml) - build/refresh a PUBLIC site `Intro-to-Data-Science-E1339.github.io` that shares this course's lecture materials and readings with the world. Opt-in + manual (the first run scaffolds the site). Pick a materials repo and choose for readings: `reading-list` (citations only) or `actual-readings` (also host the files). Because the materials repos are private, the site **hosts** the shared files itself. This is separate from each cohort's student-facing site.

### Session cadence actions:
- [**Release materials**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/release-materials.yml) - publish a given session's content, from every discovered section, into a cohort repo.
- [**Release assignment**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/release-assignment.yml) - generate one private repo per student from a chosen `assignment-*` template repo.

- [**Release code**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/release-code.yml) - run from the repo holding your package; copy a chosen path (a subpackage folder, or a single module file) into a cohort repo's tree, additively. Phased disclosure of a growing importable package - release a topic when you teach it.

NB: alternatively each materials repo *also* carries its own **Release** buttons (run from inside the
repo; there the `session` is a dropdown of that repo's sessions, and each discovered section gets its
own include checkbox).

### Grades (private, previewable):
- [**Grade assignment**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/grade-assignment.yml) - faculty-side autograder: after the deadline, run the HIDDEN tests (from the template's `solution` branch) against each submission and record the machine score into `classroom-config/grades/<assignment>.csv`. Nothing is written to student repos; faculty then add manual marks. Optional per assignment (skipped if `grading.yml` sets `autograde: false`).
- [**Sync gradebooks**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/sync-gradebooks.yml) - ensure every onboarded student has a PRIVATE `grades-<handle>` repo (the single home for all their grades). Idempotent.
- [**Render grades (preview)**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/render-grades.yml) - build per-student `gradebook/<handle>.yml` from `classroom-config/grades/<assignment>.csv` and open ONE pull request. **That PR is the preview** - review every student's grades in the diff before sending.
- [**Distribute grades**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/distribute-grades.yml) - after merging the preview PR, copy each student's gradebook into their private repo and (unless silenced) email each student a notification to their university inbox (needs the `GRAPH_*` or `SMTP_*` secrets).

- [**Scheduled release**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/scheduled-release.yml) - daily cron that auto-releases whatever each cohort's `manifests/<cohort>.yml` (in `.github`) and its `classroom-config/schedule.yml` say is due. Manual runs default to a dry-run preview ("what opens when"). Manual buttons above still work for early/ad-hoc release.

- _[**Sync site**](https://github.com/Intro-to-Data-Science-E1339/.github/actions/workflows/sync-site.yml) - regenerate a cohort's website from the org structure (releases do this automatically; standard workflow has no need for manual sync)._

## How the actions behave

**Release materials** - run it from the materials repo (per-repo `session` dropdown, real
checkboxes per discovered section) or from the course org's central `.github` repo (pick the
source repo, type the session, and optionally list sections to exclude - the source repo is
only known once you run it, so there are no per-section toggles there). It copies the *whole*
`<section>/<NN>_.../` folders - **every file** (any number of sections, and any number of
files per session) - into the cohort's `materials` repo (private + `students` read), nested
under that same folder name. Only the sessions you release appear. `include_syllabus` /
`include_readme` (default off) also copy those root files to the cohort root, overwriting.

**Release assignment** - two stages: (1) it freezes a cohort-level template repo
`<assignment>` from your `assignment-*-<year>` template; (2) it generates one private
`<assignment>-<handle>` repo per onboarded student **from that cohort template**, adding
each as collaborator. After the assignment deadline, rerun with **include_solution** to push the
template's `solution` branch into every student repo. Solutions stay on the `solution`
branch so a normal release never leaks them.

**The cohort website** - every cohort has an auto-deployed site `<org>.github.io`. It is regenerated
on every release (and via **Sync site**). Its lecture links point at the cohort's private repos, so
they only resolve for enrolled members (deliberate).

**The public course website** (optional) - `Publish course website` builds `Intro-to-Data-Science-E1339.github.io`, a public
open-courseware site for the course as a whole. Unlike the cohort sites it **hosts** the shared lecture
files (the source repos are private, so links would 404); readings are published either as a text-only
reading list or as hosted files. It is opt-in and manual - releases and refresh never touch it - so a
public site only exists, and only updates, when you run the action.

## Repository structure (required)

```
Intro-to-Data-Science-E1339/                            <- this COURSE org (persistent)
|-- .github/                      profile + faculty action buttons + cohort registry
|-- course-materials-<year>/      lectures/00_.../   readings/00_.../   (+ syllabus, README)
`-- assignment-<n>-<year>/        is_template repo:
                                    main      -> starter + autograder   (students get this)
                                    solution  -> solution/   (pushed to students on demand)

<Course>-f<year>/                 <- one COHORT org per year (Bootstrap cohort sets it up)
|-- welcome/                      Join issue -> onboard (enrol)
|-- classroom-config/             students.csv  (private roster)
|-- materials/                    released lectures/readings  (students-team read)
|-- <org>.github.io/              auto-deployed website (synced from this structure)
`-- <assignment>-<handle>/        one private repo per student
```

This whole structure is bootstrapped from the central
[`dsl-teaching-course-setup`](https://github.com/hertie-data-science-lab/dsl-teaching-course-setup)
repo (via its **Bootstrap Course Org** action), and the actions above run that same central code.

The course-level actions assume this layout - use **New materials repo** / **New assignment** above to scaffold correctly.

**Materials repo** (`course-materials-<year>`) - the source for Release materials. Any
top-level directory containing at least one ordinal-prefixed (`00_`, `01_`, ...)
subdirectory is a releasable section - no config to declare it:
- `lectures/00_.../` - one folder per session's lecture files;
- `readings/00_.../` - one folder per session's readings;
- add more sections freely (e.g. `labs/00_.../`) - **Refresh actions** picks up new ones;
- `*syllabus*`, `README.md` at the **root** (optional) - released via the syllabus / README toggles.

**Assignment repo** (`assignment-N-<year>`, an `is_template` repo) - the source for Release assignment:
- **`main` branch** - the starter code only (no tests, no autograder). This is exactly what students receive (native template-generate copies `main` only).
- **`solution` branch** - the model solution (`solution/`), plus **`grading.yml`** and the **hidden tests** that the Grade assignment button runs faculty-side. **All of this MUST live on this branch, never on `main`** - that is what guarantees it is never copied into student repos on generate. Only the `solution/` folder reaches students, and only when you run Release assignment with **include_solution** ticked (a separate, later commit); the hidden tests and `grading.yml` never do.

---
Maintained by the [Hertie Data Science Lab](https://github.com/hertie-data-science-lab).
