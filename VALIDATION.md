# Validation

## DreamSkin official validator

Source:

`themes/starship-command-deck`

Commands:

```powershell
node tools/dreamskin-runtime/theme-package-validator.mjs --source dreamskin-submission/starship-command-deck --stage dreamskin-submission/stage-deck-win --platform windows --client-version 1.0.0

node tools/dreamskin-runtime/theme-package-validator.mjs --source dreamskin-submission/starship-command-deck --stage dreamskin-submission/stage-deck-mac --platform macos --client-version 1.0.0
```

Results:

```json
{"format":"official","image":"background.webp","safeCssStatus":"validated","signatureIgnored":false}
```

## Package summary

- Theme ID: `starship-command-deck`
- Version: `5.0.0`
- Platforms: Windows, macOS
- Background: `background.webp`
- Background size: `560706` bytes
- Required files only
- No JavaScript
- No remote URL
- No infinite animation

## Studio readiness check

Importing `releases/starship-command-deck-5.0.0.zip` into DreamSkin Studio
restores every field and passes all six readiness checks:

- Background image: WEBP 7680 x 4320, 547.6 KiB
- Theme details: 星舰指挥台：夜航离港 · starship-command-deck
- theme.json source: applied and valid
- Text contrast: minimum 14.76:1 (WCAG AA)
- Safe CSS: passes dreamskin-safe-css/1
- Package metadata: passes field checks

## Codex++ userscript 5.0.1 isolated verification

Done 2026-09-27. No change was made to the live Codex++ installation
(`%APPDATA%\Codex++\user_scripts\星舰指挥台主题.js`, still `4.8.7-smaller-meteor`).

### 1. Embedded assets decode byte-identically

Parsed the `EMBEDDED_ASSETS` object out of
`codexpp/starship-command-deck.user.js` and compared every decoded payload
with the matching file in `assets/`:

| Asset | Decoded bytes | Magic | SHA256 vs original |
| --- | --- | --- | --- |
| `bg-1-earth-night-8k.webp` | 560706 | RIFF | match |
| `bg-2-earth-day-8k.webp` | 2442482 | RIFF | match |
| `bg-3-iss-8k.webp` | 1707452 | RIFF | match |
| `bg-4-earth-ring-8k.webp` | 2882510 | RIFF | match |
| `bg-5-mars-8k.webp` | 5650028 | RIFF | match |
| `bg-6-milky-way-8k.webp` | 383786 | RIFF | match |

### 2. Data URIs load in a real browser

Served an 18.17 MB fixture over a local HTTP server (Playwright blocks
`file://`) and opened it in Chromium. All six images reported
`complete=true` with `naturalWidth x naturalHeight` of `7680x4320`,
including the largest 5.65 MB payload.

### 3. Script smoke test

Loaded the userscript into a plain page containing only a `#root` div:

- `window.__codexCommandDeckTheme` exposed as an object
- style / tools / background containers created
- body classes: `cd-theme-active cd-theme-command-deck cd-holographic
  cd-frame-v41 cd-bg-earth-night cd-v4-phase-earth-night cd-image-bg`
- datasets: `cdPorthole=panoramic`, `cdTheme=command-deck`,
  `cdGeometry=rect`, `cdTraffic=on`
- background element resolved to a `data:image/webp;base64,...` value
  747638 characters long

This confirms the defaults (holographic / parallax / traffic all on) and the
embedded asset path work end to end.

### Scope of this verification

It does not replace a full integration test against a real Codex window.
Still unverified: rendering inside Codex's own DOM, the six porthole layouts,
the meteor animation, and both ship events under real conditions.
