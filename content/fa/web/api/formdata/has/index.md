---
title: "FormData: has() method"
short-title: has()
slug: Web/API/FormData/has
page-type: web-api-instance-method
browser-compat: api.FormData.has
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

متد **`has()`** از رابط {{domxref("FormData")}} مشخص می‌کند که آیا یک شیء `FormData` حاوی یک کلید مشخص است یا خیر.

## Syntax

```js-nolint
has(name)
```

### Parameters

- `name`
  - : یک رشته که نام کلیدی را که می‌خواهید آزمایش کنید، نشان می‌دهد.

### Return value

`true` اگر کلیدی از `FormData` با `name` مشخص شده مطابقت داشته باشد. در غیر این صورت `false`.

## Examples

قطعه کد زیر نتایج آزمایش وجود `username` در یک شیء `FormData` را قبل و بعد از افزودن مقدار `username` به آن با استفاده از {{domxref("FormData.append", "append()")}} نشان می‌دهد:

```js
formData.has("username"); // Returns false
formData.append("username", "Chris");
formData.has("username"); // Returns true
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using FormData objects](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}