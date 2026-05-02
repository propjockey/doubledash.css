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
<link rel="stylesheet" type="text/css" href="https://unpkg.com/@propjockey/doubledash.css@0.0.1/doubledash.css">
```

OR

Use your favorite NPM CDN and import specific functions straight into your CSS for small projects. Like so:

```css
@import url("https://unpkg.com/@propjockey/doubledash.css@0.0.1/functions/repeat.css");
```

## Functions

### --repeat(--n, --x)

`./functions/repeat.css`

`--n` is an integer greater than 0, less than 256

`--x` is anything

Outputs --x repeated --n times.

```css
--star-family: --repeat(3, 👽);
/* 👽 👽 👽 */
```

### --repeat-join(--n, --join, --x)

`./functions/repeat-join.css`

`--n` is an integer greater than 0, less than 256

`--join` is a separator

`--x` is anything

Outputs --x repeated --n times, each separated by --join

```css
text-shadow: --repeat-join(4, {, }, 0px 0px 2px black);
/* 0px 0px 2px black, 0px 0px 2px black, 0px 0px 2px black, 0px 0px 2px black */
```

## CHANGELOG:

v0.0.1 - May 3rd, 2026:
* --repeat-join(--n, --join, --x);

v0.0.1 - May 3rd, 2026:
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
