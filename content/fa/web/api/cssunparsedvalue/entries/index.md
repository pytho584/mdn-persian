---
title: "CSSUnparsedValue: entries() method"
short-title: entries()
slug: Web/API/CSSUnparsedValue/entries
page-type: web-api-instance-method
browser-compat: api.CSSUnparsedValue.entries
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`CSSUnparsedValue.entries()`** آرایه‌ای از جفت‌های `[key, value]` ویژگی‌های شمارش‌پذیر متعلق به خودِ یک شیء مشخص برمی‌گرداند، به همان ترتیبی که توسط حلقهٔ {{jsxref("Statements/for...in", "for...in")}} ارائه می‌شود (با این تفاوت که حلقهٔ for-in ویژگی‌های موجود در زنجیرهٔ prototype را نیز شمارش می‌کند).

## دستور زبان

```js-nolint
entries(obj)
```

### پارامترها

- `obj`
  - یک {{domxref('CSSUnparsedValue')}} که قرار است جفت‌های `[key, value]` ویژگی‌های شمارش‌پذیر متعلق به خودِ آن بازگردانده شوند.

### مقدار بازگشتی

آرایه‌ای از جفت‌های `[key, value]` ویژگی‌های شمارش‌پذیر متعلق به خودِ شیء `CSSUnparsedValue` داده‌شده.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSUnparsedValue.CSSUnparsedValue", "CSSUnparsedValue()")}}
- {{domxref("CSSUnparsedValue.forEach")}}
- {{domxref("CSSUnparsedValue.keys")}}
- {{domxref("CSSUnparsedValue.length")}}
- {{domxref("CSSUnparsedValue.values")}}
- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)