---
title: "HTMLImageElement: width property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/width"
---

---
title: "HTMLImageElement: width property"
short-title: width
slug: Web/API/HTMLImageElement/width
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.width
---

{{APIRef("HTML DOM")}}

**`width`** ویژگیِ رابط {{domxref("HTMLImageElement")}}، عرضی را نشان می‌دهد که تصویر با آن رسم می‌شود، بر حسب {{Glossary("CSS pixel", "پیکسلِ CSS")}}، در صورتی که تصویر در حال رسم یا رندر شدن به هر رسانهٔ تصویری مانند صفحهٔ نمایش یا چاپگر باشد. در غیر این صورت، این مقدار عرض طبیعیِ تصویر است که بر اساس تراکم پیکسلی تنظیم شده است.

## مقدار

مقداری از نوع عدد صحیح که عرض تصویر را نشان می‌دهد. نحوهٔ تعریف عرض بستگی به این دارد که آیا تصویر به یک رسانهٔ تصویری رندر می‌شود یا نه.

- اگر تصویر به یک رسانهٔ تصویری مانند صفحهٔ نمایش یا چاپگر رندر شود، عرض بر حسب {{Glossary("CSS pixel", "پیکسلِ CSS")}} بیان می‌شود.
- در غیر این صورت، عرض تصویر با استفاده از عرض طبیعی (ذاتی) آن نمایش داده می‌شود که با تراکم نمایشگری که توسط {{domxref("HTMLImageElement.naturalWidth", "naturalWidth")}} مشخص شده است، تنظیم می‌شود.

## مثال‌ها

در این مثال، دو اندازهٔ مختلف برای تصویری از یک ساعت با استفاده از ویژگی [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) فراهم شده است. یکی ۲۰۰ پیکسل عرض و دیگری ۴۰۰ پیکسل عرض دارد. علاوه بر این، ویژگی [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) نیز برای تعیین عرضی که تصویر باید با آن رسم شود، با توجه به عرض viewport، ارائه شده است.

### HTML

برای viewportهایی با عرض حداکثر ۴۰۰ پیکسل، تصویر با عرض ۲۰۰ پیکسل رسم می‌شود. در غیر این صورت، با عرض ۴۰۰ پیکسل رسم می‌شود.

```html
<p>Image width: <span class="size">?</span>px (resize to update)</p>
<img
  src="/en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-200px.png"
  alt="Clock"
  srcset="
    /en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-200px.png 200w,
    /en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-400px.png 400w
  "
  sizes="(width <= 400px) 200px, 400px" />
```

### JavaScript

کد جاوااسکریپت به `height` نگاه می‌کند تا ارتفاع تصویر را با توجه به عرضی که در حال حاضر با آن رسم شده است تعیین کند.

```js
const clockImage = document.querySelector("img");
let output = document.querySelector(".size");

const updateWidth = () => {
  output.innerText = clockImage.width;
};

updateWidth();
window.addEventListener("resize", updateWidth);
```

### نتیجه

{{EmbedLiveSample("Examples", 640, 450)}}

ممکن است آزمایش این مثال در {{LiveSampleLink('Examples', 'پنجرهٔ خودش')}} آسان‌تر باشد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.height")}}
- {{domxref("HTMLImageElement.naturalWidth")}}
- {{domxref("HTMLCanvasElement.width")}}
- {{domxref("HTMLEmbedElement.width")}}
- {{domxref("HTMLIFrameElement.width")}}
- {{domxref("HTMLObjectElement.width")}}
- {{domxref("HTMLSourceElement.width")}}
- {{domxref("HTMLVideoElement.width")}}