---
title: "ARIA: search role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: search role"
short-title: search
slug: Web/Accessibility/ARIA/Reference/Roles/search_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#search
  - https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/search.html
sidebar: accessibilitysidebar
---

نقش `search` برای شناسایی قابلیت جستجو استفاده می‌شود؛ بخشی از صفحه که برای جستجو در صفحه، سایت، یا مجموعه سایت‌ها به کار می‌رود.

```html
<form role="search">
  <!-- search input -->
</form>
```

## توضیحات

نقش `search` یک [نقش لندمارک](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) است که می‌توان آن را به عنصر محتوایی اضافه کرد که همه عناصر ترکیب‌شده برای تشکیل ویژگی جستجوی سند یا برنامه را در بر می‌گیرد، از جمله یک [`<input type="search">`](/en-US/docs/Web/HTML/Reference/Elements/input/search) فرزند. اگر یک سند بیش از یک جستجو داشته باشد، هر جستجو باید برچسب منحصربه‌فرد داشته باشد، مگر اینکه همان جستجو تکرار شده باشد؛ در این صورت از همان نام استفاده کنید. یک [`input` از نوع `search`](/en-US/docs/Web/HTML/Reference/Elements/input/search) وجود دارد، اگرچه این به خودی خود یک ناحیه جستجو را تعریف نمی‌کند. استفاده از {{HTMLElement('search')}} یک راه جایگزین برای تعریف ناحیه جستجو است.

## مثال‌ها

وقتی یک {{HTMLElement('form')}} یک فرم جستجو است، به جای نقش [`form`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role) از نقش `search` استفاده کنید.

```html
<form id="search" role="search">
  <label for="search-input">Search this site</label>
  <input type="search" id="search-input" name="search" spellcheck="false" />
  <input value="Submit" type="submit" />
</form>
```

## نگرانی‌های دسترس‌پذیری

[نقش‌های لندمارک](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) برای استفاده محدود طراحی شده‌اند تا بخش‌های بزرگ‌تر کلی سند را شناسایی کنند. استفاده بیش از حد از نقش‌های لندمارک می‌تواند در صفحه‌خوان‌ها «نویز» ایجاد کند و درک چیدمان کلی صفحه را دشوار کند.

## بهترین شیوه‌ها

### ترجیح HTML

استفاده از عنصر {{HTMLElement('search')}} به‌طور خودکار این را منتقل می‌کند که عنصر دارای نقش `search` است. در صورت امکان، ترجیح دهید به جای نقش `search` از عنصر معنایی `<search>` استفاده کنید.

اگر `<input>` شما از نوع `search` قبلاً درون یک {{HTMLElement("form")}} قرار دارد، پیچیدن فرم در یک عنصر `<search>` دیگر ممکن است نشانه‌گذاری غیرضروری باشد. در این حالت، استفاده از `role="search"` روی خود `<form>` قابل قبول است.

### برچسب‌گذاری لندمارک‌ها

#### لندمارک‌های متعدد

اگر بیش از یک نقش لندمارک `search` در یک سند وجود دارد، برای هر لندمارک یک برچسب فراهم کنید. این برچسب به کاربر فناوری کمکی امکان می‌دهد تا به سرعت هدف هر لندمارک را درک کند.

```html
<form id="site-search" role="search" aria-label="Sitewide">
  <!-- search input -->
</form>

…

<form id="page-search" role="search" aria-label="On this page">
  <!-- search input -->
</form>
```

#### لندمارک‌های تکراری

اگر یک نقش لندمارک `search` در یک سند تکرار شده باشد و هر دو لندمارک محتوای یکسانی داشته باشند، از همان برچسب برای هر لندمارک استفاده کنید. نمونه‌ای از این حالت، تکرار جستجوی سراسری در بالای صفحه و پایین صفحه است.

```html
<header>
  <form id="site-search-top" role="search" aria-label="Sitewide">
    <!-- search input -->
  </form>
</header>

…

<footer>
  <form id="site-search-bottom" role="search" aria-label="Sitewide">
    <!-- search input -->
  </form>
</footer>
```

#### توضیحات تکراری

صفحه‌خوان‌ها نوع نقشی که لندمارک دارد را اعلام می‌کنند. به همین دلیل، نیازی نیست در برچسب توصیف کنید که لندمارک چیست. برای مثال، یک اعلان `role="search"` با [`aria-label="Sitewide search"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) ممکن است به صورت تکراری اعلام شود، مانند «جستجوی سراسری جستجو».

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('form')}}
- عنصر {{HTMLElement('input')}}
- عنصر {{HTMLElement('search')}}
- [`<input type="search">`](/en-US/docs/Web/HTML/Reference/Elements/input/search)
- [استفاده از بخش‌ها و طرح کلی HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)