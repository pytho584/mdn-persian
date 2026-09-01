---
title: "HTMLTableCellElement: scope property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLTableCellElement/scope"
---

---
title: "HTMLTableCellElement: scope property"
short-title: scope
slug: Web/API/HTMLTableCellElement/scope
page-type: web-api-instance-property
browser-compat: api.HTMLTableCellElement.scope
---

{{ APIRef("HTML DOM") }}

ویژگی **`scope`** در رابط {{domxref("HTMLTableCellElement")}} دامنهٔ یک سلول {{HTMLElement("th")}} را مشخص می‌کند.

سلول‌های سربرگ را می‌توان با استفاده از ویژگی `scope` طوری پیکربندی کرد که شامل یک ردیف یا ستون مشخص، یا شامل سلول‌هایی در گروه ردیفی فعلی باشند که هنوز دامنه‌ای برایشان تعیین نشده است (یعنی همان عنصر والد {{HTMLElement("thead")}}، {{HTMLElement("tbody")}} یا {{HTMLElement("tfoot")}}). اگر مقدار مشخصی برای `scope` در نظر گرفته نشود، سربرگ به‌طور مستقیم با سلول‌ها در این قالب مرتبط نمی‌شود. مقادیر مجاز برای `scope` عبارت‌اند از:

> [!NOTE]
> این ویژگی در مرورگرها اثر بصری ندارد؛ بلکه اطلاعات معنایی را اضافه می‌کند تا فناوری‌های کمکی مانند صفحه‌خوان‌ها بتوانند جدول را به شکلی منسجم‌تر ارائه کنند.

## مقدار

یکی از مقادیر زیر:

- `col`
  - : سلول سربرگ برای سلول‌های بعدی در همان ستون (یا ستون‌ها، اگر `colspan` نیز استفاده شده باشد) اعمال می‌شود، تا پایان ستون یا تا زمانی که یک `<th>` دیگر در همان ستون دامنهٔ جدیدی ایجاد کند.
- `colgroup`
  - : سلول سربرگ برای همهٔ سلول‌های موجود در گروه ستونی فعلی که دامنه‌ای برایشان اعمال نشده باشد، اعمال می‌شود. این مقدار فقط زمانی مجاز است که سلول در یک گروه ستونی قرار داشته باشد.
- `row`
  - : سلول سربرگ برای سلول‌های بعدی در همان ردیف (یا ردیف‌ها، اگر `rowspan` نیز استفاده شده باشد) اعمال می‌شود، تا پایان ردیف یا تا زمانی که یک `<th>` دیگر در همان ردیف دامنهٔ جدیدی ایجاد کند.
- `rowgroup`
  - : سلول سربرگ برای همهٔ سلول‌های موجود در گروه ردیفی فعلی که دامنه‌ای برایشان اعمال نشده باشد، اعمال می‌شود. این مقدار فقط زمانی مجاز است که سلول در یک گروه ردیفی قرار داشته باشد.
- رشتهٔ خالی (`""`)
  - : سلول سربرگ دامنهٔ از پیش تعیین شده‌ای ندارد و عامل کاربر (user agent) بر اساس نشانه‌های زمینه‌ای (contextual clues) دامنه را تعیین خواهد کرد.

## مثال‌ها

این مثال یک برچسب دامنه به همهٔ عناصر `th` درون `thead` اضافه می‌کند.

### HTML

```html
<table>
  <caption>
    Tallest Dams
  </caption>
  <thead>
    <tr>
      <td></td>
      <th>Dam</th>
      <th>Country</th>
      <th>Height</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1.</td>
      <th scope="row">Jinping-I Dam</th>
      <td>China</td>
      <td>305 m</td>
    </tr>
    <tr>
      <td>2.</td>
      <th scope="row">Nurek Dam</th>
      <td>Tajikistan</td>
      <td>300 m</td>
    </tr>
    <tr>
      <td>3.</td>
      <th scope="row">Lianghekou Dam</th>
      <td>China</td>
      <td>295 m</td>
    </tr>
    <tr>
      <td>4.</td>
      <th scope="row">Xiowan Dam</th>
      <td>China</td>
      <td>292 m</td>
    </tr>
    <tr>
      <td>5.</td>
      <th scope="row">Balhetan Dam</th>
      <td>China</td>
      <td>289 m</td>
    </tr>
    <tr>
      <td>6.</td>
      <th scope="row">Xiluodu Dam</th>
      <td>China</td>
      <td>285.5 m</td>
    </tr>
    <tr>
      <td>7.</td>
      <th scope="row">Grande-Dixence Dam</th>
      <td>Switzerland</td>
      <td>285 m</td>
    </tr>
  </tbody>
</table>
```

### JavaScript

```js
const thElements = document.querySelectorAll("thead th");
thElements.forEach((th) => {
  th.scope = "col";
});
```

### نتیجه

{{EmbedLiveSample("Examples", "100%", 220)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}