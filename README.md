# TXT Redirect Resolver

A lightweight client-side redirector that resolves DNS TXT records and instantly redirects visitors based on their contents. Designed for Handshake/TLD redirect.

## How it works

1. Extracts the root domain from common `.redirect` gateway patterns  
2. Fetches TXT records via DNS-over-HTTPS  
3. Redirects in this priority order:
   - `url:` / `url=` / `link:` / `link=`
   - Plain `http://` or `https://`
   - `ext:` (recursively resolves another domain’s TXT records)

Redirects happen as fast as possible using `location.replace()`.

## Supported TXT formats

```txt
url:example.com
url=example.com
link=https://example.com
link:https://example.com
https://example.com
ext:anotherdomain
