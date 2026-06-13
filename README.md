# Wikivoyage

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
