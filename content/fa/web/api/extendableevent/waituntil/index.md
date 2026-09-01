---
title: "ExtendableEvent: waitUntil() method"
short-title: waitUntil()
slug: Web/API/ExtendableEvent/waitUntil
page-type: web-api-instance-method
browser-compat: api.ExtendableEvent.waitUntil
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

متد **`ExtendableEvent.waitUntil()`** به توزیع‌کنندهٔ رویداد (event dispatcher) اعلام می‌کند که کار همچنان در جریان است. همچنین می‌توان از آن برای تشخیص موفقیت‌آمیز بودن آن کار استفاده کرد. در service workerها، `waitUntil()` به مرورگر می‌گوید که کار تا زمانی که promise تعیین تکلیف شود (settle شود) ادامه دارد و اگر مرورگر می‌خواهد آن کار تکمیل شود، نباید service worker را خاتمه دهد.

رویدادهای {{domxref("ServiceWorkerGlobalScope/install_event", "install")}} در [service workerها](/en-US/docs/Web/API/ServiceWorkerGlobalScope) از `waitUntil()` استفاده می‌کنند تا service worker را تا پایان یافتن کارها در مرحلهٔ {{domxref("ServiceWorkerRegistration.installing", "installing")}} نگه دارند. اگر promiseای که به `waitUntil()` داده شده رد شود (reject شود)، نصب ناموفق در نظر گرفته می‌شود و service worker در حال نصب کنار گذاشته می‌شود. این کار عمدتاً برای اطمینان از این انجام می‌شود که service worker تا زمانی که همهٔ کش‌های اصلی که به آن‌ها وابسته است با موفقیت پر نشده‌اند، نصب‌شده در نظر گرفته نشود.

رویدادهای {{domxref("ServiceWorkerGlobalScope/activate_event", "activate")}} در [service workerها](/en-US/docs/Web/API/ServiceWorkerGlobalScope) از `waitUntil()` استفاده می‌کنند تا رویدادهای عملکردی مانند `fetch` و `push` را تا زمانی که promise داده‌شده به `waitUntil()` تعیین تکلیف شود، بافر کنند. این کار به service worker فرصت می‌دهد تا ساختار پایگاه‌داده (database schema) را به‌روزرسانی کرده و کش‌های منسوخ ({{domxref("Cache", "caches")}}) را حذف کند تا سایر رویدادها بتوانند به وضعیت کاملاً ارتقایافته تکیه کنند.

متد `waitUntil()` باید برای نخستین بار در داخل callback رویداد فراخوانی شود؛ اما پس از آن می‌توان آن را چندین بار فراخوانی کرد، تا زمانی که همهٔ promiseهای داده‌شده به آن تعیین تکلیف شوند.

## نحو

```js-nolint
waitUntil(promise)
```

### پارامترها

- `promise`
  - : یک {{jsxref("Promise")}} که طول عمر رویداد را افزایش می‌دهد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

استفاده از `waitUntil()` در رویداد `install` یک service worker:

```js
addEventListener("install", (event) => {
  const preCache = async () => {
    const cache = await caches.open("static-v1");
    return cache.addAll(["/", "/about/", "/static/styles.css"]);
  };
  event.waitUntil(preCache());
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workerها](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)