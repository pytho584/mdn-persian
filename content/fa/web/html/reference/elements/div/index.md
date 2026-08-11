---
title: "<div> HTML content division element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/div"
translated_by: "n8n + AI"
---

عنصر `<div>` یک محفظه (container) عمومی برای محتوای جریان (flow content) در HTML است. این عنصر تا زمانی که با CSS (مثلاً با اعمال مستقیم استایل، یا استفاده از مدل‌های layout مانند Flexbox روی والد) استایل‌دهی نشود، هیچ تأثیری روی محتوا یا چیدمان ندارد.

به‌عنوان یک محفظهٔ «خالص»، عنصر `<div>` به‌خودی‌خود چیزی را نشان نمی‌دهد. در عوض، از آن برای گروه‌بندی محتوا استفاده می‌شود تا بتوان با attributeهای `class` یا `id` به راحتی به آن استایل داد، یا بخشی از سند را به زبانی دیگر مشخص کرد (با attribute `lang`) و غیره.

## Attributes

این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

> [!NOTE]
> attribute `align` منسوخ شده است و دیگر نباید استفاده شود. برای تراز و موقعیت‌دهی به `<div>`ها از ویژگی‌ها یا تکنیک‌های CSS مانند [CSS Grid](/en-US/docs/Web/CSS/Guides/Grid_layout) یا [CSS Flexbox](/en-US/docs/Learn_web_development/Core/CSS_layout/Flexbox) استفاده کنید.

## نکات استفاده

- عنصر `<div>` را فقط زمانی استفاده کنید که هیچ عنصر معنایی دیگری (مانند `<article>` یا `<nav>`) مناسب نباشد.

## دسترسی‌پذیری (Accessibility)

عنصر `<div>` [نقش ضمنی `generic`](https://w3c.github.io/aria/#generic) دارد، نه `none`. این موضوع ممکن است روی برخی اعلان‌های ترکیبی ARIA که برای عملکرد صحیح به یک عنصر فرزند مستقیم با نقش خاص نیاز دارند، تأثیر بگذارد.

## مثال‌ها

### یک مثال ساده

```html
<div>
  <p>
    هر نوع محتوایی اینجا می‌تواند باشد. مثل &lt;p&gt;، &lt;table&gt;. هر چیزی که دوست دارید!
  </p>
</div>
```

### یک مثال با استایل

در این مثال، با اعمال استایل CSS به `<div>` یک جعبهٔ سایه‌دار ایجاد شده است. توجه کنید که از attribute `class` روی `<div>` برای اعمال استایل `"shadowbox"` استفاده شده است.

#### HTML

```html
<div class="shadowbox">
  <p>در اینجا یک نکتهٔ بسیار جالب در یک جعبهٔ سایه‌دار زیبا نمایش داده شده است.</p>
</div>
```

#### CSS

```css
.shadowbox {
  width: 15em;
  border: 1px solid #333333;
  box-shadow: 8px 8px 5px #444444;
  padding: 8px 12px;
  background-image: linear-gradient(180deg, white, #dddddd 40%, #cccccc);
}
```

## خلاصهٔ فنی

|                     |                                           |
| ------------------- | ----------------------------------------- |
| محتوای مجاز         | [محتوای جریان](/en-US/docs/Web/HTML/Reference/Content_categories#flow_content) |
| حذف تگ              | هیچ‌کدام، تگ شروع و پایان اجباری است.    |
| والد مجاز           | هر عنصری که [محتوای جریان](/en-US/docs/Web/HTML/Reference/Content_categories#flow_content) را بپذیرد. |
| نقش ARIA ضمنی       | `generic`                                 |
| نقش‌های ARIA مجاز   | هر نقشی                                     |

## مشخصات

| Specification                         |
| ------------------------------------- |
| [HTML Living Standard](https://html.spec.whatwg.org/multipage/grouping-content.html#the-div-element) |

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- عناصر بخش‌بندی معنایی: {{HTMLElement("section")}}, {{HTMLElement("article")}}, {{HTMLElement("nav")}}, {{HTMLElement("header")}}, {{HTMLElement("footer")}}
- {{HTMLElement("span")}} عنصر محفظهٔ مشابه برای محتوای درون‌خطی

| ویژگی | مقدار |
| --- | --- |
| دسته‌بندی محتوا | [محتوای جریان (Flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [محتوای قابل‌لمس (palpable content)](/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) |
| محتوای مجاز | [محتوای جریان (Flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content). یا (در WHATWG HTML): اگر والد یک عنصر `<dl>` باشد، یک یا چند عنصر `<dt>` و به‌دنبال آن یک یا چند عنصر `<dd>`، که به‌صورت اختیاری با عناصر `<script>` و `<template>` مخلوط می‌شوند. |
| حذف تگ | هیچ؛ هر دو تگ شروع و پایان اجباری هستند. |
| عناصر والد مجاز | هر عنصری که [محتوای جریان (Flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد. یا (در WHATWG HTML): عنصر `<dl>`. |
| نقش ضمنی ARIA | [`generic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role) |
| نقش‌های مجاز ARIA | هر نقشی |
| رابط DOM | `HTMLDivElement` |

## همچنین ببینید

- عناصر بخش‌بندی معنایی: `<section>`، `<article>`، `<nav>`، `<header>`، `<footer>`
- عنصر `<span>` برای استایل‌دهی به محتوای عبارتی (phrasing content)