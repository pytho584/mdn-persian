---
title: "HTMLImageElement: height property"
---

---
title: "HTMLImageElement: height property"
short-title: height
slug: Web/API/HTMLImageElement/height
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.height
---

{{APIRef("HTML DOM")}}

ویژگی **`height`** رابط {{domxref("HTMLImageElement")}} ارتفاعی را که تصویر در آن رسم می‌شود، بر حسب {{Glossary("CSS pixel", "پیکسل‌های CSS")}} مشخص می‌کند، در صورتی که تصویر به هر رسانه بصری مانند صفحه نمایش یا چاپگر رسم یا رندر شود. در غیر این صورت، این ارتفاع طبیعیِ تصحیح‌شده بر اساس تراکم پیکسل تصویر است.

## مقدار

مقداری صحیح که ارتفاع تصویر را نشان می‌دهد. نحوه تعریف ارتفاع بستگی به این دارد که آیا تصویر به یک رسانه بصری رندر می‌شود یا خیر.

- اگر تصویر به یک رسانه بصری مانند صفحه نمایش یا چاپگر رندر شود، ارتفاع بر حسب {{Glossary("CSS pixel", "پیکسل‌های CSS")}} بیان می‌شود.
- در غیر این صورت، ارتفاع تصویر با استفاده از ارتفاع طبیعی (ذاتی) آن، تنظیم‌شده برای تراکم نمایشگر، که توسط {{domxref("HTMLImageElement.naturalHeight", "naturalHeight")}} نشان داده می‌شود، نمایش داده می‌شود.

## مثال‌ها

در این مثال، دو اندازه مختلف برای تصویر یک ساعت با استفاده از ویژگی [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) ارائه شده است. یکی ۲۰۰ پیکسل عرض و دیگری ۴۰۰ پیکسل عرض دارد. علاوه بر این، ویژگی [`sizes`](/en-US/docs/Web/HTML/Reference/Elements/img#sizes) برای مشخص کردن عرضی که تصویر باید با توجه به عرض viewport در آن رسم شود، ارائه شده است.

### HTML

برای viewportهایی با عرض حداکثر ۴۰۰ پیکسل، تصویر با عرض ۲۰۰ پیکسل رسم می‌شود. در غیر این صورت، با عرض ۴۰۰ پیکسل رسم می‌شود.

```html
<p>Image height: <span class="size">?</span>px (resize to update)</p>
<img
  src="/en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-200px.png"
  alt="Clock"
  srcset="
    /en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-200px.png 200w,
    /en-US/docs/Web/HTML/Reference/Elements/img/clock-demo-400px.png 400w
  "
  sizes="(width <= 400px) 200px, 300px" />
```

### جاوااسکریپت

کد جاوااسکریپت به `height` نگاه می‌کند تا ارتفاع تصویر را با توجه به عرضی که در حال حاضر در آن رسم شده است تعیین کند.

```js
const clockImage = document.querySelector("img");
let output = document.querySelector(".size");

const updateHeight = () => {
  output.innerText = clockImage.height;
};

updateHeight();
window.addEventListener("resize", updateHeight);
```

### نتیجه

{{EmbedLiveSample("Examples", 640, 450)}}

ممکن است آزمایش این مثال در {{LiveSampleLink('Examples', 'پنجره جداگانه')}} آسان‌تر باشد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.width")}}
- {{domxref("HTMLImageElement.naturalHeight")}}
- {{domxref("HTMLCanvasElement.height")}}
- {{domxref("HTMLEmbedElement.height")}}
- {{domxref("HTMLIFrameElement.height")}}
- {{domxref("HTMLObjectElement.height")}}
- {{domxref("HTMLSourceElement.height")}}
- {{domxref("HTMLVideoElement.height")}}