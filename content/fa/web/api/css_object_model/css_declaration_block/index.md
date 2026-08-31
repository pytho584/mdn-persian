---
title: "CSS Declaration Block"
---

---
title: CSS Declaration Block
slug: Web/API/CSS_Object_Model/CSS_Declaration_Block
page-type: guide
spec-urls: https://drafts.csswg.org/cssom/#css-declaration-blocks
---

{{DefaultAPISidebar("CSSOM")}}

یک **بلوک اعلامیه CSS** مجموعه‌ای مرتب از ویژگی‌ها و مقادیر CSS است. در DOM به صورت یک {{domxref("CSSStyleDeclaration")}} نمایش داده می‌شود.

هر جفت ویژگی و مقدار به عنوان یک [اعلامیه CSS](/en-US/docs/Web/API/CSS_Object_Model/CSS_Declaration) شناخته می‌شود. بلوک اعلامیه CSS دارای ویژگی‌های مرتبط زیر است:

- computed flag
  - : اگر شیء {{domxref("CSSStyleDeclaration")}} یک سبک محاسبه‌شده (computed) باشد به جای سبک مشخص‌شده (specified)، تنظیم می‌شود. به طور پیش‌فرض تنظیم نیست.
- declarations
  - : [اعلامیه‌های CSS](/en-US/docs/Web/API/CSS_Object_Model/CSS_Declaration) مرتبط با این شیء.
- parent CSS rule
  - : {{domxref("CSSRule")}} که بلوک اعلامیه CSS با آن مرتبط است، در غیر این صورت null.
- owner node
  - : {{domxref("element")}} که بلوک اعلامیه CSS با آن مرتبط است، در غیر این صورت null.
- updating flag
  - : هنگامی که بلوک اعلامیه CSS در حال به‌روزرسانی ویژگی [`style`](/en-US/docs/Web/HTML/Reference/Global_attributes/style) گره مالک است، تنظیم می‌شود.

هنگامی که یک {{domxref("CSSStyleDeclaration")}} توسط یک رابط [CSS Object Model (CSSOM)](/en-US/docs/Web/API/CSS_Object_Model) بازگردانده می‌شود، این ویژگی‌ها با توجه به مشخصات به مقادیر مناسب تنظیم می‌شوند.

## مثال پایه

مثال زیر یک قانون CSS را با یک بلوک اعلامیه برای عنصر {{htmlelement("Heading_Elements","h1")}} نشان می‌دهد. بلوک اعلامیه CSS خطوط بین آکولادها است.

```css
h1 {
  margin: 0 auto;
  font-family: "Helvetica Neue", "Arial", sans-serif;
  font-style: italic;
  color: rebeccapurple;
}
```

می‌توانیم یک {{domxref("CSSStyleDeclaration")}} که نماینده این بلوک اعلامیه CSS است را با استفاده از {{domxref("CSSStyleRule.style")}} بازگردانیم.

```js
let myRules = document.styleSheets[0].cssRules;
let rule = myRules[0]; // a CSSStyleRule
console.log(rule.style); // a CSSStyleDeclaration object
```

## مشخصات

{{Specifications}}