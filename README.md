# TaskFlow — Material 3 inspired task manager

A responsive React/Vite task manager that runs in a browser and can be packaged as an Android app with Capacitor. Task data and preferences are stored locally on the current device in `localStorage`; there is no account or cloud sync.

## Features

- Create, read, update, and delete tasks
- Subtasks with individual completion toggles
- Low / medium / high priorities
- Deadline date and optional time, overdue indicator
- Search task title, notes, category, and subtask titles
- Filters by priority and category
- Today, Upcoming, Important, Completed, and Calendar views
- Light/dark themes
- Local-only persistence, JSON export/import, clear-data controls
- Responsive layout for desktop and mobile
- Material 3 inspired surfaces, color system, controls, and typography
- Android wrapper via Capacitor and local-notification integration dependency

## Requirements

- Node.js 20+ recommended
- npm
- For Android builds: Android Studio and an Android SDK
- Java version required by the installed Android Gradle plugin (use the version Android Studio recommends)

## Step 1 — Install and run on the web

```bash
npm install
npm run dev
```

Open the local URL printed by Vite (usually `http://localhost:5173`).

## Step 2 — Create a production web build

```bash
npm run build
npm run preview
```

The production bundle is generated in `dist/`.

## Step 3 — Package for Android

```bash
npm install
npx cap add android
npm run android:sync
npm run android:open
```

In Android Studio, wait for Gradle sync, select an emulator or connected Android device, then press Run. To rebuild after code changes, run `npm run android:sync` and run again from Android Studio.

If you need to re-create the Android wrapper after deleting the `android/` directory, run `npx cap add android` again.

## Reminders limitation

The current UI saves the reminder preference on each task, but does not yet schedule notification alarms. The included Capacitor Local Notifications package is the Android integration point for a follow-up implementation. Browser tabs cannot guarantee exact-time notifications while closed. For production reminders, request notification permission and schedule/cancel native notifications when a task is saved, edited, completed, or deleted.

## Local storage and backups

- Tasks: `taskflow.tasks.v1`
- Preferences: `taskflow.prefs.v1`

Clearing site/app data removes local tasks. Use Settings → Export backup to download a JSON backup and Import backup to restore it. Local storage is not encrypted and does not sync across devices.

## Notes

- Material 3 inspired, rather than an official Google Material Components implementation.
- No backend, sign-in, analytics, or cloud storage.
- Google Fonts are loaded remotely; add bundled fonts if fully offline presentation is required.
