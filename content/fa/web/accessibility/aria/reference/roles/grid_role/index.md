---
title: "ARIA: grid role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: grid role"
short-title: grid
slug: Web/Accessibility/ARIA/Reference/Roles/grid_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#grid
sidebar: accessibilitysidebar
---

نقش `grid` برای یک ویجت است که شامل یک یا چند ردیف از سلول‌ها است. موقعیت هر سلول مهم است و می‌توان با استفاده از ورودی صفحه‌کلید روی آن تمرکز کرد.

## توضیحات

نقش `grid` یک ویجت ترکیبی است که شامل مجموعه‌ای از یک یا چند ردیف با یک یا چند سلول است که برخی یا همه سلول‌های موجود در شبکه با استفاده از روش‌های ناوبری دو بعدی، مانند کلیدهای جهت‌دار، قابل تمرکز هستند.

```html
<table role="grid" aria-labelledby="id-select-your-seat">
  <caption id="id-select-your-seat">
    صندلی خود را انتخاب کنید
  </caption>
  <tbody role="presentation">
    <tr role="presentation">
      <td></td>
      <th>ردیف A</th>
      <th>ردیف B</th>
    </tr>
    <tr>
      <th scope="row">راهرو 1</th>
      <td tabindex="0">
        <button id="btn-1a" tabindex="-1">1A</button>
      </td>
      <td tabindex="-1">
        <button id="btn-1b" tabindex="-1">1B</button>
      </td>
      <!-- ستون‌های بیشتر -->
    </tr>
    <tr>
      <th scope="row">راهرو 2</th>
      <td tabindex="-1">
        <button id="btn-2a" tabindex="-1">2A</button>
      </td>
      <td tabindex="-1">
        <button id="btn-2b" tabindex="-1">2B</button>
      </td>
      <!-- ستون‌های بیشتر -->
    </tr>
  </tbody>
</table>
```

یک ویجت شبکه شامل یک یا چند ردیف با یک یا چند سلول از محتوای تعاملی مرتبط موضوعی است. اگرچه به یک نمایش بصری خاص دلالت ندارد، اما به رابطه بین عناصر دلالت دارد. کاربردها به دو دسته تقسیم می‌شوند: ارائه اطلاعات جدولی (شبکه‌های داده) و گروه‌بندی ویجت‌های دیگر (شبکه‌های چیدمان). اگرچه هر دو شبکه داده و شبکه چیدمان از همان نقش‌ها، حالات و ویژگی‌های ARIA استفاده می‌کنند، تفاوت‌های موجود در محتوا و هدف آنها عواملی را آشکار می‌کند که در طراحی تعامل با صفحه‌کلید مهم هستند. برای جزئیات بیشتر به [راهنمای شیوه‌های تألیف ARIA](https://www.w3.org/WAI/ARIA/apg/patterns/grid/) مراجعه کنید.

عناصر سلول دارای نقش [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role) هستند، مگر اینکه سرستون ردیف یا ستون باشند، که در این صورت عناصر به ترتیب [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role) و [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) هستند. عناصر سلول باید متعلق به عناصری با نقش [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) باشند. ردیف‌ها را می‌توان با استفاده از نقش [`rowgroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role) گروه‌بندی کرد.

اگر شبکه به عنوان یک ویجت تعاملی استفاده می‌شود، [تعاملات صفحه‌کلید](#تعاملات-صفحه‌کلید) باید پیاده‌سازی شوند.

### نقش‌ها، حالات و ویژگی‌های مرتبط ARIA

#### نقش‌ها

- [treegrid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) (زیرمجموعه)
  - : اگر یک شبکه دارای ستون‌هایی باشد که می‌توانند باز یا بسته شوند، می‌توان از treegrid استفاده کرد.
- [row](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
  - : یک ردیف درون شبکه.
- [rowgroup](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role)
  - : یک گروه حاوی یک یا چند [row](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role).

#### حالات و ویژگی‌ها

- [aria-level](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level)
  - : سطح سلسله‌مراتبی شبکه را درون ساختارهای دیگر نشان می‌دهد.
- [aria-multiselectable](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable)
  - : اگر `aria-multiselectable` روی `true` تنظیم شود، چندین آیتم در شبکه قابل انتخاب هستند. مقدار پیش‌فرض `false` است.
- [aria-readonly](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly)
  - : اگر کاربر بتواند در شبکه حرکت کند اما نتواند مقدار یا مقادیر شبکه را تغییر دهد، [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly) باید روی `true` تنظیم شود. مقدار پیش‌فرض `false` است.

> [!NOTE]
> برای بسیاری از موارد استفاده، یک عنصر HTML {{HTMLElement('table')}} کافی است زیرا خود آن و عناصر جدول مختلف از قبل شامل بسیاری از نقش‌های ARIA هستند.

### تعاملات صفحه‌کلید

وقتی یک کاربر صفحه‌کلید با یک شبکه مواجه می‌شود، با استفاده از کلیدهای <kbd>چپ</kbd>، <kbd>راست</kbd>، <kbd>بالا</kbd> و <kbd>پایین</kbd> در ردیف‌ها و ستون‌ها حرکت می‌کند. برای فعال کردن مؤلفه تعاملی، از کلیدهای <kbd>return</kbd> و <kbd>space</kbd> استفاده می‌کنند.

| کلید                             | عمل                                                                                                                                                                                                                                                                                             |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <kbd>→</kbd>                     | تمرکز را یک سلول به سمت راست حرکت می‌دهد. به صورت اختیاری (شبکه‌های چیدمان)، اگر تمرکز روی سمت‌راست‌ترین سلول در ردیف باشد، تمرکز ممکن است به اولین سلول در ردیف بعدی حرکت کند. اگر تمرکز روی آخرین سلول در شبکه باشد، تمرکز حرکت نمی‌کند.                                                         |
| <kbd>←</kbd>                     | تمرکز را یک سلول به سمت چپ حرکت می‌دهد. به صورت اختیاری (شبکه‌های چیدمان)، اگر تمرکز روی سمت‌چپ‌ترین سلول در ردیف باشد، تمرکز ممکن است به آخرین سلول در ردیف قبلی حرکت کند. اگر تمرکز روی اولین سلول در شبکه باشد، تمرکز حرکت نمی‌کند.                                                            |
| <kbd>↓</kbd>                     | تمرکز را یک سلول به پایین حرکت می‌دهد. به صورت اختیاری (شبکه‌های چیدمان)، اگر تمرکز روی پایین‌ترین سلول در ستون باشد، تمرکز ممکن است به بالاترین سلول در ستون بعدی حرکت کند. اگر تمرکز روی آخرین سلول در شبکه باشد، تمرکز حرکت نمی‌کند.                                                         |
| <kbd>↑</kbd>                     | تمرکز را یک سلول به بالا حرکت می‌دهد. به صورت اختیاری (شبکه‌های چیدمان)، اگر تمرکز روی بالاترین سلول در ستون باشد، تمرکز ممکن است به پایین‌ترین سلول در ستون قبلی حرکت کند. اگر تمرکز روی اولین سلول در شبکه باشد، تمرکز حرکت نمی‌کند.                                                           |
| <kbd>Page Down</kbd>             | تمرکز را به تعداد ردیف‌های مشخص‌شده توسط نویسنده به پایین حرکت می‌دهد، معمولاً به گونه‌ای اسکرول می‌کند که پایین‌ترین ردیف در مجموعه ردیف‌های قابل مشاهده فعلی تبدیل به یکی از اولین ردیف‌های قابل مشاهده شود. اگر تمرکز در آخرین ردیف شبکه باشد، تمرکز حرکت نمی‌کند.                              |
| <kbd>Page Up</kbd>               | تمرکز را به تعداد ردیف‌های مشخص‌شده توسط نویسنده به بالا حرکت می‌دهد، معمولاً به گونه‌ای اسکرول می‌کند که بالاترین ردیف در مجموعه ردیف‌های قابل مشاهده فعلی تبدیل به یکی از آخرین ردیف‌های قابل مشاهده شود. اگر تمرکز در اولین ردیف شبکه باشد، تمرکز حرکت نمی‌کند.                               |
| <kbd>Home</kbd>                  | تمرکز را به اولین سلول در ردیفی که حاوی تمرکز است حرکت می‌دهد.                                                                                                                                                                                                                                  |
| <kbd>End</kbd>                   | تمرکز را به آخرین سلول در ردیفی که حاوی تمرکز است حرکت می‌دهد.                                                                                                                                                                                                                                  |
| <kbd>ctrl</kbd> + <kbd>Home</kbd> | تمرکز را به اولین سلول در اولین ردیف حرکت می‌دهد.                                                                                                                                                                                                                                                |
| <kbd>ctrl</kbd> + <kbd>End</kbd>  | تمرکز را به آخرین سلول در آخرین ردیف حرکت می‌دهد.                                                                                                                                                                                                                                                |

اگر سلول‌ها، ردیف‌ها یا ستون‌ها قابل انتخاب باشند، ترکیب‌های کلید زیر معمولاً استفاده می‌شوند:

| ترکیب کلید                         | عمل                                                                                                                                                                                                                                                         |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <kbd>ctrl</kbd> + <kbd>Space</kbd>  | ستونی که حاوی تمرکز است را انتخاب می‌کند.                                                                                                                                                                                                                   |
| <kbd>shift</kbd> + <kbd>Space</kbd> | ردیفی که حاوی تمرکز است را انتخاب می‌کند. اگر شبکه شامل یک ستون با چک‌باکس برای انتخاب ردیف‌ها باشد، این ترکیب کلید می‌تواند برای علامت زدن آن چک‌باکس حتی اگر تمرکز روی چک‌باکس نباشد استفاده شود.                                                          |
| <kbd>ctrl</kbd> + <kbd>A</kbd>      | تمام سلول‌ها را انتخاب می‌کند.                                                                                                                                                                                                                               |
| <kbd>shift</kbd> + <kbd>→</kbd>     | انتخاب را یک سلول به سمت راست گسترش می‌دهد.                                                                                                                                                                                                                 |
| <kbd>shift</kbd> + <kbd>←</kbd>     | انتخاب را یک سلول به سمت چپ گسترش می‌دهد.                                                                                                                                                                                                                   |
| <kbd>shift</kbd> + <kbd>↓</kbd>     | انتخاب را یک سلول به پایین گسترش می‌دهد.                                                                                                                                                                                                                    |
| <kbd>shift</kbd> + <kbd>↑</kbd>     | انتخاب را یک سلول به بالا گسترش می‌دهد.                                                                                                                                                                                                                     |

## مثال‌ها

### مثال تقویم

{{EmbedLiveSample("Calendar_example", "100%", "300")}}

#### HTML

```html
<table role="grid" aria-labelledby="calendarheader">
  <caption id="calendarheader">
    سپتامبر 2018
  </caption>
  <thead role="rowgroup">
    <tr role="row">
      <td></td>
      <th role="columnheader" aria-label="یکشنبه">ی</th>
      <th role="columnheader" aria-label="دوشنبه">د</th>
      <th role="columnheader" aria-label="سه‌شنبه">س</th>
      <th role="columnheader" aria-label="چهارشنبه">چ</th>
      <th role="columnheader" aria-label="پنجشنبه">پ</th>
      <th role="columnheader" aria-label="جمعه">ج</th>
      <th role="columnheader" aria-label="شنبه">ش</th>
    </tr>
  </thead>
  <tbody role="rowgroup">
    <tr role="row">
      <th scope="row" role="rowheader">هفته 1</th>
      <td>26</td>
      <td>27</td>
      <td>28</td>
      <td>29</td>
      <td>30</td>
      <td>31</td>
      <td role="gridcell" tabindex="-1">1</td>
    </tr>
    <tr role="row">
      <th scope="row" role="rowheader">هفته 2</th>
      <td role="gridcell" tabindex="-1">2</td>
      <td role="gridcell" tabindex="-1">3</td>
      <td role="gridcell" tabindex="-1">4</td>
      <td role="gridcell" tabindex="-1">5</td>
      <td role="gridcell" tabindex="-1">6</td>
      <td role="gridcell" tabindex="-1">7</td>
      <td role="gridcell" tabindex="-1">8</td>
    </tr>
    <tr role="row">
      <th scope="row" role="rowheader">هفته 3</th>
      <td role="gridcell" tabindex="-1">9</td>
      <td role="gridcell" tabindex="-1">10</td>
      <td role="gridcell" tabindex="-1">11</td>
      <td role="gridcell" tabindex="-1">12</td>
      <td role="gridcell" tabindex="-1">13</td>
      <td role="gridcell" tabindex="-1">14</td>
      <td role="gridcell" tabindex="-1">15</td>
    </tr>
    <tr role="row">
      <th scope="row" role="rowheader">هفته 4</th>
      <td role="gridcell" tabindex="-1">16</td>
      <td role="gridcell" tabindex="-1">17</td>
      <td role="gridcell" tabindex="-1">18</td>
      <td role="gridcell" tabindex="-1">19</td>
      <td role="gridcell" tabindex="-1">20</td>
      <td role="gridcell" tabindex="-1">21</td>
      <td role="gridcell" tabindex="-1">22</td>
    </tr>
    <tr role="row">
      <th scope="row" role="rowheader">هفته 5</th>
      <td role="gridcell" tabindex="-1">23</td>
      <td role="gridcell" tabindex="-1">24</td>
      <td role="gridcell" tabindex="-1">25</td>
      <td role="gridcell" tabindex="-1">26</td>
      <td role="gridcell" tabindex="-1">27</td>
      <td role="gridcell" tabindex="-1">28</td>
      <td role="gridcell" tabindex="-1">29</td>
    </tr>
    <tr role="row">
      <th scope="row" role="rowheader">هفته 6</th>
      <td role="gridcell" tabindex="-1">30</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
```

#### CSS

```css
table {
  margin: 0;
  border-collapse: collapse;
  font-variant-numeric: tabular-nums;
}

tbody th,
tbody td {
  padding: 5px;
}

tbody td {
  border: 1px solid black;
  text-align: right;
  color: #767676;
}

tbody td[role="gridcell"] {
  color: black;
}

tbody td[role="gridcell"]:hover,
tbody td[role="gridcell"]:focus {
  background-color: #f6f6f6;
  outline: 3px solid blue;
}
```

#### JavaScript

```js
const selectables = document.querySelectorAll('table td[role="gridcell"]');

selectables[0].setAttribute("tabindex", 0);

const trs = document.querySelectorAll("table tbody tr");
let rowIndex = 0;
let colIndex = 0;
let maxRow = trs.length - 1;
let maxCol = 0;

trs.forEach((row) => {
  row.querySelectorAll("td").forEach((el) => {
    el.dataset.row = rowIndex;
    el.dataset.col = colIndex;
    colIndex++;
  });
  if (colIndex > maxCol) {
    maxCol = colIndex - 1;
  }
  colIndex = 0;
  rowIndex++;
});

function moveTo(newRow, newCol) {
  const tgt = document.querySelector(
    `[data-row="${newRow}"][data-col="${newCol}"]`,
  );
  if (tgt?.getAttribute("role") !== "gridcell") {
    return false;
  }
  document.querySelectorAll("[role=gridcell]").forEach((el) => {
    el.setAttribute("tabindex", "-1");
  });
  tgt.setAttribute("tabindex", "0");
  tgt.focus();
  return true;
}

document.querySelector("table").addEventListener("keydown", (event) => {
  const col = parseInt(event.target.dataset.col, 10);
  const row = parseInt(event.target.dataset.row, 10);
  switch (event.key) {
    case "ArrowRight": {
      const newRow = col === 6 ? row + 1 : row;
      const newCol = col === 6 ? 0 : col + 1;
      moveTo(newRow, newCol);
      break;
    }
    case "ArrowLeft": {
      const newRow = col === 0 ? row - 1 : row;
      const newCol = col === 0 ? 6 : col - 1;
      moveTo(newRow, newCol);
      break;
    }
    case "ArrowDown":
      moveTo(row + 1, col);
      break;
    case "ArrowUp":
      moveTo(row - 1, col);
      break;
    case "Home": {
      if (event.ctrlKey) {
        let i = 0;
        let result;
        do {
          let j = 0;
          do {
            result = moveTo(i, j);
            j++;
          } while (!result);
          i++;
        } while (!result);
      } else {
        moveTo(row, 0);
      }
      break;
    }
    case "End": {
      if (event.ctrlKey) {
        let i = maxRow;
        let result;
        do {
          let j = maxCol;
          do {
            result = moveTo(i, j);
            j--;
          } while (!result);
          i--;
        } while (!result);
      } else {
        moveTo(
          row,
          document.querySelector(
            `[data-row="${event.target.dataset.row}"]:last-of-type`,
          ).dataset.col,
        );
      }
      break;
    }
    case "PageUp": {
      let i = 0;
      let result;
      do {
        result = moveTo(i, col);
        i++;
      } while (!result);
      break;
    }
    case "PageDown": {
      let i = maxRow;
      let result;
      do {
        result = moveTo(i, col);
        i--;
      } while (!result);
      break;
    }
    case "Enter": {
      console.log(event.target.textContent);
      break;
    }
  }
  event.preventDefault();
});
```

### مثال‌های بیشتر

- [مثال‌های شبکه داده](https://www.w3.org/WAI/ARIA/apg/example-index/grid/dataGrids.html)
- [مثال‌های شبکه‌های چیدمان](https://www.w3.org/WAI/ARIA/apg/example-index/grid/LayoutGrids.html)
- [آموزش W3C/WAI: جداول](https://www.w3.org/WAI/tutorials/tables/)

## نگرانی‌های دسترسی

حتی اگر استفاده از صفحه‌کلید به درستی پیاده‌سازی شود، برخی کاربران ممکن است از اینکه باید از کلیدهای جهت‌دار استفاده کنند آگاه نباشند. مطمئن شوید که قابلیت و تعامل مورد نیاز با استفاده از نقش grid به بهترین شکل ممکن انجام می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `composite` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)
- [نقش `table` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)
- [نقش `treegrid` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)
- [نقش `row` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [نقش `rowgroup` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role)
- [نقش `gridcell` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [نقش `rowheader` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [نقش `columnheader` ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- {{HTMLElement('table','عنصر HTML <code>&lt;table&gt;</code>')}}
- [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level)
- [`aria-multiselectable`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable)
- [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly)