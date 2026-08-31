---
title: "ARIA: meter role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_ole"
translated_by: "n8n + AI"
---

---
title: "ARIA: نقش متر"
short-title: متر
slug: Web/Accessibility/ARIA/Reference/Roles/meter_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#meter
sidebar: accessibilitysidebar

نقش `meter` برای شناسایی عنصری که به عنوان یک متر استفاده می‌شود، به کار می‌رود.

> [!NOTE]
> در صورت امکان، توصیه می‌شود به جای نقش `meter` از عنصر بومی {{HTMLElement("meter")}} استفاده کنید، زیرا عناصر بومی توسط عوامل کاربر و فناوری‌های کمکی پشتیبانی گسترده‌تری دارند.

## توضیحات

متر یک نمایش گرافیکی از یک مقدار عددی در یک محدوده تعریف‌شده است. به عنوان مثال، نمایش درصد باتری. برای مقادیری که حداکثر معناداری ندارند، متر مناسب نیست. نباید از متر برای نشان دادن پیشرفت (مانند بارگذاری) استفاده کرد؛ برای این منظور باید از عنصر {{HTMLElement('progress')}} استفاده شود.

هر عنصر با `role="meter"` باید یکی از موارد زیر را نیز داشته باشد:

- یک ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
- یک ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) که به عنصری حاوی متنی برای توصیف متر اشاره کند.

### تمام فرزندان نمایشی هستند

برخی از انواع اجزای رابط کاربری، هنگامی که در یک API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند حاوی متن باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `meter` ندارند. برای مقابله با این محدودیت، مرورگرها به‌طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به همه عناصر فرزند هر عنصر `meter` ` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

برای مثال، عنصر `meter` زیر را در نظر بگیرید که حاوی یک عنوان است:

```html
<div role="meter"><h3>عنوان متر من</h3></div>
```

از آنجایی که فرزندان `meter` نمایشی هستند، کد زیر معادل است:

```html
<div role="meter"><h3 role="presentation">عنوان متر من</h3></div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه کدهای قبلی با مورد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="meter">عنوان متر من</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های ARIA مرتبط

- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow)
  -: به یک مقدار اعشاری بین `aria-valuemin` و `aria-valuemax` تنظیم می‌شود که مقدار فعلی متر را نشان می‌دهد.
- [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext)
  - : فناوری‌های کمکی اغلب مقدار `aria-valuenow` را به صورت درصد نمایش می‌دهند. اگر این دقیق نیست، از این ویژگی برای قابل فهم کردن مقدار متر استفاده کنید.
- [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin)
  - : به یک مقدار اعشاری که حداقل مقدار را نشان می‌دهد و کمتر از `aria-valuemax` است، تنظیم می‌شود.
- [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax)
  - : به یک مقدار اعشاری که حداکثر مقدار را نشان می‌دهد و بزرگتر از `aria-valuemin` است، تنظیم می‌شود.

توصیه می‌شود به جای نقش `meter` از عنصر بومی {{HTMLElement("meter")}} استفاده کنید. عوامل کاربر یک ویجت استایل‌ده برای عنصر {{HTMLElement("meter")}} بر اساس مقدار فعلى `value` نسبت به مقادیر `min` و `max` فرهم می‌کنند. هنگام استفاده از عناصر غیرمعنایی، تمام ویژگی‌های عنصر بومی معنایی باید با ویژگی‌های ARIA، جاوا اسکریپت و CSS بازسازی شونند.

## مثال‌ها

مثالی از یک متر با استفاده از `role="meter"`:

```html
<div
  role="meter"
  aria-valuenow="90"
  aria-valuemin="0"
  aria-valuemax="100"
  aria-labelledby="cpu_usage_label">
  <svg xmlns="http://www.w3.org/2000/svg" aria-hidden="true" style="width: 90%">
    <rect x="0" y="0" width="100%" height="100%" fill="currentColor"></rect>
  </svg>
</div>
```

در سناریوی بالا، هنگامی که مقدار `aria-valuenow` به‌روز می‌شود، عرض SVG نیز باید به‌روز شود، همانطور که در [مثال کار متر راهنمای عملی نویسندگی ARIA (APG)] (https://www.w3.org/WAI/ARIA/apg/patterns/meter/examples/meter/) مشاهده می‌شود.

## مشخصات

{{Spcifications}}

## همچنین ببینید

- {{HTMLElement('meter')}}
- {{HTMLElement('progress')}}