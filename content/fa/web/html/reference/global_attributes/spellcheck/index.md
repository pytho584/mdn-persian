---
title: "spellcheck HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck"
translated_by: "n8n + AI"
---

**`spellcheck`** یک [ویژگی سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) از نوع [شمارشی (enumerated)](/en-US/docs/Glossary/Enumerated) است که مشخص می‌کند آیا عنصر می‌تواند از نظر غلط‌های املایی بررسی شود یا نه.

> **نکته:** این ویژگی فقط یک «پیشنهاد» به مرورگر است؛ مرورگرها موظف به بررسی غلط‌های املایی نیستند. معمولاً عناصر غیرقابل ویرایش حتی اگر ویژگی `spellcheck` برابر `true` باشد و مرورگر از بررسی املا پشتیبانی کند، بررسی نمی‌شوند.

```html interactive-example
<textarea spellcheck="true">
This exampull will be checkd fur spellung when you try to edit it.</textarea>

<textarea spellcheck="false">
This exampull will nut be checkd fur spellung when you try to edit it.</textarea>
```

این ویژگی می‌تواند مقادیر زیر را داشته باشد:

- رشتهٔ خالی یا `true`، یعنی در صورت امکان، عنصر باید از نظر غلط‌های املایی بررسی شود؛
- `false`، یعنی عنصر نباید از نظر غلط‌های املایی بررسی شود.

اگر این ویژگی تنظیم نشود، مقدار پیش‌فرض آن به نوع عنصر و مرورگر بستگی دارد. این مقدار پیش‌فرض می‌تواند _به ارث برده شود_؛ یعنی محتوای عنصر تنها زمانی از نظر غلط‌های املایی بررسی می‌شود که نزدیک‌ترین جد (ancestor) آن حالت `spellcheck` برابر `true` داشته باشد.

## امنیت و حریم خصوصی

استفاده از بررسی املا می‌تواند برای امنیت و حریم خصوصی کاربران پیامدهایی داشته باشد. مشخصات (specification) نحوهٔ انجام بررسی املا را تعیین نمی‌کند و ممکن است محتوای عنصر برای دریافت نتایج بررسی املا به شخص ثالث ارسال شود (نگاه کنید به [enhanced spellchecking and "spell-jacking"](https://www.comparitech.com/blog/information-security/what-is-spell-jacking/)).

بهتر است برای عناصری که ممکن است حاوی اطلاعات حساس باشند، `spellcheck` را روی `false` قرار دهید.

## جستارهای وابسته

- همهٔ [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes).
- [`autocorrect`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect).