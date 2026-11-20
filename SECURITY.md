# Security Policy

## Supported Versions

Security fixes are applied on `main` and released for the current `1.0.x` Manifest V3 extension.

| Version | Supported |
| ------- | --------- |
| `1.0.x` (`main`) | Yes |
| `< 1.0.0` | No |

## Reporting a Vulnerability

Please do **not** report undisclosed security vulnerabilities through public GitHub issues, pull requests, or discussions.

Use GitHub's [private vulnerability reporting](https://github.com/tinywind/edge-block-devtools-shortcut/security/advisories/new) for this repository to submit a report confidentially. If you cannot use GitHub Security Advisories, contact the maintainer directly at `tinywind0@gmail.com`.

When reporting an issue, please include as much of the following as possible:

- Extension version (`manifest.json`) and Microsoft Edge version / OS platform
- Affected file (`manifest.json` or `content.js`)
- A minimal reproduction or proof of concept (with affected page or web terminal context)
- Description of the potential impact and any suggested mitigation

## Response Process

- We aim to acknowledge receipt of a vulnerability report within 7 days.
- Validated issues are tracked privately through a GitHub Security Advisory while a fix is prepared and verified.
- Once a patch is available on `main`, we will publish the advisory and credit reporters who wish to be acknowledged.

## Scope and Security Model Notes

`edge-block-devtools-shortcut` is an unpacked Manifest V3 Microsoft Edge extension with no background service worker, options page, network requests, or external dependencies. Its content script (`content.js`) intercepts only the `Ctrl+Shift+C` keyboard shortcut at `document_start`.

### In scope

- Unexpected privilege escalation, overly broad permissions in `manifest.json`, or unintended DOM/clipboard side effects in `content.js`
- Bypass or interference that exposes sensitive page data or breaks expected `document.execCommand('copy')` behavior in a security-relevant way

### Out of scope

- Browser-level keyboard shortcut behavior controlled solely by Microsoft Edge or another installed extension
- Sites or web terminals that intentionally override or consume keyboard events before or after capture phase
