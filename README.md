[![Jane Ori - PropJockey.io](https://img.shields.io/badge/Jane%20Ori%20%F0%9F%91%BD-%F0%9F%A4%8D%20PropJockey.io-7300E6.svg?labelColor=FB04C2&style=plastic)](http://jane.propjockey.io/)

# doubledash.css from <img src="https://github.com/user-attachments/assets/87119fb5-c39d-429a-9bfd-424f0e100720" alt="" width="30px"> PropJockey

NPM: https://www.npmjs.com/package/@propjockey/doubledash.css

GitHub: https://github.com/propjockey/doubledash.css

Website / Docs: https://propjockey.github.io/doubledash.css/

Install:
`$ npm install @propjockey/doubledash.css`
Then import the `/node_modules/@propjockey/doubledash.css/doubledash.css` file into your project.

OR

Use your favorite NPM CDN and include it on your page for small projects. Like so:
```html
<link rel="stylesheet" type="text/css" href="https://unpkg.com/@propjockey/doubledash.css@0.3.2/doubledash.css">
```

OR

Use your favorite NPM CDN and import specific functions straight into your CSS for small projects. Like so:

```css
@import url("https://unpkg.com/@propjockey/doubledash.css@0.3.2/functions/repeat/index.css");
```

## Visit the website documentation!

[![Visit the website!](https://propjockey.github.io/doubledash.css/assets/social-share.png)](https://propjockey.github.io/doubledash.css/)

### TODOs

So many ✨

And as soon as we have ...vargument spreading (which absolutely should have happened by default and unfortunately doesn't), maybe up to another 100 functins will be added for array processing.

Miiiight add mixins once those are here too.

## CHANGELOG:

v0.3.2 - May 15th, 2026:
* fixed type-of to allow `initial` argument

v0.3.1 - May 15th, 2026:
* fixed readme image

v0.3.0 - May 15th, 2026:
* /functions/cast/to-typed.css
  * --dd-to-typed(--dd-any) returns the same value typed if it can be, which often computes the value
* /functions/other/compute.css
  * --dd-compute(--dd-any) alias of --dd-to-typed()
* /functions/other/is-int.css
  * fixed import omission
* /functions/logic/int16/*
  * renamed functions and files for clarity
    * get-int16 became get-bit-int16
    * set-int16 became set-bit-int16
    * byte-int16 became get-byte-int16
    * nibble-int16 became get-nibble-int16
* /functions/repeat/*
  * modified repeat.css
    * --repeat(--n[, --joiner], --x);
    * added an optional joiner parameter to the signature
    * if --joiner is the keyword `comma`, it uses a comma joiner
      * so you don't have to write `--n, {,}, --x`
    * if --joiner is the keyword `none`, it doesn't use a joiner
      * so you can always write 3 parameters if you prefer
      * so it is consistent with the joiner param in loop
  * deleted `repeat-join.css`
  * modified loop.css
    * if --joiner is the keyword `comma`, it uses a comma joiner
      * so you don't have to write `--n, {,}, --x`
* /functions/logic/inverted-space-toggle/*
  * --dd-or-ist fixed export name
  * --dd-nor-ist fixed by avoiding a CSS bug/edgecase
  * --dd-xnor-ist fixed by avoiding a CSS bug/edgecase
* /functions/logic/space-toggle/*
  * --dd-xnor-st fixed by avoiding a CSS bug/edgecase
* added a website for documentation
  * https://propjockey.github.io/doubledash.css/

v0.2.2 - May 7th, 2026:
* Added more optional argument parameters to `--dd-loop()` after looking more closely at [Ana Tudor's beautiful CSS work](https://codepen.io/thebabydino/pen/AvqmXO?editors=0100) and seeing how often she needs more than I originally shipped.
* `--dd-arg4` was the previous maximum, `--dd-arg16` is now the max.

v0.2.1 - May 7th, 2026:
* Improved loop implementation so it can do 1024 iterations max instead of 128.

v0.2.0 - May 6th, 2026:
* /functions/repeat/*
  * loop.css --dd-loop(from, condition, to, calc stepper partial, loop-id)
* /functions/other/*
  * is-int.css --dd-is-int(--dd-any) // returns 1 if it's an integer, otherwise 0
  * type-of.css --dd-type-of(--dd-any) // returns a string, for example:
    * `"<length>"`
    * `"<string>"`
    * `"<integer>"`
    * `"<number>"`
    * `"<length-percentage>"`
    * `"<length-percentage>+"` // space separated list
    * `"<length-percentage>#"` // comma separated list
    * `"<custom-ident>+"`
    * `"<color>"`
    * `"<empty>"` // a valid/truthy empty value, the space of a space toggle
    * `"<initial>"` // not "technically correct" but ultimately more useful
    * "*" // if not identified
    * etc etc etc
* /functions/cast/*
  * removed length-to-px-number.css
  * removed length-to-string.css
  * added dimension-to-number.css --dd-dimension-to-number(--dd-dimension, --dd-basis)
    * basis is a unit value defaulting to 1px so the result would be a number in terms of px
    * change basis to 1rem for the number result to be in terms of rem, for example
  * added dimension-to-string.css --dd-dimension-to-string(--dd-dimension, --dd-basis: 1px, --dd-unit: "", --dd-fixed: 0, --dd-round: nearest)
    * basis is a unit value defaulting to 1px so the result would be a number in terms of px
    * if dimension is length, change basis to 1rem for the number result to be in terms of rem, for example
    * if dimension is time, change basis to 1s for the number result to be in terms of seconds
  * to-string.css --dd-to-string(--dd-any)
    * returns the string value of anything that can be converted into a string
    * returns the string "type-of" result if the value can't directly be stringified

v0.1.2 - May 5th, 2026:
* Fix filename for int16-to-hex-string.css

v0.1.1 - May 5th, 2026:
* Fixed rounding on number-to-string thanks to Jakob E
  - https://bsky.app/profile/jakob-e.bsky.social/post/3mkzgiem3322y
  - the same rounding omission affected bitwise operations so it has been fixed in two additional places as well (thank you times 3!)
* Clean up: Corrected poor naming of several internal variables
* Fixed all /functions/logic/int16/* functions
* /functions/logic/int16/*
  * shift-left-int16.css --dd-shift-left-int16(--int16, --distance)
  * shift-right-int16.css --dd-shift-right-int16(--int16, --distance)
  * msb-int16.css --dd-msb-int16(--dd-int16) // most significant bit returns [0, 15]
  * byte-int16.css --dd-byte-int16(--dd-int16, --which-byte[0, 1])
  * nibble-int16.css --dd-nibble-int16(--dd-int16, --which-nibble[0, 3])
* Added an optional base param to --dd-digit-to-string(--dd-digit, --dd-base)
  * extended the default set as base32hex number base
  * base32hex, base32, base64 are the current options
* /functions/cast/*
  * int16-to-bit-string.css --dd-int16-to-bit-string(--dd-int16, --dd-min-length: 0)
    * maximum min length is 16
    * pads left with 0 to reach the minimum length
  * int16-to-hex-string.css --dd-int16-to-bit-string(--dd-int16, --dd-min-length: 0)
    * maximum min length is 4
    * pads left with 0 to reach the minimum length
  * dcb-to-int16.css --dd-dcb-to-int16(--dd-arg1, --dd-arg2, --dd-arg3, --dd-arg4)
    * dcb = decimal coded binary.
    * allows you to write binary in CSS
    * decimal number 11 is interpreted as binary so it equals 3
    * the most significant bit is the first bit of the first argument
    * the least significant bit is the last bit of the last argument you provide
    * only --dd-arg1 is required, each arg is 4 bits (a nibble)
    * --dd-dcb-to-int16(11,1001,1101) = 925
    * --dd-dcb-to-int16(0011,1001,1101) = 925
    * --dd-dcb-to-int16(1111,1111,1111,1110) = 65534
  * int16-to-dcb-nibble.css --dd-int16-to-dcb-nibble(--dd-int16, --which-nibble[0, 3])

v0.1.0 - May 3rd, 2026:
* Added --dd- prefix
* Organized into folders
  * /repeat/repeat.css
  * /repeat/repeat-join.css
* Added index.css files in each folder that includes all functions from that folder
  * /repeat/index.css
* /functions/compare/*
  * cmp.css --dd-cmp(--left, --right)
  * eq.css --dd-eq(--left, --right)
  * neq.css --dd-neq(--left, --right)
  * gt.css --dd-gt(--left, --right)
  * gte.css --dd-gte(--left, --right)
  * lt.css --dd-lt(--left, --right)
  * lte.css --dd-lte(--left, --right)
* /functions/cast/*
  * bit-to-space-toggle.css --dd-bit-to-st(--dd-bit)
  * space-toggle-to-bit.css --dd-st-to-bit(--dd-st)
  * bit-to-inverted-space-toggle.css --dd-bit-to-ist(--dd-bit)
  * inverted-space-toggle-to-bit.css --dd-ist-to-bit(--dd-ist)
  * digit-to-string.css --dd-digit-to-string(--digit)
  * number-to-string.css --dd-number-to-string(--dd-number, --dd-fixed: 0, --dd-round: nearest)
* /functions/logic/*
  * bit/*
    * and-bit.css --dd-and-bit(--bit-a, --bit-b)
    * nand-bit.css --dd-nand-bit(--bit-a, --bit-b)
    * nor-bit.css --dd-nor-bit(--bit-a, --bit-b)
    * not-bit.css --dd-not-bit(--bit)
    * or-bit.css --dd-or-bit(--bit-a, --bit-b)
    * xnor-bit.css --dd-xnor-bit(--bit-a, --bit-b)
    * xor-bit.css --dd-xor-bit(--bit-a, --bit-b)
  * int16/*
    * and-int16.css --dd-and-int16(--int16-a, --int16-b)
    * nand-int16.css --dd-nand-int16(--int16-a, --int16-b)
    * nor-int16.css --dd-nor-int16(--int16-a, --int16-b)
    * not-int16.css --dd-not-int16(--int16)
    * or-int16.css --dd-or-int16(--int16-a, --int16-b)
    * xnor-int16.css --dd-xnor-int16(--int16-a, --int16-b)
    * xor-int16.css --dd-xor-int16(--int16-a, --int16-b)
    * toggle-int16.css --dd-toggle-int16(--int16, --which-bit)
    * set-int16.css --dd-set-int16(--int16, --which-bit, --to-bit-value)
    * get-int16.css --dd-get-int16(--int16, --which-bit)
    * bitwise.css --dd-bitwise(--int16-a, --operator, --int16-b-or-which-bit, --set-to: 0)
  * space-toggle/*
    * and-st.css --dd-and-st(--st-a, --st-b)
    * nand-st.css --dd-nand-st(--st-a, --st-b)
    * nor-st.css --dd-nor-st(--st-a, --st-b)
    * not-st.css --dd-not-st(--st)
    * or-st.css --dd-or-st(--st-a, --st-b)
    * xnor-st.css --dd-xnor-st(--st-a, --st-b)
    * xor-st.css --dd-xor-st(--st-a, --st-b)
  * inverted-space-toggle/*
    * and-ist.css --dd-and-ist(--ist-a, --ist-b)
    * nand-ist.css --dd-nand-ist(--ist-a, --ist-b)
    * nor-ist.css --dd-nor-ist(--ist-a, --ist-b)
    * not-ist.css --dd-not-ist(--ist)
    * or-ist.css --dd-or-ist(--ist-a, --ist-b)
    * xnor-ist.css --dd-xnor-ist(--ist-a, --ist-b)
    * xor-ist.css --dd-xor-ist(--ist-a, --ist-b)

v0.0.2 - May 3rd, 2026:
* --repeat-join(--n, --join, --x);

v0.0.0 - May 3rd, 2026:
* Initial release
* --repeat(--n, --x);

---

## Open Contact 👽

Please do reach out if you need help with any of this, have feature requests, or want to share what you've created!

| <small>PropJockey</small> | <small>CodePen</small> | <small>DEV Blog</small> | <small>GitHub</small> |
| :---: | :---: | :---: | :---: |
| [![PropJockey.io](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/external-social/100px/color-responsive/propjockey-lines.svg)](https://propjockey.io) | [![CodePen](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/external-social/100px/color-responsive/codepen.svg)](https://codepen.io/propjockey) | [![DEV Blog](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/external-social/100px/color-responsive/dev.svg)](https://dev.to/janeori) | [![GitHub](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/external-social/100px/color-responsive/github.svg)](https://github.com/propjockey) |

| <small>Mastodon</small> | <small>LinkedIn</small> | <small>X</small> | <small>Bluesky</small> |
| :---: | :---: | :---: | :---: |
| [![Mastodon](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/external-social/100px/color-responsive/mastodon.svg)](https://front-end.social/@JaneOri) | [![LinkedIn](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/external-social/100px/color-responsive/linkedin.svg)](https://www.linkedin.com/in/janeori/) | [![X](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/external-social/100px/color-responsive/x.svg)](https://x.com/jane0ri) | [![Bluesky](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/external-social/100px/color-responsive/bluesky.svg)](https://bsky.app/profile/janeori.propjockey.io) |

### My heart is open to receive abundance in all forms,<br>flowing to me in many expected and unexpected ways.

| PayPal | Ko-fi | Venmo |
| :---: | :---: | :---: |
| [![PayPal](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/QR-Codes/svg/200px/paypal.svg)](https://www.paypal.com/donate/?cmd=_s-xclick&hosted_button_id=9Z925L3SJJ8BS&source=qr&ssrt=1772865628068) | [![Ko-fi](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/QR-Codes/svg/200px/ko-fi.svg)](https://ko-fi.com/janeori) | [![Venmo](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/QR-Codes/svg/200px/venmo.svg)](https://account.venmo.com/u/JaneOri) |

| BTC | XRP | ETH |
| :---: | :---: | :---: |
| [![BTC bc1qe2ss8hvmskcxpmk046msrjpmy9qults2yusgn9](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/QR-Codes/svg/200px/btc.svg)](https://app.ens.domains/janeori.eth) | [![XRP rw2ciyaNshpHe7bCHo4bRWq6pqqynnWKQg : 459777128](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/QR-Codes/svg/200px/xrp.svg)](https://bithomp.com/en/account/X7zmKiqEhMznSXgj9cirEnD5sWo3iZPqbNPChdEKV9sM9WF) | [![ETH 0x674D4191dEBf9793e743D21a4B8c4cf1cC3beF54](https://raw.githubusercontent.com/propjockey/propjockey-brand/main/QR-Codes/svg/200px/eth.svg)](https://app.ens.domains/janeori.eth) |
| bc1qe...usgn9 | rw2ci...nWKQg<br>: 459777128 | 0x674...beF54 |
