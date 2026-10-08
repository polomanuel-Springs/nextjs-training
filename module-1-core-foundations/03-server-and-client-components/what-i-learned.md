# What I understood

- I learned that App Router components are Server Components by default.
- Client Components are needed for state, event handlers, and browser APIs.
- The use client directive defines a boundary and belongs at the beginning of the file.
- A server page can import a small Client Component without becoming a Client Component itself.
- I use a functional state update when the new value depends on the previous value.
- I keep secrets on the server and use serializable props across the client boundary.
