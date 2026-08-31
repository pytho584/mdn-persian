---
title: "ARIA: separator role"
short-title: separator
slug: Web/Accessibility/ARIA/Reference/Roles/separator_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#separator
  - https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-editor/
sidebar: accessibilitysidebar
translated_by: "n8n + AI"
---

نقش `separator` نشان‌دهنده عنصری است که به عنوان جداکننده بین بخش‌های محتوا یا گروه‌های آیتم‌های منو عمل می‌کند. نقش ضمنی ARIA برای عنصر جداساز موضوعی (thematic break) بومی {{HTMLElement('hr')}} برابر `separator` است.

## توضیحات

یک جداکننده (separator) عنصری است که بخش‌های محتوا یا گروه‌های آیتم‌های منو را از هم جدا کرده و مشخص می‌کند. دو نوع جداکننده وجود دارد: یک ساختار ایستا که مرز قابل مشاهده‌ای ایجاد می‌کند، مشابه عنصر HTML {{HTMLElement('hr')}}، و یک ویجت قابل تمرکز و قابل جابجایی.

عناصر دارای نقش `separator` به طور ضمنی دارای مقدار [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) برابر `horizontal` هستند.

### جداکننده غیرقابل تمرکز

یک جداکننده غیرقابل تمرکز یک عنصر ساختاری ایستا است که می‌تواند برای کمک به جدا کردن بصری دو گروه از آیتم‌های منو در یک منو یا ایجاد یک خط افقی بین دو بخش از یک صفحه استفاده شود. جداسازهای موضوعی که قابل تمرکز نیستند همچنان می‌توانند توسط کاربران صفحه‌خوان با استفاده از مکان‌نمای خواندن که به تمرکز وابسته نیست، درک شوند.

```html
<h2>اولین پست وبلاگ من</h2>
…
<img src="blueline.gif" role="separator" alt="" />
<h2>دو سال بعد، دومین پست من</h2>
…
```

در این مثال، یک تصویر یک جداکننده بصری بین دو پست وبلاگ ایجاد می‌کند. نویسنده می‌توانست از یک عنصر جداساز موضوعی معنایی {{HTMLElement('hr')}} استفاده کرده و با CSS آن را به رنگ آبی درآورد (و مجبور نباشد هنگام تغییر تم وبلاگ، تصویر را تغییر دهد)، یا می‌توانست هر پست را در عنصر معنایی {{HTMLElement('article')}} محصور کند، یا هر دو.

```html
<section role="feed">
  <article>
    <h2>اولین پست وبلاگ من</h2>
    …
  </article>
  <hr />
  <article>
    <h2>دو سال بعد، دومین پست من</h2>
    …
  </article>
</section>
```

```css
[role="feed"] > hr {
  height: 3px;
  background-color: blue;
}
```

نیازی به نام دسترسی‌پذیر نیست.

### جداکننده قابل تمرکز

نقش جداکننده می‌تواند برای شناسایی عنصر به عنوان یک جداکننده بصری بین گروه‌های آیتم‌ها در یک منو، مانند گروه‌های عناصر `menuitemradio` یا `menuitemcheckbox` استفاده شود.

اگر جداکننده قابل تمرکز باشد، یک مرز قابل مشاهده بین دو بخش از محتوا ایجاد کند و به کاربر امکان تغییر اندازه نسبی بخش‌های جدا شده با تغییر موقعیت آن را بدهد، باید مقدار [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow) به عددی تنظیم شود که موقعیت فعلی جداکننده را منعکس کند و این مقدار هنگام تغییر به‌روزرسانی شود. اگر مقادیر پیش‌فرض 0 و 100 نباشند، باید [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) و [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) نیز اضافه شوند.

اگر بیش از یک جداکننده قابل تمرکز وجود داشته باشد، باید یک نام دسترسی‌پذیر با [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) اضافه شود.

### تمام فرزندان ارائه‌ای هستند

برخی از انواع اجزای رابط کاربری، هنگامی که در یک API دسترسی‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند شامل متن باشند. APIهای دسترسی‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `separator` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به تمام عناصر فرزند هر عنصر `separator` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

به عنوان مثال، عنصر `separator` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="separator"><h3>عنوان جداکننده من</h3></div>
```

از آنجایی که فرزندان `separator` ارائه‌ای هستند، کد زیر معادل است:

```html
<div role="separator"><h3 role="presentation">عنوان جداکننده من</h3></div>
```

از دید کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه کدهای قبلی در [درخت دسترسی‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل موارد زیر هستند:

```html
<div role="separator">عنوان جداکننده من</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) (پیش‌فرض برای جداکننده افقی است)
  - : به طور پیش‌فرض، جداکننده برای نقش‌های `separator` افقی در نظر گرفته می‌شود. مقدار می‌تواند شامل شود و روی `horizontal`، `undefined` (پیش‌فرض برای سایر نقش‌ها مگر اینکه طور دیگری مشخص شود) یا `vertical` تنظیم شود.

- [`aria-valuenow`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuenow)
  - : اگر جداکننده قابل تمرکز باشد و مقدار مشخصی داشته باشد، `aria-valuenow` مقدار فعلی را تعریف می‌کند. اگر قابل تمرکز نیست یا مقدار نامشخص است، این ویژگی را اضافه نکنید.

- [`aria-valuemin`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemin) (پیش‌فرض 0)
  - : اگر جداکننده قابل تمرکز باشد و حداقل مقدار 0 نباشد، مقدار حداقل را با `aria-valuemin` اضافه کنید.

- [`aria-valuemax`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuemax) (پیش‌فرض 100)
  - : اگر جداکننده قابل تمرکز باشد و حداکثر مقدار 100 نباشد، `aria-valuemax` را با مقداری برابر یا بزرگتر از `aria-valuemin` اضافه کنید.

- [`aria-valuetext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-valuetext)
  - : اگر جداکننده قابل تمرکز باشد و `aria-valuenow` برای ارائه اطلاعات قابل استفاده به کاربر بهینه نباشد، محتوای `aria-valuetext` به جای مقدار `aria-valuenow` خوانده می‌شود.

<!--
### تعاملات صفحه‌کلید

### ویژگی‌های جاوااسکریپت مورد نیاز

## مثال‌ها

## نگرانی‌های دسترسی‌پذیری

## بهترین روش‌ها

### ترجیح HTML -->

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر جداساز موضوعی HTML {{HTMLElement('hr')}}
- [مثال جداکننده در نوار منو](https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-editor/)