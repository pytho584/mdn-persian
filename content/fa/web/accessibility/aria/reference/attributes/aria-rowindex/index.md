---
title: "ARIA: aria-rowindex attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-rowindex attribute"
short-title: aria-rowindex
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-rowindex
sidebar: accessibilitysidebar
---

ویژگی `aria-rowindex` موقعیت یک عنصر را نسبت به تعداد کل ردیف‌ها در یک جدول، گرید یا درخت‌گرید تعریف می‌کند.

## توضیحات

برخی جدول‌ها ردیف‌های بسیار زیادی دارند. بارگذاری تنها زیرمجموعه‌ای از ردیف‌ها ممکن است به‌عنوان یک الزام طراحی، برای بهبود کارایی یا بهبود تجربه کاربری انجام شود.

هنگامی که تنها زیرمجموعه‌ای از ردیف‌ها بارگذاری می‌شود، باید به همه کاربران اطلاع دهید که کدام زیرمجموعه از ردیف‌ها در حال نمایش است. از ویژگی `aria-rowindex` برای تعریف اندیس ردیف یا موقعیتِ سلول یا ردیف نسبت به تعداد کل ردیف‌های یک جدول، گرید یا درخت‌گرید استفاده می‌شود.

این ویژگی بر روی عنصر {{HTMLElement('tr')}} یا عنصری با نقش [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)، یا مستقیماً بر روی {{HTMLElement('td')}}، {{HTMLElement('th')}} یا عنصر دارای نقش [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role) یا [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role) قرار می‌گیرد؛ مقدار آن موقعیت ردیف نسبت به جدول کامل است.

مقدار `aria-rowindex` یک عدد صحیح بزرگ‌تر یا مساوی `1`، بزرگ‌تر از مقدار `aria-rowindex` هر یک از ردیف‌های قبلی و کوچک‌تر یا مساوی تعداد ردیف‌های جدول کامل است.

اگر همه ردیف‌ها بارگذاری شده و در DOM باشند، نیازی به گنجاندن `aria-rowindex` نیست، زیرا مرورگرها به‌طور خودکار اندیس هر ردیف را محاسبه می‌کنند. با این حال، وقتی تنها زیرمجموعه‌ای از ردیف‌ها در DOM وجود دارد، برای نشان دادن موقعیت هر ردیف نسبت به جدول کامل، `aria-rowindex` لازم است. اگر فقط زیرمجموعه‌ای از ردیف‌ها بارگذاری شده باشد، باید [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount) را نیز بر روی عنصر جدول بالادستی قرار دهید، حتی اگر تعداد کل ردیف‌ها را نمی‌دانید.

اگر جدولی که تنها زیرمجموعه‌ای از ردیف‌ها را دارد، سلولی داشته باشد که بیش از یک ردیف را پوشش می‌دهد، هم ردیف و هم سلول باید دارای `aria-rowindex` تنظیم‌شده باشند. اگر سلولی بیش از یک ردیف را پوشش دهد — وقتی نقش سلول شامل ویژگی `aria-rowspan` است یا سلول HTML ویژگی `rowspan` را با مقدار بزرگ‌تر از ۱ تنظیم کرده باشد — مقدار `aria-rowindex` آن ردیف را علاوه بر ویژگی مناسب پوشش ردیف، بر روی سلول پوشش‌دهنده قرار دهید. این مقدار باید اندیس ردیفی باشد که پوشش از آنجا شروع می‌شود.

> [!NOTE]
> `aria-rowindex` باید به هر ردیف اضافه شود، اما بر روی سلول‌ها اختیاری است، به‌جز سلول‌هایی که ردیف‌ها را پوشش می‌دهند: ویژگی `aria-rowindex` برای همه سلول‌های پوشش‌دهنده الزامی است.

## مثال‌ها

مثال زیر گریدی با ۲۴ ردیف را نشان می‌دهد که از میان آن‌ها ردیف اول و ردیف‌های ۷ تا ۱۰ به کاربر نمایش داده می‌شوند. آخرین سلول «position» ردیف‌های ۹ و ۱۰ را پوشش می‌دهد.

```html
<div role="grid" aria-rowcount="24">
  <div role="rowgroup">
    <div role="row" aria-rowindex="1">
      <span role="columnheader">First Name</span>
      <span role="columnheader">Last Name</span>
      <span role="columnheader">Position</span>
    </div>
  </div>
  <div role="rowgroup">
    <div role="row" aria-rowindex="7">
      <span role="gridcell">Morgan</span>
      <span role="gridcell">Brian</span>
      <span role="gridcell">Midfielder</span>
    </div>
    <div role="row" aria-rowindex="8">
      <span role="gridcell">Abby</span>
      <span role="gridcell">Dahlkemper</span>
      <span role="gridcell">Defender</span>
    </div>
    <div role="row" aria-rowindex="9">
      <span role="gridcell">Ashlyn</span>
      <span role="gridcell">Harris</span>
      <span role="gridcell" aria-rowspan="2" aria-rowindex="9">Goalkeeper</span>
    </div>
    <div role="row" aria-rowindex="10">
      <span role="gridcell">Alyssa</span>
      <span role="gridcell">Naeher</span>
    </div>
  </div>
</div>
```

توجه کنید که هر دو `aria-rowspan` و `aria-rowindex` روی سلول Goalkeeper که دو ردیف را پوشش می‌دهد، قرار دارند.

## مقادیر

- `<integer>`
  - : یک عدد صحیح بزرگ‌تر یا مساوی ۱، بزرگ‌تر از `aria-rowindex` ردیف قبلی (در صورت وجود) و کوچک‌تر یا مساوی مقدار [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount).

## رابط‌های مرتبط

- {{domxref("Element.ariaRowIndex")}}
  - : ویژگی [`ariaRowIndex`](/en-US/docs/Web/API/Element/ariaRowIndex)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-rowindex` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaRowIndex")}}
  - : ویژگی [`ariaRowIndex`](/en-US/docs/Web/API/ElementInternals/ariaRowIndex)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-rowindex` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

- [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)

به نقش‌های زیر به ارث می‌رسد:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-rowindextext`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindextext)
- [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount)
- [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan)
- [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)
- ویژگی [`rowspan`](/en-US/docs/Web/HTML/Reference/Elements/td#rowspan) بر روی {{HTMLElement('td')}}