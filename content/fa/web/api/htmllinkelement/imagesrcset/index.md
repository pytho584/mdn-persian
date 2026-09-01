---
title: "HTMLLinkElement: imageSrcset property"
short-title: imageSrcset
slug: Web/API/HTMLLinkElement/imageSrcset
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.imageSrcset
---

{{APIRef("HTML DOM")}}

ویژگی **`imageSrcset`** در رابط {{domxref("HTMLLinkElement")}}، رشته‌ای است که یک یا چند **رشتهٔ نامزد تصویر (image candidate string)** را با جداکنندهٔ کاما مشخص می‌کند. این ویژگی منعکس‌کنندهٔ مقدار ویژگی [`imagesrcset`](/en-US/docs/Web/HTML/Reference/Elements/link#imagesrcset) عنصر {{htmlelement("link")}} است و می‌توان از آن برای دریافت یا تنظیم مقدار ویژگی `imagesrcset` استفاده کرد.

هر رشتهٔ نامزد تصویر شامل یک URL تصویر و به‌صورت اختیاری یک توصیفگر عرض (width) و/یا تراکم پیکسلی (pixel density) است که شرایط استفاده از آن تصویر نامزد را مشخص می‌کند.

```plain
"images/team-photo.jpg, images/team-photo-retina.jpg 2x, images/team-photo-large.jpg 1400w"
```

برای عناصر HTML {{htmlelement("link")}} که در آن‌ها [`rel="preload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) و [`as="image"`](/en-US/docs/Web/HTML/Reference/Elements/link#as) تنظیم شده باشد، ویژگی `imagesrcset` از نظر نحو (syntax) و معناشناسی مشابه ویژگی [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) عنصر {{htmlelement("img")}} است؛ این ویژگی نشان می‌دهد که منبع مناسبِ مورد استفاده توسط یک عنصر `<img>` با مقادیر متناظر در ویژگی‌های `srcset` و `sizes` آن، از پیش بارگذاری شود.

اگر ویژگی `imageSrcset` شامل توصیفگرهای عرض باشد، ویژگی {{domxref("HTMLLinkElement.imageSizes", "imageSizes")}} باید غیر از `null` باشد؛ در غیر این صورت مقدار `imageSrcset` نادیده گرفته می‌شود.

## مقدار

رشته‌ای متشکل از فهرستی با جداکنندهٔ کاما از یک یا چند رشتهٔ نامزد تصویر، یا رشتهٔ خالی `""` در صورت تعیین‌نشده.

## مثال‌ها

با توجه به عنصر `<link>` زیر:

```html
<link
  rel="preload"
  as="image"
  imagesizes="50vw"
  imagesrcset="bg-narrow.png, bg-wide.png 800w" />
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

… می‌توانیم با استفاده از ویژگی `imageSrcset` مقدار ویژگی `imagesrcset` را بخوانیم و به‌روزرسانی کنیم:

```js
const link = document.querySelector("link");
log(`Original: ${link.imageSrcset}`);

// add an image candidate string
link.imageSrcset += ", bg-huge.png 1200w";
log(`Updated: ${link.imageSrcset}`);
```

{{EmbedLiveSample('Examples',"","80")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLLinkElement.imageSizes")}}
- {{domxref("HTMLImageElement.srcset")}}
- [بارگذاری پیش‌بینانه](/en-US/docs/Web/Performance/Guides/Speculative_loading#link_relpreload)
- [تصاویر واکنش‌گرا](/en-US/docs/Web/HTML/Guides/Responsive_images)