---
title: "<noscript> HTML noscript element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/noscript"
translated_by: "n8n + AI"
---

عنصر `<noscript>` یک بخش از HTML را مشخص می‌کند که اگر نوع اسکریپت در صفحه پشتیبانی نشود، یا اسکریپت‌نویسی در مرورگر غیرفعال باشد، درج می‌شود.

## ویژگی‌ها (Attributes)

این عنصر فقط [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) را شامل می‌شود.

## مثال

```html
<noscript>
  <!-- لینک به فایل خارجی -->
  <a href="https://www.mozilla.org/">External Link</a>
</noscript>
<p>Rocks!</p>
```

### خروجی با اسکریپت فعال

Rocks!

### خروجی با اسکریپت غیرفعال

[External Link](https://www.mozilla.org/)

Rocks!

## نکات استفاده

عنصر `<noscript>` فرزندان خود را بسته به فعال یا غیرفعال بودن اسکریپت به صورت متفاوتی نمایش می‌دهد:

- اگر اسکریپت غیرفعال باشد، عنصر `<noscript>` فرزندان خود را به عنوان [محتوای HTML](/en-US/docs/Web/API/HTMLElement) نمایش می‌دهد.
- اگر اسکریپت فعال باشد، عنصر `<noscript>` فرزندان خود را به عنوان [متن (Text)](/en-US/docs/Web/API/Text) نمایش می‌دهد.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا (Content categories)</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content">Metadata content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (Permitted content)</th>
      <td>
        وقتی اسکریپت غیرفعال است و عنصر درون `<head>` قرار دارد: به هر ترتیبی، صفر یا چند عنصر `<link>`، صفر یا چند عنصر `<style>`، و صفر یا چند عنصر `<meta>`.<br />وقتی اسکریپت غیرفعال است و عنصر درون `<head>` نیست: هر <a href="/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model">محتوای شفاف (transparent content)</a>، اما هیچ عنصر `<noscript>` نباید در میان فرزندان آن باشد.<br />در غیر این صورت: flow content یا phrasing content.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (Tag omission)</th>
      <td>هیچکدام، هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (Permitted parents)</th>
      <td>
        هر عنصری که phrasing content را می‌پذیرد، به شرطی که هیچ عنصر `<noscript>` در نیاکان نباشد؛ یا درون عنصر `<head>` (فقط برای اسناد HTML)، باز هم به شرطی که هیچ عنصر `<noscript>` در نیاکان نباشد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td>هیچ `role` مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM interface)</th>
      <td>`HTMLElement`</td>
    </tr>
  </tbody>
</table>

## Specifications

## Browser compatibility