---
title: "CSSAnimation"
slug: Web/API/CSSAnimation
page-type: web-api-interface
browser-compat: api.CSSAnimation
---

{{APIRef("Web Animations")}}

رابط **`CSSAnimation`** از {{domxref('Web Animations API','','',' ')}} نشان‌دهنده یک شیء {{domxref("Animation")}} است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط ویژگی‌های خود را از والد خود، {{domxref("Animation")}} به ارث می‌برد._

- {{domxref("CSSAnimation.animationName")}} {{ReadOnlyInline}}
  - : نام انیمیشن را به صورت یک رشته برمی‌گرداند.

## روش‌های نمونه

_این رابط متدهای خود را از والد خود، {{domxref("Animation")}} به ارث می‌برد._

## مثال‌ها

### بررسی CSSAnimation برگشتی

انیمیشن در مثال زیر در CSS با نام `slide-in` تعریف شده است. فراخوانی {{domxref("Element.getAnimations()")}} یک آرایه از تمام اشیاء {{domxref("Animation")}} برمی‌گرداند. در مورد ما، این یک شیء `CSSAnimation` را برمی‌گرداند که نشان‌دهنده انیمیشن ایجاد شده در CSS است.

```css
.animate {
  animation: slide-in 0.7s both;
}

@keyframes slide-in {
  0% {
    transform: translateY(-1000px);
  }
  100% {
    transform: translateY(0);
  }
}
```

```js
let animations = document.querySelector(".animate").getAnimations();
console.log(animations[0]);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}