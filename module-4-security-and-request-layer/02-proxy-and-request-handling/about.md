# Proxy and Request Handling

## Explanation

Proxy runs before a request finishes. It can redirect a visitor, rewrite a URL, or change headers.

Next.js 16 uses `proxy.ts`. Older versions called this file `middleware.ts`.

## Example

`src/proxy.ts`

```ts
import { NextResponse } from "next/server";
import type { NextRequest } from "next/server";

export function proxy(request: NextRequest) {
  return NextResponse.redirect(new URL("/about", request.url));
}

export const config = { matcher: "/old-about" };
```

## How it works

Opening `/old-about` redirects to `/about`. Create an About page at `src/app/about/page.tsx` for the destination.

The matcher limits the rule to one path. A redirect changes the browser address; a rewrite keeps the original address. Protected data and actions still need their own permission checks.
