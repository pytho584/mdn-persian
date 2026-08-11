---
title: "<q> HTML inline quotation element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/q"
translated_by: "n8n + AI"
---

عنصر `<q>` در HTML – نقل‌قول درون‌خطی
=========================================

عنصر **`<q>`** [HTML](/en-US/docs/Web/HTML) نشان می‌دهد که متن درون آن یک نقل‌قول کوتاه و درون‌خطی (inline) است. بیشتر مرورگرهای مدرن این نقل‌قول را با قرار دادن گیومه در اطراف متن نمایش می‌دهند. این عنصر برای نقل‌قول‌های کوتاهی که نیازی به شکست پاراگراف ندارند طراحی شده؛ برای نقل‌قول‌های بلند از عنصر `<blockquote>` استفاده کنید.

```html interactive-example
<p>
  When Dave asks HAL to open the pod bay door, HAL answers:
  <q
    cite="https://www.imdb.com/title/tt0062622/quotes/?item=qt0396921&ref_=ext_shr_lnk">
    I'm sorry, Dave. I'm afraid I can't do that.
  </q>
</p>
```

```css interactive-example
q {
  font-style: italic;
}
```

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `cite`
  - : مقدار این ویژگی یک URL است که به سند یا پیام منبع نقل‌قول اشاره می‌کند. این ویژگی برای اشاره به اطلاعاتی طراحی شده که زمینه یا مرجع نقل‌قول را توضیح می‌دهد.

## مثال‌ها

```html
<p>
  According to Mozilla's website,
  <q cite="https://www.mozilla.org/en-US/about/history/details/"
    >Firefox 1.0 was released in 2004 and became a big success.</q
  >
</p>
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Content categories</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>,
        palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>هیچکدام، هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a> را بپذیرد.</td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td><code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role">generic</a></code></td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td><code>HTMLQuoteElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- عنصر `<blockquote>` برای نقل‌قول‌های بلند.
- عنصر `<cite>` برای ارجاع به منبع.