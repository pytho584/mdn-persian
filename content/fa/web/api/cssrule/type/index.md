---
title: "CSSRule: type property"
short-title: type
slug: Web/API/CSSRule/type
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.CSSRule.type
---

{{APIRef("CSSOM")}}{{Deprecated_header}}

ویژگی فقط‌خواندنی **`type`** در رابط {{domxref("CSSRule")}} یک ویژگی منسوخ‌شده است که یک عدد صحیح برمی‌گرداند و نشان می‌دهد که {{domxref("CSSRule")}} مربوطه از کدام نوع قاعده است.

اگر نیاز به تشخیص انواع مختلف قواعد CSS دارید، جایگزین مناسبی استفاده از [`constructor.name`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/name) است:

```js
const sheets = Array.from(document.styleSheets);
const rules = sheets.map((sheet) => Array.from(sheet.cssRules)).flat();

for (const rule of rules) {
  console.log(rule.constructor.name);
}
```

## مقدار

- `CSSRule.STYLE_RULE` (`1`)
  - : قاعده یک {{domxref("CSSStyleRule")}} است، رایج‌ترین نوع قاعده: `selector { prop1: val1; prop2: val2; }`.
- `CSSRule.IMPORT_RULE` (`3`)
  - : قاعده یک {{domxref("CSSImportRule")}} است و یک قاعده {{cssxref("@import")}} را نمایش می‌دهد.
- `CSSRule.MEDIA_RULE` (`4`)
  - : قاعده یک {{domxref("CSSMediaRule")}} است.
- `CSSRule.FONT_FACE_RULE` (`5`)
  - : قاعده یک {{domxref("CSSFontFaceRule")}} است.
- `CSSRule.PAGE_RULE` (`6`)
  - : قاعده یک {{domxref("CSSPageRule")}} است.
- `CSSRule.KEYFRAMES_RULE` (`7`)
  - : قاعده یک {{domxref("CSSKeyframesRule")}} است.
- `CSSRule.KEYFRAME_RULE` (`8`)
  - : قاعده یک {{domxref("CSSKeyframeRule")}} است.
- `CSSRule.MARGIN_RULE` (`9`)
  - : قاعده یک {{domxref("CSSMarginRule")}} است.
- `CSSRule.NAMESPACE_RULE` (`10`)
  - : قاعده یک {{domxref("CSSNamespaceRule")}} است.
- `CSSRule.COUNTER_STYLE_RULE` (`11`)
  - : قاعده یک {{domxref("CSSCounterStyleRule")}} است.
- `CSSRule.SUPPORTS_RULE` (`12`)
  - : قاعده یک {{domxref("CSSSupportsRule")}} است.
- `CSSRule.FONT_FEATURE_VALUES_RULE` (`14`)
  - : قاعده یک {{domxref("CSSFontFeatureValuesRule")}} است.

مقادیر `CSSRule.UNKNOWN_RULE` (`0`)، `CSSRule.CHARSET_RULE` (`2`)، `CSSRule.DOCUMENT_RULE` (`13`)، `CSSRule.VIEWPORT_RULE` (`14`) و `CSSRule.REGION_STYLE_RULE` (`16`) دیگر قابل دریافت نیستند.

## مثال‌ها

```js
const rules = document.styleSheets[0].cssRules;
console.log(rules[0].type);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}