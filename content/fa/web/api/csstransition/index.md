---
title: CSSTransition
slug: Web/API/CSSTransition
page-type: web-api-interface
browser-compat: api.CSSTransition
---

{{APIRef("Web Animations")}}

رابط **`CSSTransition`** از {{domxref('Web Animations API','','',' ')}} یک شی {{domxref("Animation")}} را نشان می‌دهد که برای یک [CSS Transition](/en-US/docs/Web/CSS/Guides/Transitions) استفاده می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط ویژگی‌هایی را از والد خود، {{domxref("Animation")}} به ارث می‌برد._

- {{domxref("CSSTransition.transitionProperty")}} {{ReadOnlyInline}}
  - : نام خاصیت CSS انتقال را به صورت یک رشته برمی‌گرداند.

## روش‌های نمونه

_این رابط روش‌هایی را از والد خود، {{domxref("Animation")}} به ارث می‌برد._

هیچ روش خاصی ندارد.

## مثال‌ها

### بررسی CSSTransition برگشتی

انتقال در مثال زیر عرض جعبه را هنگام هاور تغییر می‌دهد. فراخوانی {{domxref("Element.getAnimations()")}} یک آرایه از تمام اشیاء {{domxref("Animation")}} بازمی‌گرداند. در مورد ما این یک شیء `CSSTransition` را بازمی‌گرداند که نشان‌دهنده انیمیشن ایجاد شده است.

```css
.box {
  background-color: #165baa;
  color: white;
  width: 100px;
  height: 100px;
  transition: width 4s;
}

.box:hover {
  width: 200px;
}
```

```js
const item = document.querySelector(".box");
item.addEventListener("transitionrun", () => {
  let animations = document.querySelector(".box").getAnimations();
  console.log(animations[0]);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}