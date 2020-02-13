# App URI Scheme (Deep links)

The URI Scheme will be used for QR code contents & for redirects. Deep linked locations will point to real (existing) HTTPS locations, so if the app is not installed, a fallback to a "get the app" page can be displayed.

- `https://xumm.app/detect/*<Another URI / ... to be parsed>`
- `https://xumm.app/tx/*<(xrpl:signed-transaction:)SIGNEDBLOB>`
- `https://xumm.app/pair/*<USERUUID>.<DEVICEUUID>`
- `https://xumm.app/sign/*<PAYLOADUUID>`

Possibly:

- `https://ripple.com//send*`
- `xrpl://*`
- `ilp://*`

# QR Contents

QR contents should allow the same formats as the Deep Links (above), and:

- `rXXXXXXXX{address}`
- `rXXXXXXXX{address}:{tag}`
- `rXXXXXXXX{address}={tag}`
- `rXXXXXXXX{address}.*dt={tag}`
- `John Doe <rXXXXXXXX{address}(:tag)*>` (e-mail client alike format)
- URL params parsed with:
  - `dt` / `tag`
  - `address` / `account` / `to`
  - `currency` (issuer + currency, `issuer:currency` / `currency:issuer`), check XRPL for existing IOU.
  - `amount`
  - `inv` / `invoice` / `invoiceid`
- HEX string (`[A-F0-9]{32,}`), and test for:
  - Signed TX to submit (Decoded = JSON + signature)
  - Signed TX to submit or add signature (Decoded = JSON + signature + existing multisigner(s))
  - TX template (Decoded = JSON without signature)
  - TX hash (view TX)
  - Public key (66 chars that derive into a valid activated account)
  - Private key (64 chars, or 66 starting with `00` or `ED`)
  
For formats and detection, see https://github.com/XRPL-Labs/xumm-string-decode/   

# Tech. Notes

- Check/Keep updated with XRP Community Standards / Drafts: https://github.com/xrp-community/standards-drafts/issues

