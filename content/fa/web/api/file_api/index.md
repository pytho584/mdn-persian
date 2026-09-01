---
title: File API
slug: Web/API/File_API
page-type: web-api-overview
spec-urls: https://w3c.github.io/FileAPI/
---

{{DefaultAPISidebar("File API")}}{{AvailableInWorkers}}

## مفهوم و کاربرد

File API به برنامه‌های وب امکان می‌دهد تا به فایل‌ها و محتوای آن‌ها دسترسی داشته باشند.

برنامه‌های وب می‌توانند زمانی به فایل‌ها دسترسی پیدا کنند که کاربر آن‌ها را در دسترس قرار دهد، چه با استفاده از [یک عنصر `<input>` فایل](/en-US/docs/Web/HTML/Reference/Elements/input/file) و چه [از طریق کشیدن و رها کردن](/en-US/docs/Web/API/DataTransfer/files).

مجموعه‌هایی از فایل‌ها که به این شکل در دسترس قرار می‌گیرند به صورت اشیاء {{domxref("FileList")}} نمایش داده می‌شوند که به برنامه وب امکان می‌دهند اشیاء {{domxref("File")}} تکی را بازیابی کند. به نوبه خود، اشیاء {{domxref("File")}} دسترسی به فراداده‌هایی مانند نام، اندازه، نوع و تاریخ آخرین تغییر فایل را فراهم می‌کنند.

اشیاء {{domxref("File")}} را می‌توان به اشیاء {{domxref("FileReader")}} ارسال کرد تا به محتوای فایل دسترسی پیدا کنند. رابط {{domxref("FileReader")}} ناهمگام است، اما یک نسخه همگام که فقط در [web workers](/en-US/docs/Web/API/Web_Workers_API) در دسترس است توسط رابط {{domxref("FileReaderSync")}} ارائه می‌شود.

## رابطه با APIهای دیگر مرتبط با فایل

دو API مهم دیگر نیز وجود دارند که با فایل‌ها سروکار دارند: [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API) و [File System API](/en-US/docs/Web/API/File_System_API).

File API پایه‌ای‌ترین آن‌هاست. این API از خواندن و پردازش داده‌های فایل که به طور صریح توسط کاربر در قالب یک ورودی عنصر فرم یا عملیات کشیدن و رها کردن ارائه شده است، پشتیبانی می‌کند. همچنین امکان مدیریت داده‌های دودویی را از طریق blobs فراهم می‌کند.

File and Directory Entries API، مانند File API، با فایل‌هایی سروکار دارد که توسط کاربر از طریق ورودی‌های فرم یا عملیات کشیدن و رها کردن ارائه می‌شوند. با این حال، عنصر ورودی اکنون به جای یک فایل، امکان انتخاب یک دایرکتوری یا چندین فایل را فراهم می‌کند. سپس API راهی برای پردازش دایرکتوری یا فایل‌ها ارائه می‌دهد. این عمدتاً اختراع خود کروم است – متوجه خواهید شد که افزونه‌های آن به سایر رابط‌ها همگی با پیشوند `webkit` هستند. [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API#history) داستان کامل‌تری درباره پیاده‌سازی و استانداردسازی خود دارد. این API در ابتدا برای پشتیبانی از یک سیستم فایل مجازی کامل در نظر گرفته شده بود، اما اکنون فقط از عملیات خواندن بر روی داده‌های ارائه شده توسط کاربر پشتیبانی می‌کند.

File System API یک سیستم فایل مجازی برای برنامه‌های وب فراهم می‌کند، به طوری که آن‌ها بتوانند داده‌ها را به صورت پایدار در یک سیستم مجازی که خصوصی به مبدأ سند است (که به عنوان [سیستم فایل خصوصی مبدأ (OPFS)](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) شناخته می‌شود) ذخیره کنند. File System Access API بیشتر File System API را گسترش می‌دهد تا به وب‌سایت‌ها اجازه دهد فایل‌های کاربر را بخوانند و بنویسند، مشروط به رضایت کاربر. بر خلاف File API و File and Directory Entries API، File System API صرفاً جاوااسکریپتی است و با ورودی‌های فرم سروکار ندارد.

## رابط‌ها

- {{domxref("Blob")}}
  - : نمایانگر یک "شیء بزرگ دودویی" است، به معنای یک شیء شبیه فایل از داده‌های خام تغییرناپذیر؛ یک {{domxref("Blob")}} می‌تواند به صورت متن یا داده‌های دودویی خوانده شود، یا به یک {{domxref("ReadableStream")}} تبدیل شود تا از روش‌های آن برای پردازش داده‌ها استفاده شود.
- {{domxref("File")}}
  - : اطلاعاتی درباره یک فایل ارائه می‌دهد و به جاوااسکریپت در یک صفحه وب اجازه می‌دهد به محتوای آن دسترسی پیدا کند.
- {{domxref("FileList")}}
  - : توسط ویژگی `files` عنصر HTML {{HTMLElement("input")}} بازگردانده می‌شود؛ این به شما امکان می‌دهد به لیست فایل‌های انتخاب شده با عنصر `<input type="file">` دسترسی پیدا کنید. همچنین برای لیستی از فایل‌هایی که هنگام استفاده از API کشیدن و رها کردن به محتوای وب رها می‌شوند استفاده می‌شود؛ برای جزئیات بیشتر در مورد این کاربرد، شیء {{domxref("DataTransfer")}} را ببینید.
- {{domxref("FileReader")}}
  - : به برنامه‌های وب امکان می‌دهد تا به صورت ناهمگام محتوای فایل‌ها (یا بافرهای داده خام) ذخیره شده روی رایانه کاربر را با استفاده از اشیاء {{domxref("File")}} یا {{domxref("Blob")}} برای مشخص کردن فایل یا داده مورد نظر برای خواندن، بخوانند.
- {{domxref("FileReaderSync")}}
  - : به برنامه‌های وب امکان می‌دهد تا به صورت همگام محتوای فایل‌ها (یا بافرهای داده خام) ذخیره شده روی رایانه کاربر را با استفاده از اشیاء {{domxref("File")}} یا {{domxref("Blob")}} برای مشخص کردن فایل یا داده مورد نظر برای خواندن، بخوانند.

### افزونه‌ها به سایر رابط‌ها

- {{domxref("URL.createObjectURL_static", "URL.createObjectURL()")}}
  - : یک URL ایجاد می‌کند که می‌تواند برای واکشی یک شیء {{domxref("File")}} یا {{domxref("Blob")}} استفاده شود.
- {{domxref("URL.revokeObjectURL_static", "URL.revokeObjectURL()")}}
  - : یک URL شیء موجود را که قبلاً با فراخوانی {{domxref("URL.createObjectURL_static", "URL.createObjectURL()")}} ایجاد شده بود، آزاد می‌کند.

## مثال‌ها

### خواندن یک فایل

در این مثال، یک [عنصر `<input>` فایل](/en-US/docs/Web/HTML/Reference/Elements/input/file) ارائه می‌دهیم، و هنگامی که کاربر فایلی را انتخاب می‌کند، محتوای اولین فایل انتخاب شده را به صورت متن می‌خوانیم و نتیجه را در یک {{HTMLElement("div")}} نمایش می‌دهیم.

#### HTML

```html
<input type="file" />
<div class="output"></div>
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
const fileInput = document.querySelector("input[type=file]");
const output = document.querySelector(".output");

fileInput.addEventListener("change", async () => {
  const [file] = fileInput.files;

  if (file) {
    output.innerText = await file.text();
  }
});
```

### نتیجه

{{EmbedLiveSample("Reading a file", "", "300")}}

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`<input type="file">`](/en-US/docs/Web/HTML/Reference/Elements/input/file): عنصر ورودی فایل
- {{domxref("Blob.text()")}}
- رابط {{domxref("DataTransfer")}}