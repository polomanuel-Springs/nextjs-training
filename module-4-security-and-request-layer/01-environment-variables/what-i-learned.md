# What I understood

- I learned to separate configuration from application code using environment variables.
- I place .env.local at the application root and keep real secrets out of version control.
- NEXT_PUBLIC_ variables can be included in browser code and are often fixed during the build.
- Private variables remain private only if server code does not expose their values.
- I restart development after environment changes and rebuild when a public build-time value changes.
- I use .env.example to describe required configuration with fictional values.
