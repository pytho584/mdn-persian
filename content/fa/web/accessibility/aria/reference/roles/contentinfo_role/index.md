---
title: "ARIA: contentinfo role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/contentinfo_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: contentinfo role"
short-title: contentinfo
slug: Web/Accessibility/ARIA/Reference/Roles/contentinfo_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#contentinfo
  - https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/contentinfo.html
sidebar: accessibilitysidebar
---

نقش `contentinfo` یک فوتر را تعریف می‌کند که شامل اطلاعات شناسایی مانند اطلاعات کپی‌رایت، پیوندهای ناوبری و بیانیه‌های حریم خصوصی است و در هر سند از یک وب‌سایت یافت می‌شود. این بخش معمولاً «فوتر» نامیده می‌شود.

```html
<div role="contentinfo">
  <h2>Footer</h2>
  <!-- footer content -->
</div>
```

این یک فوتر وب‌سایت است. توصیه می‌شود به جای آن از عنصر {{HTMLElement('footer')}} استفاده کنید:

```html
<footer>
  <h2>Footer</h2>
  <!-- footer content -->
</footer>
```

## توضیحات

نقش `contentinfo` یک [نقطه عطف](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) است که برای شناسایی فوتر صفحه استفاده می‌شود. نقاط عطف می‌توانند توسط فناوری کمکی برای شناسایی سریع و پیمایش به بخش‌های بزرگ سند استفاده شوند. هر صفحه باید فقط یک نقش نقطه عطف `contentinfo` در سطح بالا داشته باشد.

هر صفحه باید فقط یک نقطه عطف `contentinfo` داشته باشد، که با استفاده از عنصر {{HTMLElement('footer')}} یا با اعلام `role="contentinfo"` ایجاد می‌شود. نقاط عطف `contentinfo` که در محتوای جاسازی‌شده از طریق {{HTMLElement('iframe')}} وجود دارند، به این محدودیت محاسبه نمی‌شوند.

> [!NOTE]
> استفاده از عنصر {{HTMLElement('footer')}} به‌طور خودکار نشان می‌دهد که یک بخش نقش `contentinfo` دارد. توسعه‌دهندگان باید همیشه استفاده از عنصر HTML معنایی صحیح را به استفاده از ARIA ترجیح دهند و حتماً در VoiceOver {{HTMLElement('footer#accessibility', 'تست برای مشکلات شناخته‌شده')}} را انجام دهند.

## مثال‌ها

```html
<body>
  <!-- other page content -->

  <div role="contentinfo">
    <h2>MDN Web Docs</h2>
    <ul>
      <li><a href="#">Web Technologies</a></li>
      <li><a href="#">Learn Web Development</a></li>
      <li><a href="#">About MDN</a></li>
      <li><a href="#">Feedback</a></li>
    </ul>
    <p>
      © 2005-2012 Mozilla and individual contributors. Content is available
      under <a href="#">these licenses</a>.
    </p>
  </div>
</body>
```

## نگرانی‌های دسترس‌پذیری

### به‌ندرت استفاده کنید

[نقش‌های نقطه عطف](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) برای شناسایی بخش‌های بزرگ کلی سند در نظر گرفته شده‌اند. استفاده از نقش‌های نقطه عطف زیاد می‌تواند «نویز» در صفحه‌خوان‌ها ایجاد کند و درک چیدمان کلی صفحه را دشوار کند.

### یک نقطه عطف `contentinfo` در هر صفحه

#### عنصر `<body>`

باید فقط یک نقطه عطف `contentinfo` در هر سند وجود داشته باشد که به‌عنوان فرزند مستقیم عنصر {{HTMLElement('body')}} باشد.

#### مگافوترها

عناصر {{HTMLElement('footer')}} اضافی یا نقاط عطف `contentinfo` را داخل فوتر سند تو در تو نکنید. به جای آن از سایر [عناصر بخش‌بندی محتوا](/en-US/docs/Web/HTML/Reference/Elements#content_sectioning) استفاده کنید.

### برچسب‌گذاری نقاط عطف

#### چندین نقطه عطف

اگر در یک سند بیش از یک نقش نقطه عطف `contentinfo` یا عنصر {{HTMLElement('footer')}} وجود دارد، برای هر نقطه عطف یک برچسب با ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) فراهم کنید. این برچسب به کاربران فناوری کمکی امکان می‌دهد تا به‌سرعت هدف هر نقطه عطف را درک کنند.

```html
<body>
  …

  <article>
    <h2>Everyday Pad Thai</h2>
    <!-- article content -->
    <footer aria-label="Everyday Pad Thai metadata">
      <p>
        Posted on <time datetime="2021-09-23 12:17">September 23</time> by
        <a href="#">Lisa</a>.
      </p>
    </footer>
  </article>

  …

  <footer aria-label="Footer">
    <!-- footer content -->
  </footer>
</body>
```

#### توضیحات تکراری

صفحه‌خوان‌ها نوع نقشی که نقطه عطف است را اعلام می‌کنند. به همین دلیل، نیازی نیست در برچسب آن توصیف کنید که نقطه عطف چیست. برای مثال، اعلام `role="contentinfo"` با یک `aria-label="Footer"` ممکن است به‌طور تکراری به‌صورت «contentinfo footer» اعلام شود.

## بهترین روش‌ها

### ترجیح دادن HTML

وقتی عنصر {{HTMLElement('footer')}} فرزند مستقیم {{HTMLElement('body')}} باشد، به‌طور خودکار نشان می‌دهد که بخش دارای نقش `contentinfo` است (به‌جز {{HTMLElement('footer#accessibility', 'یک مشکل شناخته‌شده')}} در VoiceOver). اگر امکان دارد، به جای آن از `<footer>` استفاده کنید. توجه داشته باشید که عنصر `footer` که درون `article`، `aside`، `main`، `nav` یا `section` تودرتو شده است، به‌عنوان `contentinfo` در نظر گرفته نمی‌شود.

### مزایای اضافی

برخی فناوری‌ها مانند افزونه‌های مرورگر می‌توانند فهرستی از تمام نقش‌های نقطه عطف موجود در یک صفحه تولید کنند و به کاربرانی که از صفحه‌خوان استفاده نمی‌کنند نیز امکان می‌دهند تا به‌سرعت بخش‌های بزرگ سند را شناسایی و پیمایش کنند.

- [افزونه‌ی مرورگر Landmarks](https://matatk.agrip.org.uk/landmarks/)

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('footer')}}
- [استفاده از بخش‌ها و خطوط HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)
- [نقاط عطف قابل دسترسی | scottohara.me](https://www.scottohara.me/blog/2018/03/03/landmarks.html)
- [به‌روزرسانی عنصر فوتر | HTML5 Doctor](https://html5doctor.com/the-footer-element-update/)