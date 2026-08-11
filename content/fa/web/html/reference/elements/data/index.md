---
title: "<data> HTML data element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/data"
translated_by: "n8n + AI"
---

# عنصر `<data>` در HTML

عنصر **`<data>`** در [HTML](/en-US/docs/Web/HTML) یک تکه محتوا را با ترجمهٔ ماشین‌خوان (machine-readable) مرتبط می‌کند. اگر محتوا مربوط به زمان یا تاریخ باشد، باید از عنصر `<time>` استفاده کرد.

```html interactive-example
<p>New Products:</p>
<ul>
  <li><data value="398">Mini Ketchup</data></li>
  <li><data value="399">Jumbo Ketchup</data></li>
  <li><data value="400">Mega Jumbo Ketchup</data></li>
</ul>
```

```css interactive-example
data:hover::after {
  content: " (ID " attr(value) ")";
  font-size: 0.7em;
}
```

## ویژگی‌ها

ویژگی‌های این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `value`
  - : این ویژگی، ترجمهٔ ماشین‌خوانِ محتوای عنصر را مشخص می‌کند.

## مثال‌ها

مثال زیر نام محصولات را نشان می‌دهد و هر نام را با یک شمارهٔ محصول مرتبط می‌کند.

```html
<p>New Products</p>
<ul>
  <li><data value="398">Mini Ketchup</data></li>
  <li><data value="399">Jumbo Ketchup</data></li>
  <li><data value="400">Mega Jumbo Ketchup</data></li>
</ul>
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا (content categories)</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی (flow content)</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای متنی (phrasing content)</a>،
        محتوای قابل لمس (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (permitted content)</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای متنی (phrasing content)</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (tag omission)</th>
      <td>هیچکدام؛ تگ شروع و پایان هر دو اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (permitted parents)</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای متنی (phrasing content)</a> را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ضمنی ARIA (implicit ARIA role)</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role">generic</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های مجاز ARIA (permitted ARIA roles)</th>
      <td>هر نقشی (any)</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM interface)</th>
      <td><code>HTMLDataElement</code></td>
    </tr>
  </tbody>
</table>

## جستارهای وابسته

- عنصر [HTML `<time>`](/en-US/docs/Web/HTML/Element/time)