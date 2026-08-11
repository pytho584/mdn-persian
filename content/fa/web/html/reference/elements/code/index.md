---
title: "<code> HTML inline code element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/code"
translated_by: "n8n + AI"
---

عنصر `<code>` در HTML محتوای خود را به شکلی نمایش می‌دهد که نشان دهد متن یک قطعهٔ کوتاه از کد کامپیوتری است. به طور پیش‌فرض، متن با فونت monospace پیش‌فرض user agent (عامل کاربر) نمایش داده می‌شود.

```html interactive-example
<p>
  The <code>push()</code> method adds one or more elements to the end of an
  array and returns the new length of the array.
</p>
```

```css interactive-example
code {
  background-color: #eeeeee;
  border-radius: 3px;
  font-family: "Courier New", monospace;
  padding: 0 3px;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## مثال‌ها

یک پاراگراف متن که شامل `<code>` است:

```html
<p>
  The function <code>selectAll()</code> highlights all the text in the input
  field so the user can, for example, copy or delete the text.
</p>
```

### نتیجه

## نکات

برای نمایش چند خط کد، عنصر `<code>` را درون یک عنصر `<pre>` قرار دهید. خود `<code>` فقط یک عبارت یا خط کد را نمایش می‌دهد.

می‌توان با CSS قانونی برای selector `code` تعریف کرد تا فونت پیش‌فرض مرورگر را تغییر داد. اما تنظیمات کاربر ممکن است اولویت داشته باشد.

## خلاصهٔ فنی

| ویژگی | مقدار |
|-------|-------|
| دسته‌بندی محتوا (Content categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content), [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content), palpable content. |
| محتوای مجاز (Permitted content) | [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content). |
| حذف تگ (Tag omission) | هیچکدام، هر دو تگ شروع و پایان اجباری هستند. |
| والدین مجاز (Permitted parents) | هر عنصری که [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) می‌پذیرد. |
| نقش ARIA پیش‌فرض (Implicit ARIA role) | `code` |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | هر نقشی (Any) |
| رابط DOM (DOM interface) | `HTMLElement` (تا Gecko 1.9.2 (Firefox 4) این عنصر از `HTMLSpanElement` استفاده می‌کرد.) |

## مشخصات (Specifications)

## سازگاری با مرورگرها (Browser compatibility)

## همچنین ببینید

- {{HTMLElement("samp")}}
- {{HTMLElement("kbd")}}
- {{HTMLElement("var")}}
- {{HTMLElement("pre")}}