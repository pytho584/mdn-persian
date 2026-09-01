---
title: "DedicatedWorkerGlobalScope: postMessage() method"
short-title: postMessage()
slug: Web/API/DedicatedWorkerGlobalScope/postMessage
page-type: web-api-instance-method
browser-compat: api.DedicatedWorkerGlobalScope.postMessage
---

{{APIRef("Web Workers API")}}{{AvailableInWorkers("dedicated")}}

متد **`postMessage()`** از رابط {{domxref("DedicatedWorkerGlobalScope")}} پیامی را به ریسمان اصلی که آن را ایجاد کرده است می‌فرستد.

این متد یک پارامتر داده می‌پذیرد که حاوی داده‌هایی است که باید از worker به ریسمان اصلی کپی شوند. داده می‌تواند هر مقدار یا شیء جاوااسکریپتی باشد که الگوریتم [structured clone](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) از آن پشتیبانی می‌کند، شامل ارجاع‌های چرخه‌ای.

این متد همچنین یک آرایه اختیاری از [اشیاء قابل انتقال (transferable objects)](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) برای _انتقال_ به ریسمان اصلی می‌پذیرد. برخلاف پارامتر داده، اشیاء منتقل‌شده دیگر در ریسمان worker قابل استفاده نیستند. (در صورت امکان، اشیاء با استفاده از عملیات کپی صفر (zero-copy) با کارایی بالا منتقل می‌شوند).

ریسمان اصلی که worker را ایجاد کرده است نیز می‌تواند با استفاده از متد {{domxref("Worker.postMessage")}} اطلاعات را به worker بازگرداند.

## نحو

```js-nolint
postMessage(message)
postMessage(message, transfer)
postMessage(message, options)
```

### پارامترها

- `message`
  - : شیئی که باید به ریسمان اصلی تحویل داده شود؛ این شیء در فیلد `data` رویدادی که به رویداد {{domxref("Window/message_event", "message")}} تحویل داده می‌شود قرار خواهد گرفت. این می‌تواند هر مقدار یا شیء جاوااسکریپتی باشد که الگوریتم [structured clone](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) از آن پشتیبانی می‌کند، شامل ارجاع‌های چرخه‌ای.

- `transfer` {{optional_inline}}
  - : یک [آرایه](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) اختیاری از [اشیاء قابل انتقال (transferable objects)](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) برای انتقال مالکیت آن‌ها. مالکیت این اشیاء به سمت مقصد داده می‌شود و دیگر در سمت فرستنده قابل استفاده نیستند. این اشیاء قابل انتقال به‌طور خودکار ارسال نمی‌شوند؛ آن‌ها باید یا در پیام گنجانده شده باشند یا از طریق روش‌های دیگر در دسترس گیرنده قرار گیرند، مانند {{domxref("MessagePort")}} از طریق {{domxref("MessageEvent.ports")}}.

- `options` {{optional_inline}}
  - : یک شیء اختیاری حاوی ویژگی‌های زیر:
    - `transfer` {{optional_inline}}
      - : همان معنای پارامتر `transfer` را دارد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

قطعه کد زیر `worker.js` را نشان می‌دهد، که در آن از یک هندلر `onmessage` برای مدیریت پیام‌های رسیده از اسکریپت اصلی استفاده شده است. در داخل هندلر یک محاسبه انجام می‌شود که از آن یک پیام نتیجه ساخته می‌شود؛ سپس این پیام با استفاده از `postMessage(workerResult);` به ریسمان اصلی بازگردانده می‌شود.

```js
onmessage = (e) => {
  console.log("Message received from main script");
  const workerResult = `Result: ${e.data[0] * e.data[1]}`;
  console.log("Posting message back to main script");
  postMessage(workerResult);
};
```

در اسکریپت اصلی، `onmessage` باید روی یک `Worker object` فراخوانی شود، در حالی که در داخل اسکریپت worker فقط به `onmessage` نیاز دارید، زیرا worker عملاً حوزه سراسری ({{domxref("DedicatedWorkerGlobalScope")}}) است.

برای مشاهده یک مثال کامل، به [نمونه worker اختصاصی پایه](https://github.com/mdn/dom-examples/tree/main/web-workers/simple-web-worker) مراجعه کنید ([اجرای worker اختصاصی](https://mdn.github.io/dom-examples/web-workers/simple-web-worker/)).

> [!NOTE]
> `postMessage()` فقط می‌تواند در هر بار یک شیء را ارسال کند. همانطور که در بالا مشاهده می‌کنید، اگر می‌خواهید چند مقدار را ارسال کنید، می‌توانید یک آرایه بفرستید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

رابط {{domxref("DedicatedWorkerGlobalScope")}} که این متد به آن تعلق دارد.