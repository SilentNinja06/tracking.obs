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
  you turn them on. On iPhone and iPad, use the Shortcuts recipes below.
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

## iPhone and iPad: Shortcuts recipes

Obsidian plugins can't send notifications on iOS, but the Shortcuts app can
open Health at the right screen. Every recipe uses one of these links:

| Link | Opens |
|---|---|
| `obsidian://health?action=log-due` | the Log due sheet |
| `obsidian://health?action=as-needed` | as-needed / over-the-counter logging |
| `obsidian://health?action=symptoms` | Log symptoms |
| `obsidian://health?action=vitals` | Log vitals |
| `obsidian://health?action=report` | Make a health report |
| `obsidian://health` | the Health view |

If you have more than one vault, add `&vault=Your%20Vault%20Name` to the link.

### 1. A reminder for each dose time

Do this once for each time you take medication (e.g. 8:00 and 20:00).

1. Open **Shortcuts → Automation → + → Time of Day**.
2. Set the time (e.g. 8:00 AM), **Repeat: Daily**, and choose **Run Immediately**.
   Turn **Notify When Run** on if you want a banner.
3. Add the action **Open URLs** with `obsidian://health?action=log-due`.
4. Tap **Done**.

At that time Obsidian opens on Log due, with the doses that are due already
ticked. Tap **Log all due**, or tick and untick.

Want a gentle nudge instead of Obsidian opening by itself? Make a shortcut
called **Log meds** with just the **Open URLs** action. Then in the automation
use **Show Notification** ("Time for your medications"). Run **Log meds** from
the notification, a widget, or the Action Button.

### 2. One tap for over-the-counter meds

1. **Shortcuts → + → Add Action → Open URLs** →
   `obsidian://health?action=as-needed`.
2. Name it **Took something** and add it to your Home Screen, a Lock Screen
   widget, or the Action Button.

Health shows how many you've had today and how long since the last one, and
warns you if you're past your own limits.

### 3. Symptoms and vitals in a hurry

The same idea with `obsidian://health?action=symptoms` or `…?action=vitals`.
A Lock Screen widget makes logging a headache a two-tap job.
