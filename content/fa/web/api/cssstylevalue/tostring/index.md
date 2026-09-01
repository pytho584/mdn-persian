---
title: "CSSStyleValue: toString() method"
---

---
title: "CSSStyleValue: toString() method"
short-title: toString()
slug: Web/API/CSSStyleValue/toString
page-type: web-api-instance-method
browser-compat: api.CSSStyleValue.toString
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`toString()`** در رابط {{domxref("CSSStyleValue")}} یک {{Glossary("stringifier")}} است که مقدار را به‌صورت رشته‌ای از متن استاندارد CSS برمی‌گرداند.

## سینتکس

```js-nolint
toString()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک رشته.

## توضیحات

روش دقیق تبدیل این شیء به رشته به نحوهٔ به‌دست‌آوردن شیء `CSSStyleValue` بستگی دارد:

- اگر شیء از طریق تجزیهٔ یک رشتهٔ CSS ساخته شده باشد، مثلاً با {{domxref("CSSStyleValue.parse_static", "CSSStyleValue.parse()")}}، متد همان رشتهٔ اولیهٔ تجزیه‌شده را برمی‌گرداند.
- اگر شیء مستقیماً ساخته شده باشد، مثلاً با [یک تابع کارخانه‌ای `CSS`](/en-US/docs/Web/API/CSS/factory_functions_static) یا سازندهٔ یک زیرکلاس، رشتهٔ بازگشتی طبق قوانین سریال‌سازیِ مخصوصِ آن زیرکلاس تولید می‌شود.
- اگر شیء از CSSOM خوانده شده باشد، مثلاً با {{domxref("Element.computedStyleMap()")}} یا {{domxref("HTMLElement.attributeStyleMap")}}، رشتهٔ بازگشتی از قوانین سریال‌سازی CSSOM پیروی می‌کند.

برای اطلاعات بیشتر دربارهٔ قوانین سریال‌سازی، به [زمان و نحوهٔ سریال‌سازی مقادیر](/en-US/docs/Web/API/CSS_Object_Model/CSS_value_serialization#when_and_how_values_are_serialized) در _سریال‌سازی مقادیر CSS_ مراجعه کنید.

## مثال‌ها

### استفادهٔ پایه

```js
// Parsed from a string: returns the original string
const length1 = CSSStyleValue.parse("42.0px");
length1.toString(); // "42.0px"

// Constructed directly with a CSS factory function: subclass-specific serialization
const length2 = CSS.px(42.0);
length2.toString(); // "42px"

// Read from the CSSOM: follows CSSOM serialization rules
const element = document.createElement("div");
element.style.width = "42.0px";
const length3 = element.attributeStyleMap.get("width");
length3.toString(); // "42px"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- {{domxref("CSSStyleValue.parse_static", "CSSStyleValue.parse()")}}
- {{domxref("CSSStyleValue.parseAll_static", "CSSStyleValue.parseAll()")}}