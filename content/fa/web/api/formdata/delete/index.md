---
title: "FormData: delete() method"
short-title: delete()
slug: Web/API/FormData/delete
page-type: web-api-instance-method
browser-compat: api.FormData.delete
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

متد **`delete()`** از رابط {{domxref("FormData")}} یک کلید و مقدار(های) آن را از یک شیء `FormData` حذف می‌کند.

## نحو

```js-nolint
delete(name)
```

### پارامترها

- `name`
  - : نام کلیدی است که می‌خواهید حذف کنید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

می‌توانید یک کلید و مقادیر آن را با استفاده از `delete()` حذف کنید:

```js
formData.delete("username");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}