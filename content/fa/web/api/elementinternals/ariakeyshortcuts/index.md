---
title: "ElementInternals: ariaKeyShortcuts property"
short-title: ariaKeyShortcuts
slug: Web/API/ElementInternals/ariaKeyShortcuts
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaKeyShortcuts
---

{{APIRef("Web Components")}}

ویژگی **`ariaKeyShortcuts`** از رابط {{domxref("ElementInternals")}} منعکس‌کننده‌ی مقدار ویژگی [`aria-keyshortcuts`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-keyshortcuts) است که میان‌برهای صفحه‌کلیدی را مشخص می‌کند که نویسنده برای فعال‌سازی یا دادن تمرکز به یک عنصر پیاده‌سازی کرده‌است.

> [!NOTE]
> تنظیم ویژگی‌های aria روی `ElementInternals` امکان تعریف معناشناسی پیش‌فرض را روی یک عنصر سفارشی فراهم می‌کند. این ویژگی‌ها ممکن است توسط ویژگی‌های تعریف‌شده توسط نویسنده بازنویسی شوند، اما تضمین می‌کنند که اگر نویسنده آن ویژگی‌ها را حذف کند یا اصلاً آن‌ها را اضافه نکرده باشد، معناشناسی پیش‌فرض حفظ شود. برای اطلاعات بیشتر، [توضیح‌دهنده‌ی Accessibility Object Model](https://wicg.github.io/aom/explainer.html#default-semantics-for-custom-elements-via-the-elementinternals-object) را ببینید.

## مقدار

یک رشته (string).

## نمونه‌ها

در این مثال، مقدار `ariaKeyShortcuts` برابر با «"Alt+Shift+A"» قرار داده شده است.

```js
this.internals_.ariaKeyShortcuts = "Alt+Shift+A";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}