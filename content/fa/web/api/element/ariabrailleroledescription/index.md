---
title: "Element: ariaBrailleRoleDescription property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Element/ariaBrailleRoleDescription"
---

---
title: "Element: ariaBrailleRoleDescription property"
short-title: ariaBrailleRoleDescription
slug: Web/API/Element/ariaBrailleRoleDescription
page-type: web-api-instance-property
browser-compat: api.Element.ariaBrailleRoleDescription
---

{{APIRef("DOM")}}

ویژگی **`ariaBrailleRoleDescription`** در رابط {{domxref("Element")}} مقدار صفت [`aria-brailleroledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription) را بازتاب می‌دهد؛ این صفت، توصیف نقش بریل ARIA عنصر را تعریف می‌کند.

از این ویژگی می‌توان برای ارائه نسخه‌ای خلاصه‌شده از مقدار [`aria-roledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription) استفاده کرد.
این ویژگی فقط زمانی باید استفاده شود که `aria-roledescription` وجود داشته باشد و در موارد نادری که مقدار آن برای بریل بیش از حد طولانی است.
صفت [`aria-brailleroledescription`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-brailleroledescription) حاوی اطلاعات بیشتری درباره زمان تنظیم این ویژگی است.

## مقدار

- `<string>`
  - : مقدار یک رشته است، یک نوع مقدار بدون محدودیت، که قرار است به بریل تبدیل شود.

## مثال‌ها

### دریافت و تنظیم ariaBrailleRoleDescription

این مثال نحوه دریافت و تنظیم ویژگی `ariaBrailleRoleDescription` را نشان می‌دهد.

#### HTML

ابتدا یک عنصر `<article>` تعریف می‌کنیم که به عنوان اسلاید در یک نمایش اسلاید استفاده می‌شود.
صفت `aria-roledescription` را روی «slide» و شکل خلاصه بریل آن را در `aria-brailleroledescription` روی «sld» تنظیم می‌کنیم.

```html
<article
  id="article"
  aria-roledescription="slide"
  aria-brailleroledescription="sld"
  aria-labelledby="slide1heading">
  <h1 id="slide1heading">Welcome to my talk</h1>
</article>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 70px;
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

برای دریافت توصیف نقش عنصر، از ویژگی `ariaBrailleRoleDescription` استفاده می‌کنیم.
کد زیر ابتدا مقدار را دریافت کرده و آن را ثبت می‌کند.
سپس توصیف نقش بریل را به «sd» تغییر می‌دهد و دوباره مقدار را ثبت می‌کند (فقط برای نمایش — در کد تولیدی این مقدار را تنظیم نمی‌کنید).

```js
const article = document.getElementById("article");
log(article.ariaBrailleRoleDescription);
article.ariaBrailleRoleDescription = "sd";
log(article.ariaBrailleRoleDescription);
```

#### نتیجه

{{EmbedLiveSample("Getting and setting ariaBrailleRoleDescription")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}