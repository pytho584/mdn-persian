---
title: "writingsuggestions HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/writingsuggestions"
translated_by: "n8n + AI"
---

## ویژگی global `writingsuggestions`

ویژگی global **`writingsuggestions`** یک ویژگی enumerated (شمارشی) است که مشخص می‌کند آیا پیشنهادهای نوشتاری ارائه‌شده توسط مرورگر در محدودهٔ آن عنصر فعال باشند یا نه.

بعضی مرورگرها هنگام تایپ کاربر در فیلدهای قابل ویرایش، پیشنهادهای نوشتاری ارائه می‌دهند. این پیشنهادها معمولاً به‌صورت متن کمرنگ بعد از مکان‌نما نمایش داده می‌شوند و جملهٔ کاربر را کامل می‌کنند. هرچند این قابلیت می‌تواند مفید باشد، اما توسعه‌دهندگان ممکن است در برخی موارد بخواهند آن را غیرفعال کنند، مثلاً وقتی خودشان پیشنهادهای نوشتاری اختصاصی برای سایت فراهم می‌کنند.

ویژگی `writingsuggestions` را می‌توان روی فیلدهای قابل ویرایش مانند عنصرهای {{htmlelement('input')}} یا {{htmlelement('textarea')}}، یا روی سایر عناصر HTML تنظیم کرد تا رفتار پیشنهادهای مرورگر را در بخش‌هایی از صفحه یا کل صفحه کنترل کند.

## نحو (Syntax)

در مرورگرهایی که از این قابلیت پشتیبانی می‌کنند، پیشنهادهای نوشتاری به‌طور پیش‌فرض فعال هستند. برای غیرفعال کردن آن‌ها، مقدار ویژگی `writingsuggestions` را برابر `false` قرار دهید. تنظیم مقدار به `true` یا حذف مقدار، پیشنهادهای نوشتاری را فعال می‌کند.

برای غیرفعال کردن پیشنهادهای نوشتاری:

```html
<input type="text" writingsuggestions="false" />
```

برای فعال کردن پیشنهادهای نوشتاری:

```html
<input type="text" />
<input type="text" writingsuggestions />
<input type="text" writingsuggestions="true" />
```

## مشخصات (Specifications)

## سازگاری با مرورگرها (Browser compatibility)

## جستارهای وابسته (See also)

- [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
- [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck)
- [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable)
- {{HTMLElement("textarea")}}
- {{HTMLElement("input")}}
- {{HTMLElement("datalist")}} و ویژگی [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list)