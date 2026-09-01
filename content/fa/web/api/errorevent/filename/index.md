---
title: "ErrorEvent: filename property"
---

---
title: "ErrorEvent: filename property"
short-title: filename
slug: Web/API/ErrorEvent/filename
page-type: web-api-instance-property
browser-compat: api.ErrorEvent.filename
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`filename`** از رابط {{domxref("ErrorEvent")}} رشته‌ای را برمی‌گرداند که شامل نام فایل اسکریپتی است که خطا در آن رخ داده است.

## مقدار

یک رشته.

## مثال‌ها

```js
window.addEventListener("error", (ev) => {
  console.log(`The error occur in file: ${ev.filename}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}