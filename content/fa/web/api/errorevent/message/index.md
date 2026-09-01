---
title: "ErrorEvent: message property"
short-title: message
slug: Web/API/ErrorEvent/message
page-type: web-api-instance-property
browser-compat: api.ErrorEvent.message
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`message`** در رابط {{domxref("ErrorEvent")}} یک رشته (string) حاوی پیام خطای قابل فهم برای انسان که مشکل را شرح می‌دهد، بازمی‌گرداند.

## مقدار

یک رشته.

## مثال‌ها

```js
window.addEventListener("error", (ev) => {
  console.log(`The error message: ${ev.message}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}