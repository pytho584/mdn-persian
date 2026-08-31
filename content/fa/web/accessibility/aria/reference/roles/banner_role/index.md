---
title: "ARIA: banner role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: banner role"
short-title: banner
slug: Web/Accessibility/ARIA/Reference/Roles/banner_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#banner
  - https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/banner.html
sidebar: accessibilitysidebar
---

نقش `banner` برای تعریف سرصفحه سراسری سایت استفاده می‌شود که معمولاً شامل لوگو، نام شرکت، قابلیت جستجو و احتمالاً ناوبری سراسری یا یک شعار است. این عنصر معمولاً در بالای صفحه قرار دارد.

به‌طور پیش‌فرض، عنصر {{htmlelement("header")}} در HTML معنای یکسانی با نقطه عطف `banner` دارد، مگر اینکه فرزند یکی از عناصر {{htmlelement("aside")}}، {{htmlelement("article")}}، {{htmlelement("main")}}، {{htmlelement("nav")}} یا {{htmlelement("section")}} باشد، که در آن صورت {{htmlelement("header")}} نقش [`generic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role) را نمایش می‌دهد، نه معادل بنر سراسری سایت را.

## توضیحات

نقش نقطه عطف `banner` نقش ARIA ضمنی عنصر ظرفی را که روی آن اعمال می‌شود، بازنویسی می‌کند. این نقش باید برای محتوای سراسری و تکراری سایت که معمولاً در بالای هر صفحه قرار دارد، اختصاص داده شود.

بنر معمولاً شامل مواردی مانند لوگو یا هویت سازمانی، یا احتمالاً ابزار جستجوی مخصوص سایت است و به طور کلی چیزی است که تیم بازاریابی شما آن را «هدر» یا «بنر بالای» سایت می‌نامد. اگر از تکنیک [`عنصر header`](/en-US/docs/Web/HTML/Reference/Elements/header) برای آن بنر استفاده نمی‌شود، باید اعلان `role="banner"` برای تعریف یک نقطه عطف بنر برای فناوری‌های کمکی استفاده شود.

فناوری‌های کمکی می‌توانند عنصر `header` یک صفحه را به عنوان `banner` شناسایی کنند، اگر این عنصر فرزند [`عنصر body`](/en-US/docs/Web/HTML/Reference/Elements/body) باشد و در زیربخش‌های `article`، `aside`، `main`، `nav` یا `section` قرار نگرفته باشد.

هر صفحه می‌تواند یک نقطه عطف `banner` داشته باشد، اما هر صفحه معمولاً باید به یک عنصر واحد با نقش بنر محدود شود. در مورد صفحه‌ای که شامل نقش‌های تودرتوی `document` و/یا `application` است، هر نقش `document` یا `application` تودرتو نیز می‌تواند یک نقطه عطف `banner` داشته باشد. اگر یک صفحه شامل بیش از یک نقطه عطف `banner` باشد، هر کدام باید یک نام قابل دسترس منحصر به فرد داشته باشند.

### نقش‌ها، حالت‌ها و ویژگی‌های ARIA مرتبط

هیچ‌کدام.

### تعاملات صفحه‌کلید

هیچ‌کدام.

### ویژگی‌های جاوااسکریپت مورد نیاز

هیچ‌کدام.

## مثال‌ها

در اینجا یک بنر نمونه با لینک پرش به ناوبری، لوگو، عنوان و زیرعنوان آورده شده است. از آنجایی که این سرصفحه اصلی سایت است، ما نقش نقطه عطف `banner` را به عنصر ظرف اضافه کرده‌ایم.

```html
<div role="banner">
  <a href="#main" id="skipToMain" class="skiptocontent">Skip To main content</a>
  <img src="images/w3c.png" alt="W3C Logo" />
  <h1>ARIA Landmarks</h1>
  <p>Identifying page subsections for easy navigation</p>
  <nav>…</nav>
</div>
```

ما همچنین می‌توانستیم مثال بالا را با عنصر `header` در HTML بنویسیم:

```html
<header>
  <a href="#main" id="skipToMain" class="skiptocontent">Skip To main content</a>
  <img src="images/w3c.png" alt="W3C Logo" />
  <h1>ARIA Landmarks</h1>
  <p>Identifying page subsections for easy navigation</p>
  <nav>…</nav>
</header>
```

## بهترین روش‌ها

استفاده از عنصر {{HTMLElement('header')}} به طور خودکار به اطلاع می‌رساند که عنصر دارای نقش `banner` است. در صورت امکان، ترجیح دهید از عنصر معنایی `<header>` به جای نقش `banner` استفاده کنید.

در حالی که بهتر است از عنصر `header` استفاده کنید و مطمئن شوید که فرزند هیچ زیربخشی از صفحه نیست، گاهی اوقات به HTML اصلی دسترسی ندارید. در این صورت، می‌توانید نقش `banner` را با جاوااسکریپت به عنصری از صفحه که باید به عنوان `banner` نمایش داده شود، اضافه کنید. شناسایی بنر صفحه به این روش به بهبود دسترسی‌پذیری سایت کمک می‌کند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [عنصر `header` در HTML](/en-US/docs/Web/HTML/Reference/Elements/header)
- [مثال نقاط عطف WC3](https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/banner.html)