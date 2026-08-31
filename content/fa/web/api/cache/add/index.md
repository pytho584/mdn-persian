---
title: "Cache: add() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Cache/add"
translated_by: "n8n + AI"
---

---
title: "Cache: add() method"
short-title: add()
slug: Web/API/Cache/add
page-type: web-api-instance-method
browser-compat: api.Cache.add
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

روش **`add()`** از رابط {{domxref("Cache")}} یک URL می‌گیرد، آن را بازیابی می‌کند، و شیء پاسخ حاصل را به کش داده‌شده اضافه می‌کند.

روش `add()` از نظر عملکردی معادل کد زیر است:

```js
fetch(url).then((response) => {
  if (!response.ok) {
    throw new TypeError("bad response status");
  }
  return cache.put(url, response);
});
```

برای عملیات پیچیده‌تر، باید مستقیماً از {{domxref("Cache.put","Cache.put()")}} استفاده کنید.

> [!NOTE]
> `add()` هر جفت کلید/مقداری را که قبلاً در کش ذخیره شده و با درخواست مطابقت دارد، بازنویسی می‌کند.

## نحو

```js-nolint
add(request)
```

### پارامترها

- `request`
  - : درخواستی برای منبعی که می‌خواهید به کش اضافه کنید. این می‌تواند یک شیء {{domxref("Request")}} یا یک URL باشد.

    این پارامتر به عنوان پارامتری برای سازنده {{domxref("Request.Request()", "Request()")}} استفاده می‌شود، بنابراین URLها از همان قوانین آن سازنده پیروی می‌کنند. به‌طور خاص، URLها می‌توانند نسبت به URL پایه نسبی باشند، که {{domxref("Node.baseURI", "baseURI")}} سند در زمینه پنجره، یا {{domxref("WorkerGlobalScope.location")}} در زمینه کارگر است.

### مقدار برگشتی

یک {{jsxref("Promise")}} که با `undefined` حل می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : طرح URL `http` یا `https` نیست.

    وضعیت Response در محدوده ۲۰۰ نیست (یعنی پاسخ موفق نیست). این اتفاق می‌افتد اگر درخواست با موفقیت برنگردد، همچنین اگر درخواست یک درخواست _cross-origin no-cors_ باشد (در این صورت وضعیت گزارش‌شده همیشه ۰ است).

## مثال‌ها

این بلوک کد منتظر می‌ماند تا یک {{domxref("InstallEvent")}} فعال شود، سپس {{domxref("ExtendableEvent.waitUntil","waitUntil()")}} را برای مدیریت فرآیند نصب برنامه فراخوانی می‌کند. این شامل فراخوانی {{domxref("CacheStorage.open")}} برای ایجاد یک کش جدید، سپس استفاده از `Cache.add` برای افزودن یک دارایی به آن است.

```js
this.addEventListener("install", (event) => {
  event.waitUntil(caches.open("v1").then((cache) => cache.add("/index.html")));
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} و {{domxref("WorkerGlobalScope.caches")}}