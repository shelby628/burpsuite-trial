# burpsuite-trial
burpsuite attempt with  a tryhackme lab

=========================================================
DOCUMENTATION — ATTEMPT TO USE BURP SUITE ON TRYHACKME LAB
=========================================================

Lab Details
-----------
- Platform: TryHackMe
- Lab Type: Web Application
- Target IP: 10.10.148.104
- Goal: Practice SQL Injection on login page (Broken Authentication)

Steps Taken to Use Burp
------------------------

1. Installed Burp Suite
- Installed Burp Suite Community Edition on my machine (Ubuntu).
- Successfully launched Burp Suite.

2. Configured Firefox Proxy
- Opened Firefox.
- Went to:
    Preferences → General → Network Settings → Settings…
- Set proxy to:
    HTTP Proxy: 127.0.0.1
    Port: 8080
- Checked:
    [x] Use this proxy server for all protocols

3. Installed FoxyProxy (Optional Attempt)
- Installed FoxyProxy browser extension.
- Tried to switch proxies via FoxyProxy.
- Found it a bit confusing, and it didn’t help resolve the issue.

4. Confirmed Burp Proxy Listening
- Checked Burp under:
    Proxy → Options → Proxy Listeners
- Burp was listening on:
    127.0.0.1:8080

5. Tested Basic Connectivity
- Browsed to:
    http://example.com
- Saw the request appear in Burp HTTP History.
- Confirmed Burp was working for general internet traffic.

6. Attempted to Access TryHackMe Lab
- Typed in Firefox:
    http://10.10.148.104
- Page failed to load or kept spinning.

7. Observed No Entries in Burp
- Looked in:
    Proxy → HTTP history
- Saw no traffic for:
    10.10.148.104
- Only saw unrelated traffic like:
    GET /canonical.html
    Host: detectportal.firefox.com

8. Tried Manual Request
- Typed:
    http://10.10.148.104/testthis
- Still failed to load.
- No request appeared in Burp.

Conclusion
----------
- Burp was successfully intercepting general web traffic.
- However, it could not intercept traffic to TryHackMe’s lab IP (10.10.148.104).
- Root cause likely:
    - Burp can’t route to the VPN network used by TryHackMe.
    - VPN routes bypass the proxy or block proxy connections.

Next Steps Decided
-------------------
- Skip Burp for this TryHackMe lab.
- Use:
    - Firefox Dev Tools → Edit and Resend
    - curl or Postman
- Plan to try Burp later with local labs like DVWA or Juice Shop.

Lessons Learned
---------------
- Burp works well for:
    Local apps
    Public internet traffic
- Burp can have issues with:
    VPN networks like TryHackMe’s
    Lab IPs on private ranges
- Best practice:
    Be flexible and use other tools when Burp fails.
