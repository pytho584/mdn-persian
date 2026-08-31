---
title: "CSSFontFeatureValuesRule: ornaments property"
---

---
title: "CSSFontFeatureValuesRule: ornaments property"
short-title: ornaments
slug: Web/API/CSSFontFeatureValuesRule/ornaments
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesRule.ornaments
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **ornaments** در رابط {{domXRef("CSSFontFeatureValuesRule")}} شامل یک شیء {{domXRef("CSSFontFeatureValuesMap")}} است که [شناسه تعریف‌شده توسط کاربر](/en-US/docs/Web/CSS/Reference/Values/custom-ident) و [شاخص ویژگی](/en-US/docs/Web/CSS/Reference/Properties/font-feature-settings#optional_value) را برای یک فونت متغیر که از {{CSSXRef("font-variant-alternates", "ornaments()", "#ornaments")}} پشتیبانی می‌کند، نمایش می‌دهد.

## مقدار

یک شیء {{domxref("CSSFontFeatureValuesMap")}}.

اگرچه خود ویژگی `ornaments` از این نظر فقط‌خواندنی است که نمی‌توانید شیء `CSSFontFeatureValuesMap` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `ornaments` مقداردهی کنید. همچنین می‌توانید با استفاده از [متدهای نمونه `CSSFontFeatureValuesMap`](/en-US/docs/Web/API/CSSFontFeatureValuesMap#instance_methods) مقادیر `ornaments` را تغییر دهید.

## مثال

### کاربرد پایه

#### CSS

```css
@font-feature-values "MonteCarlo" {
  @ornaments {
    my-ornaments: 1;
  }
}
```

#### جاوااسکریپت

```js
// look for the first stylesheet and the first cssRule in that sheet
const myRule = document.styleSheets[0].cssRules[0];
// check
if (myRule instanceof CSSFontFeatureValuesRule && myRule.ornaments.size) {
  // do something with the ornaments
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{cssxRef("@font-feature-values","@ornaments","#ornaments")}}
- {{cssxRef("font-variant-alternates","ornaments()","#ornaments")}} نشانه‌گذاری تابعی
- {{domxref("CSSFontFeatureValuesMap")}}