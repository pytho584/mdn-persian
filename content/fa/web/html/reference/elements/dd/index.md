---
title: "<dd> HTML description details element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dd"
translated_by: "n8n + AI"
---

المان **`<dd>`** در [HTML](/en-US/docs/Web/HTML) توضیح، تعریف یا مقدار را برای عنوان قبلی (`<dt>`) در یک لیست توضیحات (`<dl>`) فراهم می‌کند.

```html interactive-example
<p>Cryptids of Cornwall:</p>

<dl>
  <dt>Beast of Bodmin</dt>
  <dd>A large feline inhabiting Bodmin Moor.</dd>

  <dt>Morgawr</dt>
  <dd>A sea serpent.</dd>

  <dt>Owlman</dt>
  <dd>A giant owl-like creature.</dd>
</dl>
```

```css interactive-example
p,
dt {
  font-weight: bold;
}

dl,
dd {
  font-size: 0.9rem;
}

dd {
  margin-bottom: 1em;
}
```

## Attributes

این عنصر فقط شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## Examples

برای مثال‌ها، به [مثال‌های ارائه‌شده برای المان `<dl>`](/en-US/docs/Web/HTML/Reference/Elements/dl#examples) مراجعه کنید.

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌های محتوا (Content categories)</th>
      <td>هیچ‌کدام.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>Flow content.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        تگ شروع الزامی است. اگر بلافاصله بعد از این المان، المان <code>&lt;dd&gt;</code> دیگری یا یک المان <code>&lt;dt&gt;</code> بیاید، یا محتوای دیگری در المان والد وجود نداشته باشد، می‌توان تگ پایان را حذف کرد.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        یک <code>&lt;dl&gt;</code> یا یک <code>&lt;div&gt;</code> که فرزند یک <code>&lt;dl&gt;</code> باشد.<br />این المان می‌تواند بعد از یک <code>&lt;dt&gt;</code> یا المان <code>&lt;dd&gt;</code> دیگری استفاده شود.
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
      <td><code>HTMLElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- `<dl>`
- `<dt>`