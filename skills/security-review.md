---
name: security-review
description: Web application security review covering OWASP Top 10 — secrets management, input validation, SQL injection prevention, XSS, CSRF, authentication, authorization, rate limiting, and dependency security. Use before any deployment or when handling user data.
---

# Security Review Skill

Ensures all web application code follows security best practices and identifies potential vulnerabilities before deployment.

## When to Use

- Implementing authentication or authorization
- Handling user input or file uploads
- Creating new API endpoints
- Working with secrets or credentials
- Implementing payment features
- Storing or transmitting sensitive data
- Before any production deployment

## 1. Secrets Management

**NEVER:**
```typescript
const apiKey = "sk-proj-xxxxx"  // Hardcoded secret
const dbPassword = "password123" // In source code
```

**ALWAYS:**
```typescript
const apiKey = process.env.OPENAI_API_KEY
const dbUrl = process.env.DATABASE_URL

if (!apiKey) {
  throw new Error('OPENAI_API_KEY not configured')
}
```

**Checklist:**
- [ ] No hardcoded API keys, tokens, or passwords
- [ ] All secrets in environment variables
- [ ] `.env.local` in .gitignore
- [ ] No secrets in git history
- [ ] Production secrets in hosting platform (Vercel, Netlify, Railway)

## 2. Input Validation

```typescript
import { z } from 'zod'

const CreateUserSchema = z.object({
  email: z.string().email(),
  name: z.string().min(1).max(100),
  age: z.number().int().min(0).max(150)
})

export async function createUser(input: unknown) {
  const validated = CreateUserSchema.parse(input)
  return await db.users.create(validated)
}
```

**File Upload Validation:**
- Size check (5MB max typical)
- Type check against allowlist (not blocklist)
- Extension check
- Never trust client-side validation alone

## 3. SQL Injection Prevention

**NEVER concatenate user input into SQL:**
```typescript
// DANGEROUS
const query = `SELECT * FROM users WHERE email = '${userEmail}'`
```

**ALWAYS use parameterized queries:**
```typescript
await db.query('SELECT * FROM users WHERE email = $1', [userEmail])
```

## 4. Authentication & Authorization

**Token Storage:**
```typescript
// WRONG: localStorage (vulnerable to XSS)
localStorage.setItem('token', token)

// CORRECT: httpOnly cookies
res.setHeader('Set-Cookie',
  `token=${token}; HttpOnly; Secure; SameSite=Strict; Max-Age=3600`)
```

**Authorization:** Always verify permissions before sensitive operations. Check role/ownership server-side, never client-side only.

## 5. XSS Prevention

- Sanitize any user-provided HTML with DOMPurify before rendering
- Set Content Security Policy headers
- Prefer React's built-in escaping — avoid rendering raw HTML from user input

```typescript
const securityHeaders = [{
  key: 'Content-Security-Policy',
  value: "default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:;"
}]
```

## 6. CSRF Protection

- CSRF tokens on all state-changing operations
- `SameSite=Strict` on all cookies
- Verify origin/referer headers on sensitive endpoints

## 7. Rate Limiting

```typescript
import rateLimit from 'express-rate-limit'

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100
})
app.use('/api/', limiter)
```

Apply stricter limits on: login attempts, search, file uploads, and any expensive operations.

## 8. Sensitive Data Exposure

**Logging:**
```typescript
// WRONG
console.log('User login:', { email, password })

// CORRECT
console.log('User login:', { email, userId })
```

**Error Messages:** Never expose stack traces, database details, or internal paths to users. Log details server-side; show generic messages client-side.

## 9. Dependency Security

```bash
npm audit              # Check for vulnerabilities
npm audit fix          # Fix automatically
npm outdated           # Check for outdated packages
```

- [ ] Enable Dependabot on GitHub
- [ ] Commit lock files
- [ ] Use `npm ci` in CI/CD (not `npm install`)

## Pre-Deployment Security Checklist

Before ANY production deployment:

- [ ] No hardcoded secrets — all in env vars
- [ ] All user inputs validated (Zod or equivalent)
- [ ] All database queries parameterized
- [ ] User-provided HTML sanitized with DOMPurify
- [ ] CSRF protection enabled
- [ ] Authentication uses httpOnly cookies
- [ ] Authorization checks on all sensitive endpoints
- [ ] Rate limiting on all API endpoints
- [ ] HTTPS enforced
- [ ] Security headers configured (CSP, X-Frame-Options)
- [ ] Error messages don't leak internal details
- [ ] No sensitive data in logs
- [ ] Dependencies up to date, `npm audit` clean
- [ ] CORS properly configured
- [ ] File uploads validated (size, type)

## Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Next.js Security](https://nextjs.org/docs/security)
- [Web Security Academy](https://portswigger.net/web-security)
