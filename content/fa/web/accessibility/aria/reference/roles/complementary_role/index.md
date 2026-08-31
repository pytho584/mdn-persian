---
title: "ARIA: complementary role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: complementary role"
short-title: complementary
slug: Web/Accessibility/ARIA/Reference/Roles/complementary_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#complementary
  - https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/complementary.html
sidebar: accessibilitysidebar
---

نقش `complementary` (نقش نشانه‌ای [landmark](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles)) برای تعیین بخش پشتیبان‌ای استفاده می‌شود که به محتوای اصلی مرتبط است، اما در صورت جدا شدن نیز می‌تواند به تنهایی معنا داشته باشد. این بخش‌ها اغلب به صورت نوارهای کناری یا جعبه‌های برجسته (call-out boxes) نمایش داده می‌شوند. در صورت امکان، از [عنصر HTML \<aside>](/en-US/docs/Web/HTML/Reference/Elements/aside) استفاده کنید.

```html
<div role="complementary">
  <h2>Our partners</h2>
  <!-- complementary section content -->
</div>
```

این یک نوار کناری حاوی پیوندهایی به حامیان پروژه است.

## توضیحات

نقش `complementary` یک نقش [نشانه‌ای (landmark)](/en-US/docs/Web/Accessibility/ARIA/Guides/Techniques#landmark_roles) است. نشانه‌ها (landmarks) توسط فناوری‌های کمکی برای شناسایی سریع و پیمایش به بخش‌های بزرگ سند استفاده می‌شوند. محتوایی که درون یک ظرف با نقش نشانه‌ای `complementary` قرار می‌گیرد، باید در صورت جدا شدن از محتوای اصلی سند، همچنان معنا داشته باشد.

> [!NOTE]
> استفاده از عنصر {{HTMLElement('aside')}} به طور خودکار اعلام می‌کند که یک بخش دارای نقش `complementary` است. توسعه‌دهندگان همواره باید استفاده از عنصر HTML معنایی صحیح را به استفاده از ARIA ترجیح دهند.

## مثال‌ها

```html
<div role="complementary">
  <h2>Trending articles</h2>
  <ul>
    <li><a href="#">18 tweets that will make you feel all the feels</a></li>
    <li>
      <a href="#">Stop searching! I've found the perfect lunch containers.</a>
    </li>
    <li>
      <a href="#">The time has come to decide how to call these foods</a>
    </li>
    <li><a href="#">17 really good posts we saw on Tumblr this week</a></li>
    <li><a href="#">10 parent hacks we know work because we tried them</a></li>
  </ul>
</div>
```

## نگرانی‌های دسترسی‌پذیری

[نقش‌های نشانه‌ای (Landmark roles)](/en-US/docs/Web/Accessibility/ARIA/Guides/Techniques#landmark_roles) برای استفاده محدود طراحی شده‌اند تا بخش‌های بزرگتر و کلی سند را شناسایی کنند. استفاده از تعداد زیاد نقش‌های نشانه‌ای می‌تواند در صفحه‌خوان‌ها «نویز» ایجاد کرده و درک چیدمان کلی صفحه را دشوار کند.

## بهترین روش‌ها

### ترجیح HTML

استفاده از عنصر {{HTMLElement('aside')}} به طور خودکار اعلام می‌کند که عنصر دارای نقش `complementary` است. در صورت امکان، استفاده از عنصر معنایی `<aside>` را به نقش `complementary` ترجیح دهید.

### برچسب‌گذاری نشانه‌ها

#### چندین نشانه

اگر بیش از یک نقش نشانه‌ای `complementary` یا عنصر {{HTMLElement('aside')}} در یک سند وجود دارد، برای هر نشانه با استفاده از ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یک برچسب ارائه دهید، یا اگر عنصر `aside` دارای عنوان توصیفی مناسبی است، با استفاده از ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) به آن اشاره کنید. این برچسب به کاربر فناوری کمکی امکان می‌دهد تا به سرعت هدف هر نشانه را درک کند.

```html
<aside aria-label="Note about usage">
  <!-- content -->
</aside>

…

<aside id="sidebar" aria-label="Sponsors">
  <!-- content -->
</aside>
```

#### توضیحات تکراری

صفحه‌خوان‌ها نوع نقش نشانه را اعلام می‌کنند. به همین دلیل، نیازی نیست که در برچسب توضیح دهید که نشانه چیست. برای مثال، اعلام `role="complementary"` با `aria-label="Sidebar"` ممکن است به صورت تکراری به عنوان «نوار کناری تکمیلی» اعلام شود.

### مزایای اضافه

فناوری‌هایی مانند افزونه‌های مرورگر می‌توانند لیستی از تمام نقش‌های نشانه‌ای موجود در یک صفحه ایجاد کنند و به کاربران غیر صفحه‌خوان نیز اجازه دهند تا به سرعت بخش‌های بزرگ سند را شناسایی و پیمایش کنند.

- [افزونه مرورگر Landmarks](https://matatk.agrip.org.uk/landmarks/)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [\<aside>: عنصر کناری](/en-US/docs/Web/HTML/Reference/Elements/aside)
- [استفاده از بخش‌ها و طرح‌بندی HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)
- [نقش‌های نشانه‌ای: استفاده از ARIA: نقش‌ها، حالت‌ها و ویژگی‌ها](/en-US/docs/Web/Accessibility/ARIA/Guides/Techniques#landmark_roles)
- [نشانه‌های دسترس‌پذیر | scottohara.me](https://www.scottohara.me/blog/2018/03/03/landmarks.html)
- [بازبینی Aside | HTML5 Doctor](https://html5doctor.com/aside-revisited/)