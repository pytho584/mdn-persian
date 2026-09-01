---
title: "DedicatedWorkerGlobalScope: close() method"
short-title: close()
slug: Web/API/DedicatedWorkerGlobalScope/close
page-type: web-api-instance-method
browser-compat: api.DedicatedWorkerGlobalScope.close
---

{{APIRef("Web Workers API")}}{{AvailableInWorkers("dedicated")}}

متد **`close()`** در رابط {{domxref("DedicatedWorkerGlobalScope")}}، هر وظیفه‌ای را که در حلقه رویداد (event loop) `DedicatedWorkerGlobalScope` صف شده است دور می‌ریزد و عملاً این محدوده (scope) خاص را می‌بندد.

## نحو (Syntax)

```js-nolint
close()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچکدام ({{jsxref("undefined")}}).

## مثال‌ها

اگر می‌خواهید نمونه worker خود را از داخل خود worker ببندید، می‌توانید کد زیر را فراخوانی کنید:

```js
close();
```

`close()` و `self.close()` عملاً معادل هستند – هر دو نشان‌دهنده فراخوانی `close()` از داخل محدوده داخلی worker هستند.

> [!NOTE]
> یک راه دیگر برای متوقف کردن worker از رشته اصلی (main thread) وجود دارد: متد {{domxref("Worker.terminate")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- {{domxref("DedicatedWorkerGlobalScope")}}