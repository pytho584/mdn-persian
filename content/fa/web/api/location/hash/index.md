---
title: "Location: hash property"
short-title: hash
slug: Web/API/Location/hash
page-type: web-api-instance-property
browser-compat: api.Location.hash
---

{{ APIRef("Location") }}

ویژگی **`hash`** از واسط {{domxref("Location")}} یک رشته حاوی `"#"` به همراه شناسه قطعه (fragment identifier) از URL مکان است. اگر URL شناسه قطعه نداشته باشد، این ویژگی شامل یک رشته خالی (`""`) خواهد بود.

برای اطلاعات بیشتر به {{domxref("URL.hash")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

فرض کنید کاربر به آدرس `https://example.org#examples` رفته است، کد زیر مقدار `#examples` را در خروجی ثبت می‌کند:

```js
const result = location.hash;
console.log(result);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}