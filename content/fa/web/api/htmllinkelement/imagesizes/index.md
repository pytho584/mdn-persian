---
title: "HTMLLinkElement: imageSizes property"
short-title: imageSizes
slug: Web/API/HTMLLinkElement/imageSizes
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.imageSizes
---

{{APIRef("HTML DOM")}}

ویژگی **`imageSizes`** در رابط {{domxref("HTMLLinkElement")}} اندازه و شرایط تصاویر پیش‌بارگذاری‌شده را که توسط ویژگی {{domxref("HTMLLinkElement.imageSrcset", "imageSrcset")}} تعریف شده‌اند، مشخص می‌کند. این ویژگی مقدار صفت [`imagesizes`](/en-US/docs/Web/HTML/Reference/Elements/link#imagesizes) عنصر {{htmlelement("link")}} را منعکس می‌کند. این ویژگی می‌تواند مقدار صفت `imagesizes` را بازیابی یا تنظیم کند.

صفت `imagesizes` عنصر `<link>` همان صفت `sizes` عنصر {{htmlelement("img")}} است: یک لیست **منبع اندازه** (source size) که با کاما جدا شده است. هر منبع اندازه شامل یک [شرط رسانه‌ای](/en-US/docs/Web/CSS/Guides/Media_queries)، اندازه تصویر به عنوان یک {{cssxref("length")}}، یا کلمه کلیدی `auto` (که باید اول بیاید) می‌باشد. برای اطلاعات بیشتر درباره نحو صفت `sizes`، به [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) مراجعه کنید.

صفت‌های `imagesrcset` و `imagesizes` فقط در عناصر `<link>` معنا دارند که هم صفت `rel` آن‌ها روی `preload` تنظیم شده باشد و هم صفت `as` روی `image`.

## مقدار

یک رشته متشکل از اندازه‌های منبع جدا شده با کاما، یا رشته خالی `""` در صورت عدم تعیین.

## مثال‌ها

با توجه به عنصر `<link>` زیر:

```html
<link
  rel="preload"
  as="image"
  imagesrcset="narrow.png, medium.png 600w, wide.png 1200w"
  imagesizes="(width < 400px) 200px, (400px <= width < 600px) 75vw, 50vw" />
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  padding: 0 0.25rem;
  font-size: 1.2em;
  line-height: 1.4;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

…می‌توانیم مقدار صفت `imagesizes` را با استفاده از ویژگی `imageSizes` بازیابی و به‌روزرسانی کنیم:

```js
const link = document.querySelector("link");
log(`Original: ${link.imageSizes}`);

// تغییر مقدار
link.imageSizes = "50vw";
log(`Updated: ${link.imageSizes}`);
```

{{EmbedLiveSample('Examples',"","80")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLLinkElement.imageSrcset")}}
- {{domxref("HTMLImageElement.sizes")}}
- [پرسش‌های رسانه‌ای](/en-US/docs/Web/CSS/Guides/Media_queries)
- [استفاده از صفت‌های `srcset` و `sizes`](/en-US/docs/Web/HTML/Reference/Elements/img#using_the_srcset_and_sizes_attributes)