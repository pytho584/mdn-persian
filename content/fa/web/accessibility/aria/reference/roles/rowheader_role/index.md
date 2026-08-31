---
title: "ARIA: rowheader role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: rowheader role"
short-title: rowheader
slug: Web/Accessibility/ARIA/Reference/Roles/rowheader_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#rowheader
sidebar: accessibilitysidebar
---

عنصری با `role="rowheader"` یک [سلول](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role) است که اطلاعات سربرگ برای یک [ردیف](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) در ساختار جدولی از یک [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)، [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) را شامل می‌شود.

## توضیحات

`Rowheader` سربرگ [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role) برای یک ردیف است و رابطه‌ای بین آن و سایر سلول‌های موجود در همان [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) برقرار می‌کند.

```html
<div
  role="table"
  aria-label="Populations"
  aria-describedby="country_population_desc">
  <div id="country_population_desc">World Populations by Country</div>
  <div role="rowgroup">
    <div role="row">
      <span role="columnheader" aria-sort="descending">Country</span>
      <span role="columnheader" aria-sort="none">Population</span>
    </div>
  </div>
  <div role="rowgroup">
    <div role="row">
      <span role="rowheader">Finland</span>
      <span role="cell">5.5 million</span>
    </div>
    <div role="row">
      <span role="rowheader">France</span>
      <span role="cell">67 million</span>
    </div>
  </div>
</div>
```

این معادل ساختاری عنصر {{HTMLElement('th')}} با دامنه `row`، `<th scope="row">` است. استفاده از عنصر بومی {{HTMLElement('th')}} HTML به شدت توصیه می‌شود.

برای ایجاد یک سربرگ ردیف ARIA، `role="rowheader"` را به عنصر اضافه کنید. آن سربرگ ردیف باید درون یک `row` قرار گیرد، که خود درون یک `rowgroup`، یا مستقیماً درون یک `grid`، `table` یا `treegrid` قرار دارد.

> [!NOTE] استفاده از [عناصر جدول](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics) بومی در هر زمان ممکن، به شدت توصیه می‌شود.

### نقش‌ها، وضعیت‌ها و ویژگی‌های WAI-ARIA مرتبط

#### نقش‌های زمینه

- [role="row"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
  - : تنها زمینه‌ای که در آن یک ردیف پیدا می‌کنید. این شامل یک ردیف سلول یا گروهی از سلول‌ها است که تنها یکی از آنها باید از نوع rowheader باشد. مشابه عنصر بومی {{HTMLElement('tr')}} HTML.

### تعاملات صفحه‌کلید

هیچ.

### ویژگی‌های جاوااسکریپت مورد نیاز

هیچ.

> [!NOTE] اولین قانون استفاده از ARIA این است که اگر می‌توانید از یک ویژگی بومی با معانی و رفتاری که از قبل در آن تعبیه شده استفاده کنید، به جای تغییر کاربری یک عنصر و **اضافه کردن** یک نقش، وضعیت یا ویژگی ARIA برای دسترسی‌پذیر کردن آن، این کار را انجام دهید. تا حد امکان از عناصر HTML `<table>`، `<tr>`، `<th>`، `<td>` و سایر [عناصر جدول](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics) به جای نقش‌های جدول ARIA استفاده کنید.

## مثال‌ها

```html
<div
  role="table"
  aria-label="Semantic Elements"
  aria-describedby="semantic_elements_table_desc"
  aria-rowcount="81">
  <div id="semantic_elements_table_desc">
    Semantic Elements to use instead of ARIA's roles
  </div>
  <div role="rowgroup">
    <div role="row">
      <span role="columnheader" aria-sort="none">ARIA Role</span>
      <span role="columnheader" aria-sort="none">Semantic Element</span>
    </div>
  </div>
  <div role="rowgroup">
    <div role="row" aria-rowindex="11">
      <span role="rowheader">header</span>
      <span role="cell">h1</span>
    </div>
    <div role="row" aria-rowindex="16">
      <span role="rowheader">header</span>
      <span role="cell">h6</span>
    </div>
    <div role="row" aria-rowindex="18">
      <span role="rowheader">rowgroup</span>
      <span role="cell">thead</span>
    </div>
    <div role="row" aria-rowindex="24">
      <span role="rowheader">term</span>
      <span role="cell">dt</span>
    </div>
  </div>
</div>
```

مثال بالا یک جدول ARIA غیرمعنایی است با سربرگ جدول و بدنه جدول، که پنج ردیف از ۸۱ ردیف در DOM وجود دارد: یکی در سربرگ جدول و چهار ردیف در بدنه جدول. ردیف سربرگ، که به تنهایی در یک گروه ردیف سربرگ قرار دارد، دارای دو سربرگ ستون است. ستون‌ها قابل مرتب‌سازی هستند، اما در حال حاضر مرتب نشده‌اند، همانطور که توسط ویژگی [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort) نشان داده شده است. بدنه جدول یک گروه ردیف جداگانه است، با چهار ردیف که در حال حاضر در DOM وجود دارند. هر ردیف جدول داده دارای یک سربرگ ردیف است. از آنجایی که همه ردیف‌ها در DOM نیستند، ما ویژگی [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) را روی هر ردیف اعمال کرده‌ایم.

## بهترین روش‌ها

فقط از {{HTMLElement('table')}}، {{HTMLElement('tbody')}}، {{HTMLElement('thead')}}، {{HTMLElement('tr')}}، {{HTMLElement('th')}}، {{HTMLElement('td')}} و غیره برای ساختار جدول داده استفاده کنید. می‌توانید این نقش‌های ARIA را اضافه کنید تا در صورت حذف معانی بومی جدول، مانند با CSS، دسترسی‌پذیری تضمین شود. یک مورد استفاده مرتبط برای همه نقش‌های جدول ARIA زمانی است که ویژگی `display` CSS معانی بومی یک جدول را لغو می‌کند، مانند `display: grid`. در این صورت، می‌توانید از نقش‌های جدول ARIA برای افزودن معانی استفاده کنید.

```html
<table
  role="table"
  aria-label="Semantic Elements"
  aria-describedby="semantic_elements_table_desc"
  aria-rowcount="81">
  <caption id="semantic_elements_table_desc">
    Semantic Elements to use instead of ARIA's roles
  </caption>
  <thead role="rowgroup">
    <tr role="row">
      <th role="columnheader" aria-sort="none">ARIA Role</th>
      <th role="columnheader" aria-sort="none">Semantic Element</th>
    </tr>
  </thead>
  <tbody role="rowgroup">
    <tr role="row" aria-rowindex="11">
      <th role="rowheader">header</th>
      <td role="cell">h1</td>
    </tr>
    <tr role="row" aria-rowindex="16">
      <th role="rowheader">header</th>
      <td role="cell">h6</td>
    </tr>
  </tbody>
</table>
```

در بالا روش معنایی نوشتن یک جدول آورده شده است. نقش‌های ARIA تنها در صورتی ضروری هستند که معانی بومی جدول، و در نتیجه سربرگ‌های ردیف جدول، از بین بروند، مانند تنظیم [ویژگی display به flex یا grid](/en-US/docs/Web/CSS/Reference/Properties/display#accessibility).

### مزایای اضافه

هیچ

## مشخصات

{{Specifications}}

## همچنین ببینید

- [عنصر HTML `<table>`](/en-US/docs/Web/HTML/Reference/Elements/table)
- [عنصر HTML `<th>`](/en-US/docs/Web/HTML/Reference/Elements/th)
- [آموزش جدول HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- [نقش `cell` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)
- [نقش `row` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [نقش `gridcell` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)