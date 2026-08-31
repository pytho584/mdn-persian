---
title: "ARIA: math role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/math_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: math role"
short-title: math
slug: Web/Accessibility/ARIA/Reference/Roles/math_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#math
sidebar: accessibilitysidebar
---

نقش `math` نشان‌دهنده این است که محتوا یک عبارت ریاضی را نمایش می‌دهد.

## توضیحات

محتوای دارای نقش `math` باید در قالبی قابل دسترس مانند [MathML](/en-US/docs/Web/MathML) یا با نوع دیگری از نمایش متنی نشانه‌گذاری شود که توسط مرورگر یا یک کتابخانه پلی‌فیل به فرمت قابل دسترس تبدیل شود.

متأسفانه، پشتیبانی مرورگرها از MathML جهانی نیست. اگرچه استفاده از تصویر یک عبارت ریاضی ایده‌آل نیست، اما اگر از تصویر استفاده می‌کنید، از نقش `math` استفاده کنید. اطمینان حاصل کنید که هر تصویر ریاضی با یک ویژگی `alt` که عبارت ریاضی را به صورت گفتاری توصیف می‌کند، برچسب‌گذاری شده است.

اگر عنصر math فقط فرزندان تزئینی داشته باشد و نام قابل دسترس برای انتقال عبارت ریاضی در نظر گرفته شده است، از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) برای ارائه یک رشته که بیانگر عبارت است استفاده کنید. اگر عنصر math شامل محتوای قابل پیمایشی باشد که عبارت ریاضی را منتقل می‌کند و یک برچسب قابل مشاهده برای عبارت وجود دارد، از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) استفاده کنید. در غیر این صورت، از `aria-label` برای نام‌گذاری عبارت استفاده کنید، مثلاً `aria-label="Pythagorean Theorem"`.

## مثال‌ها

اگر از تصویر یا HTML غیر معنایی برای ایجاد یک معادله استفاده می‌کنید، از نقش `math` استفاده کنید.

<div role="math" aria-label="a^{2} + b^{2} = c^{2}">
   a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup>
</div>

قضیه فیثاغورس بالا به صورت قابل دسترس به این صورت نوشته شده است:

```html
<div role="math" aria-label="a^{2} + b^{2} = c^{2}">
  a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup>
</div>
```

اگر از تصویر استفاده شده بود، ویژگی `alt` به همراه نقش `math` استفاده می‌شد:

```html
<img src="pythagorean_theorem.gif" alt="a^{2} + b^{2} = c^{2}" role="math" />
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [MathML در MDN](/en-US/docs/Web/MathML) و عنصر `<math>` (نه HTML)
- [مشخصات MathML](https://w3c.github.io/mathml/spec.html)