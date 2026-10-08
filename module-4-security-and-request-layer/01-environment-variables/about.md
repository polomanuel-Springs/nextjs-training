# Environment Variables

## Explanation

Environment variables store configuration outside the code. Place `.env.local` at the Next.js application root.

- `NEXT_PUBLIC_` values can reach the browser.
- Values without that prefix should stay in server code.

## Example

`.env.local`

```dotenv
NEXT_PUBLIC_APP_NAME="My website"
SERVICE_TOKEN="fictional-example-value"
```

`src/app/page.tsx`

```tsx
export default function HomePage() {
  return <h1>{process.env.NEXT_PUBLIC_APP_NAME ?? "Website"}</h1>;
}
```

## How it works

The page displays “My website”. The service token is available to server code, but this page never displays or returns it.

Restart development after changing the file. Public values usually require a rebuild in production. Never commit real secrets or pass private variables to the browser through props or API responses.
