---
title: "CSSFontFeatureValuesRule: swash property"
short-title: swash
slug: Web/API/CSSFontFeatureValuesRule/swash
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesRule.swash
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

ویژگیِ فقط‌خواندنی **`swash`** در رابط {{domXRef("CSSFontFeatureValuesRule")}} یک شیء {{domXRef("CSSFontFeatureValuesMap")}} را نگه می‌دارد که نشان‌دهندهٔ [نام تعریف‌شده توسط توسعه‌دهنده](/en-US/docs/Web/CSS/Reference/Values/custom-ident) و [شاخص ویژگی](/en-US/docs/Web/CSS/Reference/Properties/font-feature-settings#optional_value) برای یک فونت متغیر است که از {{CSSXRef("font-variant-alternates", "swash()", "#swash")}} پشتیبانی می‌کند.

## مقدار

یک شیء {{domxref("CSSFontFeatureValuesMap")}}.

اگرچه خود ویژگی `swash` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `CSSFontFeatureValuesMap` را جایگزین کنید، همچنان می‌توانید مستقیماً به ویژگی `swash` مقدار اختصاص دهید. همچنین می‌توانید مقادیر `swash` را با استفاده از [متدهای نمونهٔ `CSSFontFeatureValuesMap`](/en-US/docs/Web/API/CSSFontFeatureValuesMap#instance_methods) تغییر دهید.

## مثال

### استفادهٔ پایه

#### CSS

```css
@font-feature-values "MonteCarlo" {
  @swash {
    my-swashes: 1; /* نام سفارشی برای مجموعه‌ای خاص از گلیف‌های جایگزین swash */
  }
}
```

#### جاوااسکریپت

```js
// به دنبال اولین استایل‌شیت و اولین قانون css در آن بگرد
const myRule = document.styleSheets[0].cssRules[0];
// بررسی کن
if (myRule instanceof CSSFontFeatureValuesRule && myRule.swash.size) {
  // کاری با swash انجام بده
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{cssxRef("@font-feature-values","@swash","#swash")}}
- نشانه‌گذاری تابعی {{cssxRef("font-variant-alternates","swash()","#swash")}}
- {{domxref("CSSFontFeatureValuesMap")}}