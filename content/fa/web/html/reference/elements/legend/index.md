---
title: "<legend> HTML field set legend element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/legend"
translated_by: "n8n + AI"
---

عنصر **`<legend>`** در [HTML](/en-US/docs/Web/HTML)، عنوانی برای محتوای عنصر والد خود یعنی `<fieldset>` ارائه می‌دهد.

در [عناصر `<select>` قابل شخصی‌سازی](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select)، عنصر `<legend>` به عنوان فرزند `<optgroup>` مجاز است تا برچسبی فراهم کند که هدف‌گیری و استایل‌دهی به آن آسان باشد. این برچسب جایگزین هر متنی می‌شود که در attribute به نام `label` عنصر `<optgroup>` تنظیم شده باشد و معنای یکسانی دارد.

## مثال تعاملی

```html interactive-example
<fieldset>
  <legend>Choose your favorite monster</legend>

  <input type="radio" id="kraken" name="monster" value="K" />
  <label for="kraken">Kraken</label><br />

  <input type="radio" id="sasquatch" name="monster" value="S" />
  <label for="sasquatch">Sasquatch</label><br />

  <input type="radio" id="mothman" name="monster" value="M" />
  <label for="mothman">Mothman</label>
</fieldset>
```

```css interactive-example
legend {
  background-color: black;
  color: white;
  padding: 3px 6px;
}

input {
  margin: 0.4rem;
}
```

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## مثال‌ها

برای مثال‌های مربوط به `<legend>`، به عنصر `<form>` مراجعه کنید.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>هیچ‌کدام</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی (Phrasing content)</a>
        و
        <a href="/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements">عناصر heading</a>
        (تگ‌های h1 تا h6).
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>
        یک <code>&#x3C;fieldset></code> که اولین فرزند آن این
        <code>&#x3C;legend></code> باشد. در
        <a href="/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select">عناصر select قابل شخصی‌سازی</a>،
        عنصر <code>&#x3C;legend></code> به عنوان فرزند <code>&#x3C;optgroup></code> مجاز است.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLLegendElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- [نقش ARIA: فرم](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role)