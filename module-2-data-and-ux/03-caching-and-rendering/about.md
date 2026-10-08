# Caching and Rendering

## Explanation

Caching reuses data instead of requesting it every time. Revalidation refreshes cached data when needed.

- `cache: "no-store"` requests fresh data.
- `next: { revalidate: 60 }` allows cached data with a 60-second revalidation interval.

This example assumes Next.js 16 with Cache Components disabled.

## Example

`src/app/posts/page.tsx`

```tsx
type Post = { id: number; title: string };

export default async function PostsPage() {
  const response = await fetch(
    "https://jsonplaceholder.typicode.com/posts",
    { next: { revalidate: 60 } },
  );

  if (!response.ok) throw new Error("Could not load posts");

  const posts: Post[] = await response.json();
  return <ul>{posts.map((post) => <li key={post.id}>{post.title}</li>)}</ul>;
}
```

## How it works

The page can reuse the response instead of requesting all posts on every render. When it becomes stale, it can refresh in the background. This does not guarantee an immediate new response every 60 seconds.

Use a production build to check caching behavior. Keep private, user-specific data out of shared public caches.
