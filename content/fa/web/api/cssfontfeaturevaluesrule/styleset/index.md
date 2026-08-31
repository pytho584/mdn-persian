---
title: "CSSFontFeatureValuesRule: styleset property"
short-title: styleset
slug: Web/API/CSSFontFeatureValuesRule/styleset
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesRule.styleset
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **styleset** در رابط {{domXRef("CSSFontFeatureValuesRule")}} شامل یک شیء {{domXRef("CSSFontFeatureValuesMap")}} است که [شناسه تعریف‌شده توسط کاربر](/en-US/docs/Web/CSS/Reference/Values/custom-ident) و [اندیس ویژگی](/en-US/docs/Web/CSS/Reference/Properties/font-feature-settings#optional_value) را برای یک فونت متغیر که از {{CSSXRef("font-variant-alternates", "styleset()", "#styleset")}} پشتیبانی می‌کند، نمایش می‌دهد.

## مقدار

یک شیء {{domxref("CSSFontFeatureValuesMap")}}.

اگرچه خود ویژگی `styleset` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `CSSFontFeatureValuesMap` را جایگزین کنید، همچنان می‌توانید مستقیماً به ویژگی `styleset` مقدار نسبت دهید. همچنین می‌توانید مقادیر `styleset` را با استفاده از [متدهای نمونه `CSSFontFeatureValuesMap`](/en-US/docs/Web/API/CSSFontFeatureValuesMap#instance_methods) تغییر دهید.

## مثال

### استفاده پایه

#### CSS

```css
@font-feature-values "MonteCarlo" {
  @styleset {
    my-styleset: 1;
  }
}
```

#### جاوااسکریپت

```js
// به دنبال اولین شیوه‌نامه و اولین قانون CSS در آن شیوه‌نامه می‌گردیم
const myRule = document.styleSheets[0].cssRules[0];
// بررسی
if (myRule instanceof CSSFontFeatureValuesRule && myRule.styleset.size) {
  // کاری با styleset انجام دهید
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxRef("@font-feature-values","@styleset","#styleset")}}
- نماد تابعی {{cssxRef("font-variant-alternates","styleset()","#styleset")}}
- {{domxref("CSSFontFeatureValuesMap")}}