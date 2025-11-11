README.md
# README.md 
cat > README.md <<'EOF'
# RML iOS Optimizer (MDM-friendly)
Field-tested iPhone performance toolkit (iOS 17–18).  
**Includes:** hard-reset sequences, verified optimization practices, and a tap-to-run Shortcuts recipe.

[![Docs](https://img.shields.io/badge/docs-OPTIMIZATION.md-informational)](docs/OPTIMIZATION.md)
[![Hard Reset Guide](https://img.shields.io/badge/guide-HARD__RESET.md-blue)](docs/HARD_RESET.md)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)

---

## Quickstart

1. **Create the Shortcut on iPhone (iOS 17/18)**
   - Open **Shortcuts** → **+** → name it **Optimize iPhone**.
   - Add actions:
     1) **Set Airplane Mode** → On  
     2) **Wait** → 2 seconds  
     3) **Set Airplane Mode** → Off  
     4) **Show Alert** → “You’ll be taken to Safari settings. Tap ‘Clear History and Website Data’, then return.”  
     5) **Open URL** →  
        - iOS 17: `prefs:root=SAFARI&path=CLEAR_HISTORY_AND_DATA`  
        - iOS 18: `prefs:root=SAFARI&path=CLEAR_HISTORY_AND_DATA/CLEAR_HISTORY/ALL_HISTORY`
     6) **Choose from Menu** → “Reboot now?”  
        - **Yes:** Show force-restart steps; (optional) **Open URL** `App-Prefs:root=General&path=ShutDown`  
        - **No:** Show Notification “Optimization complete.”

2. **Test**
   - Confirm airplane toggles, Safari settings page opens, you can clear data, and reboot prompt appears.

3. **Export & Add to Repo**
   - In Shortcuts: long-press tile → **Share** → **Share as File** → save `.shortcut`.
   - Add it to `/shortcuts/Optimize_iPhone_iOS17-18_v1.shortcut`.

4. **(Optional) MDM Distribution**
   - Host the `.shortcut` via Release asset or iCloud share link.
   - Distribute as a managed link (web clip) with install instructions.

---

## What’s Inside

- `docs/HARD_RESET.md` — model-by-model force-restart sequences (iPhone 8 → 15 Pro Max).
- `docs/OPTIMIZATION.md` — 2025 verified practices (storage, RAM, background, Spotlight, thermal, network).
- `shortcuts/` — place exported `.shortcut` here.
- `LICENSE` — MIT.

> Note: Shortcuts cannot clear Safari history automatically. The Shortcut opens the Settings page; user taps **Clear History and Website Data**.

## Support / Issues

- Use **Discussions** for Q&A.
- Use **Issues** for bugs/requests (templates included).

## License

MIT © Rocky Mountain Logic
EOF

# .github/CONTRIBUTING.md
mkdir -p .github
cat > .github/CONTRIBUTING.md <<'EOF'
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
EOF

# PR template
cat > .github/PULL_REQUEST_TEMPLATE.md <<'EOF'
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
EOF

# Issue templates
cat > .github/ISSUE_TEMPLATE/bug_report.yml <<'EOF'
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
EOF
