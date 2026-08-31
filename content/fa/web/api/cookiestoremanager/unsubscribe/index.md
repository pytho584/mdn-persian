---
title: "CookieStoreManager: unsubscribe() method"
short-title: unsubscribe()
slug: Web/API/CookieStoreManager/unsubscribe
page-type: web-api-instance-method
browser-compat: api.CookieStoreManager.unsubscribe
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

متد **`unsubscribe()`** از رابط {{domxref("CookieStoreManager")}}، ثبت‌نام {{domxref("ServiceWorkerRegistration")}} را از دریافت رویدادهای پیش‌تر مشترک‌شده متوقف می‌کند.

## نحو (Syntax)

```js-nolint
unsubscribe(subscriptions)
```

### پارامترها

- `subscriptions`
  - : یک لیست از اشیاء که هر کدام شامل موارد زیر است:
    - `name`
      - : یک رشته شامل نام یک کوکی.
    - `url`
      - : یک رشته شامل URL محدوده (scope) که برای اشتراک در این کوکی استفاده شده است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} حل می‌شود زمانی که سرویس‌ورکر لغو اشتراک شده است.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر URL ارسال‌شده در `subscriptions` با {{domxref("ServiceWorkerRegistration.scope","scope")}} ثبت‌نام سرویس‌ورکر مطابقت نداشته باشد، پرتاب می‌شود.

## مثال‌ها

در این مثال، {{domxref("ServiceWorkerRegistration")}} که با `registration` نشان داده شده است، از تغییرات روی کوکی با نام `"cookie1"` و محدوده `"/path1"` لغو اشتراک می‌کند.

```js
const subscriptions = [{ name: "cookie1", url: `/path1` }];
await registration.cookies.unsubscribe(subscriptions);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}