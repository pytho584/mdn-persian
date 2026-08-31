```yaml
---
title: "Client: type property"
short-title: type
slug: Web/API/Client/type
page-type: web-api-instance-property
browser-compat: api.Client.type
---
```

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

خاصیت فقط-خواندنی **`type`** از رابط {{domxref("Client")}} نشان‌دهنده نوع کلاینتی است که سرویس‌ورکر آن را کنترل می‌کند.

## مقدار

یک رشته (string) که نوع کلاینت را نشان می‌دهد. مقدار می‌تواند یکی از موارد زیر باشد:

- `"window"`
- `"worker"`
- `"sharedworker"`

## مثال‌ها

```js
// service worker client (e.g. a document)
function sendMessage(message) {
  return new Promise((resolve, reject) => {
    // note that this is the ServiceWorker.postMessage version
    navigator.serviceWorker.controller.postMessage(message);
    window.serviceWorker.onMessage = (e) => {
      resolve(e.data);
    };
  });
}

// controlling service worker
self.addEventListener("message", (e) => {
  // e.source is a client object
  e.source.postMessage(`Hello! Your message was: ${e.data}`);
  // Let's also post the type value back to the client
  e.source.postMessage(e.source.type);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}