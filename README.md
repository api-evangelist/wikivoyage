# Wikivoyage

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Wikivoyage is the free, collaboratively written travel guide operated by the non-profit Wikimedia Foundation. It provides comprehensive travel destination articles covering accommodation, sightseeing, local transport, dining, and practical travel advice for cities, regions, and countries worldwide. Content is published under the Creative Commons Attribution-ShareAlike 4.0 license and is available in over 20 languages.

## APIs

Wikivoyage exposes its content through two standard MediaWiki API surfaces:

### MediaWiki Action API
- **Base URL:** `https://en.wikivoyage.org/w/api.php`
- The primary interface for querying, parsing, and editing Wikivoyage articles. Operations are dispatched via the `action=` parameter (query, parse, edit, search, etc.). JSON is the recommended response format.
- [Documentation](https://www.mediawiki.org/wiki/API:Main_page) | [Sandbox](https://en.wikivoyage.org/wiki/Special:ApiSandbox)

### MediaWiki Core REST API
- **Base URL:** `https://en.wikivoyage.org/w/rest.php/v1`
- Modern REST interface providing page CRUD, full-text search, title autocomplete, file metadata, revision history, and wikitext <-> HTML transforms.
- [Documentation](https://www.mediawiki.org/wiki/API:REST_API/Reference) | [Sandbox](https://en.wikivoyage.org/wiki/Special:RestSandbox)

## Key Endpoints

| Endpoint | Description |
|----------|-------------|
| `GET /page/{title}` | Retrieve travel article source (wikitext) |
| `GET /page/{title}/with_html` | Retrieve travel article with rendered HTML |
| `GET /page/{title}/bare` | Retrieve article metadata without content |
| `GET /search/page?q={query}` | Full-text search across travel articles |
| `GET /search/title?q={query}` | Autocomplete destination name search |
| `GET /page/{title}/history` | Retrieve article revision history |
| `GET /page/{title}/links/language` | Get equivalent articles in other languages |
| `POST /transform/wikitext/to/html/{title}` | Convert wikitext to HTML |

## Authentication

- **Read operations:** No authentication required
- **Write operations:** OAuth 2.0 bearer token required (register at [meta.wikimedia.org](https://meta.wikimedia.org/wiki/Special:OAuthConsumerRegistration/propose))

## Rate Limits and Etiquette

- A **meaningful User-Agent header** is mandatory — format: `ClientName/Version (contact@example.com) Library/Version`
- Make requests **serially**, not in parallel, for batch workloads
- Use the **`maxlag=5`** parameter in automated/bot requests to respect server load
- Implement **exponential backoff** on `ratelimited` (429) responses
- For bulk corpus access, use [Wikivoyage database dumps](https://dumps.wikimedia.org/enwikivoyage/) rather than API crawling

## Pricing

All Wikivoyage APIs are **free of charge** with no paid tiers or metered billing. The Wikimedia Foundation sustains this infrastructure through donations.

## Resources

- [Wikivoyage](https://www.wikivoyage.org)
- [Wikimedia API Usage Guidelines](https://foundation.wikimedia.org/wiki/Policy:Wikimedia_Foundation_API_Usage_Guidelines)
- [Wikimedia Status](https://www.wikimediastatus.net/)
- [Database Dumps](https://dumps.wikimedia.org/enwikivoyage/)
- [Donate to Wikimedia](https://donate.wikimedia.org/)
