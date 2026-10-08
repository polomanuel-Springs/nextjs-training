# App Router and Project Structure

## Explanation

Next.js uses folders to organize pages.

- `page.tsx` is the content of a page.
- `layout.tsx` is shared by the pages inside it.
- `src/app/about/page.tsx` creates the `/about` route.
- `(group)` organizes routes without changing their URLs. `_components` is a private folder for reusable components.

## Example

`src/app/layout.tsx`

```tsx
import type { ReactNode } from "react";

export default function RootLayout({ children }: { children: ReactNode }) {
  return (
    <html lang="en">
      <body>
        <header>My website</header>
        {children}
      </body>
    </html>
  );
}
```

`src/app/about/page.tsx`

```tsx
export default function AboutPage() {
  return <h1>About us</h1>;
}
```

## How it works

Opening `/about` displays “About us” below the shared header. `children` is the page content inserted into the layout.
