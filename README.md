RML iOS Optimizer (MDM-friendly)

Field-tested iPhone performance toolkit (iOS 17–18).
Includes: hard-reset sequences, verified optimization practices, and a tap-to-run Shortcuts recipe.






Quickstart

Create the Shortcut on iPhone (iOS 17/18)

Open Shortcuts → + → name it Optimize iPhone.

Add actions:

Set Airplane Mode → On

Wait → 2 seconds

Set Airplane Mode → Off

Show Alert → “You’ll be taken to Safari settings. Tap ‘Clear History and Website Data’, then return.”

Open URL →

iOS 17: prefs:root=SAFARI&path=CLEAR_HISTORY_AND_DATA

iOS 18: prefs:root=SAFARI&path=CLEAR_HISTORY_AND_DATA/CLEAR_HISTORY/ALL_HISTORY

Choose from Menu → “Reboot now?”

Yes: Show force-restart steps; (optional) Open URL App-Prefs:root=General&path=ShutDown

No: Show Notification “Optimization complete.”

Test

Confirm airplane toggles, Safari settings page opens, you can clear data, and reboot prompt appears.

Export & Add to Repo

In Shortcuts: long-press tile → Share → Share as File → save .shortcut.

Add it to /shortcuts/Optimize_iPhone_iOS17-18_v1.shortcut.

(Optional) MDM Distribution

Host the .shortcut via Release asset or iCloud share link.

Distribute as a managed link (web clip) with install instructions.

What’s Inside

docs/HARD_RESET.md — model-by-model force-restart sequences (iPhone 8 → 15 Pro Max).

docs/OPTIMIZATION.md — 2025 verified practices (storage, RAM, background, Spotlight, thermal, network).

shortcuts/ — place exported .shortcut here.

LICENSE — MIT.

Note: Shortcuts cannot clear Safari history automatically. The Shortcut opens the Settings page; user taps Clear History and Website Data.

Support / Issues

Use Discussions for Q&A.

Use Issues for bugs/requests (templates included).

License

MIT © Rocky Mountain Logic

Next files (same idea—no wrappers)

Create these via Add file → Create new file, each on its own branch/PR:

.github/CONTRIBUTING.md

# Contributing

## Workflow
- Fork → branch (`feature/<slug>` or `docs/<slug>`) → PR to `main`.
- Use conventional commits: `feat:`, `fix:`, `docs:`, `chore:`, `ci:`, etc.

## Docs & Style
- Markdown: wrap at ~100 chars, meaningful headings, no trailing spaces.
- Keep user steps verifiable on-device (no jailbreak-only flows).
- Link to Apple Settings paths explicitly.

## Shortcut Changes
- Provide exact Shortcuts actions in order.
- State iOS version compatibility (17/18) and any URL-scheme variations.

## Testing
- Verify: airplane toggle, Settings deep-link, user prompt flow, optional reboot guidance.
- If adding URLs, test on both iOS 17 and iOS 18.

## Security/Privacy
- No data collection. No auto-execution beyond user-approved toggles.


.github/PULL_REQUEST_TEMPLATE.md

## Summary
- What changed and why?

## iOS Compatibility
- [ ] iOS 17 tested
- [ ] iOS 18 tested

## Verification Steps
- [ ] Airplane on → wait → off works
- [ ] Safari settings deep-link opens
- [ ] Reboot prompt path works (or graceful fallback)
- [ ] Docs updated

## Screenshots / Notes


.github/ISSUE_TEMPLATE/bug_report.yml

name: Bug report
description: Something isn’t working
labels: [bug]
body:
  - type: textarea
    id: desc
    attributes:
      label: What happened?
      description: Describe the issue and expected behavior
  - type: input
    id: ios
    attributes:
      label: iOS version (17.x/18.x)
  - type: checkboxes
    id: steps
    attributes:
      label: Which steps fail?
      options:
        - label: Airplane toggle
        - label: Safari deep-link
        - label: Reboot prompt / ShutDown link
        - label: Docs mismatch
