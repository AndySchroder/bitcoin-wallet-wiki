#summary Instructions for translators

### Introduction

Below you find the list of files that are relevant for translating. These are all English versions. You can have a look at the other languages as well if that helps you understand the language, but keep in mind that the English version is most up-to-date and should be taken as a reference.

You can download the files to your local machine and translate there. Please do not edit the indentation, the HTML/XML markup itself and do not change any IDs. The files are UTF-8 encoded, if possible can you keep that encoding?

I'd suggest keeping the following Bitcoin-related terms and names like they are. This is no hard rule - if you have reason to translate a term to your language then please do so.

  * Bitcoin Wallet
  * Bitcoin
  * BTC
  * Testnet
  * Prodnet
  * Blockchain

If you discover references to existing software like Android system software or the Android Market, it would be great if you could use the same translations that have been chosen by the authors of that software.


### List of files

Here is the list of (English) reference files to translate:

  * http://code.google.com/p/bitcoin-wallet/source/browse/wallet/res/values/strings.xml
  * http://code.google.com/p/bitcoin-wallet/source/browse/wallet/assets/help.html
  * http://code.google.com/p/bitcoin-wallet/source/browse/wallet/assets/help_request_coins.html
  * http://code.google.com/p/bitcoin-wallet/source/browse/wallet/assets/help_send_coins.html
  * http://code.google.com/p/bitcoin-wallet/source/browse/wallet/assets/safety.html
  * http://code.google.com/p/bitcoin-wallet/source/browse/market/market-description.txt
  * http://code.google.com/p/bitcoin-wallet/source/browse/market/market-promo-text.txt

All translations are renamed using the following pattern, **{lc}** being the two-letter [ISO 639-1](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) language code:

  * res/values-**{lc}**/strings.xml
  * assets/help`_`**{lc}**.html
  * assets/help_request_coins`_`**{lc}**.html
  * assets/help_send_coins`_`**{lc}**.html
  * assets/safety`_`**{lc}**.html
  * web/market-description-**{lc}**.txt
  * web/market-promo-text-**{lc}**.txt


### Special considerations for strings.xml

Embedded into the text you will find some formatting like \n (new line) or replacement characters like %s or %1$s. Replacement chars are used to insert dynamic values like Bitcoin amounts. Keep them at the places that fit the context. If you are unsure, tell me and I'll have a look at it.

If you add the apostrophe sign, you need to escape it with a backslash like this: \'. Alternatively, enclose the whole string in quotation marks. Escape characters or quotation marks themselves will not appear in the app. For example, look at the string named "preferences_credits_bitcoinj_title". Again, if unsure just tell me.

In some cases, three dots are added to the end of the string (ellipse). A special unicode character is used for this; be sure to _not_ replace it with three separate dots.

In "strings.xml", can you keep in mind that translations do not get much longer than their English version? Otherwise the layout might break. In all other files, length does not matter much.


### Using git

If you happen to know how to use [git](http://git-scm.com/), I'd appreciate if you just prepare a commit I can pull. Alternatively, you could also send a patch file.