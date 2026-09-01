---
title: "CSSTransition: transitionProperty property"
short-title: transitionProperty
slug: Web/API/CSSTransition/transitionProperty
page-type: web-api-instance-property
browser-compat: api.CSSTransition.transitionProperty
---

{{APIRef("Web Animations")}}

ویژگی **`transitionProperty`** در رابط {{domxref("CSSTransition")}}، **نام گسترش‌یافتهٔ ویژگی انتقال** (transition) را برمی‌گرداند. این، همان ویژگی CSS بلندنویسی (longhand) است که انتقال برای آن ایجاد شده است.

## مقدار

یک رشته (string).

## مثال‌ها

### بازگرداندن transitionProperty

در مثال زیر، انتقال، عرض جعبه را هنگام hover تغییر می‌دهد. فراخوانی {{domxref("Element.getAnimations()")}} آرایه‌ای از همهٔ اشیاء {{domxref("Animation")}} را برمی‌گرداند. در این مورد، یک شیء `CSSTransition` بازگردانده می‌شود که نمایانگر انیمیشن ایجادشده است. ویژگی `transitionProperty` نام ویژگی‌ای را برمی‌گرداند که انتقال برای آن ساخته شده است، یعنی `width`.

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
  console.log(animations[0].propertyName);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}