# vu1nz Security Bug Report: Login Clickjacking

- Target: https://vu1nz.com
- Affected route: https://vu1nz.com/login
- Finding: login page is frameable by arbitrary origins because frame protection headers are missing
- Test date: 2026-07-07
- Testing mode: non-invasive HTTP header checks and local iframe rendering only

## Summary

`https://vu1nz.com/login` can be embedded in an iframe from a separate origin. The response does not send `Content-Security-Policy` with `frame-ancestors`, and it also does not send `X-Frame-Options`. A local proof of concept successfully rendered the real sign-in page inside an iframe.

## Impact

An attacker-controlled page can display the vu1nz login page inside a deceptive interface and induce users to click authentication controls such as `Continue with GitHub`. This is a practical clickjacking risk for authentication and protected redirect flows. The risk is stronger because `https://vu1nz.com/admin` redirects users to `/login?next=/admin`.

## Evidence

Response headers for `https://vu1nz.com/login` included:

```http
HTTP/2 200
cache-control: private, no-cache, no-store, max-age=0, must-revalidate
content-type: text/html; charset=utf-8
server: railway-hikari
x-powered-by: Next.js
```

Headers not present in the captured response:

- `Content-Security-Policy`
- `X-Frame-Options`
- `Strict-Transport-Security`
- `Referrer-Policy`
- `X-Content-Type-Options`
- `Permissions-Policy`

Iframe proof of concept:

```html
<iframe src="https://vu1nz.com/login" width="420" height="720"></iframe>
```

Screenshot evidence: [vu1nz-clickjacking-poc.png](./vu1nz-clickjacking-poc.png)

## Reproduction

1. Save the following local HTML file:

```html
<!doctype html>
<html>
  <body>
    <iframe src="https://vu1nz.com/login" width="420" height="720"></iframe>
  </body>
</html>
```

2. Serve it from a local origin:

```bash
python3 -m http.server 8765 --directory /tmp
```

3. Open the local page in a browser.
4. Observe that the real vu1nz login page renders inside the iframe.

## Recommended Fix

Add a frame restriction header on all authenticated and sensitive routes:

```http
Content-Security-Policy: frame-ancestors 'none';
```

If same-site embedding is required, use:

```http
Content-Security-Policy: frame-ancestors 'self';
```

Also consider adding `X-Frame-Options: DENY` or `SAMEORIGIN` as legacy browser defense, plus standard hardening headers such as HSTS, `Referrer-Policy`, `X-Content-Type-Options`, and `Permissions-Policy`.

## Scope Note

No credential submission, brute force, account access, payment action, destructive request, or automated exploitation was performed.
