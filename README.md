# Kalepa (kalepa)

Kalepa is a New York–headquartered insurtech founded in 2018 by Paul Monasterio and Daniel Hillman that builds Copilot, an AI underwriting workbench sold to commercial property and casualty carriers, MGAs, mutuals and brokers in its home market of the United States. Copilot covers the commercial underwriting workflow end to end — submission ingestion out of broker email and document packages (ACORD forms, statements of value, loss runs, supplemental applications), clearance and sanctions screening, triage by bindability and profitability, risk analysis, rating, quote and bind document generation, and portfolio management.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/kalepa/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/kalepa/refs/heads/main/apis.yml)

## Tags

- Insurance
- United States
- Insurtech
- Underwriting
- Property and Casualty
- Commercial Insurance
- Artificial Intelligence
- ACORD
- Partner Gated
- No Public API

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

**None.** Kalepa publishes no public, self-serve API and no developer documentation, so the `apis[]` collection in `apis.yml` is deliberately empty. Recording that absence accurately is the point of this profile.

A real API does exist operationally — `api.kalepa.com` is live and the company's own status page at [status.kalepa.com](https://status.kalepa.com/) monitors exactly two components, "Kalepa Web App" and "Kalepa API". But it is entirely customer-gated:

- `developer.kalepa.com`, `developers.kalepa.com`, `docs.kalepa.com`, `help.kalepa.com` and `support.kalepa.com` do not resolve.
- `kalepa.com/developers`, `/api`, `/developer`, `/partners`, `/integrations` and `/docs` all return **404**.
- Every specification path on the API host returns **404** — `/openapi.json`, `/openapi.yaml`, `/swagger.json`, `/v1/openapi.json`, `/api-docs`, `/docs`, `/redoc` — as do both `.well-known` OAuth/OIDC discovery documents.
- The Copilot application at `copilot.kalepa.com` **307**-redirects to `api.kalepa.com/auth/login`, a customer login wall.

Marketing does claim API integration — the carriers page states verbatim that *"Kalepa integrates via API with existing policy, underwriting, and document platforms"* — but nothing is published to substantiate it: no endpoint, base URL, auth scheme, scope or schema.

## ACORD Posture

**ACORD forms ingested as documents only; no ACORD XML, AL3, NGDS or IVANS integration documented.**

ACORD appears on the site exclusively as a document *type* Kalepa's AI extracts from — *"from standard ACORD forms to messy spreadsheets, handwritten notes, and complex loss runs"* — never as a data standard Kalepa implements or is certified against. No AL3, ACORD XML, NGDS, IVANS agency download, Applied Epic or Vertafore AMS360 reference exists anywhere on the public site. This inverts the classic US carrier posture: instead of moving ACORD as structured EDI over IVANS, Kalepa parses the ACORD form as unstructured input.

## Quote / Bind / Issue / FNOL

Copilot has Rating and Quote & Bind modules inside the product, but none of the four insurance verbs is exposed as a documented public API. Issue stays in the carrier's policy administration system and Kalepa ships no claims/FNOL product. Everything is underwriter- and partner-facing inside a licensed customer tenant.

## Links

- [Website](https://kalepa.com/)
- [Blog](https://kalepa.com/blog)
- [Newsroom](https://kalepa.com/newsroom)
- [Company](https://kalepa.com/company)
- [Status Page](https://status.kalepa.com/)
- [Vulnerability Disclosure](https://kalepa.com/security)
- [Privacy Policy](https://kalepa.com/privacy-policy)
- [Book a Demo](https://kalepa.com/book-a-demo)
- [GitHub Organization](https://github.com/Kalepa) — 29 public repos, all Terraform/infrastructure OSS, no API artifacts
- [LinkedIn](https://www.linkedin.com/company/kalepa)

## Artifacts

Enrichment round 2026-07-25 — everything below is searched or probed from Kalepa's own public surface. No spec-derived artifacts exist because there is no spec.

- [conformance/kalepa-conformance.yml](conformance/kalepa-conformance.yml) — **SOC 2 Type II** is published (on the For IT/AI Leaders page, not the security page), GDPR/UK GDPR/Swiss legal bases in the privacy policy, and per-standard conformance with evidence. No ISO 27001, PCI DSS, HIPAA or FedRAMP claim exists.
- [lifecycle/kalepa-lifecycle.yml](lifecycle/kalepa-lifecycle.yml) — Better Stack status page, both components at 99.993% uptime, a weekly Sunday 6-hour maintenance window ("usually does not last longer than 1 hour"), and eight dated incidents with root-cause notes. No versioning policy, no deprecation policy, no SLA.
- [packages/kalepa-packages.yml](packages/kalepa-packages.yml) — real first-party open source that is **not** an SDK: `safe-init` and `marshmallow-fastoneofschema` on PyPI, `kalepa-signxml` on GitHub, and 24 Terraform modules under the [Kalepa registry namespace](https://registry.terraform.io/namespaces/Kalepa) led by `shell-resource/external` at ~128k downloads.
- [security/kalepa-domain-security.yml](security/kalepa-domain-security.yml) — TLS 1.3 and HSTS on all five hosts (`api.kalepa.com` is includeSubDomains + preload), DNSSEC on three of four domains, no CAA anywhere, and no SPF/DMARC on `kalepainsurance.com` or `kalepa.io` even though both are in disclosure scope.
- [security/kalepa-vulnerability-disclosure.yml](security/kalepa-vulnerability-disclosure.yml) — the responsible-disclosure program structured: `security@kalepa.com`, four in-scope domains, six eligible and six ineligible bug classes, safe-harbour language, no paid bounty, no security.txt.
- [well-known/kalepa-well-known.yml](well-known/kalepa-well-known.yml) — every `/.well-known/` probe on both hosts, all **404**. Recorded as evidence of absence; no `WellKnown` pointer is wired because there is no discovery surface.
- [llms/kalepa-llms.txt](llms/kalepa-llms.txt) — generated (Kalepa publishes no `llms.txt`), telling an agent what exists, what does not, and not to attempt calls against `api.kalepa.com`.

## Review

See [review.yml](review.yml) for the full API Evangelist reviewer finding, including every probed URL with its HTTP status.
