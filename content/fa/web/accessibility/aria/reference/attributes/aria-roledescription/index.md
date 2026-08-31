---
title: "ARIA: aria-roledescription attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-roledescription attribute"
short-title: aria-roledescription
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-roledescription
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-roledescription
sidebar: accessibilitysidebar
---

ویژگی `aria-roledescription` یک نام خوانا و بومی‌سازی‌شده توسط نویسنده برای نقش (role) یک عنصر تعریف می‌کند.

## توضیحات

برخی از فناوری‌های کمکی (AT)، مانند صفحه‌خوان‌ها، نقش عنصر را به‌عنوان بخشی از تجربه کاربری ارائه می‌کنند. ویژگی `aria-roledescription` راهی برای تعریف یک نام خوانای متفاوت فراهم می‌کند که توسط AT به‌عنوان نقش عنصر ارائه شود.

> [!NOTE]
> فقط برای شفاف‌سازی هدف نقش‌های کانتینری غیرتعاملی و ارائه توضیح دقیق‌تر برای یک ابک (widget) از `aria-roledescription` استفاده کنید.

کاربران برای درک هدف عنصر و اگر ابک باشد، نحوه تعامل با آن، به ارائه نام نقش شناخته‌شده وابسته هستند. بنابراین، فقط برای شفاف‌سازی هدف نقش‌های کانتینری غیرتعاملی مانند `group` یا `region` و ارائه توضیح دقیق‌تر به یک ابک از `aria-roledescription` استفاده کنید.

ویژگی `aria-roledescription` نحوه بومی‌سازی و بیان نام نقش توسط ATها را بازنویسی می‌کند. هنگامی که نام نقشی را که کاربر می‌فهمد بازنویسی می‌کنید، احتمالاً توانایی کاربر در درک و تعامل با عنصر را تحت تأثیر منفی قرار می‌دهید.

از استفاده از ویژگی `aria-roledescription` خودداری کنید. وقتی یک مورد استفاده به‌اندازه کافی خاص به نظر می‌رسد که شایسته یک توضیح نقش منحصربه‌فرد باشد، اغلب می‌توان تعاملات را به بخش‌های کوچک‌تری تقسیم کرد که نقش‌های مرتبط دارند.

وقتی هیچ نقش معنایی یا نقش ابک ARIA متناظر با مدل تعامل ابک شما وجود ندارد، از `role="application"` استفاده کنید، یک `aria-roledescription` با نام نقش سفارشی خوانا و بومی‌سازی‌شده توسط نویسنده ارائه دهید و از `aria-describedby` برای ارائه دستورالعمل‌های کاربر استفاده کنید.

ATها ممکن است نام نقش‌های ARIA را سفارشی و بومی‌سازی کنند. اگر از `aria-roledescription` برای تغییر نحوه ارائه نام نقش به کاربر استفاده می‌کنید، به‌خاطر داشته باشید که بومی‌سازی را مدیریت کنید. مقدار باید هنگام بومی‌سازی صفحه ترجمه شود.

تغییر نحوه ارائه نقش به کاربر هیچ تأثیری بر عملکرد عنصر ندارد. به عنوان مثال، اگر یک عنصر دارای نقش [`region`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role) یا [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) باشد، وقتی AT عملکردهایی برای پیمایش به منطقه یا دکمه بعدی فراهم می‌کند، اگر `aria-roledescription` را به ترتیب روی `continent` و `escape` تنظیم کنید، AT همچنان به این عملکردها اجازه می‌دهد تا به مناطق و دکمه‌ها پیمایش کنند.

باز هم، از استفاده از `aria-roledescription` خودداری کنید. در این مثال، `escape` معنای مرتبطی برای کاربر ندارد، اما `button` با برچسب «escape» معنادار است.

هنگام استفاده از `aria-roledescription`، همچنین اطمینان حاصل کنید که عنصری که روی آن اعمال می‌شود دارای یک [`role`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) معتبر ARIA است یا دارای معنای نقش ضمنی است و خود مقدار خالی نیست و چیزی بیش از فاصله‌های خالی (whitespace) دارد.

هنگام استفاده از `aria-brailleroledescription`، ویژگی `aria-roledescription` الزامی است. توجه داشته باشید که به طور کلی، `aria-brailleroledescription` فقط در موارد نادری باید استفاده شود که `aria-roledescription` هنگام نمایش در بریل بیش از حد طولانی باشد.

## مثال‌ها

مثال زیر استفاده از `aria-roledescription` را نشان می‌دهد تا مشخص کند که یک کانتینر غیرتعاملی یک «اسلاید» در یک برنامه ارائه مبتنی بر وب است.

```html
<div
  role="article"
  aria-roledescription="slide"
  id="slide"
  aria-labelledby="slideheading">
  <h1 id="slideheading">Quarterly Report</h1>
  <!-- remaining slide contents -->
</div>
```

در مثال‌های قبلی، کاربر صفحه‌خوان ممکن است «گزارش فصلی، اسلاید» را بشنود، به جای عبارت کمتر دقیق «گزارش فصلی، مقاله».

## مقادیر

- `<string>`
  - : یک رشته غیر خالی، یک نوع مقدار بدون محدودیت، که شامل چیزی بیش از فاصله‌های خالی باشد.

## رابط‌های مرتبط

- {{domxref("Element.ariaRoleDescription")}}
  - : ویژگی [`ariaRoleDescription`](/en-US/docs/Web/API/Element/ariaRoleDescription)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-roledescription` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaRoleDescription")}}
  - : ویژگی [`ariaRoleDescription`](/en-US/docs/Web/API/ElementInternals/ariaRoleDescription)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-roledescription` را منعکس می‌کند.

## نقش‌های مرتبط

توسط همه نقش‌ها و همه عناصر نشانه‌گذاری پایه به جز `role="generic"` پشتیبانی می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش‌های ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles)