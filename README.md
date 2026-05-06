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
<link rel="stylesheet" type="text/css" href="https://unpkg.com/@propjockey/doubledash.css@0.2.2/doubledash.css">
```

OR

Use your favorite NPM CDN and import specific functions straight into your CSS for small projects. Like so:

```css
@import url("https://unpkg.com/@propjockey/doubledash.css@0.2.2/functions/repeat/index.css");
```

## Functions

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

### Iterative Looping (like for loops in JS)

`./functions/repeat/loop.css`

The maximum iteration count is 1024.

You can register up to 64 individual loops for use in any property contexts.
(functions are global so make sure not to overwrite any of your definitions)

They must be named `--dd-loop-id-0`, `--dd-loop-id-1`, etc up to index `63`.

You can alias them globally for easier use later:

```css
:root {
  --my-first-css-loop:       --dd-loop-id-0;
  --my-other-loop-alias:     --dd-loop-id-1;
  --propjockey-ftw:          --dd-loop-id-2;
  --give-jane-ori-abundance: --dd-loop-id-3;
}
```

Define their output functions like so:

```css
@function --dd-loop-id-0() {
  result: "--dd-i: " --dd-number-to-string(var(--dd-i))
    "\A --dd-x: " --dd-number-to-string(var(--dd-x), 2)
    "\A --dd-x-start: " --dd-number-to-string(var(--dd-x-start), 2)
    "\A --dd-x-end: " --dd-number-to-string(var(--dd-x-end), 2)
    "\A --dd-arg1: " --dd-to-string(var(--dd-arg1))
    "\A --dd-arg2: " --dd-to-string(var(--dd-arg2))
    "\A --dd-arg3: " --dd-to-string(var(--dd-arg3))
    "\A --dd-arg4: " --dd-to-string(var(--dd-arg4))
    "\A\A"
  ;
}

@function --dd-loop-id-3() {
  result: calc(var(--dd-i) + var(--dd-x)) calc(-1 * var(--dd-i) - var(--dd-x));
}
```

Your loop function body has access to the variables shown in the example.

`--dd-i` is the current integer iteration index, starting from 0. The maximum value is 1023 (1024 iterations)

`--dd-x-start` is the initial loop controller value, typically set to 0 or 1

`--dd-x` is the current iteration's cumulative loop controller value
(if you did `x = x + 2` in a for loop starting from 0, it would be i:x 0:0, 1:2, 2:4, 3:6...)

`--dd-x-end` is the ending sentinel value for your loop controller that a condition is checked against, typically the condition is "lt" meaning continue if --dd-x is less than this end value.

#### Executing your loop

To run your loop in various contexts, call `--dd-loop()` in a property value.

The loop is short-circuited and does not compute anything beyond where it ends.

```css
body::after {
  white-space: pre;
  content: --dd-loop(0, lt, 10, + 1, var(--my-first-css-loop));
  /* the same as this if you don't want to use a var() alias */
  content: --dd-loop(0, lt, 10, + 1, --dd-loop-id-0);
}
```

The required parameters in order are:

1. `--dd-x-start` a number value to begin with
   * you can cast lengths and other dimensions to a number using the cast functions if needed

2. `--dd-condition`
   * One of the following identifiers:
     * eq | gt | gte | lt | lte | neq
   * Before an iteration executes, it calculates the next would-be --dd-x and compares it to the --dd-x-end value, which is the next parameter.

3. `--dd-x-end` a number value to compare --dd-x to in order to determine if the loop should continue.

4. `--dd-calc-partial` This is the formula applied to your initial x, then to the current x each iteration. You can provide `+ 1` to increase --dd-x by one each time. You can also multiply or divide initially then add or subtract from that result by providing a calc partial such as `* 2 - 1`. Other loop controller variations are not supported yet.

5. `--dd-use-loop` - an identifier you provide that connects to the loop body function you intend to execute in this context. This is the value checked against in the `--dd-global-loops` function you overwrote to register your loops.

This is how you read these required parameters:

`--dd-loop(0, lt, 10, + 1, var(--my-first-css-loop));`
loop while `0` is **less than** `10` and **add one** each time after executing the loop body aliased by `var(--my-first-css-loop)`.

Not dissimilar to the `for (let x = 0; x < 10, x = x + 1) {...}` loop in js.

The remaining parameters are optional. In order, they are:

6. `--dd-joiner` - a value to output in between iterations.
   * It does not output before the first iteration nor after the last.
   * set it to the identifier `none` to not produce anything between iterations.
   * set it to a comma with the do-not-spread `{ , }` syntax if you want your output to be joined by commas:
     * `--dd-loop(0, + 1, lt, 10, var(--my-first-css-loop), { , });`

7. `--dd-arg1` - any value you wish to pass into this context
   * It can be a color if you want to use this loop in multiple places with different colors.
   * It can be a number if you want to modify your loop in each context you use it in.
   * etc

8. The remaining optional parameters are
   * `--dd-arg2`, through `--dd-arg16`
   * The same as `--dd-arg1`, can be anything or nothing.

> [!NOTE]
> We can't pass them as actual args because the spec is overly strict with no reason provided about calling a function with more parameters than defined (but not with fewer), which means *YOU* would have to define _all of them_ every time you define a loop function in order for me to pass them at all, or else it would just silently not work. 🙄
> (there are a TON of extremely unfortunate and irritating authoring problems with the current CSS function spec, I hide what I can for you.)

### Cast number to string

`./functions/cast/number-to-string.css`

`--dd-number-to-string(--dd-number, --dd-fixed: 0, --dd-round: nearest)`

`--dd-number` is the number to cast to string

`--dd-fixed` is an integer for the decimal precision to show in the string, defaulting to 0, maximum 6 decimal places though native CSS precision only allows up to 6 if the number is between 1 and 0, and with 6 digits left of the decimal, it doesn't have room for any decimal precision. The outuput remains fixed length in any case, using 0 as needed.

`--dd-round` is the rounding strategy used to reach the precision specified, defaulting to `nearest`.

Demo: https://codepen.io/propjockey/pen/JobdXLz?editors=0100

### Cast length and other dimensions to string

`./functions/cast/dimension-to-string.css`

`--dd-dimension-to-string(--dd-dimension, --dd-basis: 1px, --dd-unit <string>: "", --dd-fixed <integer>: 0, --dd-round: nearest)`

basis (optional for length dimensions) is the single unit value of the length or other dimension provided (96dpi, 10deg, 100ms), defaulting to `1px` which will show a length as pixels

unit (optional) is the string to append after the number, eg "px", defaulting to an empty string.

fixed (optional) is the decimal precision, same as in `cast/number-to-string.css`

round (optional) defaulting to `nearest`, same as in `cast/number-to-string.css`

Demo: https://codepen.io/propjockey/pen/dPOoMmx?editors=0100

### --dd-bit-to-st(--dd-bit)

takes a bit, 0 or 1, and returns a space toggle (space if 1, initial if 0)

### --dd-bit-to-ist(--dd-bit)

takes a bit, 0 or 1, and returns an [inverted space toggle](https://propjockey.breakpoint-system.com/#space-toggle-brief) (initial if 1, space if 0)

### --dd-st-to-bit(--dd-st)

takes a space toggle and returns a bit (1 if space, 0 if initial)

### --dd-ist-to-bit(--dd-ist)

takes an [inverted space toggle](https://propjockey.breakpoint-system.com/#space-toggle-brief) and returns a bit (1 if initial, 0 if space)

### TODO: Document the rest shown in the changelog

So many ✨

And as soon as we have ...vargument spreading (which absolutely should have happened by default and unfortunately doesn't), maybe up to another 100 functins will be added for array processing.

Miiiight add mixins once those are here too.

## CHANGELOG:

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
