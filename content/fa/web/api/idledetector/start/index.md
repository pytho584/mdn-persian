---
title: "IdleDetector: start() method"
---

---
title: "IdleDetector: start() method"
short-title: start()
slug: Web/API/IdleDetector/start
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.IdleDetector.start
---

{{securecontext_header}}{{APIRef("Idle Detection API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`start()`** در رابط {{domxref("IdleDetector")}} یک {{jsxref("Promise")}} برمی‌گرداند که وقتی تشخیص‌دهنده شروع به گوش دادن به تغییرات وضعیت بیکاری کاربر می‌کند، حل می‌شود. این متد یک شیء اختیاری `options` می‌پذیرد که شامل `threshold` بر حسب میلی‌ثانیه برای گزارش بیکاری و `signal` برای یک `AbortSignal` به منظور لغو تشخیص بیکاری است.

## نحو

```js-nolint
start()
start(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `threshold`
      - : حداقل تعداد میلی‌ثانیه‌های بیکاری پیش از شروع گزارش‌دهی.
    - `signal`
      - : ارجاعی به یک نمونه {{domxref('AbortSignal')}} که به شما امکان لغو تشخیص بیکاری را می‌دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}}.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.

## مثال‌ها

مثال زیر نحوه شروع تشخیص بیکاری را با استفاده از آرگومان `options` نشان می‌دهد. این مثال یک نمونه `AbortSignal` را از یک نمونه {{domxref("AbortController")}} می‌گیرد.

```js
const controller = new AbortController();
const signal = controller.signal;

await idleDetector.start({
  threshold: 60_000,
  signal,
});
console.log("IdleDetector is active.");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}