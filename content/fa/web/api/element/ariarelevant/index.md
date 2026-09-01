---
title: "Element: ariaRelevant property"
short-title: ariaRelevant
slug: Web/API/Element/ariaRelevant
page-type: web-api-instance-property
status:
  - non-standard
browser-compat: api.Element.ariaRelevant
---

{{APIRef("DOM")}}{{Non-standard_Header}}

خاصیت **`ariaRelevant`** از رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار صفت [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant) است که مشخص می‌کند وقتی درخت دسترسی‌پذیری درون یک ناحیهٔ زنده (live region) تغییر می‌کند، عامل کاربر چه اعلان‌هایی را ایجاد کند. این ویژگی برای توصیف این استفاده می‌شود که کدام تغییرات در یک ناحیهٔ `aria-live` مرتبط هستند و باید اعلام شوند.

## مقدار

یک رشته شامل یک یا چند مقدار از مقادیر زیر که با فاصله جدا شده‌اند:

- `"additions"`
  - : افزودن گره‌های عنصر (Element Nodes) درون ناحیهٔ زنده باید مرتبط در نظر گرفته شوند.
- `"removals"`
  - : حذف گره‌ها از ناحیهٔ زنده باید مرتبط در نظر گرفته شوند.
- `"text"`
  - : تغییرات در محتوای متنی گره‌های موجود باید مرتبط در نظر گرفته شوند.
- `"all"`
  - : معادل `"additions removals text"`.

## مثال‌ها

در این مثال، صفت [`aria-relevant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-relevant) روی عنصری با شناسهٔ `text` به `"all"` تنظیم شده است. با استفاده از `ariaRelevant` مقدار را به `"text"` به‌روزرسانی می‌کنیم.

```html
<div
  id="clock"
  role="timer"
  aria-live="polite"
  aria-atomic="true"
  aria-relevant="all"></div>
```

```js
let el = document.getElementById("clock");
console.log(el.ariaRelevant); // all
el.ariaRelevant = "text";
console.log(el.ariaRelevant); // text
```

## سازگاری با مرورگر

{{Compat}}