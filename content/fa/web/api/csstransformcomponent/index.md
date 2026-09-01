---
title: CSSTransformComponent
slug: Web/API/CSSTransformComponent
page-type: web-api-interface
browser-compat: api.CSSTransformComponent
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

**`CSSTransformComponent`** متعلق به [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Object_Model) است و بخشی از رابط {{domxref('CSSTransformValue')}} به شمار می‌رود.

## ویژگی‌های نمونه

- {{domxref("CSSTransformComponent.is2D")}}
  - : یک مقدار بولی که نشان می‌دهد تبدیل (transform) دو بعدی است یا سه بعدی.

## روش‌های نمونه

- {{domxref("CSSTransformComponent.toMatrix()")}}
  - : یک شیء جدید {{domxref('DOMMatrix')}} بازمی‌گرداند.
- {{domxref("CSSTransformComponent.toString()")}}
  - : یک رشته به شکل یک [تابع تبدیل](/en-US/docs/Web/CSS/Reference/Values/transform-function) CSS.

    این متد از مقدار `is2D` برای بازگرداندن یک تبدیل دو بعدی یا سه بعدی استفاده می‌کند. برای مثال، اگر مؤلفه نشان‌دهنده {{domxref("CSSRotate")}} باشد و `is2D` برابر `false` باشد، رشته بازگردانده‌شده به شکل تابع تبدیل CSS {{cssxref("transform-function/rotate3d", "rotate3d()")}} خواهد بود. اگر `true` باشد، رشته بازگردانده‌شده به شکل تابع دو بعدی {{cssxref("transform-function/rotate", "rotate()")}} خواهد بود.

## رابط‌های مبتنی بر CSSTransformComponent

- {{domxref('CSSTranslate')}}
- {{domxref('CSSRotate')}}
- {{domxref('CSSScale')}}
- {{domxref('CSSSkew')}}
- {{domxref('CSSSkewX')}}
- {{domxref('CSSSkewY')}}
- {{domxref('CSSPerspective')}}
- {{domxref('CSSMatrixComponent')}}

## مثال‌ها

در دست اقدام

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}