---
title: "ARIA: aria-rowcount attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-rowcount attribute"
short-title: aria-rowcount
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-rowcount
sidebar: accessibilitysidebar
---

ویژگی `aria-rowcount` تعداد کل ردیف‌ها را در یک جدول، شبکه یا درخت‌شبکه تعریف می‌کند.

## توضیحات

برخی جدول‌ها صدها یا حتی میلیون‌ها ردیف دارند. حتی برای جدول‌هایی با ردیف‌های کمتر، بارگذاری تنها زیرمجموعه‌ای از ردیف‌ها می‌تواند یک الزام طراحی باشد، عملکرد را بهبود بخشد یا تجربه کاربری را بهتر کند. وقتی فقط زیرمجموعه‌ای از ردیف‌ها بارگذاری می‌شود، باید به همه کاربران اطلاع دهید که فقط بخشی از داده‌ها نمایش داده می‌شود. ویژگی `aria-rowcount` برای تعریف تعداد کل ردیف‌های یک جدول، شبکه یا درخت‌شبکه استفاده می‌شود.

این ویژگی روی عنصر {{HTMLElement('table')}} یا روی عنصری با نقش [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role) قرار می‌گیرد؛ مقدار آن، به‌صورت یک عدد صحیح، تعداد ردیف‌های جدول کامل است. اگر تعداد کل ردیف‌ها مشخص نباشد، مقدار `aria-rowcount="-1"` را قرار دهید تا به مرورگر بگوید تعداد کل ردیف‌ها را شمارش نکند.

اگر همه ردیف‌ها بارگذاری شده‌اند و در DOM هستند، نیازی به گنجاندن `aria-rowcount` ندارید، زیرا مرورگرها به‌طور خودکار تعداد کل ردیف‌ها را شمارش می‌کنند. با این حال، اگر در هر زمان همه ردیف‌ها در DOM حضور نداشته باشند، این ویژگی برای ارائه تعداد ردیف‌ها وقتی اندازه کامل جدول مشخص است و همچنین برای گفتن به مرورگر که در صورت نامشخص بودن تعداد کل ردیف‌ها، به‌طور خودکار ردیف‌ها را شمارش نکند، لازم است.

## مثال

مثال زیر یک شبکه با ۲۴ ردیف را نشان می‌دهد که از میان آن‌ها، ردیف اول و ردیف‌های ۷ تا ۹ به کاربر نمایش داده می‌شوند.

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
      <span role="gridcell">Goalkeeper</span>
    </div>
  </div>
</div>
```

## مقادیر

- `<integer>`
  - : تعداد ردیف‌های جدول کامل، یا `-1` اگر اندازه جدول مشخص نباشد.

## رابط‌های مرتبط

- {{domxref("Element.ariaRowCount")}}
  - : ویژگی [`ariaRowCount`](/en-US/docs/Web/API/Element/ariaRowCount)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-rowcount` را بازتاب می‌دهد.
- {{domxref("ElementInternals.ariaRowCount")}}
  - : ویژگی [`ariaRowCount`](/en-US/docs/Web/API/ElementInternals/ariaRowCount)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-rowcount` را بازتاب می‌دهد.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

- [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)

به‌ارث‌رسیده در نقش‌ها:

- [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex)
- [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount)