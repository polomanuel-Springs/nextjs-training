# Performance and Optimization

## Explanation

Optimization helps a page load and respond efficiently. Start with simple improvements and measure their effect.

- `next/image` helps display images with appropriate dimensions.
- `next/font` manages fonts.
- Dynamic imports can load optional code later.

## Example

Place an actual image at `public/notebook.jpg`.

`src/app/page.tsx`

```tsx
import Image from "next/image";

export default function HomePage() {
  return (
    <Image
      src="/notebook.jpg"
      alt="A blue notebook"
      width={300}
      height={200}
    />
  );
}
```

## How it works

The dimensions reserve space before the image loads, reducing unexpected layout movement. Use dimensions matching your image's aspect ratio and alt text matching its content.

Measure loading speed, interaction, and visual stability in a production build. Only defer a component when loading it later actually helps the user.
