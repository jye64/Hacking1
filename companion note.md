# ECE 9069 Hacking Companion Notes on QRLJacker

![alt text][tool]

[tool]:  https://github.com/OWASP/QRLJacking/blob/master/QRLJacker/Screenshots/Screenshot1.png


## Overview

### QR Code

QR code (Quick Response barcode that consists of black squares and dots. As it can be readily scanned by an imaging device, such as camera of smartphones, it is now being widely used in many aspects of our daily life. Its core function is to offer a convenient way to direct smartphone users to a variety of other media, for instance, website addresses.  It also enables electronic payments, contacts sharing on social media, etc. Since the way that QR code stores information, we can only know its content after scanning, therefore QR code is susceptible to many potential vulnerabilities.

### How does QR code work?

* Four encoding modes
	> numeric, alphanumeric, binary, and [kanji](https://en.wikipedia.org/wiki/Kanji)
* Decoded by using [Reed-Solomon error correction](https://en.wikipedia.org/wiki/Reed%E2%80%93Solomon_error_correction)


### QRLJacking

 [QRLJacking](https://github.com/OWASP/QRLJacking) is a simple social engineering attack vector capable of session hijacking by exploiting some QR code vulnerabilities. It was published as an open source software by OWASP in 2016code is widely . Potentially all applications that support "Login with QR code" function can be affected. 


## Vulnerable Applications

* Whatsapp
* WeChat
* Line
* Discord
* Weibo
* ...

## Attack Flow

* The attacker initiates a client side QR session and clone the login QR code into a phishing website
* The attacker sends the phishing page to the victim and convince the victim to scan it
* The victim scans the QR code with a targeted mobile app
* The attacker captures the login session and gain control
* The server is exchaning the victim's data with the attacker's session

![alt text][attack flow]

[attack flow]:  https://github.com/OWASP/QRLJacking/blob/master/blob/images/AttackFlow.JPG


## Commands and Flags Used

- Options
	> Display available options
- Set port -- /set host --
	> Setting port and host of the attacker's web server hosting the fake QR login page
- Sessions -l
    > Display captured sessions information
- Sessions -i ID
    > Interact with a captured session by ID


## How Phishing can be done?

![alt text][phishing]

[phishing]:  https://github.com/jye64/Hacking1/blob/master/phishing-page.png

* Spam emails, social media
* Third-party login
* Fake website domain name

 
## Implications

- Account Hijacking
  > The attacker is able to get access to the victim's account
- Information Disclosure
  >The victim's data is transferred to the attacker's session
- Contact Phishing
  > The attacker is able to fauad the victim's contact and lead to reputation loss

##  Advantages & Shortcomings

### Advantages

* Easy to hidden its true content
* QR code has popularity

### Shortcomings

* Hard to keep unnoticed by victims
* Session timeout
* Victims regain control by logging out from their mobile end
* Third party warning may remind the victim of redirecting to external webpage


## Tool Command List

Session management commands
Usage: sessions -flag

|                flag  |Description            
|-------------------------------|-----------------------------|
|`-h`            |Show help message            |
|`-l`            |list all captured sessions         |
|`K`             |Remove all captured sessions|
|`s`             |search for sessions|
|`k ID`          |Remove a session by ID|
|`i ID`          |Intereact with a captured session by ID|


# References

* http://community102.com/things-you-should-know-about-the-quick-response-qr-code/

* https://www.fastprint.co.uk/blog/quick-response-codes-what-are-they-and-how-do-they-work.html#:~:text=How%20Does%20A%20QR%20Code%20Work%3F&text=Basically%2C%20a%20QR%20code%20works,represent%20certain%20pieces%20of%20information

* https://github.com/OWASP/QRLJacking

* https://owasp.org/www-community/attacks/Qrljacking#:~:text=Overview,way%20to%20login%20into%20accounts

* https://blog.beaconstac.com/2019/02/year-of-qr-codes/#:~:text=geofencing%20powered%20app.-,How%20popular%20are%20QR%20codes%20in%202021%3F,scan%20QR%20codes%20by%202020
