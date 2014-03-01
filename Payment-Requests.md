### Scan-to-pay
Scan-to-pay means you're being presented a QR-code by the payee and you're initiating a payment by scanning that code. You can generally scan QR codes using the embedded scanner whereever you see a photo button in the app: on the main screen, on the send coins screen or in the app widget. Although discouraged due to security concerns, you can also scan using an external scanner app.

There is four kinds of QR-codes around:
* Plain base58-encoded addresses. Upon scanning, a payment will be prepared to that address.
* BIP21 formatted payment request URIs. In addition to the address, those can also contain the requested amount and an address label.
* BIP72 formatted payment request URIs. In addition to what BIP21 provides, they contain a link to a BIP70 payment request that can be fetched via HTTP or HTTPS. It basically adds a signature and features like an expiration date and a refund address.
* BIP70 payment requests in base43 encoded URIs. This is an experimental format that fits a payment request into a QR code, without the need for additional HTTP requests. It is _not_ backwards compatible to BIP21/BIP72. In order to enable this format, go to the labs settings and tick "BIP70 for scan-to-pay".

All of these formats except a naked Bitcoin address can optionally include a Bluetooth address for sending direct payments in face to face situations. BIP70 also supports sending direct payments to services via HTTP or HTTPS.
