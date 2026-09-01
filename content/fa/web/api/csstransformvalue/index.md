---
title: CSSTransformValue
slug: Web/API/CSSTransformValue
page-type: web-api-interface
browser-compat: api.CSSTransformValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابط **`CSSTransformValue`** در [API مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Object_Model) مقادیر `transform-list` را که توسط ویژگی CSS {{CSSxref('transform')}} استفاده می‌شوند، نمایش می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSTransformValue.CSSTransformValue", "CSSTransformValue()")}}
  - : یک شیء جدید `CSSTransformValue` می‌سازد.

## ویژگی‌های نمونه

- {{domxref("CSSTransformValue.length")}} {{ReadOnlyInline}}
  - : تعداد مؤلفه‌های تبدیل موجود در `CSSTransformValue` را برمی‌گرداند.
- {{domxref("CSSTransformValue.is2D")}} {{ReadOnlyInline}}
  - : یک مقدار بولی (boolean) برمی‌گرداند که نشان می‌دهد تبدیل دو بعدی است یا سه بعدی.

## روش‌های نمونه

_همچنین روش‌هایی را از رابط والد خود، {{DOMxRef("CSSStyleValue")}}، به ارث می‌برد._

- {{domxref("CSSTransformValue.toMatrix()")}}
  - : یک شیء جدید {{domxref('DOMMatrix')}} برمی‌گرداند.
- {{domxref('CSSTransformValue.entries()')}}
  - : یک آرایه از جفت‌های `[key, value]` ویژگی‌های قابل شمارش خود شیء را به همان ترتیبی که توسط حلقه {{jsxref("Statements/for...in", "for...in")}} ارائه می‌شود، برمی‌گرداند (تفاوت در این است که حلقه for-in ویژگی‌های زنجیره پروتوتایپ را نیز شمارش می‌کند).
- {{domxref('CSSTransformValue.forEach()')}}
  - : یک تابع داده شده را یک بار برای هر عنصر از شیء `CSSTransformValue` اجرا می‌کند.
- {{domxref('CSSTransformValue.keys()')}}
  - : یک شیء _تکرارگر آرایه_ جدید برمی‌گرداند که حاوی کلیدهای هر شاخص در شیء `CSSTransformValue` است.
- {{domxref('CSSTransformValue.values()')}}
  - : یک شیء _تکرارگر آرایه_ جدید برمی‌گرداند که حاوی مقادیر هر شاخص در شیء `CSSTransformValue` است.

## رابط‌های مبتنی بر CSSTransformValue

- {{domxref('CSSTranslate')}}
- {{domxref('CSSRotate')}}
- {{domxref('CSSScale')}}
- {{domxref('CSSSkew')}}
- {{domxref('CSSSkewX')}}
- {{domxref('CSSSkewY')}}
- {{domxref('CSSPerspective')}}
- {{domxref('CSSMatrixComponent')}}

## مثال‌ها

برای انجام.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}