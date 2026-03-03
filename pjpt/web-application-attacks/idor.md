# Insecure Direct Object Reference (IDOR)

Access other users' resources by modifying object identifiers (IDs, filenames, etc.) in requests.

## How It Works

The application uses user-supplied input to access objects directly without checking authorization.

```
# Your profile
GET /api/user/1001

# Change the ID to access someone else's profile
GET /api/user/1002
```

## Where to Look

- URL parameters: `/profile?id=123`
- API endpoints: `/api/v1/orders/456`
- File downloads: `/download?file=report_123.pdf`
- Form hidden fields: `<input type="hidden" name="user_id" value="123">`
- Cookies or headers containing IDs

## Testing

1. Log in as User A, capture requests with Burp
2. Identify requests that reference an object (ID, filename, UUID)
3. Modify the identifier to another value
4. Check if the application returns another user's data

### Common ID Patterns

```
# Sequential integers -- easy to enumerate
/api/user/1, /api/user/2, /api/user/3

# UUIDs -- harder to guess but still vulnerable if leaked
/api/user/550e8400-e29b-41d4-a716-446655440000

# Encoded values -- decode and modify
/api/user/MTAwMQ==  (base64 for "1001")
```

### Horizontal vs Vertical

- **Horizontal IDOR** -- Access another user's data at the same privilege level
- **Vertical IDOR** -- Access admin/higher-privilege functionality

## Automation

```bash
# Burp Intruder -- cycle through IDs
# Set the ID parameter as the payload position
# Use a number list as the payload

# ffuf for API endpoint fuzzing
ffuf -u http://target.com/api/user/FUZZ -w numbers.txt -H "Cookie: session=YOUR_TOKEN"
```

## Mitigations

- Server-side authorization checks on every request
- Use indirect references (map user-specific tokens to objects)
- Avoid exposing sequential IDs
- Log and monitor access patterns
