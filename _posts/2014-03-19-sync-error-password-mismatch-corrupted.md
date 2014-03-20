---
 layout: default
 title: Password mismatch or Corrupted data.
 category: faq
 description: solution to password mismatch corrupted data error
 keywords: authenticator plus Password mismatch or Corrupted data solution
---

This error can happen due to master password mismatch or data is corrupted in dropbox account.

####**Master password mismatch:**

Master password should be same across all the devices you use for seamless sync to happen, if for any reason, if your master password in your device is not matching with the data in Dropbox, sync will fail.

To avoid any data loss follow the below steps,

1. Download the data from Dropbox (Dropbox -> Apps -> Authenticator Plus -> authplus.db)
2. In your local device, Menu -> Settings -> Import -> Authenticator Plus
3. Enter your master password for the data in Dropbox account
4. Select the downloaded authplus.db through using "..." button
5. Click import
6. Now all your data is imported to local device
7. Delete/rename the Dropbox copy of authplus.db (Dropbox -> Apps -> Authenticator Plus -> authplus.db)
8. Sync now


####**Corrupted data:**

Data in Dropbox account could be corrupted, there are various causes for this issue, there is no way to recover this issue.