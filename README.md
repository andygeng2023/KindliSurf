# KindliSurf

**The web, made readable.** A Kindle-first browser experiment focused on less frustrating navigation and better access to the web on e-ink devices.

> Status: Phase 1 — static browser shell prototype. Not a replacement browser engine and not yet a website compatibility proxy.

## What exists now

- A lightweight, high-contrast start page designed for small e-ink screens.
- Address bar that accepts website URLs or search queries.
- Back, forward, reload and home controls using the browser's native navigation.
- Quick links to text-friendly destinations.
- A local browser capability report (user agent, screen size, history, storage and Fetch API).
- A local reader-layout preview with sample content.
- No account, analytics, build step or third-party JavaScript dependency.

## Important limitations

KindliSurf currently runs as a website inside the device's existing browser. **It cannot replace or upgrade that browser's rendering engine.** When you navigate to an external website, the browser leaves the KindliSurf start page; use the browser's Back button to return.

The reader preview is sample content only. It does not yet fetch or simplify arbitrary websites. Direct navigation to modern sites remains limited by each Kindle's browser engine, firmware, JavaScript support, TLS support and the site's own behavior.

## Deploy with GitHub Pages

This repository includes a GitHub Actions workflow that publishes the static site.

1. Open **Settings → Pages** in the repository.
2. Under **Build and deployment**, choose **GitHub Actions** as the source.
3. Open the **Actions** tab and wait for the `Deploy KindliSurf to GitHub Pages` workflow to complete.
4. The site should be available at:

   https://andygeng2023.github.io/KindliSurf/

If the first deployment fails because Pages is not enabled for the repository, complete step 2 and rerun the workflow.

## Test plan

Please test on physical Kindles before claiming compatibility. Record the Kindle model and firmware, whether the start page and controls work, whether HTTPS navigation works, whether Back returns to KindliSurf, and which common sites render acceptably.

See [docs/device-matrix.md](docs/device-matrix.md) for the compatibility template.

## Roadmap

- [x] Phase 1: static start page and browser shell.
- [ ] Phase 1.1: test on physical Kindle models and fix compatibility issues.
- [ ] Phase 2: server-assisted reader mode for permitted public pages.
- [ ] Phase 3: caching and explicit compatibility fallbacks.
- [ ] Phase 4: broader device matrix and community testing.

## Security direction for future server features

A future page-fetching service must defend against SSRF, validate DNS and redirect destinations, limit response size and time, sanitize fetched HTML, avoid forwarding credentials, and avoid executing arbitrary remote scripts. The static Phase 1 site does not include a fetch proxy.

## Contributing

Bug reports should include the Kindle model, firmware version, test URL (if public), expected behavior and what actually happened. Avoid posting private URLs, cookies or account details.
