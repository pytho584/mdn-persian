---
title: "ARIA: aria-colindex attribute"
short-title: aria-colindex
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-colindex
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-colindex
sidebar: accessibilitysidebar
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex"
translated_by: "n8n + AI"
---

ویژگی `aria-colindex` موقعیت یا ایندکس ستون یک عنصر را نسبت به تعداد کل ستون‌ها در یک `table`، `grid` یا `treegrid` تعریف می‌کند.

## توضیحات

برخی جداول بسیار بزرگ هستند و در نتیجه فقط بخشی از محتوای آنها در ابتدا نمایش داده می‌شود. در حالی که بارگذاری تنها زیرمجموعه‌ای از ستون‌ها ممکن است تجربه کاربری را بهبود بخشد، باید به همه کاربران اطلاع دهید که چه بخش‌هایی از محتوا نمایش داده می‌شود و اینکه تمام محتوای جدول موجود نیست.

ARIA چندین ویژگی برای ارائه اطلاعات در مورد ساختارهای `table`، `grid` و `treegrid` فراهم می‌کند. ویژگی `aria-colindex` زیرساختار، یعنی ایندکس یا موقعیت ستون یک عنصر را نسبت به تعداد کل ستون‌ها در این ساختارها تعریف می‌کند.

این ویژگی همراه با ویژگی [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) استفاده می‌شود که به فناوری‌های کمکی اطلاع می‌دهد جدول در صورت وجود تمام ستون‌ها چند ستون خواهد داشت. `aria-colindex` برای تعیین ایندکس یا موقعیت ستون یک عنصر نسبت به آن تعداد کل ستون‌ها استفاده می‌شود.

اگر تمام ستون‌ها در DOM وجود داشته باشند، نیازی به گنجاندن `aria-colindex` نیست زیرا عامل‌های کاربر می‌توانند ایندکس ستون هر سلول یا gridcell را محاسبه کنند. با این حال، اگر هر یک از ستون‌ها در هر زمان از DOM حذف شوند، از `aria-colindex` برای نشان دادن ستون هر سلول یا gridcell نسبت به جدول کامل استفاده کنید.

مقدار `aria-colindex` یک عدد صحیح بزرگتر یا مساوی ۱ است. هر مقدار باید بزرگتر از `aria-colindex` ستون قبلی و کوچکتر یا مساوی تعداد ستون‌های جدول کامل باشد.

اگر یک سلول یا gridcell چندین ستون را پوشش می‌دهد، [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan) را به تعداد ستون‌هایی که پوشش می‌دهد تنظیم کنید (اگر از عناصر HTML {{htmlelement('td')}} و {{htmlelement('th')}} استفاده نمی‌کنید)، و `aria-colindex` را به مقدار شروع پوشش تنظیم کنید؛ مقداری که اگر فقط یک ستون عرض داشت و فقط اولین ستون خود را پوشش می‌داد، داشت.

اگر مجموعه ستون‌هایی که در DOM وجود دارند پیوسته باشند، و اگر هیچ سلولی در آن مجموعه بیش از یک سطر یا ستون را پوشش ندهد، فقط باید `aria-colindex` را یک بار در هر ردیف روی اولین ستون مجموعه قرار دهید. اگر ستون‌ها پیوسته نیستند، مقدار `aria-colindex` را روی تمام فرزندان یا عناصر متعلق به هر ردیف قرار دهید.

مثال زیر یک گرید با ۶ ستون را نشان می‌دهد که ستون‌های ۱، ۲، ۵ و ۶ به کاربر نمایش داده می‌شوند. تعداد کل ستون‌های تشکیل‌دهنده جدول به صورت `aria-colcount="6"` روی خود جدول تنظیم شده است. از آنجایی که ستون‌ها پیوسته نیستند، هر [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role) - در این مورد عناصر [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) و [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role) - دارای ویژگی `aria-colindex` هستند.

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

اولین قانون استفاده از ARIA این است: "اگر می‌توانید از یک ویژگی بومی با معنا و رفتاری که از قبل نیاز دارید استفاده کنید، به جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای دسترسی‌پذیر کردن آن، این کار را انجام دهید." اگر از معناشناسی بومی HTML با {{HTMLElement('table')}}، {{HTMLElement('th')}}، {{HTMLElement('td')}} و غیره استفاده کنیم و فقط زیرمجموعه‌ای از ستون‌ها را نمایش دهیم، ویژگی‌های `aria-colcount` و `aria-colindex` همچنان ضروری هستند، اما نشانه‌گذاری کمتر طولانی است.

هنگام استفاده از عناصر سربرگ جدول معنایی و زمانی که همه ستون‌ها در DOM نیستند، ویژگی `aria-colindex` فقط باید یک بار در هر ستون در سربرگ ستون {{HTMLElement('th')}} تعریف شود.

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

اگر تمام ستون‌ها در DOM باشند، نه `aria-colcount` و نه `aria-colindex` ضروری نیستند.

## مقادیر

- `<integer>`
  - : یک عدد صحیح بزرگتر یا مساوی ۱ و کوچکتر یا مساوی تعداد کل ستون‌ها اگر همه وجود داشتند.

## رابط‌های مرتبط

- {{domxref("Element.ariaColIndex")}}
  - : ویژگی [`ariaColIndex`](/en-US/docs/Web/API/Element/ariaColIndex)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-colindex` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaColIndex")}}
  - : ویژگی [`ariaColIndex`](/en-US/docs/Web/API/ElementInternals/ariaColIndex)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-colindex` را منعکس می‌کند.

## نقش‌های مرتبط

مورد استفاده در نقش‌ها:

- [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)

به ارث برده شده در نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-colindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindextext) ویژگی
- [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) ویژگی
- [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan) ویژگی
- HTML {{HTMLElement('table')}} عنصر
- HTML {{HTMLElement('th')}} عنصر
- HTML {{HTMLElement('td')}} عنصر