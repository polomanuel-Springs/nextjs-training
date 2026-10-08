# Server and Client Components

## Explanation

A component is a Server Component by default. Use `"use client"` when it needs state, clicks, or browser APIs.

A server page can include a Client Component. Only the interactive part needs the client directive.

## Example

`src/app/_components/Counter.tsx`

```tsx
"use client";

import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount((value) => value + 1)}>
      Count: {count}
    </button>
  );
}
```

`src/app/page.tsx`

```tsx
import Counter from "./_components/Counter";

export default function HomePage() {
  return <Counter />;
}
```

## How it works

Each click increases the number. The page remains a Server Component, while Counter handles the browser interaction. Keep private data on the server.
