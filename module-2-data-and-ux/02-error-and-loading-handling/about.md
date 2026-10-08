# Error and Loading Handling

## Explanation

Use different interfaces for different situations:

- `loading.tsx`: the page is waiting for data.
- `error.tsx`: something failed.
- `not-found.tsx`: the requested page or record does not exist.

## Example

`src/app/users/loading.tsx`

```tsx
export default function Loading() {
  return <p>Loading users...</p>;
}
```

`src/app/users/error.tsx`

```tsx
"use client";

export default function ErrorPage({ reset }: { reset: () => void }) {
  return (
    <>
      <p>Could not load users.</p>
      <button onClick={reset}>Try again</button>
    </>
  );
}
```

## How it works

These files support the users page from the previous topic. During navigation, the loading message can appear while data is pending. If the page throws an error, the retry interface appears. Retrying works only if the cause of the failure is resolved.

For a missing record, call `notFound()` from `next/navigation` and provide a `not-found.tsx` page.
