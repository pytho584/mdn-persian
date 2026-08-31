---
title: "CloseEvent: wasClean property"
short-title: wasClean
slug: Web/API/CloseEvent/wasClean
page-type: web-api-instance-property
browser-compat: api.CloseEvent.wasClean
---

{{APIRef("Websockets API")}}{{AvailableInWorkers}}

خاصیت فقط‑خواندنی **`wasClean`** از رابط {{domxref("CloseEvent")}} اگر اتصال به‌طور تمیز بسته شده باشد، `true` برمی‌گرداند.

## مقدار

یک مقدار Boolean. اگر اتصال به‌طور تمیز بسته شده باشد `true`، در غیر این صورت `false`.

## مثال‌ها

مثال زیر مقدار `wasClean` را در کنسول چاپ می‌کند.

```js
WebSocket.onclose = (event) => {
  console.log(event.wasClean);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}