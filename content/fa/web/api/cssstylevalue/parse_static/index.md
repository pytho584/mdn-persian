---
title: "CSSStyleValue: parse() static method"
---

---
title: "CSSStyleValue: parse() static method"
short-title: parse()
slug: Web/API/CSSStyleValue/parse_static
page-type: web-api-static-method
browser-compat: api.CSSStyleValue.parse_static
---

{{APIRef("CSS Typed Object Model API")}}

متد ایستای **`parse()`** از رابط {{domxref("CSSStyleValue")}}، یک ویژگی مشخص CSS را به مقادیر داده‌شده تنظیم می‌کند و اولین مقدار را به‌صورت یک شیء {{domxref('CSSStyleValue')}} برمی‌گرداند.

> [!NOTE]
> این متد در زمینه‌های {{domxref("Worker")}} یا {{domxref("Worklet")}} قابل فراخوانی نیست.
> بقیهٔ رابط `CSSStyleValue` همچنان در workerها و workletها در دسترس است.

## Syntax

```js-nolint
CSSStyleValue.parse(property, cssText)
```

### Parameters

- `property`
  - : ویژگی CSS که قرار است تنظیم شود.
- `cssText`
  - : رشتهٔ جداشده با کاما که شامل یک یا چند مقدار برای اعمال به ویژگی داده‌شده است.

### Return value

یک شیء `CSSStyleValue` شامل اولین مقدار ارائه‌شده.

## Examples

### استفادهٔ پایه

کد زیر مجموعه‌ای از اعلان‌ها را برای ویژگی `transform` تجزیه می‌کند. بلوک کد دوم، ساختار شیء بازگشت‌داده‌شده را همان‌طور که در کنسول ابزارهای توسعه‌دهنده نمایش داده می‌شود، نشان می‌دهد.

```js
const css = CSSStyleValue.parse(
  "transform",
  "translate3d(10px,10px,0) scale(0.5)",
);
```

```plain
CSSTransformValue {0: CSSTranslate, 1: CSSScale, length: 2, is2D: false}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [`CSSStyleValue.parseAll()`](/en-US/docs/Web/API/CSSStyleValue/parseAll_static)

- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [API مدل شیء تایپ‌شدهٔ CSS](/en-US/docs/Web/API/CSS_Typed_OM_API)