---
title: "Cache: addAll() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Cache/addAll"
translated_by: "n8n + AI"
---

---
title: "Cache: addAll() method"
short-title: addAll()
slug: Web/API/Cache/addAll
page-type: web-api-instance-method
browser-compat: api.Cache.addAll
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`addAll()`** در رابط {{domxref("Cache")}} یک آرایه از URL‌ها را دریافت می‌کند، آن‌ها را بازیابی می‌کند و اشیای پاسخ حاصل را به حافظه‌نهان (cache) داده شده اضافه می‌کند. اشیای درخواست ایجاد شده در طول بازیابی به عنوان کلیدهای عملیات پاسخ ذخیره شده عمل می‌کنند.

> [!NOTE]
> `addAll()` هر جفت کلید/مقداری را که قبلاً در حافظه‌نهان ذخیره شده و با درخواست مطابقت دارد، بازنویسی می‌کند، اما اگر یک عملیات `put()` حاصل بخواهد یک ورودی حافظه‌نهان قبلی که توسط همان متد `addAll()` ذخیره شده است را بازنویسی کند، شکست می‌خورد.

## نحو

```js-nolint
addAll(requests)
```

### پارامترها

- `requests`
  - : آرایه‌ای از درخواست‌ها برای منابعی که می‌خواهید به حافظه‌نهان اضافه کنید. این‌ها می‌توانند اشیای {{domxref("Request")}} یا URL باشند.

    این درخواست‌ها به عنوان پارامترهای سازنده {{domxref("Request.Request()", "Request()")}} استفاده می‌شوند، بنابراین URL‌ها از همان قوانین آن سازنده پیروی می‌کنند. به طور خاص، URL‌ها ممکن است نسبت به URL پایه (base URL) نسبی باشند که در بافت پنجره (window) {{domxref("Node.baseURI", "baseURI")}} سند و در بافت کارگر (worker) {{domxref("WorkerGlobalScope.location")}} است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با `undefined` حل می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : طرح URL (scheme) `http` یا `https` نیست.

    وضعیت پاسخ در محدوده ۲۰۰ نیست (یعنی پاسخ موفقیت‌آمیز نیست). این اتفاق زمانی می‌افتد که درخواست با موفقیت بازگردانده نشود، همچنین اگر درخواست به صورت _cross-origin no-cors_ باشد (در این صورت وضعیت گزارش شده همیشه ۰ است).

## مثال‌ها

این بلوک کد منتظر می‌ماند تا یک {{domxref("InstallEvent")} رخ دهد، سپس {{domxref("ExtendableEvent.waitUntil","waitUntil()")}} را برای مدیریت فرآیند نصب برنامه اجرا می‌کند. این شامل فراخوانی {{domxref("CacheStorage.open")}} برای ایجاد یک حافظه‌نهان جدید و سپس استفاده از `addAll()` برای افزودن مجموعه‌ای از دارایی‌ها به آن است.

```js
this.addEventListener("install", (event) => {
  event.waitUntil(
    caches
      .open("v1")
      .then((cache) =>
        cache.addAll([
          "/",
          "/index.html",
          "/style.css",
          "/app.js",
          "/image-list.js",
          "/star-wars-logo.jpg",
          "/gallery/",
          "/gallery/bountyHunters.jpg",
          "/gallery/myLittleVader.jpg",
          "/gallery/snowTroopers.jpg",
        ]),
      ),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} and {{domxref("WorkerGlobalScope.caches")}}