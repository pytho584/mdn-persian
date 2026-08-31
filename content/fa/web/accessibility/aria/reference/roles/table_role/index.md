---
title: "ARIA: table role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: table role"
short-title: table
slug: Web/Accessibility/ARIA/Reference/Roles/table_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#table
  - https://www.w3.org/WAI/ARIA/apg/patterns/table/examples/table/
sidebar: accessibilitysidebar
---

مقدار `table` از ویژگی `role` در ARIA، عنصری که این نقش را دارد را به عنوان یک ساختار جدول غیرتعاملی شامل داده‌های مرتب‌شده در سطرها و ستون‌ها، مشابه عنصر HTML بومی {{HTMLElement('table')}}، شناسایی می‌کند.

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

## توضیحات

یک عنصر با `role="table"` یک ساختار جدولی ایستا با سطرهایی شامل سلول‌ها است. سلول‌ها قابل تمرکز یا انتخاب نیستند، اگرچه ویجت‌های داخل سلول‌های جداگانه جدول می‌توانند تعاملی باشند. استفاده از عنصر HTML بومی {{HTMLElement('table')}} تا حد امکان به شدت توصیه می‌شود.

> [!WARNING]
> اگر یک جدول حالت انتخاب را حفظ می‌کند، ناوبری دو بعدی دارد، یا به کاربر اجازه می‌دهد ترتیب سلول‌ها را تغییر دهد، به جای آن از [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) استفاده کنید.

برای ایجاد یک جدول ARIA، `role="table"` را به عنصر ظرف اضافه کنید. درون آن ظرف، هر سطر دارای `role="row"` است و شامل سلول‌های فرزند می‌شود. هر سلول یکی از نقش‌های `columnheader`، `rowheader` یا `cell` را دارد. سطرها می‌توانند فرزندان جدول یا درون یک `rowgroup` باشند.

عنوان جدول را می‌توان از طریق [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) یا [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) تعریف کرد. تمام عناصر جدول معنایی دیگر، مانند {{HTMLElement('tbody')}}، {{HTMLElement('thead')}}، {{HTMLElement('tr')}}، {{HTMLElement('th')}} و {{HTMLElement('td')}}، باید از طریق نقش‌های مرتبط مانند `rowgroup`، `row`، `columnheader` و `cell` اضافه شوند.

اگر جدول شامل ستون‌ها یا سطرهای قابل مرتب‌سازی است، ویژگی [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort) باید روی عنصر سلول سرستون (نه خود جدول) اضافه شود. اگر هر سطر یا ستونی پنهان است، باید [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) یا [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount) به ترتیب برای نشان دادن تعداد کل ستون‌ها یا سطرها، همراه با [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) یا [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) روی هر سلول گنجانده شود. [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) یا [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) به ترتیب به موقعیت یک سلول درون سطر یا ستون تنظیم می‌شود. اگر جدول شامل سلول‌هایی است که چندین سطر یا چندین ستون را پوشش می‌دهند، باید [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan) یا [`aria-colspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan) نیز گنجانده شود. توجه داشته باشید که استفاده از عنصر {{HTMLElement('table')}} به همراه تمام عناصر و ویژگی‌های معنایی مرتبط که توسط تمام فناوری‌های کمکی پشتیبانی می‌شوند، بسیار ساده‌تر است.

برای ایجاد یک ویجت تعاملی که ساختار جدولی دارد، به جای آن از الگوی `grid` استفاده کنید. اگر تعامل حالت انتخاب سلول‌های جداگانه را فراهم می‌کند، ناوبری از چپ به راست و بالا به پایین ارائه می‌شود، یا اگر رابط کاربری امکان تغییر ترتیب سلول‌ها یا تغییر ترتیب سلول‌های جداگانه مانند کشیدن و رها کردن را فراهم می‌کند، به جای آن از [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) استفاده کنید.

> [!NOTE]
> استفاده از عنصر جدول HTML بومی تا حد امکان به شدت توصیه می‌شود.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- `role="rowgroup"`
  - : یک فرزند اختیاری جدول، گروه سطر یک گروه از سطرها را محصور می‌کند، مشابه {{HTMLElement('thead')}}، {{HTMLElement('tbody')}} و {{HTMLElement('tfoot')}}.
- [`role="row"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
  - : یک سطر درون جدول، و به صورت اختیاری درون یک rowgroup که شامل یک یا چند سلول، سرستون‌های ستون یا سرستون‌های سطر است.
- ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
  - : مقدار آن id عنصری است که به عنوان توضیحی برای جدول عمل می‌کند.
- ویژگی [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یک نام قابل دسترس برای جدول فراهم می‌کند.
- ویژگی [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount)
  - : این ویژگی فقط زمانی لازم است که ستون‌ها همیشه در DOM حضور نداشته باشند. این یک نشانه صریح از تعداد ستون‌ها در جدول کامل ارائه می‌دهد. مقدار را به تعداد کل ستون‌های جدول کامل تنظیم کنید. اگر نامشخص است، `aria-colcount="-1"` را تنظیم کنید.
- ویژگی [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount)
  - : این ویژگی فقط زمانی لازم است که سطرها همیشه در DOM حضور نداشته باشند، مانند جداول قابل پیمایش که سطرها را برای به حداقل رساندن تعداد گره‌های DOM دوباره استفاده می‌کنند. این یک نشانه صریح از تعداد سطرها در جدول کامل ارائه می‌دهد. مقدار را به تعداد کل سطرهای جدول کامل تنظیم کنید. اگر نامشخص است، `aria-rowcount="-1"` را تنظیم کنید.

### تعاملات صفحه کلید

هیچ‌کدام.

### ویژگی‌های JavaScript مورد نیاز

هیچ‌کدام. برای ستون‌های قابل مرتب‌سازی، به نقش aria [columnheader](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) مراجعه کنید.

> [!NOTE]
> اولین قانون استفاده از ARIA این است که اگر می‌توانید از یک ویژگی بومی با معناشناسی و رفتاری که نیاز دارید استفاده کنید، به جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای دسترس‌پذیر کردن آن، این کار را انجام دهید. تا حد امکان از عنصر HTML {{HTMLElement('table')}} به جای نقش جدول ARIA استفاده کنید.

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

مثال بالا بخشی از یک جدول است. در حالی که جدول کامل 81 ورودی دارد، همانطور که توسط ویژگی [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount) نشان داده شده است، تنها چهار مورد در حال حاضر قابل مشاهده هستند. ستون‌ها قابل مرتب‌سازی هستند، اما در حال حاضر مرتب نشده‌اند، همانطور که توسط ویژگی [`aria-sort`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-sort) روی سرستون‌های ستون نشان داده شده است.

## بهترین روش‌ها

فقط از {{HTMLElement('table')}}، {{HTMLElement('tbody')}}، {{HTMLElement('thead')}}، {{HTMLElement('tr')}}، {{HTMLElement('th')}}، {{HTMLElement('td')}} و غیره برای ساختار جدول داده استفاده کنید. می‌توانید این نقش‌های ARIA را اضافه کنید تا در صورت حذف معناشناسی بومی جدول، مانند با CSS، دسترس‌پذیری تضمین شود. یک مورد استفاده مرتبط برای نقش جدول ARIA زمانی است که ویژگی display CSS معناشناسی بومی جدول را لغو می‌کند، مانند `display: grid`. در این مورد، می‌توانید از نقش‌های جدول ARIA برای افزودن مجدد معناشناسی استفاده کنید.

## Specifications

{{Specifications}}

## همچنین ببینید

- [Learn: HTML table accessibility](/en-US/docs/Learn_web_development/Core/Structuring_content/Table_accessibility)
- [Learn: HTML table basics](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- [ARIA: `grid` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)