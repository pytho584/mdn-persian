---
title: "HTMLFormElement: reset() method"
---

---
title: "HTMLFormElement: reset() method"
short-title: reset()
slug: Web/API/HTMLFormElement/reset
page-type: web-api-instance-method
browser-compat: api.HTMLFormElement.reset
---

{{APIRef("HTML DOM")}}

متد **`HTMLFormElement.reset()`** مقادیر پیش‌فرض عنصر فرم را بازیابی می‌کند. این متد همان کاری را انجام می‌دهد که کلیک روی کنترل [`<input type="reset">`](/en-US/docs/Web/HTML/Reference/Elements/input/reset) فرم انجام می‌دهد.

اگر یک کنترل فرم (مانند دکمهٔ بازنشانی) نام یا شناسهٔ `_reset_` داشته باشد، متد `reset` فرم را می‌پوشاند. این متد سایر ویژگی‌های عنصر `input`، مانند `disabled` را بازنشانی نمی‌کند.

توجه داشته باشید که اگر {{domxref("Element.setAttribute", "setAttribute()")}} برای تنظیم مقدار یک ویژگی خاص فراخوانی شود، فراخوانی بعدی `reset()` آن ویژگی را به مقدار پیش‌فرض خود بازنشانی نمی‌کند؛ بلکه ویژگی را در همان مقداری نگه می‌دارد که فراخوانی {{domxref("Element.setAttribute", "setAttribute()")}} آن را تنظیم کرده است.

## نحو

```js-nolint
reset()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
document.getElementById("my-form").reset();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}