---
title: "Document: title property"
---

{{APIRef("DOM")}}

ویژگی **`document.title`** عنوان فعلی سند را دریافت یا تنظیم می‌کند. در صورت وجود، مقدار پیش‌فرض آن مقدار عنصر [`<title>`](/en-US/docs/Web/HTML/Reference/Elements/title) است.

## مقدار

یک رشته شامل عنوان _سند_. اگر عنوان با تنظیم `document.title` بازنویسی شده باشد، این مقدار را شامل می‌شود. در غیر این صورت، عنوان مشخص‌شده در عنصر [`<title>`](/en-US/docs/Web/HTML/Reference/Elements/title) را شامل می‌شود.

```js
document.title = newTitle;
```

`newTitle` عنوان جدید سند است. این انتساب بر مقدار بازگشتی `document.title`، عنوان نمایش‌داده‌شده برای سند (مثلاً در نوار عنوان پنجره یا برگه) تأثیر می‌گذارد و همچنین بر DOM سند (مثلاً محتوای عنصر `<title>` در یک سند HTML) تأثیر می‌گذارد.

## مثال‌ها

فرض کنید `<head>` سند به صورت زیر است:

```html
<head>
  <meta charset="UTF-8" />
  <title>Hello World!</title>
</head>
```

```js
console.log(document.title); // "Hello World!"
document.title = "Goodbye World!"; // Page title changed
console.log(document.title); // "Goodbye World!"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}