---
title: "Client: postMessage() method"
short-title: postMessage()
slug: Web/API/Client/postMessage
page-type: web-api-instance-method
browser-compat: api.Client.postMessage
---

{{APIRef("Service Worker API")}}{{AvailableInWorkers("service")}}

**`postMessage()`** متد در رابط {{domxref("Client")}} به یک service worker اجازه می‌دهد تا پیامی را به یک client (یک {{domxref("Window")}}، {{domxref("Worker")}} یا {{domxref("SharedWorker")}}) ارسال کند. این پیام در رویداد `message` روی {{domxref("ServiceWorkerContainer", "navigator.serviceWorker")}} دریافت می‌شود.

## Syntax

```js-nolint
postMessage(message)
postMessage(message, transfer)
postMessage(message, options)
```

### Parameters

- `message`
  - : پیامی که به client ارسال می‌شود. این می‌تواند هر [نوع قابل ساختار-شبیه‌سازی‌شده](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) باشد.

    > [!NOTE]
    > یک service worker در همان [خوشه عامل](/en-US/docs/Web/JavaScript/Reference/Execution_model#agent_clusters_and_memory_sharing) client خود قرار ندارد و بنابراین نمی‌تواند حافظه را به اشتراک بگذارد. اشیاء {{jsxref("SharedArrayBuffer")}} یا نماهای بافری که بر پایه آن‌ها هستند، نمی‌توانند بین خوشه‌های عامل ارسال شوند. تلاش برای انجام این کار، رویدادی به نام {{domxref("BroadcastChannel/messageerror_event", "messageerror")}} تولید می‌کند که حاوی یک {{domxref("DOMException")}} از نوع `DataCloneError` در سمت دریافت‌کننده است.

- `transfer` {{optional_inline}}
  - : یک [آرایه](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) اختیاری از [اشیاء قابل انتقال](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) برای انتقال مالکیت آن‌ها. مالکیت این اشیاء به سمت مقصد منتقل می‌شود و دیگر در سمت فرستنده قابل استفاده نیستند. این اشیاء قابل انتقال به‌طور خودکار ارسال نمی‌شوند؛ آن‌ها باید یا در پیام موجود باشند یا از طریق روش‌های دیگری مانند {{domxref("MessagePort")}} از طریق {{domxref("MessageEvent.ports")}} برای گیرنده قابل دسترسی باشند.
- `options` {{optional_inline}}
  - : یک شیء اختیاری حاوی ویژگی‌های زیر:
    - `transfer` {{optional_inline}}
      - : معنای مشابهی با پارامتر `transfer` دارد.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

کد زیر یک پیام را از service worker به یک client ارسال می‌کند. client با استفاده از متد {{domxref("Clients.get()", "get()")}} روی {{domxref("ServiceWorkerGlobalScope.clients", "clients")}} که یک متغیر سراسری در حوزه service worker است، دریافت می‌شود.

```js
addEventListener("fetch", (event) => {
  event.waitUntil(
    (async () => {
      // اگر به client دسترسی نداریم، زود خارج می‌شویم.
      // مثلاً اگر cross-origin باشد.
      if (!event.clientId) return;

      // دریافت client
      const client = await self.clients.get(event.clientId);
      // اگر client را دریافت نکردیم، زود خارج می‌شویم.
      // مثلاً اگر بسته شده باشد.
      if (!client) return;

      // ارسال پیام به client
      client.postMessage({
        msg: "Hey I just got a fetch from you!",
        url: event.request.url,
      });
    })(),
  );
});
```

دریافت آن پیام:

```js
navigator.serviceWorker.addEventListener("message", (event) => {
  console.log(event.data.msg, event.data.url);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
