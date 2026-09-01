```
---
title: "ErrorEvent: lineno property"
short-title: lineno
slug: Web/API/ErrorEvent/lineno
page-type: web-api-instance-property
browser-compat: api.ErrorEvent.lineno
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`lineno`** از رابط {{domxref("ErrorEvent")}} یک عدد صحیح برمی‌گرداند که شامل شماره خط فایل اسکریپتی است که خطا در آن رخ داده است.

## مقدار

یک عدد صحیح.

## مثال‌ها

```js
window.addEventListener("error", (ev) => {
  console.log(`The error occur in line: ${ev.lineno}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```