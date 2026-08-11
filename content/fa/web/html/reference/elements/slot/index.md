---
title: "<slot> HTML web component slot element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/slot"
translated_by: "n8n + AI"
---

عنصر **`<slot>`** یک placeholder درون یک [Web Component](/en-US/docs/Web/API/Web_components) است. وقتی از کامپوننت استفاده می‌کنید، می‌توانید slot را با نشانه‌گذاری (markup) دلخواه خود پر کنید. این کار به شما امکان می‌دهد درخت‌های DOM جداگانه بسازید و آن‌ها را با هم نمایش دهید.

Slotها می‌توانند شامل متن ساده، سایر عناصر HTML یا Web Componentهای دیگر باشند. یک slot همچنین می‌تواند محتوای پیش‌فرض داشته باشد که اگر slot محتوای دیگری به آن اختصاص داده نشود، نمایش داده می‌شود.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `name`
  - : نام slot. یک _slot نام‌دار (named slot)_ عنصر `<slot>`ای است که ویژگی `name` دارد، در حالی که یک _slot بی‌نام (unnamed slot)_ ویژگی `name` ندارد و نام آن به طور پیش‌فرض رشتهٔ خالی است.

    وقتی یک shadow root از [اختصاص slot نام‌دار (named slot assignment)](/en-US/docs/Web/HTML/Reference/Elements/template#named) استفاده می‌کند، فرزندهای سطح بالای host آن در slotهایی رندر می‌شوند که ویژگی [`slot`](/en-US/docs/Web/API/Element/slot)شان با نام slot مطابقت داشته باشد. نام slotها باید در هر shadow root یکتا باشند: اگر دو slot با نام یکسان داشته باشید، همهٔ عناصر دارای ویژگی `slot` متناظر، در _اولین_ slot رندر می‌شوند. همهٔ فرزندهای سطح بالایی که ویژگی `slot` ندارند، در اولین عنصر `<slot>` بی‌نام رندر می‌شوند که به آن _slot پیش‌فرض (default slot)_ می‌گویند. اگر shadow root از [اختصاص slot دستی (manual slot assignment)](/en-US/docs/Web/HTML/Reference/Elements/template#manual) استفاده کند، `name` تأثیری ندارد.

    برای اطلاعات بیشتر به [`shadowrootslotassignment`](/en-US/docs/Web/HTML/Reference/Elements/template#shadowrootslotassignment) روی عنصر `<template>` و [`Element.attachShadow()`](/en-US/docs/Web/API/Element/attachShadow#slotassignment) مراجعه کنید.

## مثال‌ها

### استفادهٔ پایه

این HTML نشان می‌دهد که چگونه می‌توان چند slot نام‌دار را درون یک عنصر `<template>` تعریف کرد. توجه کنید که این slotها فقط زمانی به عنوان slot استفاده می‌شوند که قالب (template) درون یک shadow root به کار رود.

```html
<template id="element-details-template">
  <style>
    details {
      font-family: "Open Sans Light","Helvetica","Arial", sans-serif;
    }
    .name {
      font-weight: bold;
      color: #217ac0;
      font-size: 120%;
    }
    h4 {
      margin: 10px 0 -8px 0;
      background: #217ac0;
      color: white;
      padding: 2px 6px;
      border: 1px solid #cee9f9;
      border-radius: 4px;
    }
    .attributes {
      margin-left: 22px;
      font-size: 90%;
    }
    .attributes p {
      margin-left: 16px;
      font-style: italic;
    }
  </style>
  <details>
    <summary>
      <code class="name">
        &lt;<slot name="element-name">NEED NAME</slot>&gt;
      </code>
      <span class="desc"><slot name="description">NEED DESCRIPTION</slot></span>
    </summary>
    <div class="attributes">
      <h4>Attributes</h4>
      <slot name="attributes"><p>None</p></slot>
    </div>
  </details>
  <hr />
</template>
```

> **توجه:** می‌توانید این مثال کامل را در [element-details](https://github.com/mdn/web-components-examples/tree/main/element-details) ببینید (نمایش زنده در [اینجا](https://mdn.github.io/web-components-examples/element-details/)). همچنین توضیحات بیشتری در [استفاده از قالب‌ها و slotها](/en-US/docs/Web/API/Web_components/Using_templates_and_slots) پیدا می‌کنید.

| ویژگی | مقدار |
| --- | --- |
| [دسته‌های محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | [محتوای جریانی](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [محتوای عبارتی](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| محتوای مجاز | [Transparent](/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model) |
| رویدادها | [slotchange](/en-US/docs/Web/API/HTMLSlotElement/slotchange_event) |
| حذف برچسب | هیچکدام؛ هر دو برچسب شروع و پایان اجباری‌اند. |
| والدین مجاز | هر عنصری که [محتوای عبارتی](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد |
| نقش ARIA ضمنی | [هیچ نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | هیچ `role` مجاز نیست |
| رابط DOM | [HTMLSlotElement](/en-US/docs/Web/API/HTMLSlotElement) |

## همچنین ببینید

- عنصر HTML [`<template>`](/en-US/docs/Web/HTML/Element/template)
- ویژگی HTML [`slot`](/en-US/docs/Web/HTML/Reference/Global_attributes/slot)
- شبه‌عنصر CSS [`::slotted`](/en-US/docs/Web/CSS/::slotted)
- شبه‌کلاس CSS [`:has-slotted`](/en-US/docs/Web/CSS/:has-slotted)
- ماژول [CSS scoping](/en-US/docs/Web/CSS/Guides/Scoping)
- [استفاده از template ها و slot ها](/en-US/docs/Web/API/Web_components/Using_templates_and_slots)