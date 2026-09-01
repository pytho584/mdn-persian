---
title: "Element: ariaBusy property"
short-title: ariaBusy
slug: Web/API/Element/ariaBusy
page-type: web-api-instance-property
browser-compat: api.Element.ariaBusy
---

{{APIRef("DOM")}}

ویژگی **`ariaBusy`** در رابط {{domxref("Element")}} منعکس‌کننده مقدار ویژگی [`aria-busy`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy) است که نشان می‌دهد آیا عنصری در حال تغییر است یا خیر؛ فناوری‌های کمکی ممکن است بخواهند تا زمان تکمیل تغییرات، آن را در اختیار کاربر قرار ندهند.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `"true"`
  - : عنصر در حال به‌روزرسانی است.
- `"false"`
  - : هیچ به‌روزرسانی مورد انتظاری برای عنصر وجود ندارد.

## مثال‌ها

در این مثال، ویژگی `aria-busy` روی عنصری با شناسه `clock` روی `"false"` تنظیم شده است. با استفاده از `ariaBusy` مقدار آن را به `"true"` تغییر می‌دهیم.

```html
<div
  id="clock"
  role="timer"
  aria-live="polite"
  aria-atomic="true"
  aria-busy="false"></div>
```

```js
let el = document.getElementById("clock");
console.log(el.ariaBusy); // false
el.ariaBusy = "true";
console.log(el.ariaBusy); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}