# What I understood

- I learned to distinguish a pending operation, an unexpected failure, and a missing resource.
- loading.tsx provides a loading interface for a route segment.
- error.tsx is a Client Component that handles errors and can offer a reset operation.
- notFound selects the not-found interface for an absent record.
- Retrying a render does not repair an unavailable backend or remove an intentionally failing input.
- Expected validation failures can be returned as data rather than thrown as unexpected errors.
