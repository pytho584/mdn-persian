---
title: "PerformanceElementTiming: renderTime property"
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`renderTime`** از رابط {{domxref("PerformanceElementTiming")}} زمان رندر المان مرتبط را بازمی‌گرداند.

## مقدار

یک {{domxref("DOMHighResTimeStamp")}} شامل زمان رندر المان.

برای تصاویر، این مقدار **زمان‌نمای رندر تصویر** خواهد بود. این مقدار به عنوان اولین نقاشی (paint) پس از بارگذاری کامل تصویر تعریف می‌شود. اگر بررسی مجوز زمان‌بندی (timing allow check) مطابق هدر [Timing-allow-origin](/en-US/docs/Web/HTTP/Reference/Headers/Timing-Allow-Origin) ناموفق باشد، این ویژگی `0` را بازمی‌گرداند.

برای گره‌های متنی، این مقدار **زمان‌نمای رندر متن** خواهد بود. این زمان به لحظه‌ای گفته می‌شود که المان به صورت متن نقاشی می‌شود (text painted).

## مثال‌ها

### ثبت `renderTime`

در این مثال، یک المان {{HTMLElement("img")}} با افزودن صفت [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) تحت نظارت قرار می‌گیرد. یک {{domxref("PerformanceObserver")}} ثبت می‌شود تا تمام ورودی‌های عملکرد از نوع `"element"` را دریافت کند و از پرچم `buffered` برای دسترسی به داده‌های قبل از ایجاد observer استفاده می‌شود. فراخوانی `entry.renderTime` زمان رندر المان تصویر را بازمی‌گرداند.

```html
<img
  src="image.jpg"
  alt="a nice image"
  elementtiming="big-image"
  id="myImage" />
```

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.identifier === "big-image") {
      console.log(entry.renderTime);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

### زمان رندر تصویر مبدأ متقاطع

به دلایل امنیتی، مقدار ویژگی `renderTime` در اصل برای درخواست‌های مبدأ متقاطع (cross-origin) `0` بود. در عوض باید از ویژگی `loadTime` به عنوان جایگزین استفاده کرد.

مرورگرها [اکنون ممکن است زمان رندر کمی درشت‌تر (coarsened) را](https://github.com/w3c/paint-timing/issues/104) در این شرایط آشکار کنند. برای [پشتیبانی مرورگر](#browser_compatibility) بررسی کنید.

برای آشکارسازی اطلاعات دقیق‌تر زمان رندر مبدأ متقاطع، باید هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} تنظیم شود.

به عنوان مثال، برای اجازه دادن به `https://developer.mozilla.org` برای دیدن یک `renderTime` دقیق، منبع مبدأ متقاطع باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

از طرفی، می‌توانید از {{domxref("PerformanceEntry.startTime", "startTime")}} استفاده کنید که اگر `renderTime` مخالف `0` باشد مقدار آن را بازمی‌گرداند، و در غیر این صورت مقدار {{domxref("PerformanceElementTiming.loadTime", "loadTime")}} این ورودی را. با این حال، توصیه می‌شود هدر {{HTTPHeader("Timing-Allow-Origin")}} را تنظیم کنید تا معیارها دقیق‌تر باشند.

اگر از `startTime` استفاده می‌کنید، می‌توانید با بررسی اینکه آیا `renderTime` استفاده شده است، هرگونه نادقتی را علامت‌گذاری کنید:

```js
const isRenderTime = Boolean(entry.renderTime);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}