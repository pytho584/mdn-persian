---
title: "CSSTransformComponent: toString() method"
short-title: toString()
slug: Web/API/CSSTransformComponent/toString
page-type: web-api-instance-method
browser-compat: api.CSSTransformComponent.toString
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`toString()`** از رابط {{domxref("CSSTransformComponent")}} یک {{Glossary("stringifier")}} است که یک تابع [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms) را برمی‌گرداند.

## نحو

```js-nolint
toString()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک رشته به شکل یک [تابع تبدیل](/en-US/docs/Web/CSS/Reference/Values/transform-function) CSS.

این متد از مقدار `is2D` برای بازگرداندن یک تبدیل دو بعدی یا سه بعدی استفاده می‌کند.
برای مثال، اگر مؤلفه نمایانگر {{domxref("CSSRotate")}} باشد و `is2D` نادرست (false) باشد، رشته بازگشتی به شکل تابع تبدیل CSS {{cssxref("transform-function/rotate3d", "rotate3d()")}} خواهد بود.
اگر درست (true) باشد، رشته بازگشتی به شکل تابع دو بعدی {{cssxref("transform-function/rotate", "rotate()")}} خواهد بود.

## مثال‌ها

برای انجام

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}
```