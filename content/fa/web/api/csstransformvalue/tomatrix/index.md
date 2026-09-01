---
title: "CSSTransformValue: toMatrix() method"
short-title: toMatrix()
slug: Web/API/CSSTransformValue/toMatrix
page-type: web-api-instance-method
browser-compat: api.CSSTransformValue.toMatrix
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`toMatrix()`** از رابط {{domxref("CSSTransformValue")}} یک شیء {{domxref('DOMMatrix')}} را برمی‌گرداند.

## نحو

```js-nolint
toMatrix()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک شیء {{domxref('DOMMatrix')}}.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر هر یک از طول‌های دخیل در تولید ماتریس با واحد px سازگار نباشند (مانند طول‌های نسبی یا درصدها) این خطا رخ می‌دهد.

## مثال‌ها

در دست نگارش

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}