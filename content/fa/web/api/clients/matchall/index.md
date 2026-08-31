---
title: "Clients: matchAll() method"
short-title: matchAll()
slug: Web/API/Clients/matchAll
page-type: web-api-instance-method
browser-compat: api.Clients.matchAll
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

متد **`matchAll()`** از رابط {{domxref("Clients")}} یک {{jsxref("Promise")}} برای فهرستی از اشیاء {{domxref("Client")}} سرویس‌ورکر برمی‌گرداند. پارامتر `options` را برای بازگرداندن تمام کلاینت‌های سرویس‌ورکر که مبدأ آن‌ها با مبدأ سرویس‌ورکر مرتبط یکسان است، وارد کنید. اگر گزینه‌ای وارد نشود، متد تنها کلاینت‌های سرویس‌ورکر تحت کنترل سرویس‌ورکر را برمی‌گرداند.

## نحو

```js-nolint
matchAll()
matchAll(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء گزینه که به شما امکان می‌دهد گزینه‌هایی برای عملیات تطبیق تنظیم کنید. گزینه‌های موجود عبارتند از:
    - `includeUncontrolled`
      - : یک مقدار بولین — اگر روی `true` تنظیم شود، عملیات تطبیق تمام کلاینت‌های سرویس‌ورکر که مبدأ یکسانی با سرویس‌ورکر جاری دارند را برمی‌گرداند. در غیر این صورت، تنها کلاینت‌های سرویس‌ورکر تحت کنترل سرویس‌ورکر جاری را برمی‌گرداند. مقدار پیش‌فرض `false` است.
    - `type`
      - : نوع کلاینت‌هایی را که می‌خواهید مطابقت داده شوند، تنظیم می‌کند. مقادیر موجود عبارتند از `"window"`، `"worker"`، `"sharedworker"` و `"all"`. مقدار پیش‌فرض `"window"` است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک آرایه از اشیاء {{domxref("Client")}} حل می‌شود. در کروم ۴۶/فایرفاکس ۵۴ و بعد از آن، این متد کلاینت‌ها را به ترتیب آخرین فوکوس شده برمی‌گرداند که مطابق با مشخصات است.

## نمونه‌ها

```js
clients.matchAll(options).then((clientList) => {
  for (const client of clientList) {
    if (client.url === "index.html") {
      clients.openWindow(client);
      // or do something else involving the matching client
    }
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}