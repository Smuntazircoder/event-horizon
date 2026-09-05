# API notes

All JSON endpoints are prefixed with `/api`. Authenticated requests use `Authorization: Bearer <token>`. Event creation requires `ORGANIZER` or `ADMIN`; admin statistics require `ADMIN`. Input is validated with Zod and list endpoints only expose approved events.
