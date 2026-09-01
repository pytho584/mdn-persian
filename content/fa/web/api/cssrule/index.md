---
title: CSSRule
slug: Web/API/CSSRule
page-type: web-api-interface
browser-compat: api.CSSRule
---

{{APIRef("CSSOM")}}

رابط **`CSSRule`** یک قانون منفرد CSS را نمایش می‌دهد. چندین نوع قانون وجود دارند که ویژگی‌های خود را از `CSSRule` به ارث می‌برند.

- {{DOMXRef("CSSGroupingRule")}}
- {{DOMXRef("CSSStyleRule")}}
- {{DOMXRef("CSSImportRule")}}
- {{DOMXRef("CSSMediaRule")}}
- {{DOMXRef("CSSFontFaceRule")}}
- {{DOMxRef("CSSFunctionDeclarations")}}
- {{DOMXRef("CSSPageRule")}}
- {{DOMXRef("CSSNamespaceRule")}}
- {{DOMXRef("CSSKeyframesRule")}}
- {{DOMXRef("CSSKeyframeRule")}}
- {{DOMXRef("CSSCounterStyleRule")}}
- {{DOMXRef("CSSSupportsRule")}}
- {{DOMXRef("CSSFontFeatureValuesRule")}}
- {{DOMXRef("CSSFontPaletteValuesRule")}}
- {{DOMXRef("CSSLayerBlockRule")}}
- {{DOMXRef("CSSLayerStatementRule")}}
- {{DOMXRef("CSSPropertyRule")}}
- {{DOMXRef("CSSNestedDeclarations")}}
- {{DOMXRef("CSSViewTransitionRule")}}

## ویژگی‌های نمونه

رابط `CSSRule` ویژگی‌های مشترک میان همهٔ قوانین را مشخص می‌کند، در حالی که ویژگی‌های منحصربه‌فرد برای انواع خاص قانون در رابط‌های تخصصی‌تر آن انواع قانون تعریف شده‌اند.

- {{domxref("CSSRule.cssText")}}
  - : نمایش متنی قانون را نشان می‌دهد، برای مثال `"h1,h2 { font-size: 16pt }"` یا `"@import 'url'"`. برای دسترسی یا تغییر بخش‌هایی از قانون (مثلاً مقدار `font-size` در مثال بالا) از ویژگی‌های رابط تخصصی آن نوع قانون استفاده کنید (به بالا مراجعه کنید).
- {{domxref("CSSRule.parentRule")}} {{ReadOnlyInline}}
  - : قانون والد را برمی‌گرداند، در غیر این صورت `null`. برای مثال اگر این قانون یک قانون استایل درون یک بلوک {{cssxref("@media")}} باشد، قانون والد همان {{domxref("CSSMediaRule")}} خواهد بود.
- {{domxref("CSSRule.parentStyleSheet")}} {{ReadOnlyInline}}
  - : شیء {{domxref("CSSStyleSheet")}} مربوط به برگه‌ی استایلی که این قانون را شامل می‌شود برمی‌گرداند.
- {{domxref("CSSRule.type")}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : یکی از ثابت‌های نوع را برای تعیین نوع قانون بازمی‌گرداند.

## مثال‌ها

می‌توان با بررسی فهرست `cssRules` یک {{domxref("CSSStyleSheet")}} به ارجاع‌هایی از `CSSRule` دست یافت.

```js
let myRules = document.styleSheets[0].cssRules; // یک CSSRuleList برمی‌گرداند
console.log(myRules);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)