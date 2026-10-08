# Server Actions

## Explanation

A Server Action is a server function called from a form. Use `"use server"` to mark the function's file.

The form sends its named fields as `FormData`. Validate them on the server before using them.

## Example

`src/app/tasks/actions.ts`

```ts
"use server";

export async function submitTask(formData: FormData) {
  const title = String(formData.get("title") ?? "").trim();

  if (!title || title.length > 80) throw new Error("Invalid task title");

  console.log("Task received:", title);
}
```

`src/app/tasks/page.tsx`

```tsx
import { submitTask } from "./actions";

export default function TasksPage() {
  return (
    <form action={submitTask}>
      <input name="title" placeholder="Task title" maxLength={80} required />
      <button type="submit">Submit</button>
    </form>
  );
}
```

## How it works

Submitting the form sends the title to the server. A valid title is printed in the server terminal; it is not saved.

In a real task application, verify the user's permissions and replace the log with a database write. After a successful write, `revalidatePath` can refresh the list and `redirect` can open another page.
