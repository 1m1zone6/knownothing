# AFTER HOURS prototype

AFTER HOURS is a fictional alternate-universe romance story built on the existing FoundPhone Studio runtime. It does not represent real people or real events.

## Current prototype

The first playable content sample uses the Osaki Shotaro route as a content prototype. The six-character selection screen is intentionally deferred so the existing phone runtime can be tested without replacing the project entry point.

The story data is in `stories/after-hours/story.json`. It keeps the existing v1 story format and uses existing registered apps. It does not replace `stories/template/story.json` or change the default test template.

## Run locally

Use Node.js 22 and install the repository dependencies first:

```bash
npm ci
STORY_FILE=stories/after-hours/story.json npm run story:validate
STORY_FILE=stories/after-hours/story.json npm run story:test
STORY_FILE=stories/after-hours/story.json npm run story:preview
```

The preview command starts the existing Vite development server. Open the local address printed by Vite. If the shell does not support inline environment variables, set `STORY_FILE` in the shell first, then run the commands.

For a production build of this story:

```bash
STORY_FILE=stories/after-hours/story.json npm run build
```

The build command writes generated runtime files under the repository's normal build paths. Do not commit generated files unless the project's normal workflow requires them.

## Design and implementation boundaries

- Reuse the existing phone shell, lock screen, app registry, story compiler, event engine, and app skins.
- Keep stable English IDs in story data.
- Keep four-digit passcodes as strings so leading zeroes are preserved.
- Use only supported structured JSON fields and safe media references. Do not embed executable HTML or JavaScript in story data.
- Keep user-provided portraits, wallpapers, videos, and music assets separate until they are supplied and their usage rights are clear.
- The current story data is an early content prototype, not a finished six-route game. Revision 2 adds a first route hook: the morning practice schedule runs late, Shotaro apologizes and offers to reschedule the photo-studio date, and related clues appear in Messages, Calendar, Mail, X, Threads, and a password-protected private note. The hook is currently authored as preloaded phone content; it is not yet a stateful event that changes in response to app visits or player choices.
- The six-character selection page, per-character route switching, and dedicated Instagram video-call interaction are deferred custom UI tasks.
- Existing browser persistence is part of the host project. Do not remove it as part of story-only work; verify route isolation before adding multi-character switching.

## License

The host project is MIT-licensed. Preserve its license and copyright notices in any redistributed copy or derivative work.
