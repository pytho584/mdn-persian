---
title: "CSSAnimation: animationName property"
short-title: animationName
slug: Web/API/CSSAnimation/animationName
page-type: web-api-instance-property
browser-compat: api.CSSAnimation.animationName
---

{{APIRef("Web Animations")}}

ویژگی **`animationName`** از رابط {{domxref("CSSAnimation")}} مقدار {{CSSXref("animation-name")}} را برمی‌گرداند. این ویژگی یک یا چند at-rule keyframe را مشخص می‌کند که انیمیشن اعمال‌شده به عنصر را توصیف می‌کنند.

## مقدار

یک رشته.

## مثال‌ها

### بازگرداندن animationName

انیمیشن در مثال زیر در CSS با نام `slide-in` تعریف شده است. فراخوانی {{domxref("Element.getAnimations()")}} یک آرایه از تمام اشیاء {{domxref("Animation")}} را برمی‌گرداند. ویژگی `animationName` نام داده شده به انیمیشن را برمی‌گرداند، که در اینجا `slide-in` است.

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
console.log(animations[0].animationName);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}