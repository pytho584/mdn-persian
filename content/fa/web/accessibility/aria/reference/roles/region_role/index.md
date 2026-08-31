---
title: "ARIA: region role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: region role"
short-title: region
slug: Web/Accessibility/ARIA/Reference/Roles/region_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#region
  - https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/region.html
sidebar: accessibilitysidebar
---

نقش **`region`** برای شناسایی بخش‌هایی از سند استفاده می‌شود که نویسنده آن‌ها را قابل توجه می‌داند. این یک landmark عمومی است که برای کمک به ناوبری در زمانی که هیچ‌یک از نقش‌های landmark دیگر مناسب نیستند، در دسترس قرار دارد.

```html
<div role="region" aria-label="Example">
  <!-- محتوای region -->
</div>
```

## توضیحات

نقش `region` یک نقش [landmark ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) است.
نقش `region` باید برای بخش‌هایی از محتوا که به اندازه کافی مهم هستند که کاربران احتمالاً بخواهند به راحتی به آن بخش پیمایش کنند و آن را در خلاصه صفحه فهرست کنند، اختصاص داده شود. نقش region یک اصطلاح عمومی‌تر است و فقط باید در صورتی استفاده شود که بخش مورد نیاز توسط یکی از سایر نقش‌های landmark مانند [`banner`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role)، [`main`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role)، [`contentinfo`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/contentinfo_role)، [`complementary`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role) یا [`navigation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role) به طور دقیق توصیف نشده باشد.

هر عنصر با نقش `region` باید دارای برچسبی باشد که هدف محتوای موجود در region را توصیف کند، ترجیحاً با [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) که به یک عنوان قابل مشاهده اشاره می‌کند. اگر عنوان قابل مشاهده مناسب موجود نباشد، باید از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده شود.

محتوای نقش landmark `region` باید در صورت جدا شدن از محتوای اصلی سند، منطقی و قابل درک باشد.

استفاده از عنصر {{HTMLElement('section')}} به طور خودکار نشان می‌دهد که یک بخش دارای نقش `region` است، اگر به آن یک نام قابل دسترس (accessible name) داده شود. توسعه‌دهندگان همیشه باید ترجیح دهند از عنصر HTML معنایی صحیح، در این مورد `<section>`، به جای استفاده از ARIA استفاده کنند.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) یا [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : از این ویژگی برای برچسب‌گذاری region استفاده کنید. اغلب، مقدار ویژگی `aria-labelledby` شناسه (id) عنصری خواهد بود که برای عنوان‌دهی به بخش استفاده می‌شود. اگر عنوان قابل مشاهده مناسب موجود نباشد، باید از `aria-label` استفاده شود.

## مثال‌ها

```html
<div role="region" aria-labelledby="region-heading">
  <h2 id="region-heading">
    ویژگی `id` این عنوان به این region کمک می‌کند تا یک نام قابل دسترس داشته باشد
  </h2>
  <!-- محتوای region -->
</div>
```

## نگرانی‌های دسترس‌پذیری

کم استفاده کنید! [نقش‌های landmark](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) برای استفاده کم در نظر گرفته شده‌اند تا بخش‌های بزرگ‌تر و کلی سند را شناسایی کنند. استفاده بیش از حد از نقش‌های landmark می‌تواند در صفحه‌خوان‌ها "نویز" ایجاد کند و درک طرح کلی صفحه را دشوار کند.

فقط در صورتی از نقش `region` استفاده کنید که هیچ [عنصر بخش‌بندی محتوا](/en-US/docs/Web/HTML/Reference/Elements#content_sectioning) مرتبط یا [نقش landmark](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) دیگری کاربرد نداشته باشد. اگر چندین region در یک صفحه وجود دارد، ممکن است ارزش بررسی مجدد ساختار کلی صفحه را داشته باشد.

## بهترین روش‌ها

### ترجیح HTML

استفاده از عنصر {{HTMLElement('section')}} به طور خودکار نشان می‌دهد که عنصر دارای نقش `region` است. در صورت امکان، استفاده از عنصر معنایی `<section>` را به جای نقش `region` ترجیح دهید.

### برچسب‌گذاری landmarkها

اگر بیش از یک نقش landmark `region` در یک سند وجود دارد، برای هر یک یک برچسب منحصر به فرد ارائه دهید. این برچسب به کاربر فناوری کمکی اجازه می‌دهد تا به سرعت هدف هر landmark را درک کند.

```html
<div role="region" aria-labelledby="use-discretion">
  <h3 id="use-discretion">لطفاً از نقش `region` با احتیاط استفاده کنید</h3>
  <!-- محتوا -->
</div>

…

<div role="region" aria-labelledby="please-reconsider">
  <h3 id="please-reconsider">لطفاً ساختار سند خود را بازنگری کنید</h3>
  <!-- محتوا -->
</div>
```

در این مثال، برچسب region توسط [ویژگی `aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) تولید می‌شود.

### مناطق محتوای قابل پیمایش با متن سرریز

اگر یک ناحیه محتوا با `tabindex="0"` وجود دارد، `role="region"` را اضافه کنید تا به کاربران صفحه‌خوان منتقل شود که این یک منطقه عمومی است. این کار برای اجازه دادن به کاربران فقط با صفحه‌کلید برای پیمایش مناطق با متن سرریز انجام می‌شود.

### SVG

`role="region"` را می‌توان بر روی بخش‌هایی از {{SVGElement('svg')}} به همراه یک `aria-label` اعلام کرد تا بخش‌های جداگانه SVG توصیف شوند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('section')}}
- [نقش ARIA: `banner`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role)
- [نقش ARIA: `main`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role)
- [نقش ARIA: `contentinfo`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/contentinfo_role)
- [نقش ARIA: `complementary`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role)
- [نقش ARIA: `navigation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role)
- [نقش‌های landmark: استفاده از ARIA: نقش‌ها، حالت‌ها و ویژگی‌ها](/en-US/docs/Web/Accessibility/ARIA/Guides/Techniques#landmark_roles)
- [Landmarkهای قابل دسترس | scottohara.me](https://www.scottohara.me/blog/2018/03/03/landmarks.html)