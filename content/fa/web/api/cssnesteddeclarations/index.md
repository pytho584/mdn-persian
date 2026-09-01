---
title: CSSNestedDeclarations
slug: Web/API/CSSNestedDeclarations
page-type: web-api-interface
browser-compat: api.CSSNestedDeclarations
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSNestedDeclarations`** در [CSS Rule API](/en-US/docs/Web/API/CSSRule) برای گروه‌بندی {{domxref("CSSRule")}}های تو در تو به کار می‌رود.

این رابط به [CSS Object Model (CSSOM)](/en-US/docs/Web/API/CSS_Object_Model) اجازه می‌دهد ساختار اسناد CSS با قواعد تو در تو را بازتاب دهد و اطمینان حاصل کند که قواعد به ترتیب اعلام‌شده تجزیه و ارزیابی می‌شوند.

> [!NOTE]
> پیاده‌سازی‌هایی که از این رابط پشتیبانی نمی‌کنند ممکن است قواعد تو در تو را به ترتیب اشتباه تجزیه کنند.
> برای اطلاعات بیشتر به [سازگاری مرورگرها](#browser_compatibility) مراجعه کنید.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از جد خود {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSNestedDeclarations.style")}} {{ReadOnlyInline}}
  - : مقادیر قواعد تو در تو را برمی‌گرداند.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از جد خود {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

### CSS

CSS زیر شامل یک انتخاب‌گر `.foo` است که دو اعلان و یک media query دارد.

```css
.foo {
  background-color: silver;
  @media screen {
    color: tomato;
  }
  color: black;
}
```

این ساختار توسط چند شیء جاوااسکریپت در [CSS Object Model](/en-US/docs/Web/API/CSS_Object_Model) نمایش داده می‌شود:

- یک شیء {{domxref("CSSStyleRule")}} که قاعدهٔ `background-color: silver` را نشان می‌دهد.
  این شیء را می‌توان از طریق `document.styleSheets[0].cssRules[0]` دریافت کرد.
- یک شیء {{domxref("CSSMediaRule")}} که قاعدهٔ `@media screen` را نشان می‌دهد و از طریق `document.styleSheets[0].cssRules[0].cssRules[0]` قابل دریافت است.
  - شیء `CSSMediaRule` شامل یک شیء `CSSNestedDeclaration` است که قاعدهٔ `color: tomato` را نشان می‌دهد و توسط قاعدهٔ `@media screen` تو در تو قرار گرفته است.
    این شیء را می‌توان از طریق `document.styleSheets[0].cssRules[0].cssRules[0].cssRules[0]` دریافت کرد.
- آخرین قاعده یک شیء `CSSNestedDeclaration` است که قاعدهٔ `color: black` را در شیوه‌نامه نشان می‌دهد و از طریق `document.styleSheets[0].cssRules[0].cssRules[1]` قابل دریافت است.

> [!NOTE]
> تمام styleهای سطح بالای بعد از اولین `CSSNestedDeclaration` نیز باید به‌عنوان اشیاء `CSSNestedDeclaration` نمایش داده شوند تا با [قاعدهٔ اعلان‌های تو در تو در CSS](/en-US/docs/Web/CSS/Guides/Nesting/Using#nested_declarations_rule) مطابقت داشته باشند.

### CSSOM (مدل شیء CSS)

```plain
↳ CSSStyleRule
  .style
    - background-color: silver
  ↳ CSSMediaRule
    ↳ CSSNestedDeclarations
      .style (CSSStyleDeclaration, 1) =
      - color: tomato
  ↳ CSSNestedDeclarations
    .style (CSSStyleDeclaration, 1) =
      - color: black
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CSSNestedDeclarations.style")}}
- [قاعدهٔ اعلان‌های تو در تو](/en-US/docs/Web/CSS/Guides/Nesting/Using#nested_declarations_rule)