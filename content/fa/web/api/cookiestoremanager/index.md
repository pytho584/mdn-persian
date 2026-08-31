---
title: CookieStoreManager
slug: Web/API/CookieStoreManager
page-type: web-api-interface
browser-compat: api.CookieStoreManager
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}{{AvailableInWorkers("window_and_service")}}

رابط **`CookieStoreManager`** از {{domxref("Cookie Store API", "", "", "nocode")}} به سرویس‌ورکرها اجازه می‌دهد تا در رویدادهای تغییر کوکی مشترک شوند. برای دریافت رویدادهای تغییر، متد {{domxref("CookieStoreManager.subscribe()","subscribe()")}} را روی یک ثبت‌نام سرویس‌ورکر خاص فراخوانی کنید.

یک `CookieStoreManager` دارای یک {{domxref("ServiceWorkerRegistration")}} مرتبط است. هر ثبت‌نام سرویس‌ورکر یک لیست اشتراک تغییر کوکی دارد که شامل لیستی از اشتراک‌های تغییر کوکی است و هر اشتراک شامل یک نام و یک URL می‌باشد. متدهای این رابط به سرویس‌ورکر اجازه می‌دهند تا اشتراک‌ها را به این لیست اضافه یا از آن حذف کند، و همچنین لیست تمام اشتراک‌ها را دریافت کند.

برای دریافت یک `CookieStoreManager`، متد {{domxref("ServiceWorkerRegistration.cookies")}} را فراخوانی کنید.

## متدهای نمونه

- {{domxref("CookieStoreManager.getSubscriptions()")}}
  - یک {{jsxref("Promise")}} برمی‌گرداند که به لیستی از اشتراک‌های تغییر کوکی برای این ثبت‌نام سرویس‌ورکر resolutions می‌شود.
- {{domxref("CookieStoreManager.subscribe()")}}
  - در تغییرات کوکی مشترک می‌شود. یک {{jsxref("Promise")}} برمی‌گرداند که هنگام موفقیت اشتراک resolutions می‌شود.
- {{domxref("CookieStoreManager.unsubscribe()")}}
  - سرویس‌ورکر ثبت‌شده را از تغییرات کوکی لغو اشتراک می‌کند. یک {{jsxref("Promise")}} برمی‌گرداند که هنگام موفقیت عملیات resolutions می‌شود.

## مثال‌ها

در این مثال، {{domxref("ServiceWorkerRegistration")}} که با `registration` نمایش داده می‌شود، در رویدادهای تغییر کوکی به نام `"cookie1"` با محدوده `"/path1"` مشترک می‌شود.

```js
const subscriptions = [{ name: "cookie1", url: `/path1` }];
await registration.cookies.subscribe(subscriptions);
```

اگر {{domxref("ServiceWorkerRegistration")}} در هر کوکی مشترک شده باشد، آنگاه {{domxref("CookieStoreManager.getSubscriptions()","getSubscriptions()")}} لیستی از کوکی‌ها را برمی‌گرداند که با اشیایی در همان قالب اشتراک اصلی نمایش داده می‌شوند.

```js
const subscriptions = await self.registration.cookies.getSubscriptions();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}