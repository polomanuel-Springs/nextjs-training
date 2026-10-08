# What I understood

- I learned that async Server Components can obtain data before rendering.
- I check response.ok because fetch does not automatically throw for every failed HTTP status.
- Suspense displays a fallback while an asynchronous section is pending.
- Independent requests can run in parallel with Promise.all; dependent requests need an appropriate sequence.
- TypeScript annotations do not validate JSON received from an external service.
- I use timeouts and an error interface when a request can fail.
