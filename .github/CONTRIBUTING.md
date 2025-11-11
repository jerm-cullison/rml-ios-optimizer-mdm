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
