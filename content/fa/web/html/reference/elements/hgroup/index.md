---
title: "<hgroup> HTML heading group element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/hgroup"
translated_by: "n8n + AI"
---

# عنصر `<hgroup>` — گروه‌بندی سرعنوان و محتوای مرتبط

عنصر **`<hgroup>`** در [HTML](/en-US/docs/Web/HTML) یک سرعنوان (heading) و محتوای مرتبط با آن را نشان می‌دهد. این عنصر یک [`<h1>` تا `<h6>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) را به همراه یک یا چند [`<p>`](/en-US/docs/Web/HTML/Reference/Elements/p) در خود گروه‌بندی می‌کند.

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

از `<hgroup>` برای گروه‌بندی یک سرعنوان با محتوای ثانویه مانند زیرعنوان (subheading)، عنوان جایگزین یا شعار (tagline) استفاده می‌شود. هر کدام از این محتواها به صورت یک عنصر `<p>` درون `<hgroup>` قرار می‌گیرند.

خود `<hgroup>` هیچ تأثیری بر ساختار outline صفحه وب ندارد. بلکه تنها سرعنوان مجاز داخل آن (یعنی همان `<h1>` تا `<h6>`) در outline صفحه نقش دارد.

## مثال

```html
<!doctype html>
<title>HTML Standard</title>
<body>
  <hgroup id="document-title">
    <h1>HTML: Living Standard</h1>
    <p>Last Updated 12 July 2022</p>
  </hgroup>
  <p>Some intro to the document.</p>
  <h2>Table of contents</h2>
  <ol id="toc">
    …
  </ol>
  <h2>First section</h2>
  <p>Some intro to the first section.</p>
</body>
```

## خلاصه فنی

| ویژگی (Property) | مقدار |
|------------------|-------|
| [دسته‌بندی محتوا (Content categories)](/en-US/docs/Web/HTML/Guides/Content_categories) | محتوای جریانی (Flow content)، محتوای سرعنوان (Heading content)، محتوای قابل لمس (Palpable content) |
| محتوای مجاز (Permitted content) | صفر یا چند عنصر `<p>`، سپس یک عنصر `<h1>`، `<h2>`، `<h3>`، `<h4>`، `<h5>` یا `<h6>`، و سپس صفر یا چند عنصر `<p>` |
| حذف تگ (Tag omission) | هیچکدام؛ هر دو تگ شروع و پایان اجباری هستند |
| والدین مجاز (Permitted parents) | هر عنصری که [محتوای جریانی (Flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد |
| نقش ARIA ضمنی (Implicit ARIA role) | [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | هر نقش (Any) |
| رابط DOM (DOM interface) | [`HTMLElement`](/en-US/docs/Web/API/HTMLElement) |

## همچنین ببینید

- [عناصر سرعنوان HTML: `<h1>` تا `<h6>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)
- [عنصر `<p>`](/en-US/docs/Web/HTML/Reference/Elements/p)

- سایر عناصر مرتبط با بخش‌ها: `<body>`، `<article>`، `<section>`، `<aside>`، `<h1>` تا `<h6>`، `<nav>`، `<header>`، `<footer>`، `<address>`
- [بخش‌بندی و ساختار کلی یک سند HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)