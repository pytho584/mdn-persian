---
title: "CSSConditionRule: conditionText property"
short-title: conditionText
slug: Web/API/CSSConditionRule/conditionText
page-type: web-api-instance-property
browser-compat: api.CSSConditionRule.conditionText
---

{{ APIRef("CSSOM") }}

ویژگی فقط‌خواندنی **`conditionText`** در رابط {{domxref("CSSConditionRule")}}، متن قانون CSS را برمی‌گرداند یا تنظیم می‌کند.

## مقدار

یک رشته (string).

## مثال‌ها

مثال زیر نحوه خواندن مقدار `conditionText` را روی یک {{domxref("CSSMediaRule")}} که رابط {{domxref("CSSConditionRule")}} را پیاده‌سازی می‌کند، نشان می‌دهد.

```css
@media (width >= 500px) {
  body {
    color: blue;
  }
}
```

```js
const targetRule = document.styleSheets[0].cssRules[0];
console.log(targetRule.conditionText); // "(width >= 500px)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)