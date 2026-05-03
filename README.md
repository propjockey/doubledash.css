[![Jane Ori - PropJockey.io](https://img.shields.io/badge/Jane%20Ori%20%F0%9F%91%BD-%F0%9F%A4%8D%20PropJockey.io-7300E6.svg?labelColor=FB04C2&style=plastic)](http://jane.propjockey.io/)

# doubledash.css from <img src="https://github.com/user-attachments/assets/87119fb5-c39d-429a-9bfd-424f0e100720" alt="" width="30px"> PropJockey

NPM: https://www.npmjs.com/package/@propjockey/doubledash.css

GitHub: https://github.com/propjockey/doubledash.css

Install:
`$ npm install @propjockey/doubledash.css`
Then import the `/node_modules/@propjockey/doubledash.css/doubledash.css` file into your project.

OR

Use your favorite NPM CDN and include it on your page for small projects. Like so:
```html
<link rel="stylesheet" type="text/css" href="https://unpkg.com/@propjockey/doubledash.css@0.1.0/doubledash.css">
```

OR

Use your favorite NPM CDN and import specific functions straight into your CSS for small projects. Like so:

```css
@import url("https://unpkg.com/@propjockey/doubledash.css@0.1.0/functions/repeat/index.css");
```

## Functions

### --dd-repeat(--n, --x)

`./functions/repeat/repeat.css`

`--n` is an integer greater than 0, less than 256

`--x` is anything

Outputs --x repeated --n times.

```css
--star-family: --dd-repeat(3, 👽);
/* 👽 👽 👽 */
```

### --dd-repeat-join(--n, --join, --x)

`./functions/repeat/repeat-join.css`

`--n` is an integer greater than 0, less than 256

`--join` is a separator

`--x` is anything

Outputs --x repeated --n times, each separated by --join

```css
text-shadow: --dd-repeat-join(4, {, }, 0px 0px 2px black);
/* 0px 0px 2px black, 0px 0px 2px black, 0px 0px 2px black, 0px 0px 2px black */
```

### Compare

* /functions/compare/*
  * cmp.css --dd-cmp(--left, --right)
  * eq.css --dd-eq(--left, --right)
  * neq.css --dd-neq(--left, --right)
  * gt.css --dd-gt(--left, --right)
  * gte.css --dd-gte(--left, --right)
  * lt.css --dd-lt(--left, --right)
  * lte.css --dd-lte(--left, --right)

These all take --left and --right which must be the same type:
`<length>|<number>`

cmp returns an integer, -1, 0, or 1 for less than, equal to, and greater than, respectively

the rest return a boolean bit flag 0 or 1
"is left gte right?"

```css
opacity: --dd-gte(50cqw, 20rem);
```

### TODO: Document the rest shown in the changelog

So many ✨

And as soon as we have ...vargument spreading (which absolutely should have happened by default and unfortunately doesn't), maybe up to another 100 functins will be added for array processing.

Miiiight add mixins once those are here too.

## CHANGELOG:

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
  * bit-to-inverted-space-toggle.css --dd-bit-to-ist(--dd-bit)
  * bit-to-space-toggle.css --dd-bit-to-st(--dd-bit)
  * inverted-space-toggle-to-bit.css --dd-ist-to-bit(--dd-bit)
  * space-toggle-to-bit.css --dd-st-to-bit(--dd-bit)
  * digit-to-string.css --dd-digit-to-string(--digit)
  * number-to-string.css --dd-number-to-string(--dd-number, --dd-fixed: 0, --dd-round: nearest)
  * length-to-string.css --dd-length-to-string(--dd-len, --dd-basis: 1px, --dd-unit: "", --dd-fixed: 0, --dd-round: nearest)
  * length-to-px-number.css --dd-length-to-px-number(--dd-length)
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
