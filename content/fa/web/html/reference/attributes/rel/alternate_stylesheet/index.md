---
title: "rel=\"alternate stylesheet\" HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel/alternate_stylesheet"
translated_by: "n8n + AI"
---

جفت‌کلیدواژهٔ **`alternate stylesheet`** وقتی به‌عنوان مقدار ویژگی [`rel`](/en-US/docs/Web/HTML/Reference/Elements/link#rel) در عنصر `<link>` استفاده شود، نشان می‌دهد که منبع هدف یک *استایل‌شیت جایگزین* است. مشخص‌کردن **استایل‌شیت‌های جایگزین** در یک صفحهٔ وب به کاربران امکان می‌دهد بر اساس نیازها یا ترجیحات خود، نسخه‌های متفاوتی از صفحه را ببینند.

> **نکته:**
>
> این ویژگی بدون افزونه در مرورگرها پشتیبانی خوبی ندارد. برای ارائهٔ حالت‌های نمایش جایگزین که با ترجیحات فعلی کاربر کار می‌کنند، به [ویژگی‌های رسانه](/en-US/docs/Web/CSS/Reference/At-rules/@media#media_features) CSS، یعنی `prefers-color-scheme` و `prefers-contrast` مراجعه کنید.

فایرفاکس به کاربران اجازه می‌دهد استایل‌شیت‌های جایگزین را از زیرمنوی _View > Page Style_ انتخاب کنند؛ در این زیرمنو مقدار ویژگی [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) نمایش داده می‌شود. سایر مرورگرها برای فعال‌کردن این قابلیت به افزونه نیاز دارند. صفحهٔ وب نیز می‌تواند رابط کاربری خودش را برای جابه‌جا شدن بین استایل‌ها فراهم کند.

## Examples

### Specifying alternate stylesheets

استایل‌شیت‌های جایگزین با استفاده از عنصر `<link>` و ویژگی‌های `rel="alternate stylesheet"` و `title="…"` مشخص می‌شوند. به عنوان مثال:

```html
<link href="reset.css" rel="stylesheet" />

<link href="default.css" rel="stylesheet" title="Default Style" />
<link href="fancy.css" rel="alternate stylesheet" title="Fancy" />
<link href="basic.css" rel="alternate stylesheet" title="Basic" />
```

در این مثال، استایل‌های «Default Style»، «Fancy» و «Basic» در زیرمنوی _Page Style_ فایرفاکس فهرست می‌شوند و «Default Style» از پیش انتخاب شده است. وقتی کاربر استایل دیگری انتخاب کند، صفحه بلافاصله با همان استایل‌شیت دوباره رندر می‌شود.

بدون توجه به استایل انتخابی، قوانین استایل‌شیت `reset.css` همیشه اعمال می‌شوند.

### آن را امتحان کنید

[یک مثال عملی را اینجا امتحان کنید](https://mdn.github.io/css-examples/alt-style-sheets/).

## Details

هر استایل‌شیت در یک سند در یکی از این دسته‌ها قرار می‌گیرد:

- **پایدار (Persistent)** (`rel="stylesheet"`، بدون `title=""`): همیشه روی سند اعمال می‌شود.
- **ترجیحی (Preferred)** (`rel="stylesheet"` با `title="…"`): به‌صورت پیش‌فرض اعمال می‌شود؛ اما اگر یک استایل‌شیت جایگزین انتخاب شود، [`disabled`](/en-US/docs/Web/API/StyleSheet/disabled) می‌شود. **فقط یک استایل‌شیت ترجیحی می‌تواند وجود داشته باشد**؛ بنابراین ارائهٔ استایل‌شیت‌هایی با `title`های متفاوت باعث می‌شود برخی از آن‌ها نادیده گرفته شوند.
- **جایگزین (Alternate)** (`rel="alternate stylesheet"` با `title="…"`): به‌صورت پیش‌فرض غیرفعال است و می‌توان آن را انتخاب کرد.

در مواردی که منوی استایل‌شیت وجود دارد، وقتی استایل‌شیت‌ها با ویژگی `title` روی عنصر `<link rel="stylesheet">` یا `<style>` ارجاع داده می‌شوند، آن عنوان به یکی از گزینه‌های ارائه‌شده به کاربر تبدیل می‌شود. استایل‌شیت‌هایی که با [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) یکسان پیوند خورده‌اند، بخشی از یک انتخاب واحد هستند. استایل‌شیت‌هایی که بدون ویژگی `title` پیوند می‌خورند همیشه اعمال می‌شوند.

برای پیوند به استایل پیش‌فرض از `rel="stylesheet"` و برای پیوند به استایل‌شیت‌های جایگزین از `rel="alternate stylesheet"` استفاده کنید. این کار به مرورگر می‌گوید کدام عنوان استایل‌شیت باید به‌صورت پیش‌فرض انتخاب شود؛ و این انتخاب پیش‌فرض در مرورگرهایی که از استایل‌شیت‌های جایگزین پشتیبانی نمی‌کنند نیز اعمال می‌شود.

## Specifications

## Browser compatibility

## See also

- [CSS](/en-US/docs/Web/CSS)
- [استفاده از اطلاعات استایل‌دهی پویا](/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)