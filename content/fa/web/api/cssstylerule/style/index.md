---
title: "CSSStyleRule: style property"
short-title: style
slug: Web/API/CSSStyleRule/style
page-type: web-api-instance-property
browser-compat: api.CSSStyleRule.style
---

{{ APIRef("CSSOM") }}

ویژگی فقط‑خواندنی **`style`** از واسط {{domxref("CSSStyleRule")}} یک شیء {{domxref("CSSStyleProperties")}} را شامل می‌شود که فهرست ویژگی‌های درون بدنهٔ این قانون سبک را نمایش می‌دهد.

هر [ویژگی CSS](/en-US/docs/Web/CSS/Reference/Properties) که توسط مرورگر پشتیبانی می‌شود، روی این شیء وجود دارد.
ویژگی‌هایی که درون اعلان CSS متناظر به‌صورت درون‌خطی (inline) تعریف نشده‌اند، برابر رشتهٔ خالی (`""`) تنظیم می‌شوند.

## مقدار

یک شیء {{domxref("CSSStyleProperties")}}.

> [!NOTE]
> نسخه‌های پیشین مشخصات یک {{domxref("CSSStyleDeclaration")}} را برمی‌گرداندند که اکنون کلاس پایهٔ {{domcursor("CSSStyleProperties")}} است.
> برای اطلاعات پشتیبانی مرورگر به جدول [سازگاری مرورگر](#browser_compatibility) مراجعه کنید.

اگرچه خود ویژگی `style` از این نظر فقط‑خواندنی است که نمی‌توانید شیء `CSSStyleProperties` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `style` مقداردهی کنید که معادل مقداردهی به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء `CSSStyleProperties` را با استفاده از روش‌های {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## مثال‌ها

### دریافت سبک‌های یک قانون سبک

CSS زیر قانون سبک را برای انتخاب‌گر `h1` تعریف می‌کند که در کد با یک نمونهٔ {{domxref("CSSStyleRule")}} نمایش داده می‌شود.
بلاک اعلان، آن بخش از قانون سبک است که درون آکولاد ظاهر می‌شود و در واقع تعاریف سبک را ارائه می‌دهد (برای انتخاب‌گر، بخشی که قبل از آکولاد می‌آید)، که در کد با ویژگی `style` نمایش داده می‌شود.

```css
h1 {
  color: pink;
}
```

با فرض اینکه قانون سبک بالا اولین قانون در سند باشد، اولین {{domxref("CSSRule")}} بازگشتی از `document.styleSheets[0].cssRules` خواهد بود.
`myRules[0].style` یک شیء {{domxref("CSSStyleProperties")}} را برمی‌گرداند که اعلان‌های تعریف‌شده برای `h1` را نمایش می‌دهد.

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].style); // یک CSSStyleProperties که اعلان‌های روی h1 را نمایش می‌دهد.
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}