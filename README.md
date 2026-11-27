# Health

> BRAT distribution repo for the Health Obsidian plugin. Install with [BRAT](https://github.com/TfTHacker/obsidian42-brat): add `SilentNinja06/tracking.obs`. Source lives in the obsidian_workspace.obs monorepo (`plugins/health`).

A general medication and health manager for Obsidian. Works on desktop and
iPhone/iPad. Everything stays in your vault as Markdown files that sync.

- **Medications.** Scheduled (one or more doses a day, each with its own time
  and amount) or as needed. Purpose, notes, start date, a dose-change timeline,
  and archive instead of delete.
- **Log due.** One sheet with every dose still to take today. Doses due now
  start ticked; tap **Log all due**, or tick and untick. A twice-daily
  medication shows each dose separately, so you can log the morning one alone.
  You can also mark doses as skipped.
- **As needed / over the counter.** One tap to log. Shows how many today and
  how long since the last one. You can set your own limits (most per day, hours
  between doses); going past them asks you to confirm. Nothing is prefilled.
- **Streaks and adherence** for every scheduled medication.
- **Symptoms** with severity, and **vitals**: weight, blood pressure, heart rate,
  temperature, blood glucose.
- **Reminders** on desktop when a dose is due. Medication names are hidden unless
  you turn them on. On iPhone, use a Shortcuts automation that runs
  `obsidian://advanced-uri?commandid=health%3Alog-due` (with Advanced URI) or
  opens Obsidian at your chosen time.
- **Provider report.** A note covering a date range, ready to export as PDF.
- **Undo** on everything you log.

## Your data

- `Health/Medications.md` holds your medications and dose changes.
- `Health/Log/YYYY-MM.md` holds doses, symptoms and vitals, one file a month.

Both are append-only, with one record per line, so Obsidian Sync can merge
two devices. Editing a medication adds a newer version of it, and undo adds an
"undo" line. Nothing is ever rewritten or deleted. Doses also appear in your
daily note under **Medications**.

## Coming from Meridian Dash

Health shows **Import from Meridian Dash** until you import:

1. You see exactly what will be copied.
2. It snapshots Meridian's files into `Health/Snapshots/`.
3. It copies everything and checks the copy against the original.

Meridian Dash's files are never changed. **Settings → Undo the import** switches
back.
