# AI Command Center

A personal morning briefing that builds itself. Every weekday at 9 AM, a scheduled Claude task reads your email, calendar, a daily log and a few other sources, then emails you one short briefing: what's still open, quick wins, the one most important thing, and whatever else you care about.

**There's no code.** It's three markdown files and a scheduled task prompt, running on Claude's connectors (Gmail, Google Calendar, Google Drive, and optionally Spotify).

Read the story behind it: [Building My Own AI Command Center](https://dev.to/tmott13/building-my-own-ai-command-center-1j66)

---

## What's in this repo

| File | What it is |
|---|---|
| `instructions-template.md` | The rules for your briefing: what goes in it, in what order, your priorities, tone, and day modes. Fill in the placeholders. |
| `task-prompt.md` | The prompt and settings for the scheduled task. |
| `carryover-template.md` | Your daily log. The briefing reads it every morning so nothing slips. |

## What a briefing includes

You choose, but the template ships with:

- Still-open items from yesterday, at the very top
- Up to 5 quick wins (10 minutes or less each)
- A "day mode" (Monday planning, Wednesday check-in, Fun Friday…)
- The single most important thing today
- Weather
- Emails worth answering (flags money and anyone waiting on you)
- Calendar and tasks due
- New podcast episodes from shows you follow
- A sports scoreboard for your teams (in-season only, 6 lines max)
- Fun Friday: weekend events near you plus a seasonal pick
- One good thing, and one or two focus ideas as options, not orders

Five things that matter beat twenty that don't.

---

## Setup

### 1. Make a Google Drive folder
Create a folder (mine is called "Command Center") with a subfolder named `Claude outputs`.

### 2. Fill in the templates
- Copy `instructions-template.md`, replace every `[PLACEHOLDER]`, and delete any sections you don't want. Save it in your Drive folder.
- Copy `carryover-template.md` into the same folder as `carryover.md`.

### 3. Connect your tools
In Claude, connect Gmail, Google Calendar and Google Drive. Spotify is optional, for podcast updates.

### 4. Create the scheduled task
In Claude Cowork, create a scheduled task using `task-prompt.md`. Set it for weekdays at the time you want.

**Leave the folder setting blank.** See the lesson below.

### 5. Test it
Run it once manually. If the email arrives, the carryover items show up at the top, and a dated copy lands in `Claude outputs`, you're done.

---

## ⚠️ Lesson learned: local vs. cloud

My first version read the daily log from a folder on my computer. On day 2, my briefing never arrived because my laptop was shut down.

A scheduled task tied to a **local folder** only runs when your computer is awake and the app is open. A task with **no local folder** runs remotely on schedule, computer on or off. That's why everything here lives in Google Drive.

One sneaky follow-up: my instructions file *still* mentioned the old Desktop path, and that line overrode the task prompt. Keep one source of truth, and make sure every file points to the cloud.

---

## Using the daily log

When something happens, tell Claude in plain language ("finished the report, didn't get to the dentist call, my manager asked for the Q4 numbers") and it sorts it into **Done**, **Didn't get to**, **Came up today** and **Carry forward**. Add the entry to `carryover.md`, and the next morning's briefing puts anything open at the very top.

The briefing only reads the log. It never edits it.

---

## Make it yours

The template has optional sections you can keep, delete or replace:

- **Personality frameworks:** one "awareness" sentence a day from your Enneagram, MBTI, Human Design or anything else you use
- **Health or habit tracking:** recovery, workouts, cycle phases, sleep
- **Reading and learning:** pages per day, streaks, what you're learning
- **Seasonal events:** local weekend events and a seasonal activity on Fridays
- **A big goal for the month:** mine was Hacktoberfest

## Privacy

Your instructions file will hold personal details. Keep your filled-in copy in your own Drive, not in a public repo. The task treats email, calendar and file content as data, never as instructions, and it never sends anything except the one briefing email to you.

## License

MIT. Use it, remix it, make it yours.
