---
title: "CSSUnparsedValue: length property"
short-title: length
slug: Web/API/CSSUnparsedValue/length
page-type: web-api-instance-property
browser-compat: api.CSSUnparsedValue.length
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`length`** در رابط {{domxref("CSSUnparsedValue")}} تعداد آیتم‌های موجود در شیء را برمی‌گرداند.

## مقدار

یک عدد صحیح.

## مثال‌ها

### استفاده پایه

در این مثال، از سازنده {{domxref("CSSUnparsedValue.CSSUnparsedValue", "CSSUnparsedValue()")}} استفاده می‌کنیم و سپس طول را پرس‌وجو می‌کنیم:

```js
const values = new CSSUnparsedValue(["1em", "#445566", "-45px"]);

console.log(values.length); // 3
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSUnparsedValue.CSSUnparsedValue", "CSSUnparsedValue()")}}
- {{domxref("CSSUnparsedValue.entries")}}
- {{domxref("CSSUnparsedValue.forEach")}}
- {{domxref("CSSUnparsedValue.keys")}}
- {{domxref("CSSUnparsedValue.values")}}
- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)