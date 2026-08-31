---
title: "Cache: delete() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Cache/delete"
translated_by: "n8n + AI"
---

---
title: "Cache: delete() method"
short-title: delete()
slug: Web/API/Cache/delete
page-type: web-api-instance-method
browser-compat: api.Cache.delete
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`delete()`** از رابط {{domxref("Cache")}}، ورودی مربوط به {{domxref("Cache")}} را که کلیدش درخواست است پیدا می‌کند و در صورت یافتن، آن ورودی {{domxref("Cache")}} را حذف کرده و یک {{jsxref("Promise")}} برمی‌گرداند که به `true` resolve می‌شود. اگر هیچ ورودی {{domxref("Cache")}} یافت نشود، به `false` resolve می‌شود.

## سینتکس

```js-nolint
delete(request)
delete(request, options)
```

### پارامترها

- `request`
  - : {{domxref("Request")}} که به دنبال حذف آن هستید.
    این می‌تواند یک شیء `Request` یا یک URL باشد.
- `options` {{optional_inline}}
  - : شیئی که ویژگی‌هایش نحوه تطبیق را در عملیات `delete` کنترل می‌کند.
    گزینه‌های موجود عبارت‌اند از:
    - `ignoreSearch`
      - : یک مقدار بولین که مشخص می‌کند آیا فرآیند تطبیق باید رشته جستجو (query string) در URL را نادیده بگیرد یا نه.
        اگر روی `true` تنظیم شود، بخش `?value=bar` از `https://example.com/?value=bar` هنگام انجام تطبیق نادیده گرفته می‌شود.
        مقدار پیش‌فرض `false` است.
    - `ignoreMethod`
      - : یک مقدار بولین که وقتی روی `true` تنظیم شود، از اعتبارسنجی متد `HTTP` در عملیات تطبیق جلوگیری می‌کند (به‌طور معمول فقط `GET` و `HEAD` مجاز هستند). مقدار پیش‌فرض `false` است.
    - `ignoreVary`
      - : یک مقدار بولین که وقتی روی `true` تنظیم شود، به عملیات تطبیق می‌گوید که تطبیق هدر `VARY` را انجام ندهد. به عبارت دیگر، اگر URL مطابقت داشته باشد، بدون توجه به اینکه شیء {{domxref("Response")}} هدر `VARY` داشته باشد یا نه، تطبیق انجام می‌شود. مقدار پیش‌فرض `false` است.
    - `cacheName`
      - : یک رشته که نمایانگر یک کش خاص برای جستجو در آن است. توجه داشته باشید که این گزینه توسط `Cache.delete()` نادیده گرفته می‌شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که اگر ورودی کش حذف شود به `true` resolve می‌شود، و در غیر این صورت به `false` resolve می‌شود.

## مثال‌ها

```js
caches
  .open("v1")
  .then((cache) => cache.delete("/images/image.png"))
  .then((response) => {
    someUIUpdateFunction();
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}