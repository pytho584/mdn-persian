---
title: "<address> HTML contact address element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/address"
translated_by: "n8n + AI"
---

عنصر `<address>` (آدرس) در HTML نشان می‌دهد که محتوای درونش اطلاعات تماس برای یک یا چند شخص یا یک سازمان را در بر دارد.

```html interactive-example
<p>با نویسنده این صفحه تماس بگیرید:</p>

<address>
  <a href="mailto:jim@example.com">jim@example.com</a><br />
  <a href="tel:+14155550132">+1 (415) 555‑0132</a>
</address>
```

```css interactive-example
a[href^="mailto"]::before {
  content: "📧 ";
}

a[href^="tel"]::before {
  content: "📞 ";
}
```

اطلاعات تماس ارائه‌شده در `<address>` می‌تواند هر شکلی متناسب با زمینه داشته باشد و شامل هر نوع اطلاعات تماس مورد نیاز مانند آدرس فیزیکی، URL، ایمیل، شماره تلفن، نام کاربری در شبکه‌های اجتماعی، مختصات جغرافیایی و غیره باشد. این عنصر باید نام شخص، افراد یا سازمانی را که اطلاعات تماس به آن اشاره دارد، در بر بگیرد.

`<address>` در زمینه‌های مختلفی قابل استفاده است؛ مثلاً در هدر صفحه برای نمایش اطلاعات تماس یک کسب‌وکار، یا درون عنصر {{HTMLElement("article")}} برای مشخص کردن نویسندهٔ مقاله.

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

- عنصر `<address>` فقط برای نمایش اطلاعات تماس نزدیک‌ترین عنصر والد {{HTMLElement("article")}} یا {{HTMLElement("body")}} خود استفاده می‌شود.
- این عنصر نباید اطلاعاتی بیش از اطلاعات تماس داشته باشد، مثلاً تاریخ انتشار (که متعلق به عنصر {{HTMLElement("time")}} است).
- معمولاً `<address>` را می‌توان درون عنصر {{HTMLElement("footer")}} بخش مربوطه قرار داد.

## مثال

این مثال استفاده از `<address>` را برای مشخص کردن اطلاعات تماس نویسنده یک مقاله نشان می‌دهد.

```html
<address>
  می‌توانید با نویسنده از طریق
  <a href="http://www.example.com/contact">www.example.com</a> تماس بگیرید.<br />
  اگر باگی دیدید، لطفاً با
  <a href="mailto:webmaster@example.com">webmaster@example.com</a> تماس بگیرید.<br />
  همچنین می‌توانید به ما سر بزنید:<br />
  Mozilla Foundation<br />
  331 E Evelyn Ave<br />
  Mountain View, CA 94041<br />
  USA
</address>
```

### نتیجه

{{EmbedLiveSample("Examples", "300", "200")}}

اگرچه `<address>` متن را با استایل پیش‌فرض مشابه عناصر {{HTMLElement("i")}} یا {{HTMLElement("em")}} نمایش می‌دهد، اما استفاده از آن برای اطلاعات تماس مناسب‌تر است، زیرا معنای معنایی (semantic) بیشتری را منتقل می‌کند.

| ویژگی | مقدار |
|---|---|
| **دسته‌بندی محتوا (Content categories)** | [محتوای جریانی (Flow content)](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، محتوای ملموس (palpable content) |
| **محتوای مجاز (Permitted content)** | [محتوای جریانی (Flow content)](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، اما بدون عنصر `<address>` تو‌در‌تو، بدون محتوای heading (`<hgroup>`، `<h1>` تا `<h6>`) و بدون محتوای بخش‌بندی (sectioning content) مانند `<article>`، `<aside>`، `<section>`، `<nav>` و همچنین بدون `<header>` یا `<footer>` |
| **حذف تگ (Tag omission)** | هیچکدام؛ هر دو تگ شروع و پایان اجباری هستند. |
| **والدین مجاز (Permitted parents)** | هر عنصری که [محتوای جریانی (Flow content)](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد، اما همیشه به استثنای عناصر `<address>` (طبق اصل تقارن منطقی: اگر `<address>` به‌عنوان والد نمی‌تواند `<address>` تو‌در‌تو داشته باشد، محتوای `<address>` نیز نمی‌تواند `<address>` را به‌عنوان والد داشته باشد). |
| **نقش ARIA ضمنی** | `group` |
| **نقش‌های ARIA مجاز** | هر (Any) |
| **رابط DOM** | `HTMLElement` (پیش از Gecko 2.0 (Firefox 4)، Gecko از رابط `HTMLSpanElement` استفاده می‌کرد) |

## مشخصات (Specifications)

(اطلاعات مشخصات در نسخه اصلی موجود است.)

## سازگاری با مرورگر (Browser compatibility)

(اطلاعات سازگاری در نسخه اصلی موجود است.)

## همچنین ببینید

- سایر عناصر مرتبط با بخش‌بندی: `<body>`، `<nav>`، `<article>`، `<aside>`، `<h1>` تا `<h6>`، `<hgroup>`، `<footer>`، `<section>`، `<header>`
- [بخش‌ها و ساختار کلی یک سند HTML (Sections and outlines of an HTML document)](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)