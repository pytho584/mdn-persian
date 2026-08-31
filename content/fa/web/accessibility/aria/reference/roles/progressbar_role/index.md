---
title: "ARIA: progressbar role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: progressbar role"
short-title: progressbar
slug: Web/Accessibility/ARIA/Reference/Roles/progressbar_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#progressbar
sidebar: accessibilitysidebar
---

نقش `progressbar` عنصری را تعریف می‌کند که وضعیت پیشرفت را برای کارهایی که زمان زیادی می‌برند، نمایش می‌دهد.

## توضیحات

ویجت محدوده `progressbar` نشان می‌دهد که یک درخواست دریافت شده است و برنامه در حال پیشرفت برای تکمیل اقدام درخواستی است.

نویسندگان **می‌توانند** `aria-valuemin` و `aria-valuemax` را برای نشان دادن حداقل و حداکثر مقادیر نشانگر پیشرفت تنظیم کنند. در غیر این صورت، مقادیر ضمنی آن‌ها از قوانین مشابه با HTML [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range) پیروی می‌کند:

- اگر [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) وجود نداشته باشد یا یک عدد نباشد، به طور پیش‌فرض `0` (صفر) است.
- اگر [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) وجود نداشته باشد یا یک عدد نباشد، به طور پیش‌فرض `100` است.
- ویژگی‌های `aria-valuemin` و `aria-valuemax` فقط زمانی برای نقش `progressbar` نیاز به تنظیم دارند که حداقل نوار پیشرفت `0` نباشد یا حداکثر مقدار `100` نباشد.
- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) فقط خواندنی باید ارائه و به‌روزرسانی شود، مگر اینکه مقدار `indeterminate` (نامشخص) باشد، که در این صورت ویژگی را شامل نشوید. اگر تنظیم شده است، مطمئن شوید که مقدار `aria-valuenow` بین حداقل و حداکثر مقادیر است.

اگر نقش `progressbar` به یک عنصر HTML {{HTMLElement('progress')}} اعمال شود، نام قابل دسترس می‌تواند از {{HTMLElement('label')}} مرتبط بیاید. در غیر این صورت، اگر یک برچسب قابل مشاهده وجود دارد از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) استفاده کنید، یا اگر برچسب قابل مشاهده‌ای وجود ندارد از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کنید.

### همه فرزندان نمایشی هستند

برخی از انواع اجزای رابط کاربری وجود دارند که وقتی در یک API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند حاوی متن باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `progressbar` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به تمام عناصر فرزند هر عنصر `progressbar` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

به عنوان مثال، عنصر `progressbar` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="progressbar"><h3>Title of my progressbar</h3></div>
```

از آنجا که فرزندان `progressbar` نمایشی هستند، کد زیر معادل است:

```html
<div role="progressbar">
  <h3 role="presentation">Title of my progressbar</h3>
</div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه کدهای قبلی با موارد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="progressbar">Title of my progressbar</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow)
  - : فقط در صورت وجود و زمانی که مقدار نامشخص (indeterminate) نباشد ضروری است. به یک مقدار اعشاری بین `0` یا `aria-valuemin` (در صورت وجود) و `aria-valuemax` تنظیم می‌شود که مقدار فعلی نوار پیشرفت را نشان می‌دهد.
- [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext)
  - : فناوری‌های کمکی اغلب مقدار `aria-valuenow` را به صورت درصد نمایش می‌دهند. اگر این کار دقیق نباشد، از این ویژگی برای قابل فهم کردن مقدار نوار پیشرفت استفاده کنید.
- [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin)
  - : به یک مقدار اعشاری که نشان‌دهنده حداقل مقدار است و کمتر از `aria-valuemax` است، تنظیم می‌شود. اگر وجود نداشته باشد، مقدار پیش‌فرض `0` است.
- [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax)
  - : به یک مقدار اعشاری که نشان‌دهنده حداکثر مقدار است و بیشتر از `aria-valuemin` است، تنظیم می‌شود. اگر وجود نداشته باشد، مقدار پیش‌فرض `100` است.
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : مقدار رشته‌ای را تعریف می‌کند یا عنصر (یا عناصری) را که عنصر progressbar را برچسب‌گذاری می‌کنند و یک نام قابل دسترس ارائه می‌دهند، مشخص می‌کند. یک نام قابل دسترس ضروری است.

توصیه می‌شود به جای نقش `progressbar` از عناصر بومی {{HTMLElement("progress")}} یا [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range) استفاده کنید. عامل‌های کاربر یک ویجت سبک‌دهی شده برای عنصر {{HTMLElement("progress")}} بر اساس مقدار فعلی `value` در رابطه با `0` (حداقل مقدار) و مقدار `max` ارائه می‌دهند. هنگام استفاده از عناصر غیر معنایی، تمام ویژگی‌های عنصر معنایی بومی باید با ویژگی‌های ARIA، جاوااسکریپت و CSS بازسازی شوند.

## مثال‌ها

در مثال زیر، نوار پیشرفت از مقادیر پیش‌فرض 0 و 100 برای `aria-valuemin` و `aria-valuemax` استفاده می‌کند:

```html
<div>
  <span id="loadinglabel">در حال بارگذاری:</span>
  <span role="progressbar" aria-labelledby="loadinglabel" aria-valuenow="23">
    <svg width="100" height="10">
      <rect height="10" width="100" stroke="black" fill="black" />
      <rect height="10" width="23" fill="white" />
    </svg>
  </span>
</div>
```

با استفاده از HTML معنایی، این می‌تواند به صورت زیر نوشته شود:

```html
<label for="loadinglabel">در حال بارگذاری:</label>
<progress id="loadinglabel" max="100" value="23"></progress>
```

## بهترین روش‌ها

اگر نوار پیشرفت وضعیت بارگذاری یک ناحیه خاص از صفحه را توصیف می‌کند، ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) را برای ارجاع به وضعیت نوار پیشرفت وارد کنید و ویژگی [`aria-busy`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy) را روی `true` در آن ناحیه تنظیم کنید تا زمانی که بارگذاری به پایان برسد.

### ترجیح HTML

توصیه می‌شود به جای نقش `progressbar` از عناصر بومی {{HTMLElement("progress")}} یا [`<input type="range">`](/en-US/docs/Web/HTML/Reference/Elements/input/range) استفاده کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر HTML {{HTMLElement('progress')}}
- سایر ویجت‌های محدوده شامل:
  - [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role)
  - [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
  - [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) (در صورت قابل تمرکز بودن)
  - [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
  - [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)