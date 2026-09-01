---
title: "CSSNumericValue: parse() static method"
short-title: parse()
slug: Web/API/CSSNumericValue/parse_static
page-type: web-api-static-method
browser-compat: api.CSSNumericValue.parse_static
---

{{APIRef("CSS Typed Object Model API")}}

متد استاتیک **`parse()`** از رابط {{domxref("CSSNumericValue")}} یک رشتهٔ مقدار را به یک شیء تبدیل می‌کند که اعضای آن مقدار و واحد هستند.

> [!NOTE]
> این متد در زمینه‌های {{domxref("Worker")}} یا {{domxref("Worklet")}} قابل فراخوانی نیست — تجزیهٔ متن CSS به نخ اصلی محدود است. تمام متدهای دیگر در رابط `CSSNumericValue` در workerها و workletها در دسترس هستند.

## Syntax

```js-nolint
CSSNumericValue.parse(cssText)
```

### Parameters

- `cssText`
  - : یک رشته که شامل بخش عددی و واحد است.

### Return value

یک {{domxref('CSSNumericValue')}}.

### Exceptions

- `SyntaxError` {{domxref("DOMException")}}
  - : TBD

## Examples

### استفادهٔ پایه

کد زیر یک شیء {{domxref('CSSUnitValue')}} را برمی‌گرداند که ویژگی `unit` آن برابر با `"px"` و ویژگی `value` آن برابر با `42` است.

```js
let numValue = CSSNumericValue.parse("42.0px");
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}