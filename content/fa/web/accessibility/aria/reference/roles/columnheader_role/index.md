---
title: "ARIA: columnheader role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: columnheader role"
short-title: columnheader
slug: Web/Accessibility/ARIA/Reference/Roles/columnheader_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#columnheader
  - https://www.w3.org/WAI/ARIA/apg/patterns/table/examples/table/
sidebar: accessibilitysidebar
---

مقدار `columnheader` از ویژگی نقش ARIA، یک عنصر را به عنوان سلولی در یک ردیف که اطلاعات سربرگ برای یک ستون را شامل می‌شود، شناسایی می‌کند، مشابه عنصر بومی {{HTMLElement('th')}} با دامنه ستون.

## توضیحات

یک عنصر با `role="columnheader"` که به‌عنوان فرزند یک عنصر با `role="row"` قرار گرفته است، یک ساختار جدولی ایستا از یک سلول سربرگ ستون در یک ظرف جدولی، خواه یک جدول یا شبکه، یا نمودار دیگری که نیاز به نمایش روابط داده دارد، می‌باشد. برای پشتیبانی، columnheader باید درون یک عنصر با [نقش `row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) قرار گیرد.

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

تمامی سربرگ‌های ستون باید درون یک [row](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) قرار گیرند. هر ردیف نیز به نوبه خود باید درون یک [grid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)، [table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)، یا [treegrid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)، یا به‌طور جایگزین درون یک [rowgroup](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) که درون یکی از موارد بالا قرار دارد، باشد.

- [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort)
  - : فقط در یک زمان به یک سربرگ ستون اعمال می‌شود، در صورت وجود، ویژگی `aria-sort` نشان می‌دهد که آیا یک ستون به ترتیب صعودی (`ascending`) یا نزولی (`descending`) مرتب شده است، یا `none` برای مرتب نبودن.

### تعاملات صفحه‌کلید

این نقش از هیچ تعامل خاص صفحه‌کلید پشتیبانی نمی‌کند.

### ویژگی‌های جاوااسکریپت مورد نیاز

جاوااسکریپت فقط در صورت استفاده از ویژگی `aria-sort` مورد نیاز است.

## مثال‌ها

```html
<table>
  <thead>
    <tr role="row">
      <th role="columnheader" scope="col">
        <button>First Name</button>
      </th>
      <th role="columnheader" scope="col">
        <button>Last Name</button>
      </th>
      <th role="columnheader" scope="col" aria-sort="ascending">
        <button>Company Name</button>
      </th>
      <th role="columnheader" scope="col">
        <button>Job Title</button>
      </th>
    </tr>
  </thead>
  <tbody>
    …
  </tbody>
</table>
```

## بهترین روش‌ها

سربرگ‌های ستون باید شامل یک عنوان یا اطلاعات سربرگ برای ستون باشند.

اولین قانون ARIA این است: اگر یک عنصر یا ویژگی HTML بومی دارای معناشناسی و رفتاری است که نیاز دارید، از آن استفاده کنید به جای اینکه یک عنصر را تغییر کاربری داده و یک نقش، حالت یا ویژگی ARIA به آن اضافه کنید تا قابل دسترسی شود. توصیه می‌شود از عنصر بومی HTML `<th>` با ویژگی `scope` تنظیم شده به `<th scope="col">` استفاده کنید به جای یک `<div>` یا عنصر دیگر. اگر از HTML معنایی `<th scope="col">` استفاده کنید، ویژگی role مورد نیاز نیست، اما می‌تواند به عنوان پشتیبان گنجانده شود تا اطمینان حاصل شود که جدول در صورت حذف معناشناسی پیش‌فرض با مقدار ویژگی display CSS، معناشناسی خود را حفظ می‌کند.

ویژگی `aria-sort` می‌تواند به یک `<th scope="col">` اضافه شود حتی زمانی که ویژگی role ARIA مشخص نشده باشد.

### ترجیح HTML

Columnheader دارای معناشناسی مشابه `<th scope="col">` است.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`table` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)
- [`grid` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
- [`treegrid` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [`row` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [`rowgroup` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role)
- [The `<th>` element](/en-US/docs/Web/HTML/Reference/Elements/th)
- [The `<table>` element](/en-US/docs/Web/HTML/Reference/Elements/table)
- [The `<tr>` element](/en-US/docs/Web/HTML/Reference/Elements/tr)
- [The `<td>` element](/en-US/docs/Web/HTML/Reference/Elements/td)