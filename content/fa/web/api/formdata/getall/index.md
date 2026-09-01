---
title: "FormData: getAll() method"
short-title: getAll()
slug: Web/API/FormData/getAll
page-type: web-api-instance-method
browser-compat: api.FormData.getAll
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

متد **`getAll()`** در رابط {{domxref("FormData")}}، تمام مقادیر مرتبط با یک کلید مشخص را از درون یک شیء `FormData` بازمی‌گرداند.

## نحو

```js-nolint
getAll(name)
```

### پارامترها

- `name`
  - : رشته‌ای که نام کلیدی را که می‌خواهید بازیابی کنید نشان می‌دهد.

### مقدار بازگشتی

آرایه‌ای از مقادیر که کلید آن‌ها با `name` مشخص‌شده مطابقت دارد. در غیر این صورت، یک لیست خالی.

## مثال‌ها

اگر دو مقدار `username` را با استفاده از {{domxref("FormData.append", "append()")}} به یک {{domxref("FormData")}} اضافه کنیم:

```js
formData.append("username", "Chris");
formData.append("username", "Bob");
```

متد `getAll()` زیر هر دو مقدار `username` را در یک آرایه برمی‌گرداند:

```js
formData.getAll("username"); // Returns ["Chris", "Bob"]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از شیءهای FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}