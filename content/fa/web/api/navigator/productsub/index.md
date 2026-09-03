---
title: "Navigator: productSub property"
short-title: productSub
slug: Web/API/Navigator/productSub
page-type: web-api-instance-property
browser-compat: api.Navigator.productSub
---

{{ ApiRef("HTML DOM") }}

خاصیت فقط‌خواندنی **`Navigator.productSub`** رشته «20030107» یا رشته «20100101» را برمی‌گرداند.

## مقدار

یا «20030107» است یا «20100101».

## مثال‌ها

```js
document.body.textContent = `productSub: ${navigator.productSub}`;
```

{{ EmbedLiveSample("Examples") }}

## نکات

در IE، این خاصیت مقدار `undefined` را برمی‌گرداند.

در Apple Safari و Google Chrome، این خاصیت همیشه `20030107` را برمی‌گرداند.

در Firefox، این خاصیت همیشه `20100101` را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}