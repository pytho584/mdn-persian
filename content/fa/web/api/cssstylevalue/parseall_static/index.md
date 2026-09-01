---
title: "CSSStyleValue: parseAll() static method"
---

---
title: "CSSStyleValue: parseAll() static method"
short-title: parseAll()
slug: Web/API/CSSStyleValue/parseAll_static
page-type: web-api-static-method
browser-compat: api.CSSStyleValue.parseAll_static
---

{{APIRef("CSS Typed Object Model API")}}

متد ایستای **`parseAll()`** از رابط {{domxref("CSSStyleValue")}} تمامی موارد یک ویژگی CSS خاص را به مقدار مشخص‌شده تنظیم می‌کند و آرایه‌ای از اشیاء {{domxref('CSSStyleValue')}} برمی‌گرداند که هر یک شامل یکی از مقادیر ارائه‌شده است.

> [!NOTE]
> این متد در بافت‌های {{domxref("Worker")}} یا {{domxref("Worklet")}} قابل فراخوانی نیست.
> بقیهٔ رابط `CSSStyleValue` همچنان در workerها و workletها در دسترس است.

## نحو

```js-nolint
CSSStyleValue.parseAll(property, value)
```

### پارامترها

- `property`
  - : یک ویژگی CSS که باید تنظیم شود.
- `value`
  - : یک رشتهٔ جدا شده با کاما که شامل یک یا چند مقدار است و روی ویژگی ارائه‌شده اعمال می‌شود.

### مقدار بازگشتی

آرایه‌ای از اشیاء `CSSStyleValue` که هر یک شامل یکی از مقادیر ارائه‌شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [`CSSStyleValue.parse()`](/en-US/docs/Web/API/CSSStyleValue/parse_static)
- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)