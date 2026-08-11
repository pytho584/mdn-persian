---
title: "<li> HTML list item element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/li"
translated_by: "n8n + AI"
---

عنصر **`<li>`** در [HTML](/en-US/docs/Web/HTML) برای نمایش یک آیتم در لیست استفاده می‌شود. این عنصر حتماً باید درون یک عنصر والد قرار گیرد: یک لیست مرتب (`<ol>`) ، یک لیست نامرتب (`<ul>`) یا یک منو (`<menu>`). در منوها و لیست‌های نامرتب، آیتم‌های لیست معمولاً با نقاط گلوله (bullet points) نمایش داده می‌شوند. در لیست‌های مرتب، معمولاً یک شمارنده صعودی (مانند عدد یا حرف) در سمت چپ آن‌ها نشان داده می‌شود.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `value`
  - : این ویژگی از نوع عدد صحیح (integer) است و مقدار ترتیبی فعلی آیتم لیست را مشخص می‌کند که توسط عنصر `<ol>` تعریف می‌شود. تنها مقدار مجاز برای این ویژگی یک عدد است، حتی اگر لیست با اعداد رومی یا حروف نمایش داده شود. آیتم‌های لیست بعد از این آیتم، شماره‌گذاری را از این مقدار ادامه می‌دهند. این ویژگی برای لیست‌های نامرتب (`<ul>`) یا منوها (`<menu>`) معنایی ندارد.
- `type` (منسوخ)
  - : این ویژگی از نوع کاراکتری است و نوع شماره‌گذاری را مشخص می‌کند:
    - `a`: حروف کوچک (lowercase)
    - `A`: حروف بزرگ (uppercase)
    - `i`: اعداد رومی کوچک
    - `I`: اعداد رومی بزرگ
    - `1`: اعداد

    این نوع شماره‌گذاری، نوع تعیین‌شده توسط عنصر والد `<ol>` (در صورت وجود) را نادیده می‌گیرد.

    > **توجه:** این ویژگی منسوخ شده است. به جای آن از ویژگی CSS `list-style-type` استفاده کنید.

## مثال‌ها

برای مثال‌های بیشتر، صفحات `<ol>` و `<ul>` را ببینید.

### لیست مرتب

```html
<ol>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

### لیست مرتب با مقدار سفارشی

```html
<ol type="I">
  <li value="3">third item</li>
  <li>fourth item</li>
  <li>fifth item</li>
</ol>
```

### لیست نامرتب

```html
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```

| ویژگی | مقدار |
| --- | --- |
| رده‌های محتوا | هیچ. |
| محتوای مجاز | محتوای جریانی (Flow content). |
| حذف تگ | تگ پایانی را می‌توان حذف کرد اگر آیتم لیست بلافاصله با یک عنصر `<li>` دیگر دنبال شود، یا اگر محتوای دیگری در عنصر والد وجود نداشته باشد. |
| والدهای مجاز | یک عنصر `<ul>`، `<ol>` یا `<menu>`. اگرچه استفادهٔ استاندارد نیست، عنصر منسوخ `<dir>` نیز می‌تواند والد باشد. |
| نقش ARIA ضمنی | `listitem` زمانی که فرزند `ol`، `ul` یا `menu` باشد. |
| نقش‌های ARIA مجاز | `menuitem`، `menuitemcheckbox`، `menuitemradio`، `option`، `none`، `presentation`، `radio`، `separator`، `tab`، `treeitem` |
| رابط DOM | `HTMLLIElement` |

## جستارهای وابسته

- سایر عناصر HTML مرتبط با لیست: [`<ul>`](/en-US/docs/Web/HTML/Reference/Elements/ul)، [`<ol>`](/en-US/docs/Web/HTML/Reference/Elements/ol)، [`<menu>`](/en-US/docs/Web/HTML/Reference/Elements/menu)، و عنصر منسوخ [`<dir>`](/en-US/docs/Web/HTML/Reference/Elements/dir).
- ویژگی‌های CSS که می‌توانند برای استایل‌دهی به عنصر `<li>` مفید باشند:
  - ویژگی `list-style`، برای انتخاب نحوهٔ نمایش شماره ترتیبی.
  - [شمارنده‌های CSS](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters)، برای مدیریت لیست‌های تو در تو.
  - ویژگی `margin`، برای کنترل تورفتگی آیتم لیست.