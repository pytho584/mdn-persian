---
title: "<figcaption> HTML figure caption element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/figcaption"
translated_by: "n8n + AI"
---

# عنصر `<figcaption>` — شرح تصویر

عنصر **`<figcaption>`** در [HTML](/en-US/docs/Web/HTML) نمایانگر یک عنوان یا شرح است که بقیهٔ محتوای عنصر والد خود، یعنی [`<figure>`](/en-US/docs/Web/HTML/Reference/Elements/figure)، را توصیف می‌کند. این عنصر به `<figure>` یک [accessible name](/en-US/docs/Glossary/Accessible_name) (نام قابل‌دسترس) می‌دهد.

## مثال تعاملی

```html interactive-example
<figure>
  <img
    src="/shared-assets/images/examples/elephant.jpg"
    alt="Elephant at sunset" />
  <figcaption>An elephant at sunset</figcaption>
</figure>
```

```css interactive-example
figure {
  border: thin silver solid;
  display: flex;
  flex-flow: column;
  padding: 5px;
  max-width: 220px;
  margin: auto;
}

img {
  max-width: 220px;
  max-height: 150px;
}

figcaption {
  background-color: #222222;
  color: white;
  font: italic smaller sans-serif;
  padding: 3px;
  text-align: center;
}
```

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## مثال‌ها

برای مثال‌های مربوط به `<figcaption>`، صفحهٔ [`<figure>`](/en-US/docs/Web/HTML/Reference/Elements/figure) را ببینید.

## خلاصهٔ فنی

| | |
| --- | --- |
| [دسته‌بندی محتوا (Content categories)](/en-US/docs/Web/HTML/Guides/Content_categories) | هیچ‌کدام. |
| محتوای مجاز | [محتوای جریان (Flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content). |
| حذف تگ | هیچ‌کدام؛ تگ شروع و پایان هر دو اجباری هستند. |
| والد مجاز | یک عنصر [`<figure>`](/en-US/docs/Web/HTML/Reference/Elements/figure)؛ عنصر `<figcaption>` باید اولین یا آخرین فرزند آن باشد. |
| نقش ARIA ضمنی | [نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role). |
| نقش‌های ARIA مجاز | [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)، [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)، [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) |
| رابط DOM | [`HTMLElement`](/en-US/docs/Web/API/HTMLElement) |

## همچنین ببینید

- عنصر [`<figure>`](/en-US/docs/Web/HTML/Reference/Elements/figure)