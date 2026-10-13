# Desktop 4.1.0 release readiness

Prepared 2026-10-13 from published desktop 4.0.0 source `81aa3a70d177ef4759bd54d5aa86f67a7827fa66`. The owner authorized a full stable desktop release, followed by a separate Android 4.1.0 APK compiled locally. This report records exercised boundaries; it does not turn unrun manual acceptance into passes.

## Scope and compatibility

Unencrypted video media uploads use the original filename as a literal caption by default. The saved per-device option can disable captions; queued jobs snapshot that choice and restore it through native process/storage restart. UTF-16-limited truncation keeps Unicode scalars intact. Protected uploads retain encrypted metadata and bypass the public-caption path. File-mode documents are unchanged. The new option is deliberately omitted from uploaded encrypted preference snapshots so older clients can continue restoring them; new readers accept development snapshots containing the boolean.

Desktop settings and vault controls share grouped rows, consistent switches, touch targets and readable light/dark accents. Protected upload selection supports inline vault setup/unlock and passphrase-only protection. A failed lazy dialog offers Cancel or an explicit application reload that cancels the pending selection and requires selecting files again. Existing queued work is not cancelled.

The desktop candidate retains the 4.0.0 account-isolation, recovery transactions/drills, durable transfers, protected-media, search, HEIC, security and release protections. TDENC2 remains frozen-format beta; independent cryptographic review remains pending. The $5.00 USD one-time lifetime ad-free license, existing activation, recovery and three-device allowance are unchanged. No production Worker deployment, transaction or D1 mutation occurred.

## Local verification

| Gate | Result and exercised boundary |
| --- | --- |
| Browser E2E | 133 passed, no skips, final source; real application UI with controlled native/Telegram/payment boundaries. New caption and protected-upload loading/cancellation journeys included. Reload fixture persists its queue and command history across documents. |
| Native E2E | 201 passed, no skips; application child-process, HTTP and persistent-storage journeys. Caption true/false survives interrupted upload restart. This regression failed on the pre-fix candidate. |
| Supporter Worker E2E | 27 passed, no skips, patched toolchain; HTTP requests and local D1 with controlled PayPal fixtures. |
| Worker-to-application entitlement | 1 passed; a locally issued entitlement is accepted only for its own device and validity window. No live payment. |
| Release assurance CLI | 14 passed, no skips; actual CLI/child-process journeys. |
| Packaged-startup harness | 4 passed, 2 Windows-only skipped on macOS. This validates the smoke harness, not manual startup on every target OS. |
| Desktop package | 1 passed; real local macOS Tauri bundle excludes native test executables. Unsigned debug packaging is not signed installed-upgrade acceptance. |
| Static/native | TypeScript production build, Rust formatting and clippy with warnings denied passed. |
| Localization/configuration | Catalog validation, original literal ceilings, E2E-only policy, WebView/capability security and workflow pins passed. |
| Dependencies | Rust advisory/license/ban/source policy passed with existing permitted duplicate warnings. Supporter npm advisories and licenses passed. App npm assurance remains disabled by the pre-existing owner policy; no gate was removed here. |
| Read-only production preflight | Matching supporter key; exact 5.00 USD and three-device contract; synchronized versions, release notes and unexpired advisory baselines. No write or payment. |

A new advisory found during preflight, [GHSA-wq5f-xc86-pv6w](https://github.com/lovell/sharp/security/advisories/GHSA-wq5f-xc86-pv6w), is fixed by the narrow Miniflare development-tool override `sharp` 0.35.4 → 0.35.5 and libvips 1.3.4. Version-specific optional-tool license exceptions retain the same declared licenses, development-only rationale, owner and expiry. The advisory was not allowlisted. Production supporter code and entitlements are unchanged.

## Locale performance review

Four new caption/reload labels are translated in all 24 catalogs. Exact encoded locale accounting grows by 9,002 bytes (0.461%), from 1,952,434 to 1,961,436; largest catalog grows 611 bytes, from 138,790 to 139,401. Dictionary plus selected English grows 368 bytes; dictionary plus the largest selected catalog grows 744 bytes. Loading remains one dictionary and one selected catalog, with no additional requests. An independent architect review approved only these exact locale ceilings under the existing performance-review policy. JavaScript, CSS, route, feature and literal ceilings stay unchanged; other translations were not shortened.

Final production measurements: initial JavaScript 504,619 / 513,000; largest chunk 523,075 / 550,000; total JavaScript 2,451,467 / 3,300,000; CSS 133,822 / 140,000; desktop route 301,769 / 302,000; Settings 120,569 / 159,000; media 249,329 / 250,000; PDF 503,734 / 510,000. All locale bytes, dictionary included, remain counted.

## Publication and remaining acceptance

The isolated desktop export excludes Android project/source/test changes and temporary test configuration/results. The publication guard reports 27 unchanged historical Android-related paths pending owner review; none are modified by this release. Their presence is not treated as approval. Audit every outgoing commit and shared hunk before push.

The tag workflow must independently pass dependency assurance, release verification, all platform builds and packaged startup, signing as configured, checksums/SBOMs/provenance generation and draft publication gates. This local report does not predeclare those future jobs passed. Downloaded artifact checksum and GitHub attestation verification follow publication.

Live Telegram, physical Android/TV devices, native-speaker review, PayPal sandbox, and manual installed desktop upgrade/OS acceptance are unrun for this candidate. The historical 4.0.0 owner decisions in [RELEASE_ACCEPTANCE.md](RELEASE_ACCEPTANCE.md) are not rewritten as 4.1.0 test results. Controlled fixtures prove only their documented boundaries. Android signed-build and upgrade evidence is recorded separately after local compilation; no Android source is published.
