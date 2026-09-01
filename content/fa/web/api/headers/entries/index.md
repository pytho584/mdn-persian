---
title: "Headers: entries() method"
---

---
title: "Headers: entries() method"
short-title: entries()
slug: Web/API/Headers/entries
page-type: web-api-instance-method
browser-compat: api.Headers.entries
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`Headers.entries()`** یک {{jsxref("Iteration_protocols",'iterator')}} برمی‌گرداند که امکان پیمایش همه‌ی جفت‌های کلید/مقدار موجود در این شیء را فراهم می‌کند. در هر جفت، هم کلید و هم مقدار، آبجکت‌های {{jsxref("String")}} هستند.

## نحو

```js-nolint
entries()
```

### پارامترها

هیچ پارامتری.

### مقدار بازگشتی

یک {{jsxref("Iteration_protocols","iterator")}} برمی‌گرداند.

## مثال‌ها

```js
// Create a test Headers object
const myHeaders = new Headers();
myHeaders.append("Content-Type", "text/xml");
myHeaders.append("Vary", "Accept-Language");

// Display the key/value pairs
for (const pair of myHeaders.entries()) {
  console.log(`${pair[0]}: ${pair[1]}`);
}
```

نتیجه به این صورت است:

```plain
content-type: text/xml
vary: Accept-Language
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)