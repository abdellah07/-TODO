# what is CSRF
    Cross-Site Request Forgery (CSRF) is an attack that forces an end user to execute
    unwanted actions on a web application in which they’re currently authenticated… With
    a little help of social engineering (such assending a link via email or chat), an attacker
    may trick the users of a web application intoexecuting actions of the attacker’s choosing


# state management  <cookies>
    small piece of information stored on client side machien 

    -can be set in http header


# state management <sessions >
    generally handled by a web framework 
    helps to distinguish between other simultaneous sessions
    we can store data in sessions <workflow ,shopping cart ,login>
    a session id is set in the browser (on cookie)

    Pros/Cons: data managed at and by server

# state management <URL rewriting >
    URLs modified to:
    – store parameters (RESTful approach)
        E.g., http://host:port/shopping.html;sessionid=value
    – Force the use of a proxy: destination becomes a parameter

    • Pros: cannot be suppressed by client

# the browser same origin policy 
    • A script can only access resources (and notably cookies) associated with the same origin
        – prevents hostile script from tampering with other pages in the browser
        – prevents script from snooping on input (passwords) of other windows
    • Security Problems: mostly browser bugs
    – Especially in the late 1990s – early 2000s


# how does CSRF WORK ??

    < Hijacks inherent browser functionality and some aspects of HTTP specification
         SOP controls and cookies
    < Privilege escalation type of attack
         “Confused deputy”: browser thinks tag/form/XHR is from same origin as destination
    < Attacker performs blind attacks (cannot see server responses)
        Unless combined with XSS …
    
# Broader view of CSRF
    • Abuse of cross-site data export feature
        – From user’s browser to honest server
        – Disrupts integrity of user’s session
    • Why mount a CSRF attack?
        – Network connectivity
        – Read browser state
        – Write browser state
    • Not just “session riding”

# The attacker’s perspective
    • The attacker can:
        – Control the form/XHR payload
        – Control the content type (« enctype » attribute)
        – Control the method (GET or POST)

    • The attacker cannot:
        – Control other headers
        – Control cookies

# CSRF Basic Defenses
    • Referer Validation    
        in the most common situation, this means that when a user clicks a hyperlink in a web browser, causing the browser to send a request to the server holding the destination web page, the request may include the Referer field, which indicates the last page the user was on (the one where they clicked the link).

    • Persistent authentication (login/session data):

        – Client-Side Storage of session information (not effective)
    • But vulnerable to XSS attacks …

    • … and user manipulation of server state 
        – Server-Side session ID + Secret Token Validation

    • Custom HTTP Header: simpler approach for AJAX/XHR

# Referer Validation Defense

    • HTTP Referer header
        – Referer: http://www.gmail.com/                ok
        – Referer: http://www.bad.com/evil.html         not ok
        – Referer:                                         can know what to do

    • Lenient Referer validation
        – Doesn’t block request if Referer is missing
    • Strict Referer validation
        – Secure, but Referer is sometimes absent…


# Secret Token Validation
    • Requests include a hard-to-guess secret
        – Unguessability replaces unforgeability

    • Variations
        – Session identifier
        – Session-independent token
        – Session-dependent token
        – HMAC / MD5 / SHA-1 of session identifier for integrity protection

# XSS: HttpOnly Cookies
    • Cookie sent over HTTP(s), but not accessible to scripts
    • cannot be read via document.cookie
    • Also blocks access from XMLHttpRequest headers
    • Helps prevent cookie theft via XSS
   
        … but does not stop most other risks: typical attack is to
        overflow cookie repository (replace cookie with attacker value)!
        This is dependent on browser implementation …
    
# Other Mitigation Strategies
    CSRF TOKEN

    Additional anti-CSRF HTTP elements
        – Origin header
        – SameSite cookies (draft RFC 6265bis since 2017)

    User Interaction Based CSRF Defense before critical operati
    captchas ...


# Defense in Depth: ---------------------------------------STRONG SOLUTION  

# Origin Header
    Alternative to Referer with fewer privacy problems
    • Sent only on POST, sends only necessary data
    • Defense against redirect-based attacks

# Defense in Depth: SameSite Cookie

        – Strict: the cookie will not be included in requests sent by third-parties (can affect browsing experience negatively)
        – Lax: the cookie will be sent along with the GET request initiated by third party website, but only for
            top-level navigation requests (URL has to be changed in browser)
        – Browsers are progressively integrating this feature


# One more thing…
    • Cookie Scope:
        – based on Path attribute + Host/domain
        – Restricts usage of cookie to some application on the website
        – This is separate from SOP which is based on Host/domain+port
    – May further restrict cookie abuse
