# Authentication and Authorization

## Explanation

- Authentication answers: who is the user?
- Authorization answers: what can the user do?

Use an authentication library to obtain a verified session. Being signed in does not automatically allow editing every record.

## Example

This example uses the Auth.js v5-style API. It requires a compatible `next-auth` package, a configured GitHub OAuth application, and the server variables `AUTH_SECRET`, `AUTH_GITHUB_ID`, and `AUTH_GITHUB_SECRET`.

`src/auth.ts`

```ts
import NextAuth from "next-auth";
import GitHub from "next-auth/providers/github";

export const { auth, handlers } = NextAuth({ providers: [GitHub] });
```

`src/app/api/auth/[...nextauth]/route.ts`

```ts
import { handlers } from "@/auth";

export const { GET, POST } = handlers;
```

`src/app/account/page.tsx`

```tsx
import { auth } from "@/auth";
import { redirect } from "next/navigation";

export default async function AccountPage() {
  const session = await auth();

  if (!session?.user) redirect("/api/auth/signin");

  return <h1>Welcome, {session.user.name ?? "user"}</h1>;
}
```

## How it works

The server checks the session. A visitor without one is sent to sign-in; a signed-in user sees the account page. The provider and callback URL must be configured before login can work.

For editing protected records, also check ownership or roles using trusted server data. Never trust a browser parameter such as `role=admin`.
