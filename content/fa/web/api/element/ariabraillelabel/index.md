---
title: "Element: ariaBrailleLabel property"
short-title: ariaBrailleLabel
slug: Web/API/Element/ariaBrailleLabel
page-type: web-api-instance-property
browser-compat: api.Element.ariaBrailleLabel
---

{{APIRef("DOM")}}

ویژگی **`ariaBrailleLabel`** از رابط {{domxref("Element")}} مقدار ویژگی [`aria-braillelabel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-braillelabel) را منعکس می‌کند که برچسب بریل ARIA عنصر را تعریف می‌کند.

این برچسب عنصر ممکن است توسط فناوری‌های کمکی که می‌توانند محتوا را به خط بریل ارائه دهند استفاده شود، اما تنها زمانی باید تنظیم شود که برچسب مخصوص بریل تجربه کاربری را بهبود بخشد. ویژگی [`aria-braillelabel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-braillelabel) حاوی اطلاعات بیشتری درباره زمان تنظیم این ویژگی است.

## Value

- `<string>`
  - مقدار یک رشته است؛ نوع مقداری بدون محدودیت که قرار است به خط بریل تبدیل شود.

## Examples

### Getting and setting ariaBrailleLabel

این مثال نحوه دریافت و تنظیم ویژگی `ariaBrailleLabel` را نشان می‌دهد.

#### HTML

ابتدا یک دکمه با متن برچسب «3 out of 5 stars» و یک ویژگی `aria-braillelabel` با مقدار `"\*\*\*"` تعریف می‌کنیم. این کار به نمایشگر بریل اجازه می‌دهد تا «btn \*\*\*» را به جای عبارت مفصّل‌تر «btn gra 3 out of 5 stars» نمایش دهد.

```html
<button id="button" aria-braillelabel="\*\*\*">3 out of 5 stars</button>
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

#### JavaScript

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

سپس کد از ویژگی `ariaBrailleLabel` دکمه استفاده می‌کند تا ابتدا برچسب بریل را دریافت و ثبت کند. سپس برچسب بریل را به «3\*» تنظیم و مقدار را دوباره ثبت می‌کند.

```js
const button = document.getElementById("button");
log(button.ariaBrailleLabel);
button.ariaBrailleLabel = "3*";
log(button.ariaBrailleLabel);
```

#### Result

{{EmbedLiveSample("Getting and setting ariaBrailleLabel")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}