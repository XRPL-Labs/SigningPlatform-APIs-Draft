# App URI Scheme (Deep links)

The URI Scheme will be used for QR code contents & for redirects. Deep linked locations will point to real (existing) HTTPS locations, so if the app is not installed, a fallback to a "get the app" page can be displayed.

- `https://xign.app/detect/*<Another URI / ... to be parsed>`
- `https://xign.app/tx/*<(xrpl:signed-transaction:)SIGNEDBLOB>`
- `https://xign.app/pair/*<USERUUID>.<DEVICEUUID>`
- `https://xign.app/sign/*<PAYLOADUUID>`

Possibly:

- `https://ripple.com//send*`
- `xrpl://*`
- `ilp://*`

# Tech. Notes

- Check/Keep updated with XRP Community Standards / Drafts: https://github.com/xrp-community/standards-drafts/issues

