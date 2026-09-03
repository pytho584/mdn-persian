---
title: "PerformanceResourceTiming: initiatorType property"
short-title: initiatorType
slug: Web/API/PerformanceResourceTiming/initiatorType
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.initiatorType
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`initiatorType`** یک رشته (string) است که ویژگی پلتفرم وب که بارگذاری منبع را آغاز کرده است را نشان می‌دهد.

> [!NOTE]
> این خاصیت نشان‌دهنده نوع محتوای دریافت‌شده نیست. یک فایل `.css` می‌تواند با استفاده از عنصر {{HTMLElement("link")}} دریافت شود که در این صورت مقدار `initiatorType` برابر با `link` خواهد بود. هنگام بارگذاری تصاویر با استفاده از `background: url()` در یک فایل CSS، مقدار `initiatorType` برابر با `css` خواهد بود و نه `img`.

## مقدار

خاصیت `initiatorType` می‌تواند مقادیر زیر را داشته باشد، یا اگر هیچ‌کدام از شرایط مطابقت نداشتند، مقدار `other` را.

- `audio`
  - : اگر درخواست توسط ویژگی `src` عنصر {{HTMLElement("audio")}} آغاز شده باشد.
- `beacon`
  - : اگر درخواست توسط روش {{domxref("navigator.sendBeacon()")}} آغاز شده باشد.
- `body`
  - : اگر درخواست توسط ویژگی `background` عنصر {{HTMLElement("body")}} آغاز شده باشد.
- `css`
  - : اگر درخواست توسط تابع `url()` در CSS آغاز شده باشد.
- `early-hint`
  - : اگر درخواست توسط پاسخ {{HTTPStatus("103")}} `Early Hint` آغاز شده باشد.
- `embed`
  - : اگر درخواست توسط ویژگی `src` عنصر {{HTMLElement("embed")}} آغاز شده باشد.
- `fetch`
  - : اگر درخواست توسط روش {{domxref("Window/fetch", "fetch()")}} آغاز شده باشد.
- `frame`
  - : اگر درخواست با بارگذاری یک عنصر {{HTMLElement("frame")}} آغاز شده باشد.
- `iframe`
  - : اگر درخواست توسط ویژگی `src` عنصر {{HTMLElement("iframe")}} آغاز شده باشد.
- `icon` {{non-standard_inline}}
  - : اگر درخواست توسط favicon آغاز شده باشد. غیراستاندارد و فقط توسط Safari گزارش می‌شود.
- `image`
  - : اگر درخواست توسط عنصر {{SVGElement("image")}} آغاز شده باشد.
- `img`
  - : اگر درخواست توسط ویژگی `src` یا `srcset` عنصر {{HTMLElement("img")}} آغاز شده باشد.
- `input`
  - : اگر درخواست توسط عنصر {{HTMLElement("input")}} از نوع `image` آغاز شده باشد.
- `link`
  - : اگر درخواست توسط عنصر {{HTMLElement("link")}} آغاز شده باشد.
- `navigation`
  - : اگر درخواست توسط یک درخواست ناوبری آغاز شده باشد.
- `object`
  - : اگر درخواست توسط عنصر {{HTMLElement("object")}} آغاز شده باشد.
- `ping`
  - : اگر درخواست توسط ویژگی `ping` عنصر {{HTMLElement("a")}} آغاز شده باشد.
- `script`
  - : اگر درخواست توسط عنصر {{HTMLElement("script")}} آغاز شده باشد.
- `track`
  - : اگر درخواست توسط ویژگی `src` عنصر {{HTMLElement("track")}} آغاز شده باشد.
- `video`
  - : اگر درخواست توسط ویژگی `poster` یا `src` عنصر {{HTMLElement("video")}} آغاز شده باشد.
- `xmlhttprequest`
  - : اگر درخواست توسط {{domxref("XMLHttpRequest")}} آغاز شده باشد.

## مثال‌ها

### فیلتر کردن منابع

از خاصیت `initiatorType` می‌توان برای دریافت فقط برخی از ورودی‌های زمان‌بندی منابع استفاده کرد. به عنوان مثال، فقط آن‌هایی که توسط عناصر {{HTMLElement("script")}} آغاز شده‌اند.

مثال با استفاده از {{domxref("PerformanceObserver")}}، که با ثبت شدن ورودی‌های جدید عملکرد `resource` در خط زمانی عملکرد مرورگر، آن‌ها را اطلاع‌رسانی می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد observer استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  const scripts = list
    .getEntries()
    .filter((entry) => entry.initiatorType === "script");
  console.log(scripts);
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}}، که فقط ورودی‌های عملکرد `resource` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی این روش نشان می‌دهد:

```js
const scripts = performance
  .getEntriesByType("resource")
  .filter((entry) => entry.initiatorType === "script");
console.log(scripts);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}