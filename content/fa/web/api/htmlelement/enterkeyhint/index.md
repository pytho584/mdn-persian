---
title: "HTMLElement: enterKeyHint property"
short-title: enterKeyHint
slug: Web/API/HTMLElement/enterKeyHint
page-type: web-api-instance-property
browser-compat: api.HTMLElement.enterKeyHint
---

{{APIRef("HTML DOM")}}

ویژگی **`enterKeyHint`** یک ویژگی شمارشی است که مشخص می‌کند چه برچسب عملیاتی (یا نمادی) برای کلید Enter در صفحه‌کلید مجازی نمایش داده شود. این ویژگی بازتاب‌دهندهٔ ویژگی سراسری HTML [`enterkeyhint`](/en-US/docs/Web/HTML/Reference/Global_attributes/enterkeyhint) است و یک ویژگی شمارشی به شمار می‌رود که تنها مقادیر رشته‌ای زیر را می‌پذیرد:

- `'enter'` — معمولاً نشان‌دهندهٔ درج یک خط جدید.
- `'done'` — معمولاً به این معنی است که چیز دیگری برای ورود وجود ندارد و ویرایشگر روش ورودی (IME) بسته خواهد شد.
- `'go'` — معمولاً به این معنی است که کاربر به مقصد متنی که تایپ کرده هدایت می‌شود.
- `'next'` — معمولاً کاربر را به فیلد بعدی که متن می‌پذیرد می‌برد.
- `'previous'` — معمولاً کاربر را به فیلد قبلی که متن می‌پذیرد می‌برد.
- `'search'` — معمولاً کاربر را به نتایج جستجو برای متنی که تایپ کرده می‌برد.
- `'send'` — معمولاً متن را به مقصد خود تحویل می‌دهد.

اگر هیچ مقداری برای `enterKeyHint` مشخص نشده باشد یا اگر مقداری غیر از مقادیر مجاز به آن داده شده باشد، یک رشتهٔ خالی بازگردانده می‌شود.

## مثال‌ها

به صفحه‌کلید مجازی اشاره می‌کند که کلید Enter چگونه برچسب‌گذاری شود (بسته به سیستم عامل یا زبان کاربر، ممکن است به صورت <kbd>Send</kbd> و <kbd>Search</kbd> نمایش داده شود).

```js
const send = document.getElementById("sendInput");
const search = document.getElementById("searchInput");

send.enterKeyHint = "send";
search.enterKeyHint = "search";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- ویژگی سراسری HTML [`enterkeyhint`](/en-US/docs/Web/HTML/Reference/Global_attributes/enterkeyhint)