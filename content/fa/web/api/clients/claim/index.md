---
title: "Clients: claim() method"
short-title: claim()
slug: Web/API/Clients/claim
page-type: web-api-instance-method
browser-compat: api.Clients.claim
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

متد **`claim()`** در رابط {{domxref("Clients")}} به یک service worker فعال اجازه می‌دهد تا خود را به‌عنوان {{domxref("ServiceWorkerContainer.controller", "کنترل‌کننده")}} برای همهٔ کلاینت‌های درون {{domxref("ServiceWorkerRegistration.scope", "حوزهٔ (scope)")}} خود تنظیم کند. این کار باعث می‌شود رویداد `controllerchange` روی {{domxref("ServiceWorkerContainer","navigator.serviceWorker")}} در هر کلاینتی که تحت کنترل این service worker قرار می‌گیرد، آغاز شود.

هنگامی که یک service worker برای اولین بار ثبت می‌شود، صفحات تا بارگذاری بعدی خود از آن استفاده نمی‌کنند. متد `claim()` باعث می‌شود آن صفحات بلافاصله تحت کنترل قرار گیرند. توجه داشته باشید که این کار سبب می‌شود service worker شما صفحاتی را کنترل کند که به‌طور عادی از طریق شبکه بارگذاری شده‌اند یا احتمالاً توسط یک service worker دیگر کنترل می‌شده‌اند.

## نحو

```js-nolint
claim()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به `undefined` resolve می‌شود.

## مثال‌ها

مثال زیر از `claim()` درون شنوندهٔ رویداد `activate` سرویس‌ورکر استفاده می‌کند تا کلاینت‌هایی که در همان حوزهٔ (scope) بارگذاری شده‌اند، پیش از اینکه درخواست‌هایشان از این سرویس‌ورکر عبور کند، نیازی به بارگذاری مجدد نداشته باشند.

```js
self.addEventListener("activate", (event) => {
  event.waitUntil(clients.claim());
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [چرخهٔ حیات سرویس‌ورکر](https://web.dev/articles/service-worker-lifecycle)
- {{domxref("ServiceWorkerGlobalScope.skipWaiting()", "self.skipWaiting()")}} - رد شدن از مرحلهٔ انتظار سرویس‌ورکر