# Data Fetching

## Explanation

An `async` Server Component can request data before displaying it. `await` waits for the request, and `response.json()` reads the JSON result.

Always check `response.ok` to detect failed HTTP responses. Independent requests can run together with `Promise.all`.

## Example

`src/app/users/page.tsx`

```tsx
type User = { id: number; name: string };

export default async function UsersPage() {
  const response = await fetch(
    "https://jsonplaceholder.typicode.com/users",
    { cache: "no-store" },
  );

  if (!response.ok) throw new Error("Could not load users");

  const users: User[] = await response.json();

  return <ul>{users.map((user) => <li key={user.id}>{user.name}</li>)}</ul>;
}
```

## How it works

The server requests users and displays their names. This example requires internet access. In a real integration, also validate the service response and provide loading and error feedback.
