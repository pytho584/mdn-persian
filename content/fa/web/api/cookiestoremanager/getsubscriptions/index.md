---
title: "CookieStoreManager: getSubscriptions() method"
short-title: getSubscriptions()
slug: Web/API/CookieStoreManager/getSubscriptions
page-type: web-api-instance-method
browser-compat: api.CookieStoreManager.getSubscriptions
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

متد **`getSubscriptions()`** در رابط {{domxref("CookieStoreManager")}} فهرستی از همهٔ اشتراک‌های تغییر کوکی مربوط به این {{domxref("ServiceWorkerRegistration")}} را برمی‌گرداند.

## Syntax

```js-nolint
getSubscriptions()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با فهرستی از اشیاء resolve می‌شود؛ هر شیء شامل:

- `name`
  - : یک رشته شامل نام یک کوکی.
- `url`
  - : یک رشته شامل URL محدوده‌ای (scope) که برای اشتراک‌گذاری در آن کوکی(ها) استفاده شده است.

## مثال‌ها

اگر {{domxref("ServiceWorkerRegistration")}} که با `registration` نمایش داده می‌شود، در هر رویداد تغییر کوکی مشترک شده باشد، `subscriptions` به فهرستی از اشیاء حاوی نام و URL آن کوکی‌ها resolve می‌شود.

```js
const subscriptions = await self.registration.cookies.getSubscriptions();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}