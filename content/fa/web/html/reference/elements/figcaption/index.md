---
title: "<figcaption> HTML figure caption element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/figcaption"
translated_by: "n8n + AI"
---

# عنصر `<figcaption>`

عنصر `<figcaption>` در [HTML](/en-US/docs/Web/HTML) یک caption یا legend است که بقیهٔ محتوای عنصر والد خود یعنی `<figure>` را توصیف می‌کند و برای `<figure>` یک نام دسترس‌پذیر (accessible name) فراهم می‌کند.

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

این عنصر فقط [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) را شامل می‌شود.

## مثال‌ها

برای مشاهدهٔ مثال‌های `<figcaption>`، به صفحهٔ [`<figure>`](/en-US/docs/Web/HTML/Reference/Elements/figure) مراجعه کنید.

## خلاصهٔ فنی

| عنوان | مقدار |
|---|---|
| دسته‌بندی محتوا (Content categories) | هیچکدام. |
| محتوای مجاز (Permitted content) | محتوای جریان (Flow content). |
| حذف تگ (Tag omission) | هیچکدام؛ هر دو تگ شروع و پایان الزامی هستند. |
| والدهای مجاز (Permitted parents) | یک عنصر `<figure>`؛ عنصر `<figcaption>` باید اولین یا آخرین فرزند آن باشد. |
| نقش ARIA ضمنی (Implicit ARIA role) | هیچ نقش متناظری ندارد (No corresponding role). |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)، [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)، [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) |
| رابط DOM (DOM interface) | `HTMLElement` |

## همچنین ببینید

- عنصر [`<figure>`](/en-US/docs/Web/HTML/Reference/Elements/figure)