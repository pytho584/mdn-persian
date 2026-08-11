---
title: "writingsuggestions HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/writingsuggestions"
translated_by: "n8n + AI"
---

ویژگی سراسری **`writingsuggestions`** یک ویژگی شمارشی (enumerated) است که مشخص می‌کند آیا پیشنهادهای نوشتاری ارائه‌شده توسط مرورگر باید در محدودهٔ آن عنصر فعال باشند یا نه.

برخی مرورگرها هنگام تایپ کاربر در فیلدهای قابل ویرایش، پیشنهادهایی برای نوشتن ارائه می‌دهند. این پیشنهادها معمولاً به صورت متن خاکستری‌رنگ بعد از مکان‌نما ظاهر می‌شوند و جملهٔ کاربر را کامل می‌کنند. اگرچه این قابلیت می‌تواند برای کاربران مفید باشد، توسعه‌دهندگان ممکن است در برخی موارد آن را غیرفعال کنند؛ مثلاً وقتی خودشان پیشنهادهای نوشتاری مخصوص سایت خود ارائه می‌دهند.

ویژگی `writingsuggestions` می‌تواند روی فیلدهای قابل ویرایش مانند عنصر `<input>` یا `<textarea>` تنظیم شود، یا روی سایر عناصر HTML قرار گیرد تا رفتار پیشنهادهای مرورگر را در بخش‌هایی از صفحه یا کل صفحه کنترل کند.

## نحو

در مرورگرهایی که از این ویژگی پشتیبانی می‌کنند، پیشنهادهای نوشتاری به‌صورت پیش‌فرض فعال هستند. برای غیرفعال کردن آن‌ها، مقدار ویژگی `writingsuggestions` را برابر `false` قرار دهید. تنظیم مقدار `true` یا حذف مقدار، پیشنهادهای نوشتاری را فعال می‌کند.

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

## همچنین ببینید

- ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
- ویژگی [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck)
- ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable)
- [`<textarea>`](/en-US/docs/Web/HTML/Reference/Elements/textarea)
- [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input)
- [`<datalist>`](/en-US/docs/Web/HTML/Reference/Elements/datalist) و ویژگی [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list)