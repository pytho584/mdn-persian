---
title: "FormData: entries() method"
short-title: entries()
slug: Web/API/FormData/entries
page-type: web-api-instance-method
browser-compat: api.FormData.entries
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

متد **`FormData.entries()`** یک [iterator](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) (تکرارگر) برمی‌گرداند که روی تمام جفت‌های کلید/مقدار موجود در {{domxref("FormData")}} پیمایش می‌کند. کلید هر جفت یک رشته (string) است و مقدار آن یا یک رشته است یا یک {{domxref("Blob")}}.

## نحو

```js-nolint
entries()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک [iterator](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) (تکرارگر) از جفت‌های کلید/مقدار {{domxref("FormData")}}.

## مثال‌ها

```js
formData.append("key1", "value1");
formData.append("key2", "value2");

// Display the key/value pairs
for (const pair of formData.entries()) {
  console.log(pair[0], pair[1]);
}
```

نتیجه به این صورت است:

```plain
key1 value1
key2 value2
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using FormData objects](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}