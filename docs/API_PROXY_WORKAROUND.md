# Same-origin API proxy workaround (Vercel)

## Why this fixes the CORS errors

Your browser is currently making cross-origin requests from:

- `https://www.yohannescodes.com`

To:

- `https://garage-os-backend-alpha.vercel.app/api/...`

Because the backend response does not include an `Access-Control-Allow-Origin` header for `https://www.yohannescodes.com`, the browser blocks those responses.

With the Vercel rewrite in `vercel.json`, the browser can request:

- `/api/...`

from the same origin (`https://www.yohannescodes.com`). Vercel then proxies that request server-side to:

- `https://garage-os-backend-alpha.vercel.app/api/...`

No browser CORS enforcement is triggered for same-origin requests.

## Frontend change required

To use this workaround, your frontend should call relative API paths, for example:

- ✅ `fetch('/api/website')`
- ❌ `fetch('https://garage-os-backend-alpha.vercel.app/api/website')`

If your frontend is configured with an API base URL variable, set it to `/api` in production.

## Important limitation

This workaround only solves **CORS blocking**.

If the backend endpoint itself returns `500` or non-JSON strings like `Server error`, those errors will still happen through the proxy and must be fixed in the backend service.
