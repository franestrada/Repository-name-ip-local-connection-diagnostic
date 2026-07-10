# ip-local.com Connection Diagnostic

A small, self-hostable browser tool that creates a clean connection report for help desks, technicians and IT support teams.

**Live demo:** https://ip-local.com/en/connection-diagnostic/

## Why this exists

When a user reports a router, VPN, firewall, browser or access problem, support often needs the same basic context before troubleshooting can begin. This tool collects that context in one page and lets the user copy or download it as plain text.

## Included in the diagnostic

- Public IP address
- Browser
- Operating system or platform
- Language
- Time zone
- Screen size
- Viewport size
- User agent
- Page checked
- Local date and time
- A note explaining why the local/private IP is not detected automatically

## What is not collected

- Name
- Email address
- Passwords
- Account details
- Form submissions
- Precise GPS location

The open-source build contains **no advertising code, cookies or analytics**.

## Public IP lookup

The browser tries two methods:

1. `/cdn-cgi/trace` on the current host when Cloudflare provides it.
2. `https://api.ipify.org` as a fallback.

This means the browser may contact Cloudflare or ipify to obtain the public IP. Review or replace these providers before deploying in an environment with stricter privacy requirements.

## Quick start

No build process or dependencies are required.

```bash
git clone https://github.com/ip-local/ip-local-connection-diagnostic.git
cd ip-local-connection-diagnostic
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

Opening `index.html` directly also works, although the public IP lookup may depend on the browser's cross-origin policy.

## Self-hosting

Upload `index.html` to any static host:

- GitHub Pages
- Cloudflare Pages
- Netlify
- Apache
- Nginx
- An internal help-desk portal

For a private deployment, replace the public IP provider in `fetchIp()` with an endpoint you control.

## Customization

Useful places to edit:

- `buildSupportDiagnostic()` to change the copied report
- `fetchIp()` to change the public IP provider
- the support-team panel to add internal instructions
- the links to local-IP guides
- the theme variables at the top of the embedded CSS

## Privacy model

The report is assembled in the browser. Copying or downloading the report does not submit it to this project. The user decides where to paste or send it.

The public IP and user agent are technical identifiers. Users should share the report only with support teams they trust.

## Limitations

A normal browser cannot reliably expose the device's local/private IP address. Modern browsers intentionally restrict this information. The tool therefore links to manual guides instead of claiming to detect it.

## Official translations

- English: https://ip-local.com/en/connection-diagnostic/
- Spanish: https://ip-local.com/es/diagnostico-conexion/
- French: https://ip-local.com/fr/diagnostic-connexion/
- German: https://ip-local.com/de/verbindungsdiagnose/

## License

MIT. See [LICENSE](LICENSE).

## Project

Created by [ip-local.com](https://ip-local.com/), a small independent project focused on practical local-network and router help.
