# Novel Architect

Novel Architect is a desktop writing workspace for planning, drafting, revising, and reviewing long-form fiction. It keeps your books, chapters, versions, and context notes in a local SQLite database, while optional backend features provide account sync, Google login, story points, AI chapter drafting, AI revision, AI editorial reviews, and payments.

## Download

Download the release asset for your operating system:

- Windows: use the `.msi` or `.exe` installer when available.
- macOS: use the `.dmg` package when available.
- Linux: use the `.deb` package when available.
- Portable Java build: use the release uber jar when available. This requires Java 11 or newer.

Installer builds are produced from the Compose Desktop package configuration and use the app name `novel-architect`.

## What You Can Do

- Manage a library of novels from a dedicated book selection screen.
- Edit book metadata, descriptions, genres, and the per-book AI behavior prompt.
- Draft chapters in a focused editor with skeleton and story modes.
- Save explicit chapter drafts instead of writing every keystroke directly to disk.
- Keep chapter version history, including title, skeleton, story, and timestamp per version.
- Reorder chapters and export a complete manuscript to PDF.
- Maintain structured context notes for characters, locations, worldbuilding, and other reference material.
- Use built-in English spellcheck with red underlines and click-to-correct suggestions.
- Switch between light and dark themes.
- Request AI chapter drafts, revisions, and editorial reviews when connected to the backend.
- Buy and spend story points for backend AI features when account and payment features are available.

## First Launch

On startup, Novel Architect opens behind an authentication screen.

When the backend is reachable, you can log in, register, or continue with Google. Google login opens your browser and returns to the desktop app through the `novelwriter://auth/callback` protocol.

When the backend is unavailable, the app supports offline profiles and cached remote users. Local library data remains available, but backend-only features such as Google login, story points, payments, and AI generation stay disabled until the app can reconnect.

## Local Data

Your writing data is stored locally under:

```text
%USERPROFILE%\.novelwriter\novel_writer.db
```

On non-Windows systems this resolves under your home directory as:

```text
~/.novelwriter/novel_writer.db
```

Back up this database file if you want an external copy of your local library. Local password verifiers are stored as salted hashes; plaintext passwords are not stored.

## AI And Story Points

AI features use the hosted Novel Architect backend configured in the app. They require:

- a reachable backend connection
- a connected remote account
- available spendable story points

AI chapter generation and review run as background jobs. Completed AI output is saved locally before the app acknowledges the job to the backend, so generated work is not intentionally discarded if an acknowledgement retry is needed.

## Current Notes

- The app is built with JetBrains Compose Desktop and Kotlin.
- The rich chapter editor depends on Compose Desktop `1.1.0`; this release keeps that version pinned for editor scroll stability.
- Story-point pricing and package availability are controlled by the backend.
- The release build currently targets desktop use, not mobile or browser use.
