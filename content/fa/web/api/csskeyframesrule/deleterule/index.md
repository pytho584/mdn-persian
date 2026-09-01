---
title: "CSSKeyframesRule: deleteRule() method"
short-title: deleteRule()
slug: Web/API/CSSKeyframesRule/deleteRule
page-type: web-api-instance-method
browser-compat: api.CSSKeyframesRule.deleteRule
---

{{APIRef("CSSOM") }}

متد **`deleteRule()`** در رابط {{domxref("CSSKeyframeRule")}}، قانون {{domxref("CSSKeyFrameRule")}}ای را که با انتخابگر keyframe مشخصشده همخوانی دارد حذف میکند.

## Syntax

```js-nolint
deleteRule(select)
```

### پارامترها

- `select`
  - : رشتهای شامل [انتخابگر keyframe](/en-US/docs/Web/CSS/Reference/Selectors/Keyframe_selectors) قانون موردنظر برای حذف، که باید یکی از اینها باشد:
    - فهرستی از مقادیر درصدی که با کاما از هم جدا شدهاند، بین ۰٪ و ۱۰۰٪؛
    - یا کلیدواژههای `from` یا `to`.

    توجه داشته باشید که تعداد و ترتیب مقادیر در انتخابگر keyframe مشخصشده باید با قانون(های) keyframe هدف مطابقت داشته باشد. فاصلههای خالی نادیده گرفته میشوند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثالها

CSS شامل یک at-rule به نام keyframes است. این قانون، اولین {{domxref("CSSRule")}} خواهد بود که توسط `document.styleSheets[0].cssRules` بازگردانده میشود.
`myRules[0]` یک شیء {{domxref("CSSKeyframesRule")}} برمیگرداند. بازگرداندن ویژگی `cssRules` یک {{domxref("CSSRuleList")}} شامل دو قانون را برمیگرداند.

پس از حذف یک قانون با استفاده از `deleteRule()`، ویژگی `cssRules` یک {{domxref("CSSRuleList")}} شامل یک قانون را برمیگرداند.

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
keyframes.deleteRule("to");
console.log(keyframes.cssRules); // یک شیء CSSRuleList با یک قانون
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}