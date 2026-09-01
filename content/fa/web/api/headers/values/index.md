---
title: "Headers: values() method"
short-title: values()
slug: Web/API/Headers/values
page-type: web-api-instance-method
browser-compat: api.Headers.values
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

متد **`Headers.values()`** یک {{jsxref("Iteration_protocols",'iterator')}} برمی‌گرداند که امکان عبور از تمام مقادیر موجود در این شیء را فراهم می‌کند. مقادیر، اشیاء {{jsxref("String")}} هستند.

## Syntax

```js-nolint
values()
```

### Parameters

هیچ.

### Return value

یک {{jsxref("Iteration_protocols","iterator")}} برمی‌گرداند.

## Examples

```js
// Create a test Headers object
const myHeaders = new Headers();
myHeaders.append("Content-Type", "text/xml");
myHeaders.append("Vary", "Accept-Language");

// Display the values
for (const value of myHeaders.values()) {
  console.log(value);
}
```

نتیجه به صورت زیر است:

```plain
text/xml
Accept-Language
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [ServiceWorker API](/en-US/docs/Web/API/Service_Worker_API)
- [HTTP access control (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)