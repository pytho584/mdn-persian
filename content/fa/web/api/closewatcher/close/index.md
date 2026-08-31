---
title: "CloseWatcher: close() method"
short-title: close()
slug: Web/API/CloseWatcher/close
page-type: web-api-instance-method
browser-compat: api.CloseWatcher.close
---

{{APIRef("HTML DOM")}}

متد **`close()`** از رابط {{domxref("CloseWatcher")}} به شما امکان می‌دهد تا هر منطقی را در کنترل‌کننده رویداد `cancel` نادیده گرفته و بلافاصله رویداد `close` را فعال کنید. سپس، watcher بسته شدن را غیرفعال می‌کند، گویی که متد `destroy()` فراخوانی شده است.

## نحو

```js-nolint
close()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچکدام ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده از متد `close()`

از متد `close()` برای غیرفعال کردن watcher بسته شدن و نابود کردن آن استفاده کنید.

```js
watcher.close();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}