---
title: "<span> HTML content span element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/span"
translated_by: "n8n + AI"
---

The **`<span>`** [HTML](/en-US/docs/Web/HTML) element یک کانتینر توکار (inline) عمومی برای محتوای نحوی (phrasing content) است که ذاتاً معنی مشخصی ندارد. از آن می‌توان برای گروه‌بندی عناصر به‌منظور اعمال استایل (با استفاده از خصوصیت‌های [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) یا [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id)) یا برای زمانی که عناصر مقادیر صفات مشترک دارند — مثل [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) — استفاده کرد. `<span>` تنها زمانی باید به‌کار رود که هیچ عنصر معنایی (semantic) دیگری مناسب نباشد. `<span>` بسیار شبیه عنصر `<div>` است، اما `<div>` یک [block-level element](/en-US/docs/Glossary/Block-level_content) است در حالی که `<span>` یک [inline-level element](/en-US/docs/Glossary/Inline-level_content) محسوب می‌شود.

```html interactive-example
<p>
  Add the <span class="ingredient">basil</span>,
  <span class="ingredient">pine nuts</span> and
  <span class="ingredient">garlic</span> to a blender and blend into a paste.
</p>

<p>
  Gradually add the <span class="ingredient">olive oil</span> while running the
  blender slowly.
</p>
```

```css interactive-example
span.ingredient {
  color: red;
}
```

## Attributes

این عنصر فقط شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## Example

### Example 1

#### HTML

```html
<p><span>Some text</span></p>
```

#### Result

### Example 2

#### HTML

```html
<li>
  <span>
    <a href="portfolio.html" target="_blank">See my portfolio</a>
  </span>
</li>
```

#### CSS

```css
li span {
  background: gold;
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
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >.
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
      <td>هیچ‌یک؛ تگ شروع و پایان هر دو الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a> را بپذیرد، یا هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a> را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >No corresponding role</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>Any</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>
        HTMLSpanElement
      </td>
    </tr>
  </tbody>
</table>

## Specifications

## Browser compatibility

## See also

- HTML <div> element