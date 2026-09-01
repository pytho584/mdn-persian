---
title: "HTMLElement: writingSuggestions property"
short-title: writingSuggestions
slug: Web/API/HTMLElement/writingSuggestions
page-type: web-api-instance-property
browser-compat: api.HTMLElement.writingSuggestions
---

{{APIRef("HTML DOM")}}

ویژگی **`writingSuggestions`** از رابط {{domxref("HTMLElement")}} یک رشته است که نشان می‌دهد آیا پیشنهادهای نوشتاری ارائه‌شده توسط مرورگر باید در محدودهٔ این عنصر فعال شوند یا خیر.

این ویژگی منعکس‌کنندهٔ مقدار ویژگی عمومی HTML [`writingsuggestions`](/en-US/docs/Web/HTML/Reference/Global_attributes/writingsuggestions) است.

## مقدار

یک مقدار شمارشی؛ مقادیر ممکن:

- `"true"`
  - : مرورگر به‌طور خودکار صفحه‌کلید مجازی را هنگامی که کاربر روی عنصر ضربه می‌زند یا آن را متمرکز می‌کند، نمایش می‌دهد.
- `"false"`
  - : مرورگر به‌طور خودکار صفحه‌کلید مجازی را نمایش نمی‌دهد: نمایش/پنهان کردن صفحه‌کلید مجازی به‌صورت دستی توسط اسکریپت مدیریت می‌شود.

## مثال‌ها

مثال زیر نحوهٔ غیرفعال کردن پیشنهادهای نوشتاری ارائه‌شده توسط عامل‌های کاربر را از طریق اسکریپت نشان می‌دهد:

```js
const element = document.querySelector("input");

// disable user agent writing suggestions
element.writingSuggestions = "false";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [`writingsuggestions`](/en-US/docs/Web/HTML/Reference/Global_attributes/writingsuggestions) ویژگی عمومی HTML