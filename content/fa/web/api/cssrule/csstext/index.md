---
title: "CSSRule: cssText property"
short-title: cssText
slug: Web/API/CSSRule/cssText
page-type: web-api-instance-property
browser-compat: api.CSSRule.cssText
---

{{APIRef("CSSOM") }}

ویژگی **`cssText`** در رابط {{domxref("CSSRule")}} متن واقعی یک قاعده‌ی سبک را از {{domxref("CSSStyleSheet")}} برمی‌گرداند.

> [!NOTE]
> این ویژگی را با {{domxref("CSSStyleDeclaration.cssText")}} که مربوط به استایلِ عنصر است، اشتباه نگیرید.

توجه داشته باشید که این ویژگی قبلاً تغییرپذیر بود، اما اکنون فقط‌خواندنی است. تلاش برای مقداردهی به آن _هیچ کاری انجام نمی‌دهد_ و حتی هیچ هشدار یا خطایی هم صادر نمی‌کند. علاوه بر این، هیچ زیرویژگی قابل تنظیمی ندارد. بنابراین، برای تغییر آن، از ویژگی‌های {{domxref("CSSRuleList", "cssRules[index]")}} شیوه‌نامه، یعنی {{domxref("CSSStyleRule.selectorText", ".selectorText")}} و {{domxref("CSSStyleRule.style", ".style")}} (یا زیرویژگی‌هایشان) استفاده کنید. برای جزئیات بیشتر، [Using dynamic styling information](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information) را ببینید.

## مقدار

یک رشته که متن واقعی قاعده‌ی {{domxref("CSSStyleSheet")}} را شامل می‌شود.

## مثال‌ها

```css
body {
  background-color: darkblue;
}
```

```js
let stylesheet = document.styleSheets[0];
console.log(stylesheet.cssRules[0].cssText); // body { background-color: darkblue; }
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}