---
title: "<small> HTML side comment element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/small"
translated_by: "n8n + AI"
---

عنصر `<small>` در HTML برای توضیحات حاشیه‌ای و متن ریز مثل حق‌کپی و متن‌های قانونی استفاده می‌شود، بدون وابستگی به نمایش ظاهری آن. به طور پیش‌فرض، اندازه فونت متن درون خود را یک درجه کوچک‌تر می‌کند، مثلاً از `small` به `x-small`.

```html
<p>
  MDN Web Docs is a learning platform for Web technologies and the software that
  powers the Web.
</p>

<hr />

<p>
  <small
    >The content is licensed under a Creative Commons Attribution-ShareAlike 2.5
    Generic License.</small
  >
</p>
```

```css
small {
  font-size: 0.7em;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

## مثال‌ها

### استفاده پایه

```html
<p>
  This is the first sentence.
  <small>This whole sentence is in small letters.</small>
</p>
```

### جایگزین با CSS

```html
<p>
  This is the first sentence.
  <span class="small">This whole sentence is in small letters.</span>
</p>
```

```css
.small {
  font-size: 0.8em;
}
```

## نکات

هرچند ممکن است تصور شود که عنصر `<small>` مانند `<b>` و `<i>` اصل جداسازی ساختار از نمایش را نقض می‌کند، اما هر سه در HTML معتبر هستند. به نویسندگان توصیه می‌شود که با توجه به شرایط تصمیم بگیرند از `<small>` استفاده کنند یا CSS.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوی جریانی (flow content)</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوی عبارتی (phrasing content)</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوی عبارتی</a>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف برچسب</th>
      <td>هیچکدام؛ باید هم تگ شروع و هم تگ پایان داشته باشد.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوی عبارتی</a>
        را بپذیرد، یا هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوی جریانی</a>
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role">generic</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>HTMLElement</td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- `<b>`
- `<sub>` و `<sup>`
- `<font>`
- `<style>`