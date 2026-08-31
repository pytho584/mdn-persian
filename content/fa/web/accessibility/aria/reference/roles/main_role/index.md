---
title: "ARIA: main role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: main role"
short-title: main
slug: Web/Accessibility/ARIA/Reference/Roles/main_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#main
  - https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/main.html
sidebar: accessibilitysidebar
---

نقش نشانه (`main`) برای نشان دادن محتوای اصلی یک سند استفاده می‌شود. ناحیه محتوای اصلی شامل محتوایی است که مستقیماً با موضوع مرکزی یک سند مرتبط است یا آن را گسترش می‌دهد، یا عملکرد اصلی یک برنامه را فراهم می‌کند.

```html
<div id="main" role="main">
  <h1>Avocados</h1>
  <!-- main section content -->
</div>
```

این بخش اصلی از سندی است که درباره آووکادو بحث می‌کند. زیربخش‌های این سند می‌توانند تاریخچه، انواع مختلف، مناطقی که در آن رشد می‌کنند، و غیره را بررسی کنند.

## توضیحات

نقش `main` یک نقش [نشانه](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) پیمایشی است که محتوای اصلی یک سند را شناسایی می‌کند. نشانه‌ها می‌توانند توسط فناوری‌های کمکی مانند صفحه‌خوان‌ها برای شناسایی سریع و پیمایش به بخش‌های بزرگ سند استفاده شوند.

با طبقه‌بندی و برچسب‌گذاری بخش‌های یک صفحه، اطلاعات ساختاری که به‌طور بصری از طریق طرح‌بندی منتقل می‌شوند، می‌توانند به‌صورت برنامه‌نویسی ارائه شوند. صفحه‌خوان‌ها از نقش‌های نشانه برای ارائه پیمایش صفحه‌کلید به بخش‌های مهم یک صفحه استفاده می‌کنند. برای کسانی که از طریق نقش‌های نشانه پیمایش می‌کنند، نقش main جایگزینی برای پیوندهای «پرش به محتوای اصلی» است.

در هر سند فقط یک نقش نشانه `main` باید وجود داشته باشد.

عنصر {{HTMLElement('main')}} دارای نقش `main` است. توسعه‌دهندگان باید به‌جای استفاده از ARIA از HTML معنایی — در این مورد {{HTMLElement('main')}} — استفاده کنند.

### نقش‌ها، حالت‌ها و ویژگی‌های ARIA مرتبط

- [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns)
  - : ویژگی `aria-owns` روابطی را در لایه دسترس‌پذیری ایجاد می‌کند که در DOM وجود ندارند. اسناد و برنامه‌ها می‌توانند در DOM تودرتو باشند، که ممکن است منجر به داشتن بیش از یک عنصر main به‌عنوان نوادگان DOM شود. در این صورت، `aria-owns` را برای شناسایی رابطه main با سند یا برنامه ancestor خود وارد کنید.

- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا `aria-labelledby`
  - : اگر یک عنوان قابل مشاهده وجود دارد، نام قابل دسترس را با [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) شناسایی کنید. در غیر این صورت، گنجاندن یک [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) می‌تواند برای جهت‌دهی به کاربران فناوری کمکی مفید باشد، به‌ویژه در برنامه‌های تک‌صفحه‌ای که تغییرات محتوای اصلی بدون ایجاد رویداد بارگذاری صفحه اتفاق می‌افتد.

## مثال

```html
<body>
  <!-- primary navigation -->

  <div role="main">
    <h1>The First Indochina War</h1>
    <!-- article content -->
  </div>

  <!-- sidebar and footer -->
</body>
```

## نگرانی‌های دسترس‌پذیری

### فقط یک نقش `main` در هر سند استفاده کنید

نقش [نشانه](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) `main` باید فقط یک بار در هر سند استفاده شود.

اگر یک سند شامل دو نقش `main` باشد، مثلاً هنگام به‌روزرسانی محتوای صفحه با جاوااسکریپت، وجود نقش `main` غیرفعال باید از فناوری کمکی حذف شود، از طریق تکنیک‌هایی مانند تغییر [`ویژگی hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden).

```html
<main>
  <h1>Active `main` element</h1>
  <!-- content -->
</main>

<main hidden>
  <h1>Hidden `main` element</h1>
  <!-- content -->
</main>
```

همچنین مفید است که یک نام قابل دسترس برای کمک به جهت‌دهی کاربران فناوری کمکی لحاظ شود، به‌ویژه در برنامه‌های تک‌صفحه‌ای که تغییرات محتوای اصلی بدون ایجاد رویداد بارگذاری صفحه اتفاق می‌افتد. این مورد می‌تواند با `aria-labelledby` اضافه شود اگر نام مناسبی در محتوا وجود داشته باشد، یا با `aria-label` اگر وجود نداشته باشد.

## بهترین روش‌ها

### HTML را ترجیح دهید

استفاده از عنصر {{HTMLElement('main')}} به‌طور خودکار منتقل می‌کند که عنصر دارای نقش `main` است. در صورت امکان، ترجیح دهید از عنصر معنایی `<main>` به‌جای نقش `main` استفاده کنید.

### پرش از ناوبری

پرش از ناوبری، همچنین به‌عنوان "skipnav" شناخته می‌شود، تکنیکی است که به کاربر فناوری کمکی اجازه می‌دهد به‌سرعت از بخش‌های بزرگ محتوای تکراری (ناوبری اصلی، بنرهای اطلاعاتی و غیره) عبور کند. این کار به کاربر اجازه می‌دهد سریع‌تر به محتوای اصلی صفحه دسترسی یابد.

افزودن یک [`ویژگی id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) به عنصری با اعلان `role="main"` به آن اجازه می‌دهد تا هدف پیوند پرش از ناوبری برای کاربران باشد.

```html
<body>
  <a href="#main-content">Skip to main content</a>

  <!-- navigation and header content -->

  <div id="main-content" role="main">
    <!-- main page content -->
  </div>
</body>
```

که معادل است با:

```html
<body>
  <a href="#main-content">Skip to main content</a>

  <!-- navigation and header content -->

  <main id="main-content">
    <!-- main page content -->
  </main>
</body>
```

- [پیوندهای «پرش از ناوبری» WebAIM](https://webaim.org/techniques/skipnav/)

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('main')}}
- [استفاده از بخش‌ها و طرح‌های HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)
- [نشانه‌های قابل دسترس | scottohara.me](https://www.scottohara.me/blog/2018/03/03/landmarks.html)
- [عنصر main | HTML5 Doctor](https://html5doctor.com/the-main-element/)