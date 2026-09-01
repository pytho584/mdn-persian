---
title: "FetchEvent: FetchEvent() constructor"
short-title: FetchEvent()
slug: Web/API/FetchEvent/FetchEvent
page-type: web-api-constructor
browser-compat: api.FetchEvent.FetchEvent
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

سازندهٔ **`FetchEvent()`** یک شیء جدید {{domxref("FetchEvent")}} می‌سازد.

## نحو

```js-nolint
new FetchEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد. به بزرگی و کوچکی حروف حساس است و مرورگرها همیشه آن را روی `fetch` قرار می‌دهند.
- `options`
  - : شیئی که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `request`
      - : شیء {{domxref("Request")}} که باعث فعال شدن کنترل‌کنندهٔ رویداد می‌شود.
    - `preloadResponse`
      - : یک {{jsxref("Promise")}} که پاسخ بارگذاری‌شدهٔ قبلی را به کلاینت بازمی‌گرداند.
    - `clientId` {{optional_inline}}
      - : {{domxref("Client")}} که سرویس‌ورکر فعلی آن را کنترل می‌کند. پیش‌فرض آن `""` است.
    - `isReload` {{deprecated_inline}} {{optional_inline}}
      - : یک مقدار بولین که نشان می‌دهد هنگام ارسال رویداد، صفحه بارگذاری مجدد شده است یا نه. اگر بله `true` و اگر نه `false`. به‌طور معمول، فشردن دکمهٔ بازنشانی (refresh) در مرورگر بارگذاری مجدد است، در حالی که کلیک روی یک پیوند و فشردن دکمهٔ بازگشت (back) این‌گونه نیست. اگر وجود نداشته باشد، پیش‌فرض `false` است.
    - `replacesClientId` {{optional_inline}}
      - : رشته‌ای که کلاینتی را که توسط `resultingClientId` جایگزین می‌شود، مشخص می‌کند. پیش‌فرض آن `""` است.
    - `resultingClientId` {{optional_inline}}
      - : رشته‌ای حاوی `clientId` جدید، اگر در نتیجهٔ بارگذاری صفحه، کلاینت تغییر کند. پیش‌فرض آن `""` است.
    - `handled`
      - : یک promise _در حالت انتظار_ که پس از مدیریت شدن رویداد، fulfilled (برآورده) می‌شود.

### مقدار بازگشتی

یک شیء جدید {{domxref("FetchEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## جستارهای وابسته

- {{jsxref("Promise")}}
- [Fetch API](/en-US/docs/Web/API/Fetch_API)