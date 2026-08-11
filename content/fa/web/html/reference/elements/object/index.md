---
title: "<object> HTML external object element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/object"
translated_by: "n8n + AI"
---

## `<object>` — منبع خارجی HTML

عنصر **`<object>`** یک منبع خارجی را نمایش می‌دهد که می‌تواند به عنوان تصویر، یک زمینه مرورگر تو در تو (nested browsing context) یا یک منبع برای پردازش توسط یک افزونه (plugin) در نظر گرفته شود.

## ویژگی‌ها

این عنصر از [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) نیز پشتیبانی می‌کند.

- `archive` (منسوخ شده)
  - : یک لیست جدا شده با فاصله از URIهای بایگانی منابع برای object.
- `border` (منسوخ شده)
  - : عرض حاشیه دور کنترل، بر حسب پیکسل.
- `classid` (منسوخ شده)
  - : URI پیاده‌سازی object. می‌تواند همراه با ویژگی `data` یا به جای آن استفاده شود.
- `codebase` (منسوخ شده)
  - : مسیر پایه برای حل URIهای نسبی مشخص شده توسط `classid`، `data` یا `archive`. اگر مشخص نشود، پیش‌فرض URI پایه سند فعلی است.
- `codetype` (منسوخ شده)
  - : نوع محتوای داده مشخص شده توسط `classid`.
- `data`
  - : آدرس منبع به صورت یک URL معتبر. حداقل یکی از `data` و `type` باید مشخص شود.
- `declare` (منسوخ شده)
  - : وجود این ویژگی بولی این عنصر را فقط به یک اعلان تبدیل می‌کند. object باید توسط یک عنصر `<object>` بعدی نمونه‌سازی شود. هر بار که منبع دوباره استفاده می‌شود، عنصر `<object>` را به طور کامل تکرار کنید.
- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)
  - : عنصر فرمی که object با آن مرتبط است (مالک فرم). مقدار این ویژگی باید یک ID از یک عنصر `<form>` در همان سند باشد.
- `height`
  - : ارتفاع منبع نمایش داده شده، به صورت یک عدد صحیح (integer) بر حسب پیکسل CSS.
- `name`
  - : نام یک زمینه مرورگر معتبر (HTML5) یا نام کنترل (HTML 4). این نام به یک خاصیت از اشیاء `Window` و `Document` تبدیل می‌شود که حاوی ارجاع به پنجره جاسازی شده یا خود عنصر است.
- `standby` (منسوخ شده)
  - : پیامی که مرورگر می‌تواند در هنگام بارگذاری پیاده‌سازی و داده‌های object نمایش دهد.
- `type`
  - : [نوع محتوا](/en-US/docs/Glossary/MIME_type) منبع مشخص شده توسط `data`. حداقل یکی از `data` و `type` باید مشخص شود.
- `usemap` (منسوخ شده)
  - : یک ارجاع به یک عنصر `<map>` با استفاده از نام هش؛ یعنی یک `#` به دنبال مقدار ویژگی `name` یک عنصر map.
- `width`
  - : عرض منبع نمایش داده شده، به صورت یک عدد صحیح (integer) بر حسب پیکسل CSS.

## مثال‌ها

### قرار دادن یک ویدیو

```html
<object
  type="video/webm"
  data="/shared-assets/videos/flower.webm"
  width="600"
  height="140">
  <img
    src="/shared-assets/images/examples/flowers.jpg"
    alt="Some beautiful flowers" />
</object>
```

اگر ویدیو در مثال بارگذاری نشود، کاربر یک تصویر به عنوان محتوای جایگزین (fallback) خواهد دید. از تگ `<img>` برای نمایش تصویر استفاده شده است. ویژگی `src` مسیر تصویر و ویژگی `alt` یک نام دسترس‌پذیر برای تصویر فراهم می‌کند. اگر تصویر هم بارگذاری نشود، محتوای ویژگی `alt` نمایش داده می‌شود.

| ویژگی | مقدار |
| --- | --- |
| دسته‌های محتوا | [محتوای جریانی](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) (Flow content)؛ [محتوای عبارتی](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) (phrasing content)؛ [محتوای جاسازی‌شده](/en-US/docs/Web/HTML/Guides/Content_categories#embedded_content) (embedded content)، محتوای ملموس (palpable content)؛ اگر عنصر دارای ویژگی [`usemap`](#usemap) باشد، [محتوای تعاملی](/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content) (interactive content)؛ [فهرست‌شده](/en-US/docs/Web/HTML/Guides/Content_categories#listed) (listed)، [قابل‌ارسال](/en-US/docs/Web/HTML/Guides/Content_categories#submittable) (submittable)، و [عنصر مرتبط با فرم](/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content) (form-associated). |
| محتوای مجاز | صفر یا بیشتر عنصر `<param>`، سپس [محتوای شفاف](/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model) (transparent). |
| حذف تگ | هیچ‌کدام؛ هم تگ شروع و هم تگ پایان الزامی هستند. |
| والدهای مجاز | هر عنصری که [محتوای جاسازی‌شده](/en-US/docs/Web/HTML/Guides/Content_categories#embedded_content) (embedded content) را بپذیرد. |
| نقش ARIA ضمنی | [بدون نقش متناظر](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)، [`document`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role)، [`img`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role) |
| رابط DOM | `HTMLObjectElement` |

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- `<embed>`
- `<param>`