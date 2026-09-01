---
title: "HashChangeEvent: oldURL property"
---

---
title: "HashChangeEvent: oldURL property"
short-title: oldURL
slug: Web/API/HashChangeEvent/oldURL
page-type: web-api-instance-property
browser-compat: api.HashChangeEvent.oldURL
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`oldURL`** از رابط {{domxref("HashChangeEvent")}} نشانی وب قبلی را که پنجره به آن ناوبری شده بود برمی‌گرداند.

## مقدار

یک رشته (string).

## مثال‌ها

```js
window.addEventListener("hashchange", (event) => {
  console.log(`Hash changed from ${event.oldURL}`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}