---
title: "HashChangeEvent: newURL property"
---

---
title: "HashChangeEvent: newURL property"
short-title: newURL
slug: Web/API/HashChangeEvent/newURL
page-type: web-api-instance-property
browser-compat: api.HashChangeEvent.newURL
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`newURL`** در رابط {{domxref("HashChangeEvent")}}، نشانی وب جدیدی را برمی‌گرداند که پنجره به آن هدایت می‌شود.

## مقدار

یک رشته.

## مثال‌ها

```js
window.addEventListener("hashchange", (event) => {
  console.log(`Hash changed to ${event.newURL}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}