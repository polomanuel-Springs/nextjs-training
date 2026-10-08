# What I understood

- I learned that Next.js 16 uses proxy.ts for request handling previously called middleware.
- In a src-based application, proxy.ts belongs next to app.
- matcher limits the routes where the handler runs.
- A redirect changes the browser URL, while a rewrite serves another destination without changing the visible URL.
- Simple unconditional redirects may belong in next.config instead of Proxy.
- Protected data and actions still need their own identity and permission checks.
