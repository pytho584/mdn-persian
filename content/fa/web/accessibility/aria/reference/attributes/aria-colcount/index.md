---
title: "ARIA: aria-colcount attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount"
translated_by: "n8n + AI"
---
---
title: "ARIA: aria-colcount attribute"
short-title: aria-colcount
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-colcount
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-colcount
sidebar: accessibilitysidebar
---

ویژگی `aria-colcount` تعداد کل ستون‌ها را در یک [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)، [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) تعریف می‌کند، زمانی که همه ستون‌ها در [DOM](/en-US/docs/Glossary/DOM) حضور ندارند.

## توضیحات

برخی جداول بسیار بزرگ هستند و نمایش تمام ستون‌ها به کاربر امکان‌پذیر نیست. یا ممکن است امکان‌پذیر باشد، اما داشتن جدولی به این پهن‌ی تجربه کاربری بدی ایجاد می‌کند. از ویژگی `aria-colcount` استفاده کنید تا به فناوری‌های کمکی بگویید جدول اگر همه ستون‌ها حضور داشتند چند ستون داشت. مقدار آن یک عدد صحیح است که تعداد ستون‌های تشکیل‌دهنده جدول کامل را نشان می‌دهد. اگر تعداد کل ستون‌های یک جدول را نمی‌دانید، اما می‌دانید که همه آن‌ها در DOM نخواهند بود، از مقدار -1 استفاده کنید، یعنی `aria-colcount="-1"`. این مقدار به عامل کاربر می‌گوید که تعداد فعلی ستون‌های موجود در DOM ممکن است تعداد واقعی ستون‌های جدول نباشد.

اگر همه ستون‌های یک جدول در DOM حضور داشته باشند، ویژگی `aria-colcount` نیازی نیست، زیرا مرورگرها به‌طور خودکار تعداد کل ستون‌ها را محاسبه می‌کنند. با این حال، اگر فقط بخشی از ستون‌ها در یک لحظه خاص در DOM حضور داشته باشند، آن زمان است که این ویژگی مفید و ضروری است.

هنگام استفاده از `aria-colcount` زمانی که تعداد ستون‌ها مشخص است، مطمئن شوید که از [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) نیز برای برچسب‌گذاری هر ستون استفاده کنید، یا اگر ستون‌ها متوالی هستند - یعنی گروهی از ستون‌ها به ترتیب اصلی بدون شکاف - هر ردیف را برچسب‌گذاری کنید.

مثال زیر یک شبکه با ۶ ستون را نشان می‌دهد که ستون‌های ۱، ۲، ۵ و ۶ به کاربر نمایش داده می‌شوند. تعداد کل ستون‌های تشکیل‌دهنده جدول به صورت `aria-colcount="6"` روی خود جدول تنظیم شده است. از آنجایی که ستون‌ها متوالی نیستند، هر [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role) - در اینجا عناصر [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) و [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role) - دارای ویژگی `aria-colindex` هستند.

```html
<div role="grid" aria-colcount="6">
  <div role="rowgroup">
    <div role="row">
      <div role="columnheader" aria-colindex="1">First name</div>
      <div role="columnheader" aria-colindex="2">Last name</div>
      <div role="columnheader" aria-colindex="5">City</div>
      <div role="columnheader" aria-colindex="6">Zip</div>
    </div>
  </div>
  <div role="rowgroup">
    <div role="row">
      <div role="gridcell" aria-colindex="1">Debra</div>
      <div role="gridcell" aria-colindex="2">Burks</div>
      <div role="gridcell" aria-colindex="5">New York</div>
      <div role="gridcell" aria-colindex="6">14127</div>
    </div>
  </div>
  …
</div>
```

اولین قانون استفاده از ARIA این است: «اگر می‌توانید از یک ویژگی بومی با معناشناسی و رفتاری که نیاز دارید استفاده کنید، به جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای دسترسی‌پذیر کردن آن، این کار را انجام دهید.» اگر از معناشناسی بومی HTML با {{HTMLElement('table')}}، {{HTMLElement('th')}}، {{HTMLElement('td')}} و غیره استفاده کنیم، ویژگی `aria-colcount` همچنان ضروری است، اما نشانه‌گذاری کم‌حجم‌تر است. هنگام استفاده از عناصر سرستون جدول معنایی و زمانی که همه ستون‌ها در DOM نیستند، باید همچنان از `aria-colcount` استفاده شود، اما ویژگی `aria-colindex` فقط یک بار برای هر ستون در سرستون ستون {{HTMLElement('th')}} باید تعریف شود.

```html
<table aria-colcount="6">
  <thead>
    <tr>
      <th aria-colindex="1" scope="col">First name</th>
      <th aria-colindex="2" scope="col">Last name</th>
      <th aria-colindex="5" scope="col">City</th>
      <th aria-colindex="6" scope="col">Zip</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Debra</td>
      <td>Burks</td>
      <td>New York</td>
      <td>14127</td>
    </tr>
    …
  </tbody>
</table>
```

## مقادیر

- `<integer>`
  - : تعداد ستون‌ها در جدول کامل

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)

به ارث برده می‌شود به نقش‌ها:

- [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)