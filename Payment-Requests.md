This document describes the possibilities of Bitcoin Wallet version 3.38+ to initiate payments and respond to payment requests. Note the described procedures and interfaces can be implemented by any wallet app. If you have more than one wallet apps installed, a chooser dialog should appear as needed.

### Scan-to-pay

Scan-to-pay means you're being presented a QR-code by the payee and you're paying by scanning that code. You can generally scan QR-codes using the embedded scanner whereever you can tap a photo button in the app: on the main screen, on the send coins screen or in the app widget. Although discouraged due to security concerns, you can also scan using an external scanner app.

There are four kinds of QR-codes around:
* Plain base58-encoded addresses. Upon scanning, a payment will be prepared to that address.
* BIP21 formatted bitcoin request URIs. In addition to the address, those can also contain the requested amount and an address label.
* BIP72 formatted bitcoin request URIs. In addition to what BIP21 provides, they contain a link to a BIP70 payment request that can be fetched via HTTP or HTTPS. It basically adds features like an expiration date and a refund address and some security by signing the request.
* BIP70 payment requests in base43 encoded URIs. This is an experimental format that fits a (small) payment request into a QR-code, without the need for additional HTTP requests. It is _not_ backwards compatible to BIP21/BIP72. In order to enable this format on the payee side, go to the labs settings and tick "BIP70 for scan-to-pay".

All of these formats except a naked Bitcoin address can optionally include a Bluetooth address for sending direct payments in face to face situations. BIP70 also supports sending direct payments to services via HTTP or HTTPS. Direct payments make use of payment messages and payment acks as defined in BIP70.

### Tap-to-pay

Tap-to-pay means your tapping another device with your phone. Targets include a phone or tablet owned by the payee, payment terminals or vending machines. It makes use of Near-Field Communication (NFC), specifically NFC Data Exchange Format (NDEF) messages. Those messages can also be written to a passive tag, although it for security concerns it is discouraged to use them for more than just testing.

There is three types of NDEF messages:
* BIP21 and BIP72 formatted bitcoin request URIs are stored in an URI record. They work exactly like in the scan-to-pay usecase.
* BIP70 payment request in a mime record. This is an experimental format that transmit a full-size payment request via NFC, without the need for additional HTTP requests. In order to enable this format on the payee side, go to the labs settings and tick "BIP70 for tap-to-pay".

All of these formats can optionally include a Bluetooth address for sending direct payments, just like with scan-to-pay.

### Click-to-pay

Click-to-pay means you're clicking a link on a web site, e.g. when checking out from a shop. It can contain:
* BIP21 and BIP72 formatted bitcoin request URIs that work exactly like in the scan-to-pay usecase.
* BIP70 payment requests in base43 encoded URIs. This is an experimental format that fits a payment request into the href of a link, without the need for additional HTTP requests. It is _not_ backwards compatible to BIP21/BIP72.

These formats can optionally include an HTTP or HTTPS address for sending direct payments, just like with scan-to-pay.

Click-to-pay only works if your web browser has whitelisted the "bitcoin" scheme. Fortunately on Android this generally seems to be the case.

### In-app payments

This means an app on the same device as the wallet requests a payment. It is done by throwing an Action.VIEW intent. It can contain either of
* BIP21 and BIP72 formatted bitcoin request URI in the data field (again see scan-to-pay). You'll get a success code and optionally a transaction hash returned in the result.
* BIP70 formatted payment request in the intent extra. You'll get a BIP70 formatted payment message returned in the result.

There is a sub-project "integration-android" that implements helper methods for in-app payments. The exact API is described in the [[InAppPayments]] document.

### Various

Here is some use-cases that are implemented (mostly as a by-product of the above) but are not expected to be used much:
* Open BIP70 formatted payment request from e-mail attachment. This could be useful if a payment processor e-mails you a request and you somehow missed the first request in the click-to-pay workflow.
* Open BIP70 formatted payment request from cloud storage, e.g. Google Drive.

### Links

[BIP21: Bitcoin request URIs](https://github.com/bitcoin/bips/blob/master/bip-0021.mediawiki)

[BIP70: Payment protocol](https://github.com/bitcoin/bips/blob/master/bip-0070.mediawiki)

[BIP71: MIME-types used in Payment protocol](https://github.com/bitcoin/bips/blob/master/bip-0071.mediawiki)

[BIP72: Bitcoin request URI extensions for Payment Protocol](https://github.com/bitcoin/bips/blob/master/bip-0072.mediawiki)
