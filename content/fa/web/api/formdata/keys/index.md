---
title: "FormData: keys() method"
short-title: keys()
slug: Web/API/FormData/keys
page-type: web-api-instance-method
browser-compat: api.FormData.keys
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

روش **`FormData.keys()`** یک [تکرارکننده (iterator)](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) برمی‌گرداند که روی تمام کلیدهای موجود در {{domxref("FormData")}} تکرار می‌کند. کلیدها رشته‌ها هستند.

## نحو

```js-nolint
keys()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک [`تکرارکننده`](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) از کلیدهای {{domxref("FormData")}}.

## مثال‌ها

```js
const formData = new FormData();
formData.append("key1", "value1");
formData.append("key2", "value2");

// Display the keys
for (const key of formData.keys()) {
  console.log(key);
}
```

نتیجه:

```plain
key1
key2
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}