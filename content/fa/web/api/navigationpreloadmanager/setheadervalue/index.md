---
title: "NavigationPreloadManager: setHeaderValue() method"
short-title: setHeaderValue()
slug: Web/API/NavigationPreloadManager/setHeaderValue
page-type: web-api-instance-method
browser-compat: api.NavigationPreloadManager.setHeaderValue
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`setHeaderValue()`** در رابط {{domxref("NavigationPreloadManager")}} مقدار هدر {{HTTPHeader("Service-Worker-Navigation-Preload")}} را تنظیم می‌کند که با درخواست‌های ناشی از عملیات {{domxref("Window/fetch", "fetch()")}} در حین پیش‌بارگذاری ناوبری سرویس‌ورکر ارسال می‌شود. این متد یک {{jsxref("Promise")}} خالی برمی‌گرداند که با `undefined` حل می‌شود.

حضور هدر {{HTTPHeader("Service-Worker-Navigation-Preload")}} در درخواست‌های پیش‌بارگذاری به سرورها امکان می‌دهد تا منبع برگشتی را برای درخواست‌های پیش‌بارگذاری به شکلی متفاوت از درخواست‌های عادی پیکربندی کنند. مقدار پیش‌فرض این دستور `true` است؛ این متد امکان پیکربندی چندین پاسخ متفاوت به درخواست‌های پیش‌بارگذاری را فراهم می‌کند.

> [!NOTE]
> اگر تنظیم این هدر ممکن است پاسخ متفاوتی ایجاد کند، سرور باید `Vary: Service-Worker-Navigation-Preload` را تنظیم کند تا اطمینان حاصل شود که پاسخ‌های متفاوت در حافظه پنهان ذخیره می‌شوند.

## نحو (Syntax)

```js-nolint
setHeaderValue(value)
```

### پارامترها

- `value`
  - : یک رشته دلخواه که سرور مقصد از آن برای تعیین اینکه چه چیزی برای منبع درخواست‌شده برگردانده شود، استفاده می‌کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref('undefined')}} حل می‌شود.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : هیچ worker فعالی با ثبت (registration) مرتبط با این {{domxref("NavigationPreloadManager")}} وجود ندارد.

## مثال‌ها

کد زیر نحوه تنظیم مقدار را نشان می‌دهد.

```js
navigator.serviceWorker.ready
  .then((registration) =>
    registration.navigationPreload.setHeaderValue(newValue),
  )
  .then(() => console.log("Done!"))
  .catch((e) =>
    console.error(`NavigationPreloadManager not supported: ${e.message}`),
  );
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}