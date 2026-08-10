---
title: "<div> HTML content division element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/div"
translated_by: "n8n + AI"
---

The **`<div>`** [HTML](/en-US/docs/Web/HTML) element is the generic container for flow content. It has no effect on the content or layout until styled in some way using CSS (e.g., styling is directly applied to it, or some kind of layout model like [Flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) is applied to its parent element).

```html interactive-example
<div class="warning">
  <img
    src="/shared-assets/images/examples/leopard.jpg"
    alt="An intimidating leopard." />
  <p>Beware of the leopard</p>
</div>
```

```css interactive-example
.warning {
  border: 10px ridge red;
  background-color: yellow;
  padding: 0.5rem;
  display: flex;
  flex-direction: column;
}

.warning img {
  width: 100%;
}

.warning p {
  font: small-caps bold 1.2rem sans-serif;
  text-align: center;
}
```

به‌عنوان یک کانتینر "خالص"، عنصر `<div>` ذاتاً نمایندهٔ چیزی نیست. در عوض برای گروه‌بندی محتوا استفاده می‌شود تا بتوان آن را به‌راحتی با صفت‌های [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) یا [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) استایل داد، یا ناحیه‌ای از سند را به‌عنوان نوشته‌شده به زبان دیگری علامت‌گذاری کرد (با استفاده از صفت [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang))، و موارد مشابه.

## Attributes

This element includes the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

> [!NOTE]
> The `align` attribute is obsolete; do not use it anymore. Instead, you should use CSS properties or techniques such as [CSS Grid](/en-US/docs/Web/CSS/Guides/Grid_layout) or [CSS Flexbox](/en-US/docs/Learn_web_development/Core/CSS_layout/Flexbox) to align and position `<div>` elements on the page.

## Usage notes

- The `<div>` element should be used only when no other semantic element (such as article or nav) is appropriate.

## Accessibility

The `<div>` element has [an implicit role of `generic`](https://w3c.github.io/aria/#generic), and not none. This may affect certain ARIA combination declarations that expect a direct descendant element with a certain role to function properly.

## Examples

### A basic example

```html
<div>
  <p>
    Any kind of content here. Such as &lt;p&gt;, &lt;table&gt;. You name it!
  </p>
</div>
```

#### Result

### A styled example

This example creates a shadowed box by applying a style to the `<div>` using CSS. Note the use of the [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) attribute on the `<div>` to apply the style named "shadowbox" to the element.

#### HTML

```html
<div class="shadowbox">
  <p>Here's a very interesting note displayed in a lovely shadowed box.</p>
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

#### Result

## Technical summary

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
        >, <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content">palpable content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >.<br />یا (در WHATWG HTML): اگر والد یک عنصر <dl> باشد: یک یا چند عنصر <dt> که به دنبال آن یک یا چند عنصر <dd> قرار می‌گیرند، که به‌صورت اختیاری می‌توانند با عناصر <script> و <template> درهم‌آمیخته شوند.
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>هیچ‌کدام — هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        هر عنصر که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        > را می‌پذیرد.<br />یا (در WHATWG HTML): عنصر <dl>.
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
      <td>هر کدام</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td><code>HTMLDivElement</code></td>
    </tr>
  </tbody>
</table>

## See also

- المان‌های بخش‌بندی معنایی: <section>, <article>, <nav>, <header>, <footer>
- عنصر <span> برای استایل‌دهی به phrasing content