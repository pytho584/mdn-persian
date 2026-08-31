---
title: "CSSKeyframeRule: keyText property"
short-title: keyText
slug: Web/API/CSSKeyframeRule/keyText
page-type: web-api-instance-property
browser-compat: api.CSSKeyframeRule.keyText
---

{{APIRef("CSSOM") }}

ویژگی **`keyText`** در رابط {{domxref("CSSKeyframeRule")}} نشان‌دهندهٔ [انتخابگر keyframe](/en-US/docs/Web/CSS/Reference/Selectors/Keyframe_selectors) به صورت فهرستی از مقادیر درصدی است که با ویرگول از هم جدا شده‌اند. کلمات کلیدی `from` و `to` به ترتیب به `0%` و `100%` نگاشت می‌شوند.

## مقدار

یک رشته.

### استثناها

- {{jsxref("SyntaxError")}}
  - : اگر `keyText` با یک انتخابگر keyframe نامعتبر به‌روزرسانی شود، این خطا پرتاب می‌شود؛ در این صورت `keyText` بدون تغییر باقی می‌ماند.

## مثال‌ها

CSS شامل یک at-rule کلیدفریم است. این اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده می‌شود.
`myRules[0]` یک شیء {{domxref("CSSKeyframesRule")}} برمی‌گرداند که شامل اشیاء جداگانهٔ {{domxref("CSSKeyFrameRule")}} برای هر کلیدفریم است.

```css
@keyframes slide-in {
  from {
    transform: translateX(0%);
  }

  to {
    transform: translateX(100%);
  }
}
```

```js
let myRules = document.styleSheets[0].cssRules;
let keyframes = myRules[0]; // a CSSKeyframesRule
console.log(keyframes[0].keyText); // a string containing 0%
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}