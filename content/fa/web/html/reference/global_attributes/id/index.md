---
title: "id HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/id"
translated_by: "n8n + AI"
---

**`id`** یک [global attribute](/en-US/docs/Web/HTML/Reference/Global_attributes) است که یک شناسه (ID) تعریف می‌کند. این شناسه باید در کل سند یکتا باشد.

```html interactive-example
<p>A normal, boring paragraph. Try not to fall asleep.</p>

<p id="exciting">The most exciting paragraph on the page. One of a kind!</p>
```

```css interactive-example
#exciting {
  background: linear-gradient(to bottom, #ffe8d4, #f69d3c);
  border: 1px solid dimgrey;
  padding: 10px;
  border-radius: 10px;
  box-shadow: 2px 2px 1px black;
}

#exciting::before {
  content: "ℹ️";
  margin-right: 5px;
}
```

## نحو

مقدار یک attribute با نام `id` نباید شامل کاراکترهای [ASCII whitespace](/en-US/docs/Glossary/Whitespace#in_html) باشد. مرورگرها وقتی با id نامعتبری مواجه می‌شوند که شامل whitespace است، آن را طوری تفسیر می‌کنند که گویی whitespace بخشی از خود id است. برخلاف attribute با نام [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) که مقادیر جداشده با فاصله را می‌پذیرد، عناصر فقط می‌توانند یک مقدار id داشته باشند.

از نظر فنی، مقدار یک attribute از نوع id می‌تواند شامل هر کاراکتر Unicode دیگری باشد. اما وقتی از این مقدار در CSS selectors استفاده می‌شود، چه از طریق JavaScript با APIهایی مثل `Document.querySelector()` و چه در stylesheetهای CSS، مقدار attribute باید یک [CSS identifier](/en-US/docs/Web/CSS/Reference/Values/ident) معتبر باشد. یعنی اگر مقدار id یک CSS identifier معتبر نباشد (مثلاً `my?id` یا `1234`)، قبل از استفاده در selector باید escape شود؛ یا با متد `CSS.escape()` یا به صورت دستی.

به همین دلیل توصیه می‌شود توسعه‌دهندگان برای attribute های id مقداری انتخاب کنند که یک CSS identifier معتبر باشد و نیازی به escape کردن نداشته باشد.

همچنین همهٔ مقادیر معتبر برای attribute id، شناسه‌های معتبر JavaScript نیستند. برای مثال، `1234` یک مقدار معتبر برای attribute است، اما یک JavaScript identifier معتبر نیست. این یعنی این مقدار، نام متغیر معتبری نیست؛ بنابراین نمی‌توانید با کدی مثل `window.1234` به عنصر دسترسی پیدا کنید. البته می‌توانید با `window["1234"]` به آن دسترسی داشته باشید.

## توضیحات

هدف از attribute id این است که یک عنصر واحد را هنگام لینک‌دادن (با استفاده از fragment identifier)، اسکریپت‌نویسی یا استایل‌دهی (با CSS) شناسایی کند.

می‌توانید عناصری را که attribute id دارند، به عنوان ویژگی‌های سراسری (global properties) شیء `window` در دسترس بگیرید؛ به این صورت که نام property همان مقدار id است و مقدار property، عنصر متناظر است. برای مثال، با این markup:

```html
<p id="preamble"></p>
```

می‌توانید این عنصر paragraph را در JavaScript با کد زیر دسترسی بگیرید:

```js
const content = window.preamble.textContent;
```

> [!WARNING]
> اتکا به الگوی `window["id-value"]` یا `window.idValue` خطرناک است و توصیه نمی‌شود، چون می‌تواند با APIهای فعلی یا آینده در مرورگر تداخل‌های غیرمنتظره ایجاد کند.
> برای مثال، اگر مرورگری در آینده یک ویژگی سراسری داخلی به نام `preamble` معرفی کند، کد شما دیگر نمی‌تواند به عنصر HTML دسترسی داشته باشد.
> برای جلوگیری از چنین تداخل‌هایی، همیشه از متد `Document.getElementById()` یا `Document.querySelector()` برای دسترسی به عناصر با id استفاده کنید.

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- همه [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- `Element.id` که این attribute را بازتاب می‌دهد
- متد `Document.getElementById`
- [ID selectors](/en-US/docs/Web/CSS/Reference/Selectors/ID_selectors) در CSS