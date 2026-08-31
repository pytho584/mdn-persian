---
title: "ARIA: aria-current attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-current"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-current attribute"
short-title: aria-current
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-current
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-current
sidebar: accessibilitysidebar
---

حالت `aria-current` غیر-تهی روی یک عنصر نشان می‌دهد که این عنصر نشان‌دهنده مورد جاری در یک ظرف یا مجموعه‌ای از عناصر مرتبط است.

## توضیحات

وقتی گروهی از عناصر مرتبط دارید، مانند چندین پیوند در مسیر ناوبری (breadcrumb) یا مراحل یک فرآیند چندمرحله‌ای، و یک عنصر در گروه به‌گونه‌ای متفاوت از بقیه استایل‌دهی شده است تا به کاربر بینا نشان دهد که این عنصر جاری در گروه است، باید از `aria-current` استفاده کنید تا به کاربر فناوری کمکی اطلاع داده شود که چه چیزی از طریق استایل‌دهی نشان داده شده است.

در یک لیست breadcrumb، وقتی پیوندی در مجموعه‌ای از پیوندهای صفحه‌بندی به‌گونه‌ای استایل می‌شود که نشان دهد کاربر در حال حاضر در آن صفحه است، باید `aria-current="page"` روی آن پیوند تنظیم شود. در یک فرآیند مبتنی بر مراحل چندگانه با نشانگر مرحله، مانند نظرسنجی چندصفحه‌ای یا فرآیند پرداخت یا ثبت‌نام چندمرحله‌ای، وقتی نماد مرحله جاری از نظر بصری متفاوت است تا نشان دهد مرحله جاری است، ظرف حاوی آن نماد باید برای کاربران فناوری کمکی که ممکن است نتوانند تفاوت بصری را «ببینند»، `aria-current="step"` داشته باشد.

ویژگی `aria-current` نشان می‌دهد که عنصری که روی آن تنظیم شده است، با مقداری غیر از `false`، نشان‌دهنده مورد جاری در یک ظرف یا مجموعه‌ای از عناصر مرتبط است. فقط یک عنصر را در مجموعه‌ای از عناصر با `aria-current` به‌عنوان جاری علامت‌گذاری کنید.

ویژگی `aria-current` فهرست محدودی از [مقادیر](#values) را می‌پذیرد، از جمله `page`، `step`، `location`، `date`، `time`، `true` و `false`. هر مقدار رشته‌ای غیر-تهی که در این فهرست از مقادیر شمارش‌شده نباشد، به‌گونه‌ای رفتار می‌شود که گویی `aria-current="true"` تنظیم شده است، نه مقدار پیش‌فرض `false`. اگر ویژگی وجود نداشته باشد، رشته خالی باشد، بدون مقدار باشد، یا روی `aria-current="false"` تنظیم شود، به کاربر نمایش داده نمی‌شود.

وقتی چیزی به‌جای «جاری بودن» «انتخاب شده» است، مانند یک [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) در یک [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role)، از [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) برای نشان دادن tabpanel نمایش‌داده‌شده فعلی استفاده کنید.

> [!NOTE]
> از `aria-current` به‌عنوان جایگزینی برای [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) در [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)، [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) یا [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) استفاده نکنید.

## مثال

breadcrumb برای «صفحه جاری» باید `aria-current="page"` روی آن تنظیم شود.

```html
<nav aria-label="Breadcrumb" class="breadcrumb">
  <ol>
    <li>
      <a href="../../../../../">Web technology for developers</a>
    </li>
    <li>
      <a href="../../../../">Accessibility</a>
    </li>
    <li>
      <a href="../../../">ARIA</a>
    </li>
    <li>
      <a href="../../">ARIA States and Properties</a>
    </li>
    <li>
      <a href="./" aria-current="page">ARIA: `aria-current` attribute</a>
    </li>
  </ol>
</nav>
```

اگر عنصر نشان‌دهنده صفحه جاری در breadcrumb یک پیوند نبود، تنظیم `aria-current` اختیاری است.

## مقادیر

- `page`
  - : نشان‌دهنده صفحه جاری در مجموعه‌ای از صفحات، مانند پیوند به سند جاری در یک breadcrumb.
- `step`
  - : نشان‌دهنده مرحله جاری در یک فرآیند، مانند مرحله فعلی در یک فرآیند پرداخت چندمرحله‌ای شمارش‌شده.
- `location`
  - : نشان‌دهنده مکان جاری در یک محیط یا زمینه، مانند تصویری که به‌عنوان مؤلفه فعلی یک نمودار جریان به‌صورت بصری برجسته شده است.
- `date`
  - : نشان‌دهنده تاریخ جاری در مجموعه‌ای از تاریخ‌ها، مانند تاریخ فعلی در یک تقویم.
- `time`
  - : نشان‌دهنده زمان جاری در مجموعه‌ای از زمان‌ها، مانند زمان فعلی در یک جدول زمان‌بندی.
- `true`
  - : نشان‌دهنده مورد جاری در یک مجموعه.
- `false` (پیش‌فرض)
  - : مورد جاری در یک مجموعه را نشان نمی‌دهد.

## رابط‌های مرتبط

- {{domxref("Element.ariaCurrent")}}
  - : ویژگی [`ariaCurrent`](/en-US/docs/Web/API/Element/ariaCurrent)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-current` را بازتاب می‌دهد.
- {{domxref("ElementInternals.ariaCurrent")}}
  - : ویژگی [`ariaCurrent`](/en-US/docs/Web/API/ElementInternals/ariaCurrent) از رابط {{domxref("ElementInternals")}} مقدار ویژگی `aria-current` را بازتاب می‌دهد.

## نقش‌های مرتبط

قابل استفاده در همه نقش‌ها؛ به‌جز عناصر با نقش [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)، [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) و [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) که در آن‌ها باید از [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) استفاده شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected)
- {{cssxref(':local-link')}}
- [پیمایش Breadcrumb با `aria-current`](/en-US/docs/Web/CSS/How_to/Layout_cookbook/Breadcrumb_navigation)