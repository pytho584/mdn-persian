---
title: "<hr> HTML thematic break (horizontal rule) element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/hr"
translated_by: "n8n + AI"
---

المان **`<hr>`** (خط افقی یا جداکننده موضوعی) در HTML یک عنصر block-level است که یک break موضوعی (thematic break) بین عناصر پاراگراف‌سطح را نشان می‌دهد. به عبارت دیگر، تغییر صحنه در یک داستان یا تغییر موضوع در یک بخش را مشخص می‌کند.

```html interactive-example
<p>§1: The first rule of Fight Club is: You do not talk about Fight Club.</p>

<hr />

<p>§2: The second rule of Fight Club is: Always bring cupcakes.</p>
```

```css interactive-example
hr {
  border: none;
  border-top: 3px double #333333;
  color: #333333;
  overflow: visible;
  text-align: center;
  height: 5px;
}

hr::after {
  background: white;
  content: "§";
  padding: 0 4px;
  position: relative;
  top: -13px;
}
```

از لحاظ تاریخی، `<hr>` همیشه به‌صورت یک خط افقی (horizontal rule) نمایش داده می‌شده است. اگرچه هنوز هم در مرورگرهای بصری ممکن است به‌صورت یک خط افقی نشان داده شود، اما این عنصر اکنون از نظر معنایی (semantic) تعریف می‌شود، نه از نظر نمایشی (presentational). بنابراین اگر می‌خواهید یک خط افقی رسم کنید، باید با اضافه کردن border به یک عنصر موجود با استفاده از CSS این کار را انجام دهید.

خواص `border-*` (مثلاً {{cssxref("border-style")}} و {{cssxref("border-color")}}) به شما امکان می‌دهند ظاهر خط را به‌طور قابل‌توجهی سفارشی کنید، چه در حال سفارشی‌سازی یک عنصر `<hr>` باشید و چه border رسم‌شده روی عنصری دیگر.

## Attributes

این عنصر شامل attributes عمومی (global attributes) [HTML](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `align` {{deprecated_inline}} {{Non-standard_Inline}}
  - : تراز خط را در صفحه تنظیم می‌کند. اگر مقداری مشخص نشود، مقدار پیش‌فرض `left` است.
- `color` {{deprecated_inline}} {{Non-standard_Inline}}
  - : رنگ خط را با نام رنگ یا مقدار هگزادسیمال تنظیم می‌کند.
- `noshade` {{deprecated_inline}} {{Non-standard_Inline}}
  - : خط را بدون سایه‌بندی (shading) تنظیم می‌کند.
- `size` {{deprecated_inline}} {{Non-standard_Inline}}
  - : ارتفاع خط را بر حسب پیکسل تنظیم می‌کند.
- `width` {{deprecated_inline}} {{Non-standard_Inline}}
  - : طول خط را در صفحه با مقدار پیکسل یا درصد تنظیم می‌کند.

## مثال

### HTML

```html
<p>
  This is the first paragraph of text. This is the first paragraph of text. This
  is the first paragraph of text. This is the first paragraph of text.
</p>

<hr />

<p>
  This is the second paragraph of text. This is the second paragraph of text.
  This is the second paragraph of text. This is the second paragraph of text.
</p>
```

### Result

{{EmbedLiveSample("Example")}}

## خلاصه فنی

| ویژگی | مقدار |
|----------|-------|
| [Categories](/en-US/docs/Web/HTML/Content_categories) | [Flow content](/en-US/docs/Web/HTML/Content_categories#flow_content), [palpable content](/en-US/docs/Web/HTML/Content_categories#palpable_content). |
| Permitted content | None; it is a [void element](/en-US/docs/Web/HTML/Void_elements). |
| Tag omission | Must have a start tag, and must not have an end tag. |
| Permitted parents | Any element that accepts [flow content](/en-US/docs/Web/HTML/Content_categories#flow_content). |
| Implicit ARIA role | [`separator`](/en-US/docs/Web/Accessibility/ARIA/Roles/separator_role) |
| Permitted ARIA roles | [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Roles/presentation_role) or [`none`](/en-US/docs/Web/Accessibility/ARIA/Roles/none_role) |
| DOM interface | [`HTMLHRElement`](/en-US/docs/Web/API/HTMLHRElement) |

| ویژگی | مقدار |
| --- | --- |
| دسته‌بندی محتوا | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) |
| محتوای مجاز | هیچ؛ این یک void element است. |
| حذف تگ | باید تگ شروع داشته باشد و نباید تگ پایانی داشته باشد. |
| والدین مجاز | هر عنصری که [flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد؛ همچنین عنصر [`<select>`](/en-US/docs/Web/HTML/Reference/Elements/select) |
| نقش ضمنی ARIA | [separator](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) |
| نقش‌های مجاز ARIA | [presentation](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) یا [none](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role) |
| رابط DOM | `HTMLHRElement` |

## همچنین ببینید

- [`<p>`](/en-US/docs/Web/HTML/Reference/Elements/p)
- [`<hr>` در `<select>`](/en-US/docs/Web/HTML/Reference/Elements/select#select_with_grouping_options)