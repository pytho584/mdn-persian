```
---
title: "ARIA: row role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: row role"
short-title: row
slug: Web/Accessibility/ARIA/Reference/Roles/row_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#row
  - https://www.w3.org/WAI/ARIA/apg/patterns/table/examples/table/
sidebar: accessibilitysidebar
---

یک عنصر با `role="row"` یک ردیف از خانه‌ها در یک ساختار جدولی است. یک ردیف شامل یک یا چند خانه، خانه‌های شبکه‌ای یا سرستون‌های ستون، و احتمالاً یک سرستون ردیف، درون یک [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)، [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) و به‌صورت اختیاری درون یک [`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) است.

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

عنصر با `role="row"` یک ردیف درون یک [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)، [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) و به‌صورت اختیاری درون یک [`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) است که شامل یک یا چند عنصر [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)، [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) یا [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role) در یک ساختار جدولی ایستا است. استفاده از عنصر بومی [HTML `<tr>`](/en-US/docs/Web/HTML/Reference/Elements/tr) در صورت امکان به‌شدت توصیه می‌شود.

برای ایجاد یک ردیف ARIA، `role="row"` را به عنصر ظرف اضافه کنید. آن ردیف باید درون یک grid، table یا treegrid قرار گیرد. یک گروه از ردیف‌ها می‌توانند مستقیماً درون یک grid، table یا treegrid قرار گیرند، یا درون یک rowgroup در یکی از آن ظرف‌ها. هر ردیف شامل سلول‌های فرزند است. این سلول‌ها بسته به اینکه سرستون ستون یا ردیف باشند، یا سلول‌های شبکه‌ای یا معمولی باشند، می‌توانند از انواع مختلفی باشند.

یک ردیف می‌تواند شامل تعدادی ویژگی باشد که نقش ردیف را روشن می‌کنند، از جمله [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)، [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level)، [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) و [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected).

اگر ردیف درون یک treegrid باشد، ردیف‌ها می‌توانند ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) را شامل شوند و از این ویژگی برای نشان دادن وضعیت فعلی استفاده کنند. این مورد برای یک table یا grid معمولی صدق نمی‌کند، جایی که ویژگی `aria-expanded` وجود ندارد.

برای ایجاد یک ویجت تعاملی که ساختار جدولی دارد، به جای آن از الگوی grid استفاده کنید. اگر تعامل وضعیت انتخاب سلول‌های منفرد را فراهم کند، اگر پیمایش از چپ به راست و از بالا به پایین ارائه شود، یا اگر رابط کاربری امکان بازچینی ترتیب سلول‌ها یا تغییر ترتیب سلول‌های منفرد را به روش دیگری مانند کشیدن و رها کردن فراهم کند، به جای آن از [grid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [treegrid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) استفاده کنید.

> [!NOTE]
> استفاده از عنصر جدول HTML بومی ({{HTMLElement('table')}}) به‌همراه عنصر ردیف جدول ({{HTMLElement('tr')}}) در صورت امکان به‌شدت توصیه می‌شود.

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

#### نقش‌های زمینه‌ای

- [role="rowgroup"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role)
  - : یک والد ردیف اختیاری زمینه‌ای، که رابطه بین ردیف‌های فرزند را برقرار می‌کند. معادل ساختاری عناصر thead، tfoot و tbody در یک عنصر جدول HTML است.
- [role="table"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)
  - : یکی از سه زمینه ممکن (به‌همراه grid و treegrid) که در آن یک ردیف یافت می‌شود، ردیف را به‌عنوان بخشی از یک ساختار جدولی غیرتعاملی شناسایی می‌کند که شامل داده‌های چیده‌شده در سطرها و ستون‌ها است، مشابه عنصر HTML بومی {{HTMLElement('table')}}.
- [role="grid"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
  - : یکی از سه زمینه ممکن (به‌همراه table و treegrid) که در آن یک ردیف یافت می‌شود، ردیف را به‌عنوان بخشی از یک ساختار جدولی تعاملی شناسایی می‌کند که شامل داده‌های چیده‌شده در سطرها و ستون‌ها است، مشابه عنصر HTML بومی {{HTMLElement('table')}}.
- [role="treegrid"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)
  - : شبیه به grid، اما با ردیف‌هایی که می‌توانند به همان روش درخت گسترش یابند و جمع شوند.

#### نقش‌های فرزند

- [role="cell"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)
  - : یک سلول در یک ردیف درون یک ظرف جدولی.
- [role="gridcell"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
  - : یک سلول در یک ردیف درون یک grid یا treegrid.
- [role="columnheader"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
  - : یک سلول سرستون که معادل ساختاری عنصر HTML {{HTMLElement('th')}} با دامنه ستون است ({{HTMLElement('tr', '<code>&lt;tr scope="col"&gt;</code>')}}). برخلاف یک سلول ساده، نقش columnheader رابطه بین آن و همه سلول‌های ستون مربوطه را برقرار می‌کند.
- [role="rowheader"](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
  - : یک سلول سرستون که معادل ساختاری عنصر HTML {{HTMLElement('th')}} با دامنه ردیف است ({{HTMLElement('tr', '<code>&lt;tr scope="row"&gt;</code>')}}). برخلاف یک سلول ساده، نقش rowheader رابطه بین آن و همه سلول‌های ردیف مربوطه را برقرار می‌کند.

#### حالت‌ها و ویژگی‌ها

- [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) حالت
  - : ویژگی `aria-expanded` که وضعیت ردیف را تعریف می‌کند، می‌تواند یکی از سه مقدار را بگیرد یا حذف شود:
    - `aria-expanded="true"`: ردیف در حال حاضر گسترش یافته است.
    - `aria-expanded="false"`: ردیف در حال حاضر جمع شده است.
    - `aria-expanded="undefined"` یا ویژگی وجود نداشته باشد: ردیف نه قابل گسترش است و نه قابل جمع‌شدن.

    اگر عنصر دارای ویژگی `aria-expanded` گسترش یک ظرف گروه‌بندی دیگر را کنترل کند که «متعلق به» عنصر نیست، نویسنده **باید** با استفاده از ویژگی `aria-controls` به آن ظرف اشاره کند.

- [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) حالت
  - : فقط زمانی مرتبط است که ردیف در یک ظرف تعاملی، مانند grid یا treegrid باشد، اما اگر ردیف در یک table باشد مرتبط نیست. ویژگی `aria-selected` می‌تواند یکی از سه مقدار را بگیرد یا حذف شود:
    - `aria-selected="true"`: ردیف در حال حاضر انتخاب شده است.
    - `aria-selected="false"`: ردیف در حال حاضر انتخاب نشده است.
    - `aria-selected="undefined"` یا ویژگی وجود نداشته باشد: ردیف قابل انتخاب نیست.

- [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) ویژگی
  - : ویژگی `aria-colindex` تنها زمانی لازم است که ستون‌ها از DOM پنهان شده باشند. معمولاً بر روی فرزندان ردیف قرار می‌گیرد، نه بر روی خود ردیف. اگر ستون‌های نمایش‌داده‌شده پیوسته باشند، می‌توان آن را روی ردیف قرار داد.

    این ویژگی یک عدد صحیح بین 1 و تعداد کل ستون‌های موجود در table، grid یا treegrid را به‌عنوان مقدار می‌پذیرد. وقتی روی ردیف قرار می‌گیرد، `aria-colindex` شاخص ستون یا موقعیت یک عنصر را نسبت به تعداد کل ستون‌های درون یک ردیف تعیین می‌کند. برای مثال، در یک جدول با ۱۵ ستون، و ستون‌های ۴، ۵ و ۶ در DOM قرار دارند، `aria-colindex="4"` می‌تواند روی هر ردیف تنظیم شود.

    اگر مجموعه ستون‌هایی که در DOM وجود دارند **پیوسته** نباشد، یا اگر سلول‌هایی وجود داشته باشند که بیش از یک ردیف یا ستون را پوشش می‌دهند، به جای خود ردیف، `aria-colindex` را روی همه فرزندان هر ردیف قرار دهید.

    اگر همه ستون‌ها در DOM باشند، این ویژگی ضروری نیست.

- [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) ویژگی
  - : ویژگی `aria-rowindex` تنها زمانی لازم است که ردیف‌ها از DOM پنهان شده باشند، تا مشخص کند کدام ردیف، در فهرست کل ردیف‌ها، در حال خوانده شدن است. این ویژگی که با یک مقدار یکتا روی هر ردیف قرار می‌گیرد، یک عدد صحیح بین 1 و تعداد کل ردیف‌های موجود در table، grid یا treegrid را به‌عنوان مقدار می‌پذیرد و موقعیت یا شاخص هر ردیف را نشان می‌دهد. برای مثال، اگر یک جدول ۱۵۰۰ ردیف داشته باشد، اما فقط سربرگ و ردیف‌های ۴۷ و ۵۲ در DOM باشند، `aria-rowindex="1"` روی ردیف سربرگ، و `aria-rowindex="47"` و `aria-rowindex="52"` به ترتیب روی ردیف ۴۷ و ۵۲ تنظیم می‌شوند.

    اگر همه ردیف‌ها در DOM حضور داشته باشند، این ویژگی ضروری نیست.

### تعاملات صفحه‌کلید

هیچ.

### ویژگی‌های جاوااسکریپت مورد نیاز

هیچ. برای ستون‌های قابل مرتب‌سازی، نقش aria [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) را ببینید.

> [!NOTE]
> اولین قانون استفاده از ARIA این است که اگر می‌توانید از یک ویژگی بومی با معنا و رفتاری که از قبل در آن تعبیه شده استفاده کنید، به جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای قابل‌دسترس کردن آن، این کار را انجام دهید. در صورت امکان به جای نقش table از عنصر HTML {{HTMLElement('table')}} استفاده کنید.

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

نمونه بالا یک جدول ARIA غیرمعنایی با پنج ردیف از ۸۱ ردیف موجود در DOM است: یک ردیف در سربرگ جدول و چهار ردیف در بدنه جدول. ردیف سربرگ، که به‌تنهایی در یک rowgroup سربرگ قرار دارد، دارای دو سرستون ستون است. ستون‌ها قابل مرتب‌سازی هستند، اما در حال حاضر مرتب نشده‌اند، همانطور که ویژگی `aria-sort` نشان می‌دهد. بدنه جدول در یک rowgroup جداگانه قرار دارد و در حال حاضر چهار ردیف در DOM وجود دارد. از آنجا که همه ردیف‌ها در DOM نیستند، ویژگی `aria-rowindex` را روی هر ردیف قرار داده‌ایم.

## بهترین روش‌ها

برای ساختار جدول داده فقط از {{HTMLElement('table')}}، {{HTMLElement('tbody')}}، {{HTMLElement('thead')}}، {{HTMLElement('tr')}}، {{HTMLElement('th')}}، {{HTMLElement('td')}} و غیره استفاده کنید. می‌توانید این نقش‌های ARIA را اضافه کنید تا در صورت حذف معنای بومی جدول، مثلاً با CSS، دسترس‌پذیری تضمین شود. یک مورد استفاده مرتبط برای نقش table آرایه‌ای زمانی است که معنای بومی جدول توسط ویژگی display در CSS لغو شود، مانند display: grid. در این حالت، می‌توانید از نقش‌های ARIA جدول برای بازگرداندن معنا استفاده کنید.

```html
<table
  role="table"
  aria-label="Semantic Elements"
  aria-describedby="semantic_elements_table_desc"
  aria-rowcount="