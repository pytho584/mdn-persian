---
title: "ARIA: landmark role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/landmark_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: landmark role"
short-title: landmark
slug: Web/Accessibility/ARIA/Reference/Roles/landmark_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#landmark
sidebar: accessibilitysidebar
---

لندمارک (landmark) زیربخش مهمی از یک صفحه است. نقش `landmark` یک ابرکلاس انتزاعی برای مقادیر نقش ARIA در بخش‌هایی از محتوا است که به اندازه کافی مهم هستند که کاربران احتمالاً بخواهند بتوانند مستقیماً به آن‌ها پیمایش کنند.

> [!NOTE]
> نقش `landmark` یک [نقش انتزاعی](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#6._abstract_roles) است. این نقش برای کامل‌بودن مستندات در اینجا آورده شده است. نباید توسط نویسندگان وب استفاده شود.

## توضیحات

`landmark` یک نقش انتزاعی برای بخشی از محتوا است که به اندازه کافی مهم است که کاربران احتمالاً بخواهند به راحتی به آن بخش پیمایش کنند و آن را در خلاصه‌ای که به صورت پویا از صفحه تولید می‌شود داشته باشند. لندمارک‌ها به فناوری‌های کمکی امکان می‌دهند که سریع پیمایش کنند و محتوا را بیابند.

برای ایجاد یک نقش لندمارک، هدف محتوا را با استفاده از یک عنصر معنایی مانند `<section>`، `<nav>` یا `<main>` تعریف کنید، یا یک نقش ARIA که زیرکلاس نقش `landmark` است اضافه کنید، مانند [`role="banner"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role)، [`role="complementary"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role) یا [`role="region"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role). از `role="landmark"` استفاده نکنید.

هر نقش لندمارک عینی معادل عنصر معنایی HTML خود را دارد:

| نقش ARIA                                                                                | عنصر HTML               |
| --------------------------------------------------------------------------------------- | ----------------------- |
| [`banner`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role)              | {{HTMLElement('header')}} |
| [`complementary`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role) | {{HTMLElement('aside')}}  |
| [`contentinfo`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/contentinfo_role)    | {{HTMLElement('footer')}} |
| [`form`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role)                  | {{HTMLElement('form')}}   |
| [`main`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role)                  | {{HTMLElement('main')}}   |
| [`navigation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role)      | {{HTMLElement('nav')}}    |
| [`region`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role)              | {{HTMLElement('section')}} |
| [`search`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)              | {{HTMLElement('search')}} |

باید یک برچسب قابل مشاهده ارائه شود که با [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) ارجاع داده شود. در صورت لزوم، می‌توان یک برچسب کوتاه و توصیفی با [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) ارائه داد.

برای کاربران صفحه‌خوان، افزودن نقش‌های لندمارک عملاً «پیوندهای پرش» (skip links) برای کاربران صفحه‌خوان ایجاد می‌کند، اما جایگزین پیمایش درون صفحه نمی‌شوند، زیرا نقش‌های لندمارک به شکل دیگری در دسترس قرار نمی‌گیرند.

## بهترین روش‌ها

از `role="landmark"` استفاده نکنید؛ در عوض، در صورت امکان از نقش‌های لندمارک زیرکلاس به‌صورت مناسب یا از HTML معنایی استفاده کنید. اگرچه دیگر ضروری نیست، اما برای مرورگرهای قدیمی، افزودن نقش‌های لندمارک زیرکلاس به‌صورت تکراری همراه با عنصر معنایی مرتبط، یک روش خوب محسوب می‌شود. این کار بهتر از استفاده از نقش‌های لندمارک روی عناصر غیرمعنایی مانند {{HTMLElement('div')}} است، اما حداقل از یکی از `role` یا عناصر معنایی برای ایجاد لندمارک استفاده کنید. در غیر این صورت، محتوای شما برای کاربران صفحه‌خوان کمتر قابل پیمایش خواهد بود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش ARIA: `section`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/section_role)
- [نقش ARIA: `banner`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role)
- [نقش ARIA: `complementary`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role)
- [نقش ARIA: `contentinfo`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/contentinfo_role)
- [نقش ARIA: `form`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role)
- [نقش ARIA: `main`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role)
- [نقش ARIA: `navigation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role)
- [نقش ARIA: `region`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role)
- [نقش ARIA: `search`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)
- [استفاده از نقش‌های لندمارک HTML برای بهبود دسترسی‌پذیری](/en-US/blog/aria-accessibility-html-landmark-roles/) در وبلاگ MDN (2023)