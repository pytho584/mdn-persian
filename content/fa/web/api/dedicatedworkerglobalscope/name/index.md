---
title: "DedicatedWorkerGlobalScope: name property"
short-title: name
slug: Web/API/DedicatedWorkerGlobalScope/name
page-type: web-api-instance-property
browser-compat: api.DedicatedWorkerGlobalScope.name
---

{{APIRef("Web Workers API")}}{{AvailableInWorkers("dedicated")}}

ویژگی فقط‌خواندنی **`name`** در رابط {{domxref("DedicatedWorkerGlobalScope")}} نامی را برمی‌گرداند که (به‌صورت اختیاری) هنگام ایجاد {{domxref("Worker")}} به آن داده شده است. این همان نامی است که سازندهٔ {{domxref("Worker.Worker", "Worker()")}} می‌تواند برای دریافت ارجاع به {{domxref("DedicatedWorkerGlobalScope")}} ارسال کند.

## مقدار

یک رشته.

## مثال‌ها

اگر یک worker با استفاده از سازنده‌ای با گزینهٔ `name` ایجاد شود:

```js
const myWorker = new Worker("worker.js", { name: "myWorker" });
```

در این صورت {{domxref("DedicatedWorkerGlobalScope")}} نامی برابر با "myWorker" خواهد داشت که با اجرای:

```js
self.name;
```

از داخل worker قابل بازگرداندن است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DedicatedWorkerGlobalScope")}}