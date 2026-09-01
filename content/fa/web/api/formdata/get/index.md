```markdown
---
title: "FormData: get() method"
short-title: get()
slug: Web/API/FormData/get
page-type: web-api-instance-method
browser-compat: api.FormData.get
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

متد **`get()`** از رابط {{domxref("FormData")}} اولین مقداری را که با یک کلید مشخص در یک شیء `FormData` مرتبط است، برمی‌گرداند. اگر انتظار چندین مقدار دارید و همه‌ی آنها را می‌خواهید، از متد {{domxref("FormData.getAll()","getAll()")}} استفاده کنید.

## نحو (Syntax)

```js-nolint
get(name)
```

### پارامترها

- `name`
  - : یک رشته (string) که نام کلیدی را که می‌خواهید بازیابی کنید، مشخص می‌کند.

### مقدار بازگشتی

یک مقدار که کلید آن با `name` مشخص‌شده مطابقت دارد. در غیر این صورت، [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null).

## مثال‌ها

اگر دو مقدار `username` را با استفاده از {{domxref("FormData.append", "append()")}} به یک {{domxref("FormData")}} اضافه کنیم:

```js
formData.append("username", "Chris");
formData.append("username", "Bob");
```

متد `get()` زیر تنها اولین مقدار `username` را برمی‌گرداند:

```js
formData.get("username"); // Returns "Chris"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}
```