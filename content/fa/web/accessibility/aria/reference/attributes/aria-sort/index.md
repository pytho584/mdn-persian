---
title: "ARIA: aria-sort attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-sort attribute"
short-title: aria-sort
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-sort
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-sort
sidebar: accessibilitysidebar
---

ویژگی `aria-sort` نشان می‌دهد که آیا آیتم‌های یک جدول یا شبکه به ترتیب صعودی یا نزولی مرتب شده‌اند.

## توضیحات

اگر یک شبکه یا جدول قابلیت مرتب‌سازی را فراهم کند، ویژگی `aria-sort` باید روی عنصر سلول سرستون برای ستون یا ردیف مرتب‌شده، به یکی از مقادیر `ascending` یا `descending` (یا `other`) تنظیم شود.

ویژگی `aria-sort` فقط روی ستون یا ردیف مرتب‌شده در حال حاضر تنظیم می‌شود. برای نشان دادن اینکه سلول‌های داده در ستون یا ردیف به ترتیب صعودی مرتب شده‌اند، `aria-sort="ascending"` را تنظیم کنید. اگر ترتیب مرتب‌سازی معکوس شود، مقدار را به `aria-sort="descending"` تغییر دهید. هنگامی که یک ستون یا ردیف دیگر مرتب می‌شود، ویژگی `aria-sort` به سلول سرستون ستون یا ردیف جدیداً مرتب‌شده با مقدار مناسب منتقل می‌شود.

ویژگی `aria-sort` فقط باید در یک زمان به یک سرستون جدول یا شبکه اضافه شود. این ویژگی برای اطلاع‌رسانی به کاربران فناوری‌های کمکی درباره ستون یا ردیف مرتب‌شده تنظیم می‌شود و هیچ تأثیری بر ترتیب واقعی مرتب‌سازی ندارد.

## مثال‌ها

این جدول با ستون نام خانوادگی به ترتیب صعودی بارگذاری می‌شود.

```html
<table>
  <caption>
    اعضای کمیته راهبری
  </caption>
  <thead>
    <tr>
      <th>
        <button>نام</button>
      </th>
      <th aria-sort="ascending">
        <button>نام خانوادگی</button>
      </th>
      <th>
        <button>شرکت</button>
      </th>
      <th>ایمیل</th>
    </tr>
  </thead>
  <tbody>
    …
  </tbody>
</table>
```

اگر کاربر روی دکمه _نام خانوادگی_ کلیک کند، [`aria-pressed="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) به عنصر {{HTMLElement('button')}} اضافه می‌شود و مقدار `aria-sort` با استفاده از جاوااسکریپت به `"descending"` تغییر می‌کند. اگر کاربر روی دکمه سرستون دیگری کلیک کند، `aria-sort` از سرستون _نام خانوادگی_ حذف شده و روی والد {{HTMLElement('th')}} دکمه کلیک‌شده قرار می‌گیرد.

ما دستورالعمل‌هایی را در عنوان جدول برای فناوری‌های کمکی که ممکن است فلش‌های پایین را نبینند، ارائه داده‌ایم. این فلش‌ها را با استفاده از CSS و انتخابگرهای `th[aria-sort="ascending"]` و `th[aria-sort="descending"]` اضافه خواهیم کرد.

## مقادیر

- `ascending`
  - : آیتم‌ها به ترتیب صعودی توسط این ستون مرتب شده‌اند.
- `descending`
  - : آیتم‌ها به ترتیب نزولی توسط این ستون مرتب شده‌اند.
- `none` (پیش‌فرض)
  - : هیچ مرتب‌سازی مشخصی برای ستون اعمال نشده است.
- `other`
  - : یک الگوریتم مرتب‌سازی غیر از صعودی یا نزولی اعمال شده است.

## رابط‌های مرتبط

- {{domxref("Element.ariaSort")}}
  - : ویژگی [`ariaSort`](/en-US/docs/Web/API/Element/ariaSort) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-sort` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaSort")}}
  - : ویژگی [`ariaSort`](/en-US/docs/Web/API/ElementInternals/ariaSort) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-sort` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [مثال جدول قابل مرتب‌سازی](https://www.w3.org/WAI/ARIA/apg/patterns/table/examples/sortable-table/) - راهنمای شیوه‌های تألیف ARIA (APG)
- [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed)
- عنصر {{HTMLElement('th')}}