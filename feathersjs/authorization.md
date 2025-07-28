# User Authentication in Feathers.js v5




## Overview
Feathers.js v5 provides **built-in authentication** via the `@feathersjs/authentication` package. It supports strategies like JWT, local (email/password), and others through a standardized hook-based system.



## Key Concepts
    * `authenticate('jwt')`  -  A built-in Feathers hook that verifies JWT access tokens
    * `feathers generate authentication`  -  CLI tool to scaffold a secure auth system
    * `users` service  -  Manages user accounts and password storage
    * `authentication` service  -  Handles login, logout, token generationa



## Setup Authentication

### 1. Generate Authentication Boilerplate

```bash
feathers generate authentication
```

This creates:

- `src/authentication.ts` (JWT strategy)
- `src/services/users/` (user model, password hash hooks)
- Automatic token handling (login, refresh)


### 2. Configure `authentication.ts`

Ensure the JWT strategy is enabled:

```ts
import { AuthenticationService, JWTStrategy } from '@feathersjs/authentication'

app.configure(authentication)

authentication.register('jwt', new JWTStrategy())
```


### 3. Protect Routes Using `authenticate('jwt')`

In the service hook files (e.g., `prices.hooks.ts`):

```ts
import { authenticate } from '@feathersjs/authentication'

export default {
  around: {
    all: [authenticate('jwt')] // 🛡️ Ensures only authenticated users can access
  }
}
```


### Example: Logging In

#### POST `/authentication`

```json
{
  "strategy": "local",
  "email": "user@example.com",
  "password": "secret123"
}
```

**Response:**

```json
{
  "accessToken": "JWT_TOKEN",
  "user": {
    "id": "...",
    "email": "user@example.com"
  }
}
```

## Use the `accessToken` in future requests:

```http
Authorization: Bearer JWT_TOKEN
```


## Password Security
Feathers automatically:
    - Hashes passwords using bcrypt
    - Prevents raw password leaks
    - Validates on login using `@feathersjs/authentication-local`


## Optional Enhancements
    - Rate limiting  -  Add Koa middleware like `koa-ratelimit`
    - Token expiration  -  Configure TTL in `authentication.ts`
    - IP logging  -  Add custom hook in `authentication.hooks.ts`


## Best Practices
    - Use `authenticate('jwt')`  |  ❌ Don't manually verify JWT in service code   |
    - Use `schemaHooks.validateQuery()`  |  ❌ Don’t write custom AJV validators           |
    - Keep shared data model for public data  |  ❌ Don’t implement multi-tenancy unnecessarily |


## Other
For public APIs or SaaS platforms, additional strategies like OAuth, email verification, and session tracking may be needed.
