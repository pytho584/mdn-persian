```yaml
---
title: "CSSFontFeatureValuesRule: annotation property"
short-title: annotation
slug: Web/API/CSSFontFeatureValuesRule/annotation
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSFontFeatureValuesRule.annotation
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **annotation** از رابط {{domXRef("CSSFontFeatureValuesRule")}} یک شیء {{domXRef("CSSFontFeatureValuesMap")}} را شامل می‌شود که نمایانگر یک [شناسه سفارشی تعریف‌شده توسط کاربر](/en-US/docs/Web/CSS/Reference/Values/custom-ident) و [شاخص ویژگی](/en-US/docs/Web/CSS/Reference/Properties/font-feature-settings#optional_value) برای یک فونت متغیر است که از {{CSSXRef("font-variant-alternates", "annotation()", "#annotation")}} پشتیبانی می‌کند.

## مقدار

یک شیء {{domxref("CSSFontFeatureValuesMap")}}.

اگرچه خود ویژگی `annotation` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `CSSFontFeatureValuesMap` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `annotation` مقداردهی کنید. همچنین می‌توانید مقادیر `annotation` را با استفاده از [متدهای نمونه `CSSFontFeatureValuesMap`](/en-US/docs/Web/API/CSSFontFeatureValuesMap#instance_methods) تغییر دهید.

## مثال‌ها

### استفاده پایه

#### CSS

```css
@font-feature-values "MonteCarlo" {
  @annotation {
    my-annotations: 1;
  }
}
```

#### JavaScript

```js
// اولین شیوه‌نامه و اولین قانون css در آن را پیدا کنید
const myRule = document.styleSheets[0].cssRules[0];
// بررسی کنید
if (myRule instanceof CSSFontFeatureValuesRule && myRule.annotation.size) {
  // کاری با annotation انجام دهید
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxRef("@font-feature-values","@annotation","#annotation")}}
- نشانه‌گذاری تابعی {{cssxRef("font-variant-alternates","annotation()","#annotation")}}
- {{domxref("CSSFontFeatureValuesMap")}}
```