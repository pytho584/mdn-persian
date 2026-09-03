---
title: "PerformanceResourceTiming: renderBlockingStatus property"
short-title: renderBlockingStatus
slug: Web/API/PerformanceResourceTiming/renderBlockingStatus
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.renderBlockingStatus
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`renderBlockingStatus`** وضعیت مسدودسازی رندرِ منبع را برمی‌گرداند.

این ویژگی برای شناسایی منابعی مفید است که:

- مسدودکننده‌ی رندر نبوده‌اند و بنابراین می‌توانسته‌اند به تعویق بیفتند، یا
- مسدودکننده‌ی رندر بوده‌اند و بنابراین می‌توانسته‌اند از پیش بارگذاری شوند.

## توضیحات

منابع مسدودکننده‌ی رندر، فایل‌های ایستایی مانند فونت‌ها، CSS و جاوااسکریپت هستند که رندر کردن محتوای صفحه در مرورگر را مسدود یا به تأخیر می‌اندازند. مرورگر این منابع مسدودکننده را به‌طور خودکار تعیین می‌کند و پیش از بارگذاری و ارزیابی همه‌ی برگه‌های سبک و اسکریپت‌های همگام، هیچ پیکسلی را روی صفحه نمایش نمی‌دهد. این کار از نمایش فلشِ محتوای بدون استایل («FOUC») جلوگیری می‌کند.

علاوه بر سازوکار خودکار مسدودسازی رندر، می‌توان ویژگی `blocking="render"` را به عناصر {{HTMLElement("script")}}، {{HTMLElement("style")}} یا {{HTMLElement("link")}} اضافه کرد تا مسدودسازی رندر به‌صورت صریح مشخص شود. برای مثال:

```html
<script blocking="render" src="important.js" defer></script>
```

## مقدار

ویژگی `renderBlockingStatus` می‌تواند مقادیر زیر را داشته باشد:

- `"blocking"`
  - : منبع احتمالاً رندر را مسدود می‌کند.
- `"non-blocking"`
  - : منبع رندر را مسدود نمی‌کند.

## مثال‌ها

### ثبت منابعی که رندر را مسدود می‌کنند

از ویژگی `renderBlockingStatus` می‌توان برای مشاهده‌ی منابعی که رندر را مسدود می‌کنند استفاده کرد.

مثال زیر با استفاده از {{domxref("PerformanceObserver")}}، که هنگام ثبت ورودی‌های جدید عملکرد `resource` در جدول زمانی عملکرد مرورگر، آن‌ها را اطلاع‌رسانی می‌کند. از گزینه‌ی `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.renderBlockingStatus === "blocking") {
      console.log(`${entry.name} is render-blocking.`);
    }
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  if (entry.renderBlockingStatus === "blocking") {
    console.log(`${entry.name} is render-blocking.`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}