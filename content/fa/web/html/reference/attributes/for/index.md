---
title: "for HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/for"
translated_by: "n8n + AI"
---

# ویژگی `for`

ویژگی `for` یک ویژگی مجاز برای المان‌های `<label>` و `<output>` است. وقتی روی `<label>` استفاده شود، مشخص می‌کند که این برچسب به کدام المان فرم اشاره دارد. وقتی روی `<output>` استفاده شود، رابطهٔ صریحی بین المان‌هایی برقرار می‌کند که مقادیرشان در خروجی استفاده می‌شوند.

## نکات استفاده

وقتی به عنوان ویژگی `<label>` به کار رود، مقدار `for` برابر با `id` المان فرم مرتبط است:

```html
<label for="username">Your name</label> <input type="text" id="username" />
```

وقتی به عنوان ویژگی `<output>` به کار رود، مقدار `for` یک لیست جدا شده با فاصله از `id` المان‌هایی است که برای تولید خروجی استفاده می‌شوند:

```html
<input type="range" id="b" name="b" value="50" /> +
<input type="number" id="a" name="a" value="10" /> =
<output name="result" for="a b">60</output>
```

## مثال‌ها

مثال‌های استفاده را می‌توانید در صفحهٔ مربوط به هر یک از المان‌های `<label>` و `<output>` ببینید.