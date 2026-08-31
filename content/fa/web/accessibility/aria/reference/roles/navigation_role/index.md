---
title: "ARIA: navigation role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: navigation role"
short-title: navigation
slug: Web/Accessibility/ARIA/Reference/Roles/navigation_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#navigation
  - https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/navigation.html
sidebar: accessibilitysidebar
---

نقش `navigation` برای شناسایی گروه‌های اصلی از پیوندها که برای پیمایش در یک وب‌سایت یا محتوای صفحه استفاده می‌شود، به کار می‌رود.

```html
<div role="navigation" aria-label="Main">
  <!-- list of links to main website locations -->
</div>
```

این ناوبری اصلی یک وب‌سایت است.

## توضیحات

نقش `navigation` یک [نقش نشانه‌گذاری](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) است. نقش‌های نشانه‌گذاری راهی برای شناسایی سازمان و ساختار یک صفحه وب فراهم می‌کنند. با طبقه‌بندی و برچسب‌گذاری بخش‌های یک صفحه، اطلاعات ساختاری که به صورت بصری از طریق چیدمان منتقل می‌شود، به صورت برنامه‌نویسی‌شده نمایش داده می‌شود. صفحه‌خوان‌ها از نقش‌های نشانه‌گذاری برای ارائه ناوبری صفحه‌کلید به بخش‌های مهم یک صفحه استفاده می‌کنند. مانند عنصر {{HTMLElement('nav')}} در HTML، نشانه‌های ناوبری راهی برای شناسایی گروه‌ها (مانند فهرست‌ها) از پیوندها که برای پیمایش وب‌سایت یا محتوای صفحه در نظر گرفته شده‌اند، فراهم می‌کنند. اگر یک صفحه بیش از یک نشانه ناوبری داشته باشد، هر یک باید دارای یک برچسب منحصربه‌فرد باشد. اگر دو یا چند نشانه ناوبری در یک صفحه مجموعه پیوندهای یکسانی داشته باشند، از برچسب یکسانی برای هر کدام استفاده کنید.

ترجیحاً از عنصر [`<nav>`](/en-US/docs/Web/HTML/Reference/Elements/nav) HTML5 برای تعریف یک نشانه ناوبری استفاده شود. اگر از تکنیک عنصر nav HTML5 استفاده نمی‌شود، از یک ویژگی `role="navigation"` برای تعریف یک نشانه ناوبری استفاده کنید.

> [!NOTE]
> استفاده از عنصر {{HTMLElement('nav')}} به طور خودکار اعلام می‌کند که یک بخش دارای نقش `navigation` است. توسعه‌دهندگان همیشه باید ترجیح دهند از عنصر معنایی صحیح HTML به جای استفاده از ARIA استفاده کنند.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : توضیح مختصری از هدف ناوبری، با حذف عبارت "navigation"، زیرا صفحه‌خوان هم نقش و هم محتوای برچسب را می‌خواند.

### تعاملات صفحه‌کلید

هیچ‌کدام.

### ویژگی‌های جاوااسکریپت مورد نیاز

هیچ‌کدام.

## مثال‌ها

```html
<div role="navigation" aria-label="Customer service">
  <ul>
    <li><a href="#">Help</a></li>
    <li><a href="#">Order tracking</a></li>
    <li><a href="#">Shipping &amp; Delivery</a></li>
    <li><a href="#">Returns</a></li>
    <li><a href="#">Contact us</a></li>
    <li><a href="#">Find a store</a></li>
  </ul>
</div>
```

## نگرانی‌های دسترسی

[نقش‌های نشانه‌گذاری](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) به منظور استفاده محدود، برای شناسایی بخش‌های بزرگ‌تر کلی سند در نظر گرفته شده‌اند. استفاده از تعداد زیاد نقش‌های نشانه‌گذاری می‌تواند در صفحه‌خوان‌ها "نویز" ایجاد کند و درک چیدمان کلی صفحه را دشوار سازد.

## بهترین روش‌ها

### ترجیح HTML

استفاده از عنصر {{HTMLElement('nav')}} به طور خودکار اعلام می‌کند که عنصر دارای نقش `navigation` است. در صورت امکان، ترجیح دهید از عنصر معنایی `<nav>` به جای نقش `navigation` استفاده کنید.

### برچسب‌گذاری نشانه‌ها

#### چندین نشانه

اگر بیش از یک نقش نشانه `navigation` یا عنصر {{HTMLElement('nav')}} در یک سند وجود داشته باشد، برای هر نشانه یک برچسب ارائه دهید. این برچسب به کاربر فناوری کمکی امکان می‌دهد تا به سرعت هدف هر نشانه را درک کند.

```html
<div id="main-nav" role="navigation" aria-label="Main">
  <!-- content -->
</div>

…

<nav id="footer-nav" aria-label="Footer">
  <!-- content -->
</nav>
```

#### نشانه‌های تکراری

اگر یک نقش نشانه `navigation` یا عنصر {{HTMLElement('nav')}} در یک سند تکرار شود و هر دو نشانه محتوای یکسانی داشته باشند، از برچسب یکسانی برای هر نشانه استفاده کنید. نمونه‌ای از این می‌تواند تکرار ناوبری اصلی در بالا و پایین صفحه باشد.

```html
<header>
  <nav id="main-nav" aria-label="Main">
    <!-- list of links to main website locations -->
  </nav>
</header>

…

<footer>
  <nav id="footer-nav" aria-label="Main">
    <!-- list of links to main website locations -->
  </nav>
</footer>
```

#### توضیحات تکراری

صفحه‌خوان‌ها نوع نقش نشانه را اعلام می‌کنند. به همین دلیل، نیازی نیست که در برچسب خود توضیح دهید که نشانه چیست. برای مثال، اعلام `role="navigation"` با `aria-label="Primary navigation"` ممکن است به صورت تکراری به عنوان "primary navigation navigation" اعلام شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('nav')}}
- [استفاده از بخش‌ها و طرح‌بندی HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)
- [نشانه‌های قابل دسترس | scottohara.me](https://www.scottohara.me/blog/2018/03/03/landmarks.html)
- [ناوبری معنایی با عنصر nav | HTML5 Doctor](https://html5doctor.com/nav-element/)