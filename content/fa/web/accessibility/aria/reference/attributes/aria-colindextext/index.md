---
title: "ARIA: aria-colindextext attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindextext"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-colindextext attribute"
short-title: aria-colindextext
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-colindextext
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-colindextext
sidebar: accessibilitysidebar
---

ویژگی `aria-colindextext` یک جایگزین متنیِ قابل‌خواندن برای انسان برای [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) عددی تعریف می‌کند.

## توضیحات

هنگامی که یک جدول بسیار بزرگ دارید یا به‌طور عمدی می‌خواهید فقط بخشی از یک جدول را نمایش دهید، ممکن است همه ستون‌ها در DOM حضور نداشته باشند. در این حالت، از [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) با یک مقدار صحیح استفاده می‌کنیم تا مشخص کنیم جدول (یا شبکه) اگر همه ستون‌ها حضور داشتند چند ستون می‌داشت و ویژگی [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) را روی هر ستون اضافه می‌کنیم تا اطلاعاتی درباره شاخص ستون در آن جدول بزرگ‌تر فراهم کند.

در قطعه HTML زیر، جدول ما ۸ ستون دارد، اما ما فقط ۴ ستون را نمایش می‌دهیم. ستون «city» پنجمین ستون جدول بزرگ‌تر ما است، همان‌طور که توسط `aria-colindex="5"` تعریف شده است.

```html
<table aria-colcount="8">
  <thead>
    <tr>
      <th aria-colindex="1" scope="col">First name</th>
      <th aria-colindex="2" scope="col">Last name</th>
      <th aria-colindex="5" scope="col">City</th>
      <th aria-colindex="7" scope="col">Zip</th>
    </tr>
  </thead>
  …
</table>
```

این جدول چندان پیچیده نیست. اگر این یک صفحه‌گسترده با بیش از ۱۰۰ ستون یا یک شبکه بدون سرستون، مانند صفحه شطرنج بود، مقدار ارائه‌شده یا محاسبه‌شده `aria-colindex` ممکن بود معنادار نباشد یا شاخص نمایش‌داده‌شده را منعکس نکند. در این صورت، می‌توان `aria-colindextext` را اضافه کرد. مقدار این ویژگی یک رشته است که جایگزین متنی قابل‌خواندن برای انسان برای `aria-colindex` عددی است.

```html
<table aria-colcount="128">
  <thead>
    <tr>
      <th aria-colindex="1" aria-colindextext="NYSE stock symbol" scope="col">
        NYSE
      </th>
      <th
        aria-colindex="110"
        aria-colindextext="Value at start of 2021"
        scope="col">
        01/21
      </th>
      <th
        aria-colindex="122"
        aria-colindextext="Value at start of 2022"
        scope="col">
        01/22
      </th>
      <th aria-colindex="124" scope="col">Recommendation</th>
    </tr>
  </thead>
  …
</table>
```

در مثال بالا، جدول ۱۲۸ ستون دارد که تنها ۴ ستون از آن‌ها نشان داده شده است. از `aria-colindextext` در سه ستون برای ارائه جایگزین‌های متنی قابل‌خواندن برای انسان استفاده شده است. با گنجاندن `aria-colindextext="Value at start of 2021"`، فناوری‌های کمکی می‌توانند به‌جای «ستون ۱۱۰»، «Value at start of 2021» را اعلام کنند.

تنها زمانی از `aria-colindextext` استفاده کنید که مقدار ارائه‌شده یا محاسبه‌شده `aria-colindex` معنادار نباشد یا شاخص نمایش‌داده‌شده را منعکس نکند. هر زمان که `aria-colindextext` را اضافه می‌کنید، `aria-colindex` را نیز حفظ کنید، زیرا برخی فناوری‌های کمکی برای پیگیری موقعیت کاربر و ارائه ناوبری جایگزین جدول به شاخص عددی ستون متکی هستند.

> [!NOTE]
> در حالی که `aria-colindex` را می‌توان به یک ردیف اضافه کرد، زمانی که همه ستون‌های موجود متوالی هستند و مقادیر ترتیبی قابل استنتاج هستند، `aria-colindextext` به‌هیچ‌وجه ویژگی پشتیبانی‌شده برای نقش [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) نیست.

همچنین ببینید: [`aria-rowindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindextext).

## مقادیر

- `<string>`
  - : جایگزین متنی قابل‌خواندن برای انسان برای [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) عددی.

## رابط‌های مرتبط

- {{domxref("Element.ariaColIndexText")}}
  - : ویژگی [`ariaColIndexText`](/en-US/docs/Web/API/Element/ariaColIndexText) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-colindextext` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaColIndexText")}}
  - : ویژگی [`ariaColIndexText`](/en-US/docs/Web/API/ElementInternals/ariaColIndexText) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-colindextext` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

- [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)

به نقش‌های زیر به ارث می‌رسد:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`Element.ariaColIndexText`](/en-US/docs/Web/API/Element/ariaColIndexText)
- [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)
- [`aria-rowindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindextext)
- [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount)
- نقش [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)
- نقش [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- نقش [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)