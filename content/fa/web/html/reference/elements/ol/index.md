---
title: "<ol> HTML ordered list element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/ol"
translated_by: "n8n + AI"
---

عنصر `<ol>` در HTML یک لیست مرتب (ordered list) از آیتم‌ها را نشان می‌دهد — معمولاً به‌صورت یک لیست شماره‌دار نمایش داده می‌شود.

## ویژگی‌ها (Attributes)

این عنصر همچنین [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) را می‌پذیرد.

- `compact` {{Deprecated_inline}} {{non-standard_inline}}
  - : این ویژگی Boolean به مرورگر پیشنهاد می‌دهد که لیست را به صورت فشرده نمایش دهد. تفسیر این ویژگی به مرورگر بستگی دارد. به جای آن از [CSS](/en-US/docs/Web/CSS) استفاده کنید: برای ایجاد اثری مشابه `compact`، می‌توانید از ویژگی CSS {{cssxref("line-height")}} با مقدار `80%` استفاده کنید.
- `reversed`
  - : این ویژگی Boolean مشخص می‌کند که آیتم‌های لیست به ترتیب معکوس (از بالا به پایین) شماره‌گذاری شوند. یعنی شماره‌ها از بالا (بزرگترین) شروع شده و کاهش می‌یابند.
- `start`
  - : یک عدد صحیح که شمارش آیتم‌های لیست از آن شروع می‌شود. همیشه به صورت عدد عربی (1, 2, 3, …) نوشته می‌شود، حتی اگر نوع شماره‌گذاری (`type`) حروف یا اعداد رومی باشد. مثلاً اگر می‌خواهید شماره‌گذاری از حرف «d» یا عدد رومی «iv» شروع شود، از `start="4"` استفاده کنید.
- `type`
  - : نوع شماره‌گذاری را تعیین می‌کند:
    - `a` برای حروف کوچک انگلیسی
    - `A` برای حروف بزرگ انگلیسی
    - `i` برای اعداد رومی کوچک
    - `I` برای اعداد رومی بزرگ
    - `1` برای اعداد معمولی (پیش‌فرض)

    نوع مشخص‌شده برای کل لیست اعمال می‌شود، مگر اینکه روی یک عنصر {{HTMLElement("li")}} داخل آن، ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/li#type) متفاوتی تنظیم شده باشد.

    > [!NOTE]
    > اگر نوع شماره‌گذاری از نظر معنایی مهم نیست (مثلاً در اسناد حقوقی یا فنی که به آیتم‌ها با شماره/حرف ارجاع داده می‌شود)، بهتر است از ویژگی CSS {{CSSxRef("list-style-type")}} استفاده کنید.

## نکات استفاده (Usage notes)

معمولاً آیتم‌های یک لیست مرتب با یک نشانگر (marker) مانند عدد یا حرف در ابتدا نمایش داده می‌شوند.

عناصر `<ol>` و {{HTMLElement("ul")}} (و معادل {{HTMLElement("menu")}}) می‌توانند تا هر سطحی تودرتو (nest) شوند و به دلخواه بین `<ol>`، `<ul>` (یا `<menu>`) جابه‌جا شوند.

تفاوت `<ol>` و {{HTMLElement("ul")}} در این است که در `<ol>` ترتیب آیتم‌ها مهم است. مثلاً:

- مراحل یک دستور پخت
- مسیرهای گام‌به‌گام
- لیست مواد تشکیل‌دهنده به ترتیب کاهش درصد در برچسب‌های تغذیه‌ای

برای انتخاب نوع لیست، ترتیب آیتم‌ها را تغییر دهید؛ اگر معنی محتوا تغییر کرد، از `<ol>` استفاده کنید، وگرنه از {{HTMLElement("ul")}} یا اگر لیست منو است از {{HTMLElement("menu")}}.

## مثال‌ها

### مثال ساده

```html
<ol>
  <li>Fee</li>
  <li>Fi</li>
  <li>Fo</li>
  <li>Fum</li>
</ol>
```

### استفاده از نوع شماره‌گذاری رومی

```html
<ol type="i">
  <li>Introduction</li>
  <li>List of Grievances</li>
  <li>Conclusion</li>
</ol>
```

### استفاده از ویژگی start

```html
<p>Finishing places of contestants not in the winners' circle:</p>

<ol start="4">
  <li>Speedwalk Stu</li>
  <li>Saunterin' Sam</li>
  <li>Slowpoke Rodriguez</li>
</ol>
```

### لیست‌های تودرتو

```html
<ol>
  <li>First item</li>
  <li>
    Second item
    <ol>
      <li>Second item first subitem</li>
      <li>Second item second subitem</li>
      <li>Second item third subitem</li>
    </ol>
  </li>
  <li>Third item</li>
</ol>
```

```html
<ol>
  <li>first item</li>
  <li>
    second item
    <!-- closing </li> tag is not here! -->
    <ol>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ol>
  </li>
  <!-- Here's the closing </li> tag -->
  <li>third item</li>
</ol>
```

#### نتیجه

### لیست نامرتب درون لیست مرتب

```html
<ol>
  <li>first item</li>
  <li>
    second item
    <!-- closing </li> tag is not here! -->
    <ul>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ul>
  </li>
  <!-- Here's the closing </li> tag -->
  <li>third item</li>
</ol>
```

#### نتیجه

## خلاصه فنی

| ویژگی | توضیح |
|-------|-------|
| [دسته‌بندی محتوا](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories) | [محتوی جریانی](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) و اگر فرزندان `<ol>` حداقل یک عنصر `<li>` داشته باشند، [محتوی قابل لمس](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) |
| محتوای مجاز | صفر یا بیشتر عنصر `<li>`، `<script>` و `<template>` |
| حذف تگ | مجاز نیست؛ هر دو تگ شروع و پایان اجباری هستند |
| والدین مجاز | هر عنصری که [محتوی جریانی](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد |
| نقش ARIA ضمنی | `list` |
| نقش‌های ARIA مجاز | `directory`، `group`، `listbox`، `menu`، `menubar`، `none`، `presentation`، `radiogroup`، `tablist`، `toolbar`، `tree` |
| رابط DOM | `HTMLOListElement` |```

- سایر المان‌های HTML مرتبط با لیست: `<ul>`، `<li>`، `<menu>`
- خصوصیات CSS که ممکن است برای استایل‌دهی به المان `<ol>` مفید باشند:
  - ویژگی `list-style`، برای انتخاب نحوهٔ نمایش اعداد ترتیبی
  - [شمارنده‌های CSS](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters)، برای مدیریت لیست‌های تو در تو پیچیده
  - ویژگی `line-height`، برای شبیه‌سازی صفت منسوخ `compact`
  - ویژگی `margin`، برای کنترل تورفتگی لیست