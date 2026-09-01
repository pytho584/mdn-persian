---
title: DataTransfer
slug: Web/API/DataTransfer
page-type: web-api-interface
browser-compat: api.DataTransfer
---

{{APIRef("HTML Drag and Drop API")}}

شیء **`DataTransfer`** برای نگهداری هر داده‌ای که بین زمینه‌ها منتقل می‌شود، مانند یک عملیات کشیدن و رها کردن (drag and drop) یا خواندن/نوشتن کلیپ‌بورد، استفاده می‌شود. این شیء ممکن است یک یا چند آیتم داده را نگه دارد که هر یک از یک یا چند نوع داده تشکیل شده است.

`DataTransfer` در ابتدا به‌عنوان ویژگی {{domxref("DragEvent.dataTransfer")}} برای [API کشیدن و رها کردن HTML](/en-US/docs/Web/API/HTML_Drag_and_Drop_API) طراحی شد و همچنان در بخش کشیدن و رها کردن HTML تعریف می‌شود، اما اکنون APIهای دیگری مانند {{domxref("ClipboardEvent.clipboardData")}} و {{domxref("InputEvent.dataTransfer")}} نیز از آن استفاده می‌کنند. با این حال، سایر APIها فقط از بخش‌های خاصی از رابط آن استفاده می‌کنند و ویژگی‌هایی مانند `dropEffect` را نادیده می‌گیرند. مستندات `DataTransfer` عمدتاً کاربرد آن را در عملیات کشیدن و رها کردن بررسی خواهند کرد؛ برای کاربرد `DataTransfer` در آن زمینه‌ها باید به مستندات سایر APIها مراجعه کنید.

## سازنده

- {{domxref("DataTransfer.DataTransfer","DataTransfer()")}}
  - : یک شیء جدید `DataTransfer` ایجاد کرده و آن را برمی‌گرداند.

## ویژگی‌های نمونه

- {{domxref("DataTransfer.dropEffect")}}
  - : نوع عملیات کشیدن و رها کردن انتخاب‌شده را دریافت می‌کند یا عملیات را به نوع جدیدی تنظیم می‌کند. مقدار باید `none`، `copy`، `link` یا `move` باشد.
- {{domxref("DataTransfer.effectAllowed")}}
  - : همه انواع عملیات‌های ممکن را فراهم می‌کند. باید یکی از مقادیر `none`، `copy`، `copyLink`، `copyMove`، `link`، `linkMove`، `move`، `all` یا `uninitialized` باشد.
- {{domxref("DataTransfer.files")}} {{ReadOnlyInline}}
  - : فهرستی از تمام فایل‌های محلی موجود در انتقال داده را در بر می‌گیرد. اگر عملیات کشیدن شامل کشیدن فایل‌ها نباشد، این ویژگی یک فهرست خالی است.
- {{domxref("DataTransfer.items")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("DataTransferItemList")}} را فراهم می‌کند که فهرستی از تمام داده‌های کشیدن است.
- {{domxref("DataTransfer.types")}} {{ReadOnlyInline}}
  - : آرایه‌ای از رشته‌ها که قالب‌های تنظیم‌شده در رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} را ارائه می‌دهد.

## روش‌های نمونه

- {{domxref("DataTransfer.addElement()")}} {{experimental_inline}} {{non-standard_inline}}
  - : منبع کشیدن را برای عنصر مشخص‌شده تنظیم می‌کند. این عنصر، عنصری خواهد بود که رویدادهای {{domxref("HTMLElement/drag_event", "drag")}} و {{domxref("HTMLElement/dragend_event", "dragend")}} روی آن فعال می‌شوند، نه هدف پیش‌فرض (گره‌ای که کشیده شده است). مخصوص فایرفاکس.
- {{domxref("DataTransfer.clearData()")}}
  - : داده‌های مرتبط با یک نوع مشخص را حذف می‌کند. آرگومان type اختیاری است. اگر type خالی یا مشخص نشده باشد، داده‌های مرتبط با همه انواع حذف می‌شوند. اگر داده‌های نوع مشخص‌شده وجود نداشته باشد یا انتقال داده حاوی داده‌ای نباشد، این روش هیچ تأثیری نخواهد داشت.
- {{domxref("DataTransfer.getData()")}}
  - : داده‌های یک نوع مشخص را بازیابی می‌کند، یا اگر داده‌های آن نوع وجود نداشته باشد یا انتقال داده حاوی داده‌ای نباشد، یک رشته خالی برمی‌گرداند.
- {{domxref("DataTransfer.setData()")}}
  - : داده‌های یک نوع مشخص را تنظیم می‌کند. اگر داده‌های آن نوع وجود نداشته باشد، در انتها اضافه می‌شود، به طوری که آخرین آیتم در فهرست types قالب جدید خواهد بود. اگر داده‌های آن نوع از قبل وجود داشته باشد، داده‌های موجود در همان موقعیت جایگزین می‌شوند.
- {{domxref("DataTransfer.setDragImage()")}}
  - : تصویری را که برای کشیدن استفاده می‌شود تنظیم می‌کند، در صورتی که تصویر سفارشی مورد نظر باشد.

## مثال‌ها

هر روش و ویژگی فهرست‌شده در این سند، صفحه مرجع مخصوص به خود را دارد و هر صفحه مرجع یا مستقیماً شامل نمونه‌ای از این رابط است یا پیوندی به یک مثال دارد.

### خواندن داده‌ها در رویداد جایگذاری یا رها کردن

در مثال زیر، یک {{htmlelement("form")}} داریم که شامل سه نوع مختلف ورودی متنی است: یک عنصر {{htmlelement("input")}} متنی، یک عنصر {{htmlelement("textarea")}} و یک عنصر {{htmlelement("div")}} با ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) که روی `true` تنظیم شده است. کاربر می‌تواند متن را در هر یک از این عناصر جایگذاری یا رها کند و داده‌های موجود در شیء {{domxref("ClipboardEvent.clipboardData")}} یا {{domxref("DragEvent.dataTransfer")}} نمایش داده خواهند شد.

#### HTML

```html
<form>
  <fieldset>
    <legend>&lt;input /></legend>
    <input type="text" />
    <table class="center">
      <tbody>
        <tr>
          <th scope="row">Operation type</th>
          <td></td>
        </tr>
        <tr>
          <th scope="row">Content type</th>
          <td></td>
        </tr>
      </tbody>
    </table>
  </fieldset>
  <fieldset>
    <legend>&lt;textarea /></legend>
    <textarea></textarea>
    <table class="center">
      <tbody>
        <tr>
          <th scope="row">Operation type</th>
          <td></td>
        </tr>
        <tr>
          <th scope="row">Content type</th>
          <td></td>
        </tr>
      </tbody>
    </table>
  </fieldset>
  <fieldset>
    <legend>&lt;div contenteditable /></legend>
    <div contenteditable></div>
    <table class="center">
      <tbody>
        <tr>
          <th scope="row">Operation type</th>
          <td></td>
        </tr>
        <tr>
          <th scope="row">Content type</th>
          <td></td>
        </tr>
      </tbody>
    </table>
  </fieldset>
  <p class="center">
    <input type="reset" />
  </p>
</form>
```

#### CSS

```css
.center {
  text-align: center;
}

form > fieldset > * {
  vertical-align: top;
}
form input,
form textarea,
form [contenteditable] {
  min-width: 15rem;
  padding: 0.25rem;
}
[contenteditable] {
  appearance: textfield;
  display: inline-block;
  min-height: 1rem;
  border: 1px solid;
}

form table {
  display: inline-table;
}
table ol {
  text-align: left;
}
```

#### JavaScript

```js
const form = document.querySelector("form");

function displayData(event) {
  if (event.type === "drop") event.preventDefault();

  const cells = event.target.nextElementSibling.querySelectorAll("td");
  cells[0].textContent = event.type;
  const transfer = event.clipboardData || event.dataTransfer;
  const ol = document.createElement("ol");
  cells[1].textContent = "";
  cells[1].appendChild(ol);
  for (const item of transfer.items) {
    const li = document.createElement("li");
    li.textContent = `${item.kind} ${item.type}`;
    ol.appendChild(li);
  }
}

form.addEventListener("paste", displayData);
form.addEventListener("drop", displayData);
form.addEventListener("reset", () => {
  for (const cell of form.querySelectorAll("[contenteditable], td")) {
    cell.textContent = "";
  }
});
```

#### نتیجه

{{EmbedLiveSample("Reading the data in a paste or drop event", "", 400, , , , , "allow-forms")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [Drag and drop](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [Drag Operations](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [Working with the drag data store](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)