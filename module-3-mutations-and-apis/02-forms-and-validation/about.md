# Forms and Validation

## Explanation

Validation checks whether input is acceptable. Browser checks help the user, but server checks are still required.

Zod lets you define validation rules in one schema. Install it in the application with `npm install zod`.

## Example

`src/app/contact/actions.ts`

```ts
"use server";

import { z } from "zod";

const schema = z.object({ email: z.string().trim().email() });

export async function checkEmail(formData: FormData) {
  const result = schema.safeParse({ email: formData.get("email") });

  if (!result.success) throw new Error("Enter a valid email");

  console.log("Valid email:", result.data.email);
}
```

`src/app/contact/page.tsx`

```tsx
import { checkEmail } from "./actions";

export default function ContactPage() {
  return (
    <form action={checkEmail}>
      <input name="email" type="email" required />
      <button type="submit">Check email</button>
    </form>
  );
}
```

## How it works

The browser checks the email field, and Zod checks the submitted value again on the server. A valid email is logged; nothing is sent or saved.

This small example shows the validation rule. A complete form would return field errors using `useActionState` and show a pending button using `useFormStatus`.
