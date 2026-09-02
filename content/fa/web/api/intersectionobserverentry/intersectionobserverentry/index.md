---
title: "IntersectionObserverEntry: IntersectionObserverEntry() constructor"
short-title: IntersectionObserverEntry()
slug: Web/API/IntersectionObserverEntry/IntersectionObserverEntry
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.IntersectionObserverEntry.IntersectionObserverEntry
---

{{APIRef("Intersection Observer API")}}{{SeeCompatTable}}

سازنده **`IntersectionObserverEntry()`** یک شیء جدید از نوع {{domxref("IntersectionObserverEntry")}} ایجاد و بازمی‌گرداند.

> [!NOTE] در استفاده معمول، نیازی به فراخوانی دستی این سازنده ندارید. اشیاء `IntersectionObserverEntry` به‌طور خودکار توسط مرورگر ایجاد شده و در زمان مشاهده یک تقاطع به callback {{domxref("IntersectionObserver")}} تحویل داده می‌شوند، یا توسط {{domxref("IntersectionObserver.takeRecords()")}} بازگردانده می‌شوند.

## Syntax

```js-nolint
new IntersectionObserverEntry(intersectionObserverEntryInit)
```

### پارامترها

- `intersectionObserverEntryInit`
  - : یک شیء با ویژگی‌های زیر که همگی الزامی هستند:
    - `boundingClientRect`
      - : یک شیء که مکان و ابعاد مستطیل محدودکننده عنصر هدف را مشخص می‌کند، با ویژگی‌های `x`، `y`، `width` و `height`. این معادل مستطیلی است که توسط {{domxref("Element.getBoundingClientRect()")}} بازگردانده می‌شود.
    - `intersectionRatio`
      - : یک عدد که نسبت مساحت `intersectionRect` به مساحت `boundingClientRect` را نشان می‌دهد. اگر مساحت `boundingClientRect` صفر باشد، این مقدار در صورت `true` بودن `isIntersecting` برابر 1 و در غیر این صورت 0 است.
    - `intersectionRect`
      - : یک شیء که مکان و ابعاد ناحیه قابل مشاهده هدف درون مستطیل تقاطع ریشه را مشخص می‌کند، با ویژگی‌های `x`، `y`، `width` و `height`.
    - `isIntersecting`
      - : یک مقدار بولی که اگر عنصر هدف با ریشه observer تقاطع داشته باشد `true` است، در غیر این صورت `false`.
    - `isVisible`
      - : یک مقدار بولی که اگر عنصر هدف کاملاً قابل مشاهده و بدون پوشش (unoccluded) تشخیص داده شده باشد و هیچ افکت بصری که نمایش آن را روی صفحه تغییر دهد نداشته باشد، `true` است. مقدار `false` به این معنی است که یا دید هدف کاهش یافته است یا این تشخیص امکان‌پذیر نبوده است.
    - `rootBounds`
      - : یک شیء که مکان و ابعاد مستطیل تقاطع ریشه را مشخص می‌کند، با ویژگی‌های `x`، `y`، `width` و `height`، یا `null`.
    - `target`
      - : عنصر {{domxref("Element")}} که تقاطع آن با ریشه تغییر کرده است.
    - `time`
      - : یک {{domxref("DOMHighResTimeStamp")}} که زمان ثبت تقاطع را نشان می‌دهد، نسبت به [مبدأ زمانی](/en-US/docs/Web/API/Performance/timeOrigin) `IntersectionObserver`.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("IntersectionObserverEntry")}} که ویژگی‌های آن با مقادیر مشخص شده در `intersectionObserverEntryInit` مقداردهی اولیه می‌شوند.

## مثال‌ها

### ایجاد یک IntersectionObserverEntry

این مثال یک `IntersectionObserverEntry` پایه ایجاد می‌کند که یک عنصر کاملاً قابل مشاهده را توصیف می‌کند. اگرچه می‌توانید به صورت دستی یک ورودی مانند این بسازید، در عمل این اشیاء توسط مرورگر ایجاد شده و به طور خودکار به callback {{domxref("IntersectionObserver")}} شما ارسال می‌شوند.

```js
const entry = new IntersectionObserverEntry({
  time: performance.now(),
  rootBounds: { x: 0, y: 0, width: 1024, height: 768 },
  boundingClientRect: { x: 10, y: 20, width: 200, height: 100 },
  intersectionRect: { x: 10, y: 20, width: 200, height: 100 },
  isIntersecting: true,
  isVisible: false,
  intersectionRatio: 1.0,
  target: document.body,
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- {{domxref("IntersectionObserverEntry")}}
- {{domxref("IntersectionObserver")}}
- [Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API)