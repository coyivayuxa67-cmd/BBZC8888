# Validation

## DreamSkin official validator

Source:

`themes/starship-command-deck-night`

Commands:

```powershell
node tools/dreamskin-runtime/theme-package-validator.mjs --source dreamskin-submission/starship-command-deck-night --stage dreamskin-submission/stage-windows --platform windows --client-version 1.0.0

node tools/dreamskin-runtime/theme-package-validator.mjs --source dreamskin-submission/starship-command-deck-night --stage dreamskin-submission/stage-macos --platform macos --client-version 1.0.0
```

Results:

```json
{"format":"official","image":"background.webp","safeCssStatus":"validated","signatureIgnored":false}
```

## Package summary

- Theme ID: `starship-command-deck-night`
- Version: `5.0.0`
- Platforms: Windows, macOS
- Background: `background.webp`
- Background size: `560706` bytes
- Required files only
- No JavaScript
- No remote URL
- No infinite animation
