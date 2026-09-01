---
title: "Headers: keys() method"
---

---
title: "Headers: keys() method"
short-title: keys()
slug: Web/API/Headers/keys
page-type: web-api-instance-method
browser-compat: api.Headers.keys
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`Headers.keys()`** یک {{jsxref("Iteration_protocols",'iterator')}} برمی‌گرداند که می‌توان برای گذر از تمام کلیدهای موجود در این شیء از آن استفاده کرد. کلیدها اشیاء {{jsxref("String")}} هستند.

## سینتکس

```js-nolint
keys()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{jsxref("Iteration_protocols","iterator")}} برمی‌گرداند.

## مثال‌ها

```js
// Create a test Headers object
const myHeaders = new Headers();
myHeaders.append("Content-Type", "text/xml");
myHeaders.append("Vary", "Accept-Language");

// Display the keys
for (const key of myHeaders.keys()) {
  console.log(key);
}
```

نتیجه به این صورت است:

```plain
content-type
vary
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)