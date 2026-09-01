---
title: "CSSKeyframesRule: findRule() method"
short-title: findRule()
slug: Web/API/CSSKeyframesRule/findRule
page-type: web-api-instance-method
browser-compat: api.CSSKeyframesRule.findRule
---

{{APIRef("CSSOM") }}

متد **`findRule()`** از رابط {{domxref("CSSKeyframeRule")}}، قاعده‌ی {{domxref("CSSKeyFrameRule")}} را می‌یابد که با انتخابگر keyframe مشخص‌شده مطابقت دارد.

## Syntax

```js-nolint
findRule(select)
```

### پارامترها

- `select`
  - : رشته‌ای که شامل [انتخابگر keyframe](/en-US/docs/Web/CSS/Reference/Selectors/Keyframe_selectors) قاعده‌ی موردنظر برای یافتن است. این رشته باید یکی از موارد زیر باشد:
    - فهرستی از مقادیر درصدی بین 0٪ و 100٪ که با کاما از هم جدا شده‌اند؛
    - یا کلیدواژه‌های `from` یا `to`

    توجه داشته باشید که تعداد و ترتیب مقادیر در انتخابگر keyframe مشخص‌شده باید با قاعده(های) keyframe هدف مطابقت داشته باشد. فاصله‌های خالی نادیده گرفته می‌شوند.

### مقدار بازگشتی

یک {{domxref("CSSKeyframeRule")}} که آخرین قاعده‌ی منطبق است. اگر هیچ قاعده‌ای یافت نشود، چیزی بازگردانده نمی‌شود.

## مثال‌ها

CSS شامل یک at-rule از نوع keyframes است. این قاعده، اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده می‌شود.
`myRules[0]` یک شیء {{domxref("CSSKeyframesRule")}} برمی‌گرداند. فراخوانی `findRule("to")` یک {{domxref("CSSKeyframeRule")}} بازمی‌گرداند که نمایانگر قاعده‌ی دوم است.

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
let keyframes = myRules[0]; // یک CSSKeyframesRule
console.log(keyframes.findRule("to")); // یک شیء CSSKeyframeRule
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}