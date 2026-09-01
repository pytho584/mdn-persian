---
title: FileList
slug: Web/API/FileList
page-type: web-api-interface
browser-compat: api.FileList
---

{{APIRef("File API")}}{{AvailableInWorkers}}

رابطه‌ی **`FileList`**، شیءای از این نوع را نمایش می‌دهد که توسط ویژگی `files` عنصر HTML {{HTMLElement("input")}} بازگردانده می‌شود؛ این امکان را به شما می‌دهد تا به فهرست فایل‌های انتخاب‌شده با عنصر `<input type="file">` دسترسی داشته باشید. همچنین برای فهرست فایل‌هایی که هنگام استفاده از API کشیدن و رها کردن (drag and drop) در محتوای وب رها می‌شوند نیز استفاده می‌شود؛ برای جزئیات این کاربرد، شیء {{domxref("DataTransfer")}} را ببینید.

همه‌ی گره‌های عنصر `<input>` دارای ویژگی `files` از نوع `FileList` هستند که دسترسی به موارد موجود در این فهرست را فراهم می‌کند. برای مثال، اگر HTML شامل ورودی فایل زیر باشد:

```html
<input id="fileItem" type="file" />
```

خط کد زیر، اولین فایل را از فهرست فایل‌های گره به‌صورت یک شیء {{domxref("File")}} دریافت می‌کند:

```js
const file = document.getElementById("fileItem").files[0];
```

این رابط، [تلاشی برای ایجاد یک فهرست غیرقابل تغییر](https://stackoverflow.com/questions/74630989/why-use-domstringlist-rather-than-an-array/74641156#74641156) بود و فقط برای این پشتیبانی می‌شود که کدهایی که قبلاً از آن استفاده می‌کنند دچار مشکل نشوند. APIهای مدرن، ساختارهای فهرستی را با استفاده از انواع مبتنی بر [آرایه‌های](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) جاوااسکریپت نمایش می‌دهند، بنابراین بسیاری از متدهای آرایه در دسترس هستند و در عین حال معنای دیگری را بر استفاده از آن‌ها تحمیل می‌کنند (مانند فقط‌خواندنی کردن موارد آن‌ها).

این دلایل تاریخی به این معنا نیست که شما به‌عنوان یک توسعه‌دهنده باید از `FileList` اجتناب کنید. شما خودتان اشیاء `FileList` را نمی‌سازید، بلکه آن‌ها را از APIهایی مانند {{domxref("HTMLInputElement.files")}} دریافت می‌کنید و این APIها منسوخ نشده‌اند. با این حال، مراقب تفاوت‌های معنایی آن با یک آرایه‌ی واقعی باشید.

## ویژگی‌های نمونه

- {{DOMxRef("FileList.length", "length")}} {{ReadOnlyInline}}
  - : یک مقدار فقط‌خواندنی که تعداد فایل‌های موجود در فهرست را نشان می‌دهد.

## متدهای نمونه

- {{DOMxRef("FileList.item()", "item()")}}
  - : یک شیء {{domxref("File")}} را بازمی‌گرداند که نشان‌دهنده‌ی فایل در فهرست فایل‌ها با ایندکس مشخص‌شده است.

## مثال

### ثبت نام فایل‌ها

در این مثال، نام همه‌ی فایل‌های انتخاب‌شده توسط کاربر را ثبت می‌کنیم.

#### HTML

```html
<input id="myfiles" multiple type="file" />
<pre class="output">Selected files:</pre>
```

#### CSS

```css
.output {
  overflow: scroll;
  margin: 1rem 0;
  height: 200px;
}
```

#### JavaScript

```js
const output = document.querySelector(".output");
const fileInput = document.querySelector("#myfiles");

fileInput.addEventListener("change", () => {
  for (const file of fileInput.files) {
    output.innerText += `\n${file.name}`;
  }
});
```

#### نتیجه

{{EmbedLiveSample("Logging filenames")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)
- {{domxref("File")}}
- {{domxref("FileReader")}}