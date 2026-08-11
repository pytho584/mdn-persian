---
title: "<span> HTML content span element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/span"
translated_by: "n8n + AI"
---

عنصر **`<span>`** [HTML](/en-US/docs/Web/HTML) یک ظرف (container) درون‌خطی (inline) عمومی برای محتوای phrasing است و به خودی خود معنای خاصی را نشان نمی‌دهد. می‌توان از آن برای گروه‌بندی عناصر به‌منظور استایل‌دادن (با استفاده از attributeهای [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) یا [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id)) یا به دلیل اشتراک در مقدار attributeهایی مانند [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) استفاده کرد. فقط زمانی باید از آن استفاده کرد که هیچ عنصر معنایی دیگری مناسب نباشد. `<span>` شباهت زیادی به عنصر `<div>` دارد، اما `<div>` یک عنصر [block-level](/en-US/docs/Glossary/Block-level_content) است در حالی که `<span>` یک عنصر [inline-level](/en-US/docs/Glossary/Inline-level_content) است.

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

## ویژگی‌ها

این عنصر فقط [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) را شامل می‌شود.

## مثال

### مثال ۱

#### HTML

```html
<p><span>Some text</span></p>
```

#### نتیجه

### مثال ۲

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

#### نتیجه

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
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ؛ هم تگ شروع و هم تگ پایانی الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >
        را بپذیرد، یا هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        >
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >No corresponding role</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقش</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>
        <code>HTMLSpanElement</code>
      </td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- عنصر `<div>` در HTML