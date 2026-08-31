---
title: "ARIA: rowgroup role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: rowgroup role"
short-title: rowgroup
slug: Web/Accessibility/ARIA/Reference/Roles/rowgroup_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#rowgroup
sidebar: accessibilitysidebar
---

یک عنصر با `role="rowgroup"` گروهی از [ردیف‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) در یک ساختار جدولی است. یک `rowgroup` شامل یک یا چند ردیف از [سلول‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)، [سلول‌های شبکه‌ای](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [سرستون‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) یا [سرردیف‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role) در یک [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)، [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) است.

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
      <span role="cell">Finland</span>
      <span role="cell">5.5 million</span>
    </div>
    <div role="row">
      <span role="cell">France</span>
      <span role="cell">67 million</span>
    </div>
  </div>
</div>
```

## توضیحات

`Rowgroup` رابطه‌ای بین عناصر ردیف متعلق به خود برقرار می‌کند و معادل ساختاری عناصر {{HTMLElement('thead')}}، {{HTMLElement('tfoot')}} و {{HTMLElement('tbody')}} در HTML است. با این حال، هیچ تمایزی بین انواع مختلف گروه‌های ردیف وجود ندارد. عناصر آن‌ها باید در عناصری با نقش [table](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role) یا [grid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) قرار داشته باشند یا متعلق به آن‌ها باشند. استفاده از عناصر بومی HTML {{HTMLElement('thead')}}، {{HTMLElement('tfoot')}} و {{HTMLElement('tbody')}} در صورت امکان، به شدت توصیه می‌شود.

برای ایجاد سربرگ جدول، پابرگ جدول یا بدنه جدول ARIA، `role="rowgroup"` را به عنصر اضافه کنید. آن گروه ردیف باید درون یک grid، table یا treegrid قرار گیرد و گروهی از یک یا چند ردیف را در بر بگیرد. هر ردیف به نوبه خود شامل سلول‌های فرزند است. این سلول‌ها بسته به اینکه سرستون یا سرردیف باشند یا سلول‌های ساده یا شبکه‌ای، می‌توانند انواع مختلفی داشته باشند.

> [!NOTE]
> استفاده از عنصر بومی HTML جدول ({{HTMLElement('table')}}) به همراه عناصر سربرگ جدول ({{HTMLElement('thead')}})، پابرگ ({{HTMLElement('tfoot')}}) و بدنه ({{HTMLElement('tbody')}}) در صورت امکان به شدت توصیه می‌شود.

### نقش‌های زمینه

- [role="table"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)
  - : یکی از سه زمینه ممکن (به همراه grid و treegrid) که در آن یک ردیف پیدا می‌کنید. این ردیف را به عنوان بخشی از یک ساختار جدولی غیرتعاملی شامل داده‌های مرتب‌شده در سطرها و ستون‌ها شناسایی می‌کند، مشابه عنصر بومی HTML {{HTMLElement('table')}}.
- [role="grid"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
  - : یکی از سه زمینه ممکن (به همراه table و treegrid) که در آن یک ردیف پیدا می‌کنید. این ردیف را به عنوان بخشی از یک ساختار جدولی غیرتعاملی شامل داده‌های مرتب‌شده در سطرها و ستون‌ها شناسایی می‌کند، مشابه عنصر بومی HTML {{HTMLElement('table')}}.
- [role="treegrid"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)
  - : مشابه یک grid، اما با ردیف‌هایی که می‌توانند به همان روش درخت باز و بسته شوند.

### نقش‌های فرزند

- [role="row"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
  - : یک ردیف از سلول‌ها در یک ساختار جدولی. یک ردیف شامل یک یا چند [سلول](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)، [سلول شبکه‌ای](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role) یا [سرستون‌ها](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) و گاهی یک [سرردیف](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role) است.

### تعاملات صفحه‌کلید

هیچ‌کدام.

### ویژگی‌های جاوااسکریپت مورد نیاز

هیچ‌کدام.

> [!NOTE]
> اولین قانون استفاده از ARIA این است که اگر می‌توانید از یک ویژگی بومی با معنا و رفتار مورد نیاز خود که از قبل ساخته شده است استفاده کنید، به جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای قابل دسترس کردن آن، این کار را انجام دهید. در صورت امکان به جای نقش ARIA جدول، از عنصر HTML `<table>` استفاده کنید.

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
      <span role="cell">header</span>
      <span role="cell">h1</span>
    </div>
    <div role="row" aria-rowindex="16">
      <span role="cell">header</span>
      <span role="cell">h6</span>
    </div>
    <div role="row" aria-rowindex="18">
      <span role="cell">rowgroup</span>
      <span role="cell">thead</span>
    </div>
    <div role="row" aria-rowindex="24">
      <span role="cell">term</span>
      <span role="cell">dt</span>
    </div>
  </div>
</div>
```

نمونه بالا یک جدول ARIA غیر معنایی با سربرگ جدول و بدنه جدول است که پنج ردیف از ۸۱ ردیف در DOM وجود دارد: یکی در سربرگ جدول و چهار ردیف در بدنه جدول. ردیف سربرگ، که به تنهایی در یک گروه ردیف سربرگ قرار دارد، دو سرستون دارد. ستون‌ها قابل مرتب‌سازی هستند، اما در حال حاضر مرتب نشده‌اند، همان‌طور که ویژگی [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort) نشان می‌دهد. بدنه جدول یک گروه ردیف جداگانه است که چهار ردیف در DOM دارد. از آنجا که همه ردیف‌ها در DOM نیستند، ویژگی [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) را روی هر ردیف قرار داده‌ایم.

## بهترین روش‌ها

فقط از {{HTMLElement('table')}}، {{HTMLElement('tbody')}}، {{HTMLElement('thead')}}، {{HTMLElement('tr')}}، {{HTMLElement('th')}}، {{HTMLElement('td')}} و غیره برای ساختار جدول داده استفاده کنید. می‌توانید این نقش‌های ARIA را برای تضمین دسترسی‌پذیری اضافه کنید اگر معنای ذاتی جدول حذف شود، مثلاً با CSS. یک مورد استفاده مرتبط برای نقش ARIA table زمانی است که ویژگی display در CSS معنای ذاتی جدول را لغو کند، مانند `display: grid`. در این حالت، می‌توانید از نقش‌های ARIA table برای افزودن معنا استفاده کنید.

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
      <td role="cell">header</td>
      <td role="cell">h1</td>
    </tr>
    <tr role="row" aria-rowindex="16">
      <td role="cell">header</td>
      <td role="cell">h6</td>
    </tr>
  </tbody>
</table>
```

در بالا روش معنایی نوشتن جدول آمده است. نقش‌های ARIA تنها زمانی لازم هستند که معنای ذاتی جدول، و در نتیجه ردیف‌های جدول، از بین بروند، مانند تنظیم [خاصیت display روی flex یا grid](/en-US/docs/Web/CSS/Reference/Properties/display#accessibility).

### مزایای افزوده

هیچ‌کدام

## مشخصات

{{Specifications}}

## جستارهای وابسته

- [جدول HTML](/en-US/docs/Web/HTML/Reference/Elements/table)
- [بدنه جدول HTML](/en-US/docs/Web/HTML/Reference/Elements/tbody)
- [پابرگ جدول HTML](/en-US/docs/Web/HTML/Reference/Elements/tfoot)
- [سربرگ جدول HTML](/en-US/docs/Web/HTML/Reference/Elements/thead)