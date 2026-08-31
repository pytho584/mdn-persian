---
title: "Clients: get() method"
short-title: get()
slug: Web/API/Clients/get
page-type: web-api-instance-method
browser-compat: api.Clients.get
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

متود **`get()`** از رابط {{domxref("Clients")}} یک سرویس‌ورکر کلاینت را که با `id` داده‌شده مطابقت دارد دریافت می‌کند و آن را در یک {{jsxref("Promise")}} برمی‌گرداند.

## Syntax

```js-nolint
get(id)
```

### Parameters

- `id`
  - : یک رشته که شناسه کلاینتی را که می‌خواهید دریافت کنید، نشان می‌دهد.

### Return value

یک {{jsxref("Promise")}} که به یک شیء {{domxref("Client")}} یا `undefined` resolve می‌شود.

## Examples

```js
self.clients.get(id).then((client) => {
  self.clients.openWindow(client.url);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}