# Route Handlers and APIs

## Explanation

A Route Handler returns an HTTP response. Create it in a file named `route.ts` and export a method such as `GET` or `POST`.

Use it when another application needs to request data from your server.

## Example

`src/app/api/hello/route.ts`

```ts
export async function GET() {
  return Response.json({ message: "Hello from Next.js" });
}
```

## How it works

Opening `/api/hello` returns:

```json
{ "message": "Hello from Next.js" }
```

A mobile app or another client can read this JSON with `fetch`. For a POST endpoint, read the request body, validate it, and return an appropriate status code. Protected endpoints also need identity and permission checks.
