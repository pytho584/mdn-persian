---
title: "ElementInternals: ariaBrailleLabel property"
short-title: ariaBrailleLabel
slug: Web/API/ElementInternals/ariaBrailleLabel
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaBrailleLabel
---

{{APIRef("Web Components")}}

ویژگی **`ariaBrailleLabel`** از رابط {{domxref("ElementInternals")}} مقدار صفت [`aria-braillelabel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-braillelabel) را منعکس می‌کند که برچسب بریل ARIA عنصر را تعریف می‌کند.

این برچسب عنصر ممکن است توسط فناوری‌های کمکی که قادر به نمایش محتوا به صورت بریل هستند استفاده شود، اما تنها زمانی باید تنظیم شود که یک برچسب مخصوص بریل تجربه کاربری را بهبود بخشد.
صفت [`aria-braillelabel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-braillelabel) حاوی اطلاعات بیشتری درباره زمان مناسب برای تنظیم این ویژگی است.

## مقدار

یک رشته که قرار است به بریل تبدیل شود.

## مثال‌ها

این مثال نحوه دریافت و تنظیم ویژگی `ariaBrailleLabel` را نشان می‌دهد.

فرض می‌کنیم یک عنصر سفارشی به نام `<star-rating>` تعریف کرده‌ایم که در آن برچسب بریل داخلی عنصر برابر با مقدار صفت `aria-braillelabel` عنصر تنظیم می‌شود:

```js
class StarRating extends HTMLElement {
  constructor() {
    super();
    this._internals = this.attachInternals();
    this._internals.ariaRole = "slider";
    this._internals.ariaBrailleLabel = this.ariaBrailleLabel;
  }

  // …
}

customElements.define("star-rating", StarRating);
```

و عنصر سفارشی را با متن برچسب "3 out of 5 stars" و یک صفت `aria-braillelabel` با مقدار `"3"` قرار می‌دهیم.
این کار باعث می‌شود نمایشگر بریل به جای نمایش "slider gra 3 out of 5 stars" (که طولانی‌تر است) عبارت "slider 3" را به صورت بریل نشان دهد.

```html
<star-rating id="rate" aria-braillelabel="3">3 out of 5 stars</star-rating>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logInternals = document.querySelector("#log");
function log(text) {
  logInternals.innerText = `${logInternals.innerText}${text}\n`;
  logInternals.scrollTop = logInternals.scrollHeight;
}
```

کد از ویژگی `ariaBrailleLabel` برای دریافت و تنظیم برچسب بریل استفاده می‌کند.

```js
const el = document.querySelector("star-rating");
log(el._internals.ariaBrailleLabel);
el._internals.ariaBrailleLabel += "*";
log(el._internals.ariaBrailleLabel);
```

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ElementInternals.ariaBrailleRoleDescription")}}