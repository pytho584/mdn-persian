---
title: "Blob: Blob() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob/Blob"
translated_by: "n8n + AI"
---

{{APIRef("File API")}}{{AvailableInWorkers}}

سازنده **`Blob()`** یک شیء {{domxref("Blob")}} جدید بازمی‌گرداند. محتوای blob شامل الحاق مقادیر داده شده در پارامتر `blobParts` است.

## Syntax

```js-nolint
new Blob(blobParts)
new Blob(blobParts, options)
```

### Parameters

- `blobParts` {{optional_inline}}
  - : یک شیء [iterable](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#the_iterable_protocol) مانند {{jsxref("Array")}}، حاوی {{jsxref("ArrayBuffer")}}ها، {{jsxref("TypedArray")}}ها، {{jsxref("DataView")}}ها، {{domxref("Blob")}}ها، رشته‌ها، یا ترکیبی از هر یک از این عناصر، که درون {{domxref("Blob")}} قرار می‌گیرند. رشته‌ها باید Unicode خوب‌فرم باشند، و surrogateهای تنها با استفاده از همان الگوریتم {{jsxref("String.prototype.toWellFormed()")}} پالایش می‌شوند. رشته حاصل به صورت UTF-8 رمزگذاری می‌شود.

- `options` {{optional_inline}}
  - : یک شیء که ممکن است هر یک از ویژگی‌های زیر را مشخص کند:
    - `type` {{optional_inline}}
      - : نوع {{Glossary("MIME type")}} داده‌ای که در blob ذخیره خواهد شد. مقدار پیش‌فرض رشته خالی (`""`) است.
    - `endings` {{optional_inline}}
      - : نحوه تفسیر کاراکترهای خط جدید (`\n`) درون محتوا، اگر داده متن باشد. مقدار پیش‌فرض `transparent`، کاراکترهای خط جدید را بدون تغییر در blob کپی می‌کند. برای تبدیل خطوط جدید به قرارداد بومی سیستم میزبان، مقدار `native` را مشخص کنید.

### Return value

یک شیء {{domxref("Blob")}} جدید حاوی داده‌های مشخص شده.

## Examples

```js
const blobParts = ['<q id="a"><span id="b">hey!</span></q>']; // an array consisting of a single string
const blob = new Blob(blobParts, { type: "text/html" }); // the blob
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}