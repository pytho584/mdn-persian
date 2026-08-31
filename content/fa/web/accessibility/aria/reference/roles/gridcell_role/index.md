---
title: "ARIA: gridcell role"
short-title: gridcell
slug: Web/Accessibility/ARIA/Reference/Roles/gridcell_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#gridcell
sidebar: accessibilitysidebar
translated_by: "n8n + AI"

---

نقش `gridcell` برای ایجاد یک سلول در [grid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [treegrid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) استفاده می‌شود. این نقش برای شبیه‌سازی عملکرد عنصر HTML {{HTMLElement('td')}} برای گروه‌بندی اطلاعات به صورت جدولی طراحی شده است.

```html
<div role="gridcell">Potato</div>
<div role="gridcell">Cabbage</div>
<div role="gridcell">Onion</div>
```

عناصری که `role="gridcell"` به آن‌ها اعمال شده است، باید فرزند عنصری با نقش [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) باشند.

```html
<div role="row">
  <div role="gridcell">Jane</div>
  <div role="gridcell">Smith</div>
  <div role="gridcell">496-619-5098</div>
  …
</div>
```

اولین قانون ARIA این است: اگر یک عنصر یا ویژگی HTML بومی دارای معناشناسی و رفتاری است که نیاز دارید، از آن استفاده کنید به جای اینکه عنصری را تغییر کاربری داده و ARIA اضافه کنید. به جای آن از عنصر HTML {{HTMLElement('td')}} استفاده کنید:

```html
<td>Potato</td>
<td>Cabbage</td>
<td>Onion</td>
```

## توضیحات

### gridcell‌های دارای ردیف‌ها و ستون‌هایی که به صورت پویا اضافه، پنهان یا حذف می‌شوند

هر عنصری که `role="gridcell"` به آن اعمال شده است، باید از ARIA برای توصیف ترتیب خود در گروه‌بندی جدولی استفاده کند، به شرطی که جدول، grid یا treegrid توانایی افزودن، پنهان کردن یا حذف پویای ردیف‌ها و/یا ستون‌ها را داشته باشد.

از [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) برای توصیف ترتیب یک `gridcell` در لیست ستون‌ها و از [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex) برای توصیف ترتیب یک gridcell در لیست ردیف‌ها استفاده کنید. از [`aria-colcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colcount) و [`aria-rowcount`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowcount) روی عنصر والد با [`role="grid"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) برای تعیین تعداد کل ستون‌ها یا ردیف‌ها استفاده کنید.

این کد نمونه یک گروه‌بندی جدولی از اطلاعات را نشان می‌دهد که در آن ستون‌های سوم و چهارم حذف شده‌اند. از [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex) برای توصیف موقعیت ردیف‌ها استفاده شده است و به کاربر فناوری کمکی امکان می‌دهد تشخیص دهد که برخی ردیف‌ها حذف شده‌اند:

```html
<div role="grid" aria-colcount="6">
  <div role="rowgroup">
    <div role="row">
      <div role="columnheader" aria-colindex="1">First name</div>
      <div role="columnheader" aria-colindex="2">Last name</div>
      <div role="columnheader" aria-colindex="5">City</div>
      <div role="columnheader" aria-colindex="6">Zip</div>
    </div>
  </div>
  <div role="rowgroup">
    <div role="row">
      <div role="gridcell" aria-colindex="1">Debra</div>
      <div role="gridcell" aria-colindex="2">Burks</div>
      <div role="gridcell" aria-colindex="5">New York</div>
      <div role="gridcell" aria-colindex="6">14127</div>
    </div>
  </div>
  …
</div>
```

### توصیف موقعیت gridcell‌ها زمانی که ساختار کلی ناشناخته است

در شرایطی که گروه‌بندی جدولی محتوا اطلاعاتی در مورد ستون‌ها و ردیف‌ها ارائه نمی‌دهد، موقعیت gridcell‌ها باید با استفاده از [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) به صورت برنامه‌نویسی توصیف شود. [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id)های ارائه شده برای `aria-describedby` باید با عناصر والد که به عنوان ردیف‌ها و ستون‌ها در نظر گرفته شده‌اند، مطابقت داشته باشند.

با ارجاع به عناصر والد با نقش‌های [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role) یا [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role) که از طریق `aria-describedby` به آن‌ها اعمال شده است، فناوری کمکی می‌تواند موقعیت و رابطه عنصر `gridcell` را با بقیه گروه‌بندی جدولی محتوا درک کند.

### Gridها و Treegridهای تعاملی

#### سلول‌های قابل ویرایش

هم عناصر `<td>` و هم عناصر با نقش `gridcell` می‌توانند قابل ویرایش شوند و عملکردی مشابه ویرایش یک صفحه گسترده را شبیه‌سازی کنند. این کار با اعمال ویژگی HTML [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) انجام می‌شود.

```html
<td contenteditable="true">Notes</td>

<div role="gridcell" contenteditable="true">Item cost</div>
```

`contenteditable` باعث می‌شود عنصری که به آن اعمال شده است با کلید <kbd>Tab</kbd> قابل فوکوس باشد. اگر یک gridcell به صورت شرطی به حالتی تغییر کند که ویرایش ممنوع است، [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly) را روی عنصر gridcell تغییر دهید.

#### سلول‌های قابل گسترش

در یک [treegrid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)، gridcell‌ها را می‌توان با تغییر ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) قابل گسترش کرد. توجه داشته باشید که اگر این ویژگی ارائه شود، فقط برای همان gridcell خاص اعمال می‌شود.

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- `grid`
  - : نشان می‌دهد که یک عنصر والد یک گروه‌بندی جدولی یا درختی از اطلاعات است.
- `row`
  - : برای نشان دادن اینکه `gridcell` بخشی از یک ردیف از گروه‌بندی جدولی اطلاعات است، الزامی است.
- `columnheader`
  - : مشخص می‌کند کدام عنصر سرستون مرتبط است.
- [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)
  - : موقعیت یک عنصر را نسبت به بقیه ستون‌های گروه‌بندی جدولی اطلاعات شناسایی می‌کند.
- `rowheader`
  - : مشخص می‌کند کدام عنصر سرردیف مرتبط است.
- [`aria-rowindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowindex)
  - : موقعیت یک عنصر را نسبت به بقیه ردیف‌های گروه‌بندی جدولی اطلاعات شناسایی می‌کند.

### مثال‌ها

مثال زیر یک گروه‌بندی جدولی از اطلاعات ایجاد می‌کند:

```html
<h3 id="table-title">Jovian gas giant planets</h3>
<div role="grid" aria-describedby="table-title">
  <div role="rowgroup">
    <div role="row">
      <div role="columnheader">Name</div>
      <div role="columnheader">Diameter (km)</div>
      <div role="columnheader">Length of day (hours)</div>
      <div role="columnheader">Distance from Sun (10<sup>6</sup>km)</div>
      <div role="columnheader">Number of moons</div>
    </div>
  </div>
  <div role="rowgroup">
    <div role="row">
      <div role="gridcell">Jupiter</div>
      <div role="gridcell">142,984</div>
      <div role="gridcell">9.9</div>
      <div role="gridcell">778.6</div>
      <div role="gridcell">67</div>
    </div>
  </div>
  <div role="rowgroup">
    <div role="row">
      <div role="gridcell">Saturn</div>
      <div role="gridcell">120,536</div>
      <div role="gridcell">10.7</div>
      <div role="gridcell">1433.5</div>
      <div role="gridcell">62</div>
    </div>
  </div>
</div>
```

## ملاحظات دسترسی‌پذیری

پشتیبانی از `gridcell` و برخی نقش‌ها و ویژگی‌های ARIA مرتبط با `gridcell` در فناوری‌های کمکی ضعیف است. در صورت امکان، از [نشانه‌گذاری جدول HTML](/en-US/docs/Web/HTML/Reference/Elements/table) به جای آن استفاده کنید.

## بهترین روش‌ها

اولین قانون ARIA این است: اگر یک عنصر یا ویژگی HTML بومی دارای معناشناسی و رفتاری است که نیاز دارید، از آن استفاده کنید به جای اینکه عنصری را تغییر کاربری داده و یک نقش، حالت یا ویژگی ARIA به آن اضافه کنید تا قابل دسترسی شود. بنابراین توصیه می‌شود به جای بازسازی فرم و عملکرد یک جدول با ARIA و جاوااسکریپت، از [نشانه‌گذاری جدول HTML بومی](/en-US/docs/Web/HTML/Reference/Elements/table) استفاده کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [عنصر Table](/en-US/docs/Web/HTML/Reference/Elements/table)
- [ARIA: نقش Grid](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
- [عنصر ردیف جدول](/en-US/docs/Web/HTML/Reference/Elements/tr)
- [ARIA: نقش row](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [ARIA: نقش rowgroup](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowgroup_role)
- [عنصر سرستون جدول](/en-US/docs/Web/HTML/Reference/Elements/th)
- [عنصر سلول داده جدول](/en-US/docs/Web/HTML/Reference/Elements/td)