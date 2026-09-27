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
