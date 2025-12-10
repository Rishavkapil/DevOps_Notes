
It is an HTTP response header sent by your server to the browser. 
Its job : Control whether your webpage is allowed to load inside `<iframe>` , `<frame>`

**This is used to prevent ClickJacking** 

### What is ClickJacking ?

Attacker loads your website inside an invisible iframe on website, tricks the user into clicking something on your site(like "Transfer Money", "Delete Account") while they're clicking somewhere else. 

So X-frame option protects by blocking such embedding. 

### Directives 

1. **Deny :** 

```
X-Frame-Options: DENY
```

This means : 
- Your site CANNOT be shown inside any iframe.
- Not by you.
- Not by others.
- No exceptions.

Even if you try from your own site, it will still be blocked.

2. **Same Origin**

```
X-Frame-Options: SAMEORIGIN
```

Meaning:

- Your page can be iframed **ONLY by pages with the same origin**.
- For example:
    - Page from `https://example.com` → **allowed**
    - Page from `https://evil.com` → **blocked**

Use this when your own site legitimately uses iframes internally.


3. **ALLOW-FROM origin(Depricated)**

```
X-Frame-Options: ALLOW-FROM https://partner.com
```

Meaning:

- “Allow only this specific site to iframe my page.”
But:  
🚫 Most modern browsers **ignore this** completely.  
This means the header becomes useless if you use ALLOW-FROM.


