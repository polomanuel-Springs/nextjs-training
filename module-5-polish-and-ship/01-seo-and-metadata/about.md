# SEO and Metadata

## Explanation

Metadata describes a page. It can set the browser tab title, a search description, and sharing information.

Use `metadata` for fixed values or `generateMetadata` when values depend on page data. These exports belong in Server Components.

## Example

`src/app/about/page.tsx`

```tsx
import type { Metadata } from "next";

export const metadata: Metadata = {
  title: "About us",
  description: "Learn about our team.",
};

export default function AboutPage() {
  return <h1>Our team</h1>;
}
```

## How it works

The page displays “Our team”, while its metadata sets the tab title and description. A parent layout can also apply a shared title template.

For a published site, use real canonical URLs and Open Graph images. `sitemap.ts` lists public pages; `robots.ts` describes crawler rules. Neither replaces access control.
