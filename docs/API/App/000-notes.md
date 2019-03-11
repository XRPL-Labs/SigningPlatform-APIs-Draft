# `Notes` App (API)

### 1. Intro & Terms

Multiple screens. The button to go to the next page (and ability to swipe next) will be enabled after a (in-button?) countdown hits zero. The user **must** take some time to read.

- Some info on the features the app provides, explaining the app is an interface to the XRP ledger. 
- App is **not** a custodian wallet: at no point in time (not even when signing) will your information and/or secret keys be sent to the app developers.
- Info that all sensitive data is stored **locally** on the device. Users promises to use the app responsibly and is fully aware the app developers cannot be liable for the safety of your funds.
  
  > _We need to put this in a way that doesn't scare users._
- Of course the app can be used read-only as well :)


### 2. OS Permissions

To use the app, the app needs some permissions. There permissions are mandatory: the app will not be able to fully function without the permissions. Users will get a one-by-one request to access certain features. If the user didn't give permission, the setup will not continue. 
 > _Check: possible?_
 
 - **Camera** permission - To scan QR codes (payments, payment requests, pairing)
 - **Push** notifications - To send notifications for received payments\*, confirmations of sent payments\* to your accounts & payment requests
 - **Fingerprint / FaceID** - If available: _mandatory_. (Set app password anyway if available, fallback for if fp/fid no longer available somehow).
 - **Camera Roll / Storage** - _THIS ONE IS OPTIONAL!_ Allow people to "scan" QR codes from the camera roll / storage (picture) when sending a payment, instead of a live camera view.

\* _Payments_: XRPL objects, can also be escrow, etc.

###### 🎉 Pre-setup ready. Now on to the actual fun stuff...
