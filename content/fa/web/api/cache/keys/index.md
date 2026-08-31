---
title: "Cache: keys() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Cache/keys"
translated_by: "n8n + AI"
---

---
title: "Cache: keys() method"
short-title: keys()
slug: Web/API/Cache/keys
page-type: web-api-instance-method
browser-compat: api.Cache.keys
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`keys()`** از رابط {{domxref("Cache")}} یک {{jsxref("Promise")}} را برمی‌گرداند که به آرایه‌ای از اشیاء {{domxref("Request")}} تبدیل می‌شود و کلیدهای {{domxref("Cache")}} را نشان می‌دهد.

درخواست‌ها به همان ترتیبی که درج شده‌اند بازگردانده می‌شوند.

> [!NOTE]
> اگر پاسخ‌های درخواست‌هایی با URL‌های تکراری اما هدرهای متفاوت، هدر `VARY` را تنظیم کرده باشند، می‌توانند بازگردانده شوند.

## Syntax

```js-nolint
keys()
keys(request)
keys(request, options)
```

### Parameters

- `request` {{optional_inline}}
  - : {{domxref("Request")}} مورد نظر برای بازگرداندن، در صورت نیاز به یک کلید خاص. این می‌تواند یک شیء `Request` یا یک URL باشد.
- `options` {{optional_inline}}
  - : یک شیء که ویژگی‌های آن نحوه تطبیق در عملیات `keys` را کنترل می‌کند. گزینه‌های موجود عبارتند از:
    - `ignoreSearch`
      - : یک مقدار بولی که مشخص می‌کند آیا فرآیند تطبیق باید رشته جستجو در URL را نادیده بگیرد. اگر روی `true` تنظیم شود، قسمت `?value=bar` از `https://example.com/?value=bar` هنگام انجام تطبیق نادیده گرفته می‌شود. مقدار پیش‌فرض `false` است.
    - `ignoreMethod`
      - : یک مقدار بولی که وقتی روی `true` تنظیم شود، از اعتبارسنجی متد {{domxref("Request")}} `HTTP` توسط عملیات تطبیق جلوگیری می‌کند (معمولاً فقط `GET` و `HEAD` مجاز هستند). مقدار پیش‌فرض `false` است.
    - `ignoreVary`
      - : یک مقدار بولی که وقتی روی `true` تنظیم شود، به عملیات تطبیق می‌گوید که تطبیق هدر `VARY` را انجام ندهد. به عبارت دیگر، اگر URL مطابقت داشته باشد، بدون توجه به اینکه شیء {{domxref("Response")}} هدر `VARY` داشته باشد، تطبیق انجام می‌شود. مقدار پیش‌فرض `false` است.
    - `cacheName`
      - : یک رشته که یک کش خاص را برای جستجو در آن مشخص می‌کند. توجه داشته باشید که این گزینه توسط `Cache.keys()` نادیده گرفته می‌شود.

### Return value

یک {{jsxref("Promise")}} که به آرایه‌ای از اشیاء {{domxref("Request")}} تبدیل می‌شود.

## Examples

```js
caches
  .open("v1")
  .then((cache) => cache.keys())
  .then((keys) => {
    keys.forEach((request, index, array) => {
      cache.delete(request);
    });
  });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}