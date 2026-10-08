# Routing and Navigation

## Explanation

Use `Link` to move between pages. A folder named `[id]` allows the same page to handle different identifiers.

For example, `/products/1` and `/products/2` use `products/[id]/page.tsx`. In Next.js 16, route parameters are asynchronous.

## Example

`src/app/products/page.tsx`

```tsx
import Link from "next/link";

export default function ProductsPage() {
  return <Link href="/products/1">View product 1</Link>;
}
```

`src/app/products/[id]/page.tsx`

```tsx
type Props = { params: Promise<{ id: string }> };

export default async function ProductPage({ params }: Props) {
  const { id } = await params;
  return <h1>Product {id}</h1>;
}
```

## How it works

Clicking the link opens `/products/1`. The detail page reads `id` and displays “Product 1”. A real catalog would use that ID to look up the product and handle missing records.
