---
title: "<bdo> HTML bidirectional text override element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/bdo"
translated_by: "n8n + AI"
---

عنصر `<bdo>` در HTML جهت‌گیری فعلی متن را override می‌کند، به طوری که متن داخل آن در جهتی متفاوت نمایش داده می‌شود.

نویسه‌های متن از نقطه شروع در جهت داده شده رسم می‌شوند؛ جهت تک‌تک نویسه‌ها تغییر نمی‌کند (مثلاً نویسه‌ها برعکس کشیده نمی‌شوند).

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `dir`
  - : جهتی که متن درون عنصر باید نمایش داده شود. مقادیر ممکن عبارتند از:
    - `ltr`: نشان می‌دهد متن باید از چپ به راست جریان یابد.
    - `rtl`: نشان می‌دهد متن باید از راست به چپ جریان یابد.

## مثال‌ها

```html
<!-- تغییر جهت متن -->
<p>This text will go left to right.</p>
<p><bdo dir="rtl">This text will go right to left.</bdo></p>
```

## نکات

در مشخصات HTML 4 رویدادهایی برای این عنصر تعریف نشده بود؛ این رویدادها در XHTML اضافه شدند. این احتمالاً یک oversight است.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>هیچکدام؛ هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >
        می‌پذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role"
            >generic</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>
        {{domxref("HTMLElement")}} — تا Gecko 1.9.2 (Firefox 4)
        از اینترفیس
        <code
          ><a href="/en-US/docs/Web/API/HTMLSpanElement"
            >HTMLSpanElement</a
          ></code
        >
        برای این عنصر استفاده می‌کرد.
      </td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- عنصر مرتبط: `<bdi>`