---
title: "ARIA: cell role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role"
translated_by: "n8n + AI"
short-title: cell
slug: Web/Accessibility/ARIA/Reference/Roles/cell_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#cell
  - https://www.w3.org/WAI/ARIA/apg/patterns/table/examples/table/
sidebar: accessibilitysidebar
---

مقدار `cell` از ویژگی _role_ ARIA یک عنصر را به عنوان یک سلول در یک ظرف جدولی که حاوی اطلاعات سرستون ستون یا ردیف نیست، شناسایی می‌کند. برای پشتیبانی، سلول باید درون یک عنصر با نقش `row` قرار گیرد.

```html
<div role="row">
  <span role="cell">France</span>
  <span role="cell">67 million</span>
</div>
```

روش بهتر و معنایی‌تر برای نوشتن سلول‌های بالا استفاده از عنصر معنایی [`<td>`](/en-US/docs/Web/HTML/Reference/Elements/td) است.

```html
<tr role="row">
  <td role="cell">France</td>
  <td role="cell">67 million</td>
</tr>
```

## توضیحات

عنصری با `role="cell"` یک سلول درون یک ردیف است، به‌طور اختیاری درون یک [`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) و درون یک [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role). اگر سلول در یک [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) باشد، از [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role) استفاده کنید. استفاده از عناصر بومی HTML {{HTMLElement('td')}} تا حد امکان به شدت توصیه می‌شود.

هر عنصر با `role="cell"` باید درون یک عنصر ظرف با [`role="row"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) قرار گیرد. آن ردیف نیز به نوبه خود می‌تواند درون یک عنصر با [`role="rowgroup"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) قرار گیرد و باید درون یک `grid`، `table` یا `treegrid` باشد. اگر یک سلول حاوی اطلاعات سرستون ستون یا ردیف است، به ترتیب از نقش‌های `columnheader` یا `rowheader` استفاده کنید. اگر سلول حاوی اطلاعات سرستون نیست و درون `grid` یا `treegrid` قرار دارد، نقش `gridcell` ممکن است مناسب‌تر باشد.

یک سلول می‌تواند دارای تعدادی ویژگی (attribute) باشد که موقعیت سلول را در ساختار داده‌های جدولی مشخص می‌کند، از جمله [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)، [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan)، [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) و [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan).

> [!NOTE]
> استفاده از عنصر جدول HTML بومی ({{HTMLElement('table')}}) به همراه عنصر ردیف جدول ({{HTMLElement('tr')}}) و عنصر سلول جدول ({{HTMLElement('td')}}) تا حد امکان به شدت توصیه می‌شود.

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

#### نقش‌های زمینه

- [role="row"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
  - : یک عنصر با `role="row"` یک ردیف از سلول‌ها درون یک ساختار جدولی است. یک ردیف شامل یک یا چند سلول، سلول‌های شبکه، سرستون‌های ستون یا سرستون‌های ردیف درون یک [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)، [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role) یا `treegrid` و به‌طور اختیاری درون یک [`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) است.
- [role="rowgroup"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role)
  - : `Row` یک والد ضروری برای سلول است. `Rowgroup` یک والد ردیف زمینه‌ای اختیاری است. این نقش یک رابطه بین ردیف‌های فرزند برقرار می‌کند. از نظر ساختاری معادل عناصر [`thead`](/en-US/docs/Web/HTML/Reference/Elements/thead)، [`tfoot`](/en-US/docs/Web/HTML/Reference/Elements/tfoot) و [`tbody`](/en-US/docs/Web/HTML/Reference/Elements/tbody) در یک عنصر [HTML `table`](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics) است.
- [role="table"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)
  - : یکی از سه زمینه ممکن (به همراه `grid` و `treegrid`) که در آن یک ردیف حاوی سلول پیدا می‌کنید. Table سلول را به عنوان بخشی از یک ساختار جدولی غیرتعاملی حاوی داده‌های مرتب‌شده در ردیف‌ها و ستون‌ها، مشابه عنصر بومی HTML [`<table>`](/en-US/docs/Web/HTML/Reference/Elements/table) شناسایی می‌کند.
- [role="grid"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
  - : یکی از سه زمینه ممکن (به همراه `table` و `treegrid`) که در آن یک ردیف حاوی `cells` و `gridcells` پیدا می‌کنید. `Grid` یک سلول را به عنوان بخشی از یک ساختار جدولی احتمالاً تعاملی حاوی داده‌های مرتب‌شده در ردیف‌ها و ستون‌ها، مشابه عنصر HTML بومی [`<table>`](/en-US/docs/Web/HTML/Reference/Elements/table) شناسایی می‌کند.
- [role="treegrid"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)
  - : مشابه یک grid، اما با ردیف‌هایی که می‌توانند به همان روش یک درخت باز و بسته شوند.

#### نقش‌های زیرمجموعه

- [role="gridcell"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
  - : یک سلول در یک ردیف درون یک `grid` یا `treegrid`.
- [role="columnheader"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
  - : یک سلول سرستون که از نظر ساختاری معادل عنصر HTML [`<th>`](/en-US/docs/Web/HTML/Reference/Elements/th) با دامنه ستون است. برخلاف یک سلول ساده، نقش `columnheader` یک رابطه بین آن و تمام سلول‌های ستون مربوطه برقرار می‌کند.
- [role="rowheader"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
  - : یک سلول سرستون که از نظر ساختاری معادل عنصر HTML [`<th>`](/en-US/docs/Web/HTML/Reference/Elements/th) با دامنه ردیف است. برخلاف یک سلول ساده، نقش `rowheader` یک رابطه بین آن و تمام سلول‌های ردیف مربوطه برقرار می‌کند.

#### حالت‌ها و ویژگی‌ها

- [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan)
  - : مشابه ویژگی colspan در HTML [`<th>`](/en-US/docs/Web/HTML/Reference/Elements/th) و [`<td>`](/en-US/docs/Web/HTML/Reference/Elements/td)، تعداد ستون‌هایی که سلول در بر می‌گیرد را تعریف می‌کند.
- [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan)
  - : مشابه ویژگی rowspan در HTML [`<th>`](/en-US/docs/Web/HTML/Reference/Elements/th) و [`<td>`](/en-US/docs/Web/HTML/Reference/Elements/td)، تعداد ردیف‌هایی که سلول در بر می‌گیرد را تعریف می‌کند.
- [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)
  - : ویژگی `aria-colindex` فقط زمانی لازم است که ستون‌ها از DOM پنهان شده باشند. این ویژگی یک عدد صحیح بین 1 و تعداد کل ستون‌های داخل `table`، `grid` یا `treegrid` را به عنوان مقدار می‌گیرد. `aria-colindex` شاخص یا موقعیت ستون یک عنصر را نسبت به تعداد کل ستون‌های داخل یک ردیف تعریف می‌کند. اگر همه ستون‌ها در DOM باشند، این ویژگی ضروری نیست.
- [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex)
  - : ویژگی `aria-rowindex` فقط زمانی لازم است که ردیف‌ها از DOM پنهان شده باشند، تا مشخص کند سلول جاری در کدام ردیف از لیست کل ردیف‌ها قرار دارد. این ویژگی یک عدد صحیح بین 1 و تعداد کل ردیف‌های داخل جدول، grid یا treegrid را به عنوان مقدار می‌گیرد که موقعیت یا شاخص سلول را نشان می‌دهد. برای مثال، یک سلول در اولین ردیف از اولین سرستون احتمالاً `aria-rowindex="1"` را تنظیم کرده است، و سلول‌های ردیف 47 دارای `aria-rowindex="47"` خواهند بود، اگر به دلیل نبودن همه ردیف‌ها در DOM نیاز به `aria-rowindex` باشد. اگر ردیف‌هایی که قابل مشاهده هستند متوالی باشند و هیچ سلولی با `colspan` یا `rowspan` بزرگتر از یک وجود نداشته باشد، این ویژگی می‌تواند به ردیف‌های والد اضافه شود نه به تمام سلول‌های ردیف‌ها.

### تعاملات صفحه‌کلید

هیچ‌کدام.

### ویژگی‌های جاوااسکریپت مورد نیاز

اولین قانون استفاده از ARIA این است که اگر می‌توانید از یک ویژگی بومی با معانی و رفتار مورد نیاز خود استفاده کنید که از قبل تعبیه شده است، به جای تغییر کاربری یک عنصر و **اضافه کردن** یک نقش، حالت یا ویژگی ARIA برای دسترسی‌پذیر کردن آن، این کار را انجام دهید. تا حد امکان از عنصر HTML [`<td>`](/en-US/docs/Web/HTML/Reference/Elements/td) به جای نقش ARIA `cell` استفاده کنید.

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
      <span role="columnheader" aria-sort="none" aria-rowindex="1"
        >ARIA Role</span
      >
      <span role="columnheader" aria-sort="none" aria-rowindex="1"
        >Semantic Element</span
      >
    </div>
  </div>
  <div role="rowgroup">
    <div role="row">
      <span role="cell" aria-rowindex="11">header</span>
      <span role="cell" aria-rowindex="11">h1</span>
    </div>
    <div role="row">
      <span role="cell" aria-rowindex="16">header</span>
      <span role="cell" aria-rowindex="16">h6</span>
    </div>
    <div role="row">
      <span role="cell" aria-rowindex="18">rowgroup</span>
      <span role="cell" aria-rowindex="18">thead</span>
    </div>
    <div role="row">
      <span role="cell" aria-rowindex="24">term</span>
      <span role="cell" aria-rowindex="24">dt</span>
    </div>
  </div>
</div>
```

مثال بالا یک جدول ARIA غیرمعنایی است که پنج ردیف از 81 ردیف در DOM وجود دارد: یکی درون سربرگ جدول و چهار ردیف درون بدنه جدول. از آنجایی که همه ردیف‌ها در DOM نیستند، ویژگی `aria-rowindex` را روی هر سلول قرار داده‌ایم. اگر هیچ سلولی بیش از یک ردیف یا ستون را پوشش نمی‌داد، می‌توانستیم `aria-rowindex` را روی ردیف به جای سلول‌های جداگانه ردیف قرار دهیم.

## بهترین روش‌ها

فقط از {{HTMLElement('table')}}، {{HTMLElement('tbody')}}، {{HTMLElement('thead')}}، {{HTMLElement('tr')}}، {{HTMLElement('th')}}، {{HTMLElement('td')}} و غیره برای ساختار جدول داده استفاده کنید. می‌توانید نقش‌های ARIA را برای اطمینان از دسترسی‌پذیری در صورت حذف معانی بومی جدول، مانند با CSS، اضافه کنید. یک مورد استفاده مرتبط برای نقش ARIA table زمانی است که معانی بومی یک جدول توسط [ویژگی display در CSS، مانند display: grid](/en-US/docs/Web/CSS/Reference/Properties/display#accessibility) لغو می‌شود. در این صورت، می‌توانید از نقش‌های جدول ARIA برای بازگرداندن معانی استفاده کنید.

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
      <th role="columnheader" aria-sort="none" aria-rowindex="1">ARIA Role</th>
      <th role="columnheader" aria-sort="none" aria-rowindex="1">
        Semantic Element
      </th>
    </tr>
  </thead>
  <tbody role="rowgroup">
    <tr role="row">
      <td role="cell" aria-rowindex="11">header</td>
      <td role="cell" aria-rowindex="11">h1</td>
    </tr>
    <tr role="row">
      <td role="cell" aria-rowindex="16">header</td>
      <td role="cell" aria-rowindex="16">h6</td>
    </tr>
    <tr role="row">
      <td role="cell" aria-rowindex="18">rowgroup</td>
      <td role="cell" aria-rowindex="18">thead</td>
    </tr>
    <tr role="row">
      <td role="cell" aria-rowindex="24">term</td>
      <td role="cell" aria-rowindex="24">dt</td>
    </tr>
  </tbody>
</table>
```

در بالا روش معنایی نوشتن یک جدول نشان داده شده است. نقش‌های ARIA در صورت عدم تغییر معانی بومی جدول و بنابراین ردیف‌های جدول، مانند از طریق [ویژگی display](/en-US/docs/Web/CSS/Reference/Properties/display#accessibility)، ضروری نیستند.

### مزایای اضافه

هنگامی که روی یک {{HTMLElement('td')}} اعمال شود، معانی سلول را به عنصر باز می‌گرداند در صورتی که معانی حذف شده باشند، مانند با `display: grid;`.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`role="row"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [`role="gridcell"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [HTML `<td>` element](/en-US/docs/Web/HTML/Reference/Elements/td)
- [HTML `<th>` element](/en-US/docs/Web/HTML/Reference/Elements/th)
- [Learn: HTML table accessibility](/en-US/docs/Learn_web_development/Core/Structuring_content/Table_accessibility)
- [Learn: HTML table basics](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)