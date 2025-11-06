# Routine Buddy (prototype)

Routine Buddy is a single-page prototype that helps track recurring routines on a weekly cadence. The app runs entirely in the browser and persists data locally, so it can be installed like a lightweight PWA and used offline.

## Interface tour

### Weekly overview
- The top summary displays the count of routines that are **On track**, need you to **Keep Up**, or require you to **Catch Up** in a single status line: `🟩X On track 🟨X Keep Up 🟥X Catch Up`.
- Week navigation controls allow browsing past weeks while preventing travel beyond the current week. The active range is shown beside the navigation buttons.
- The home grid lists every category. Each card shows:
  - The category name.
  - A compact counter such as `3/5` indicating how many scheduled occurrences have been completed for the selected week (or "No activities" when empty).
  - A dedicated catch-up row beneath the title with emoji reminders for overdue **must-do** routines.
  - Seven day cells (Monday → Sunday) coloured according to aggregate progress for that day (green, yellow, red, future, or off).

### Category detail
- Selecting a category opens a focused view with a back arrow (`←`) to return home.
- The header simply repeats the category name—categories no longer carry emoji or accent colours.
- The summary strip from the home view is hidden here, keeping the focus on the category’s activities.
- Every activity appears as a card showing its emoji, title, priority stripe (red for must, yellow for should), and a row of seven day cells for the chosen week.
- Clicking a due day cell toggles completion. Cells representing future dates are disabled.
- When a category has no activities, a neutral hint clarifies that the list is empty.

### Configuration panel
- The gear button in the header opens the configuration view.
- From there you can add categories, add activities, and manage backups via import/export.
- The configuration dialog for categories only asks for a name; activities keep the richer set of fields described below.

## Activities
- An activity stores a **name**, an optional **emoji** (used as the activity icon), a **priority** (`must` or `should`), and a **recurrence** rule.
- Supported recurrence types:
  - **Daily** – due every day of the selected week.
  - **Specific day(s)** – due only on the checked weekdays.
  - **Weekly target** – choose how many times the activity should occur during the week.
- Activity dialogs allow editing, deleting, and picking emoji via a searchable helper.

## Data & persistence
- All information is saved to `localStorage` under the key `ROUTINE_BUDDY_V3`.
- The prototype does not rely on external services; everything runs locally in the browser.
- A service worker is registered on load so the app can be installed and revisited offline.
