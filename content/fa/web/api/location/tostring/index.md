---
title: "Location: toString() method"
short-title: toString()
slug: Web/API/Location/toString
page-type: web-api-instance-method
browser-compat: api.Location.toString
---

{{ApiRef("Location")}}

متد **`toString()`** از نوع {{Glossary("stringifier")}} در رابط
{{domxref("Location")}} رشته‌ای شامل کل URL را برمی‌گرداند. این متد نسخهٔ فقط‌خواندنی از {{domxref("Location.href")}} است.

## Syntax

```js-nolint
toString()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک رشته که URL شیء را نشان می‌دهد.

## مثال‌ها

```js
// فرض کنید این کد روی https://example.com/path?search#hash اجرا می‌شود
const result = window.location.toString(); // برمی‌گرداند: 'https://example.com/path?search#hash'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}