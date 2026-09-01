---
title: CSSKeyframesRule
slug: Web/API/CSSKeyframesRule
page-type: web-api-interface
browser-compat: api.CSSKeyframesRule
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSKeyframesRule`** شیئی را توصیف می‌کند که یک مجموعهٔ کامل از keyframeها را برای یک انیمیشن CSS نشان می‌دهد. این رابط با محتویات کل یک [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) از نوع {{cssxref("@keyframes")}} مطابقت دارد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از کلاس والد خود، {{domxref("CSSRule")}}، به ارث می‌برد._

- {{domxref("CSSKeyframesRule.name")}}
  - : نام keyframeها را نشان می‌دهد که توسط ویژگی {{cssxref("animation-name")}} استفاده می‌شود.
- {{domxref("CSSKeyframesRule.cssRules")}} {{ReadOnlyInline}}
  - : یک {{domxref("CSSRuleList")}} از keyframeهای موجود در فهرست را برمی‌گرداند.
- {{domxref("CSSKeyframesRule.length")}} {{ReadOnlyInline}}
  - : تعداد keyframeهای فهرست را برمی‌گرداند.

## روش‌های نمونه

_روش‌ها را از کلاس والد خود، {{domxref("CSSRule")}}، به ارث می‌برد._

- {{domxref("CSSKeyframesRule.appendRule()")}}
  - : یک قانون keyframe جدید را در CSSKeyframesRule فعلی درج می‌کند. پارامتر رشته‌ای است شامل یک keyframe با همان قالبی که در یک at-rule از نوع {{cssxref("@keyframes")}} استفاده می‌شود. اگر بیش از یک قانون keyframe داشته باشد، یک {{domxref("DOMException")}} با `SYNTAX_ERR` پرتاب می‌شود.
- {{domxref("CSSKeyframesRule.deleteRule()")}}
  - : یک قانون keyframe را از CSSKeyframesRule فعلی حذف می‌کند. پارامتر، ایندکس keyframe موردنظر برای حذف است که به‌صورت یک رشته بیان می‌شود و به عددی بین `0%` و `100%` تفسیر می‌شود.
- {{domxref("CSSKeyframesRule.findRule()")}}
  - : یک قانون keyframe متناظر با کلید داده‌شده را برمی‌گرداند. کلید رشته‌ای است شامل ایندکس keyframeای که باید برگردانده شود و به درصدی بین `0%` و `100%` تفسیر می‌شود. اگر چنین keyframeای وجود نداشته باشد، `findRule` مقدار `null` را برمی‌گرداند.

## مثال

### استفاده از CSSKeyframesRule

CSS شامل یک at-rule از نوع keyframes است. این، اولین {{domxref("CSSRule")}}ای خواهد بود که توسط `document.styleSheets[0].cssRules` برگردانده می‌شود. `myRules[0]` یک شیء `CSSKeyframesRule` برمی‌گرداند.

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
const myRules = document.styleSheets[0].cssRules;
const keyframes = myRules[0]; // a CSSKeyframesRule
```

### دسترسی به ایندکس‌ها

`CSSKeyframesRule` را می‌توان مانند یک آرایه ایندکس‌گذاری کرد و عملکردی مشابه ویژگی {{domxref("CSSKeyframesRule.cssRules", "cssRules")}} آن دارد.

```js
const keyframes = document.styleSheets[0].cssRules[0];

for (let i = 0; i < keyframes.length; i++) {
  console.log(keyframes[i].keyText);
}

// Output:
// 0%
// 100%
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@keyframes")}}
- {{domxref("CSSKeyFrameRule")}}