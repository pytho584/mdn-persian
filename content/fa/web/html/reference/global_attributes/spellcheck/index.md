---
title: "spellcheck HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck"
translated_by: "n8n + AI"
---

ویژگی سراسری **`spellcheck`** یک ویژگی شمارشی (enumerated) است که مشخص می‌کند آیا عنصر می‌تواند از نظر غلط‌های املایی بررسی شود یا خیر.

> **نکته:** این ویژگی فقط یک راهنمایی برای مرورگر است: مرورگرها الزامی به بررسی غلط‌های املایی ندارند. معمولاً عناصر غیرقابل ویرایش حتی اگر `spellcheck` روی `true` تنظیم شده باشد و مرورگر از بررسی املا پشتیبانی کند، بررسی نمی‌شوند.

```html
<textarea spellcheck="true">
This exampull will be checkd fur spellung when you try to edit it.</textarea>

<textarea spellcheck="false">
This exampull will nut be checkd fur spellung when you try to edit it.</textarea>
```

این ویژگی می‌تواند مقادیر زیر را داشته باشد:

- رشتهٔ خالی یا `true` – نشان می‌دهد که عنصر باید در صورت امکان از نظر غلط‌های املایی بررسی شود.
- `false` – نشان می‌دهد که عنصر نباید از نظر غلط‌های املایی بررسی شود.

اگر این ویژگی تنظیم نشده باشد، مقدار پیش‌فرض آن به نوع عنصر و مرورگر بستگی دارد. این مقدار پیش‌فرض ممکن است _به‌ارث_ برده شود، به این معنی که محتوای عنصر فقط در صورتی از نظر املا بررسی می‌شود که نزدیک‌ترین جد (ancestor) آن حالت `spellcheck` برابر `true` داشته باشد.

## ملاحظات امنیتی و حریم خصوصی

استفاده از بررسی املا می‌تواند پیامدهایی برای امنیت و حریم خصوصی کاربران داشته باشد. مشخصات (specification) نحوهٔ انجام بررسی املا را تنظیم نمی‌کند و ممکن است محتوای عنصر برای دریافت نتایج به شخص ثالث ارسال شود (به [بررسی املای پیشرفته و «ربودن املا»](https://www.comparitech.com/blog/information-security/what-is-spell-jacking/) مراجعه کنید).

برای عناصری که می‌توانند حاوی اطلاعات حساس باشند، توصیه می‌شود `spellcheck` را روی `false` تنظیم کنید.

## مشخصات

مشخصات این ویژگی در استاندارد HTML تعریف شده است.

## سازگاری با مرورگر

اطلاعات سازگاری مرورگرها بر اساس جدول سازگاری MDN موجود است.

## جستارهای وابسته

- همهٔ [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes)
- [`autocorrect`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect)