---
title: "FormData: values() method"
short-title: values()
slug: Web/API/FormData/values
page-type: web-api-instance-method
browser-compat: api.FormData.values
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

روش **`FormData.values()`** یک [تکرارگر](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) بازمی‌گرداند که بر روی تمام مقادیر موجود در {{domxref("FormData")}} تکرار می‌کند. مقادیر، رشته‌ها یا اشیاء {{domxref("Blob")}} هستند.

## نحو

```js-nolint
values()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک [`تکرارگر`](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) از مقادیر {{domxref("FormData")}}.

## مثال‌ها

```js
const formData = new FormData();
formData.append("key1", "value1");
formData.append("key2", "value2");

// Display the values
for (const value of formData.values()) {
  console.log(value);
}
```

نتیجه به صورت زیر است:

```plain
value1
value2
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}