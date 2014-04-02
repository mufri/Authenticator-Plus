---
 layout: default
 title: Design
 category: page

---

Authenticator is based on [Google Authenticator](https://code.google.com/p/google-authenticator/) and support the HMAC-Based One-time Password (HOTP) algorithm specified in [RFC 4226](https://tools.ietf.org/html/rfc4226) and the Time-based One-time Password (TOTP) algorithm specified in [RFC 6238](https://tools.ietf.org/html/rfc6238).


**Technical overview**

- Account data are encrypted with AES 256-bit encryption with 64000 PBKDF2 iterations
- All sensitive data is encrypted and decrypted locally before syncing. Your master password never leaves your device. Your data stays accessible only to you.



**Technical details**

- A master password is required to use Authenticator Plus, which will never be sent outside your device
- Since master password is never stored outside only locally, there is no way to recover the data if master password is lost
- Data is stored in [SQLCipher encrypted database](http://sqlcipher.net/design)
    1. SQLCipher uses 256-bit AES encryption
    2. Master password will be used to derive encryption key using 64000 PBKDF2 iterations(OpenSSL’s PKCS5_PBKDF2_HMAC_SHA1).
    3. SQLCipher uses [OpenSSL libcrypto](http://openssl.org/) for all cryptographic functions
- Encrypted database which contains data is synchronized across devices using [Dropbox Sync API](https://www.dropbox.com/developers/sync)
    1. When a change a made in a device, complete encrypted database is sent to other devices 
    2. Other devices will download the database and decrypt it using locally stored master password
    3. This way your master password is never leave your device yet still data sync works
- Master password is stored Android local database
    1. If PIN lock is configured, master password is encrypted with your PIN
    2. In non-rooted device, local app database is well protected by [Android Security model](http://source.android.com/devices/tech/security/)
    3. Other than Authenticator Plus app, no other app or user will be able to access it
    4. In rooted device, PIN lock is mandated, and your master password is encrypted with your PIN


**Freedom of choice**

- If an user don't want to use Dropbox to sync, they can use available backup / restore functionality to sync across your devices
- Data can be exported as QR code or encrypted HTML with QR codes, this way if you would like to try other apps you can easily move out of Authenticator plus


** FAQ **

***What if someone else get physical access to my device?***

 - If you have enabled PIN lock, others will not be able to access your PIN even if they have your device.
 - If PIN lock is not enabled, others will be able to access our PIN, however without your actual user name and password for each accounts its of no use
 - They will not be able to export your data to QR or ZIP
 - Though they can access your backup, without your master password they cannot open the database


***What if someone hacks my dropbox account?***

  - Without your master password, hacker will not be able to open your database



**Your master password is key to your data security, stronger the password stronger the security**        



