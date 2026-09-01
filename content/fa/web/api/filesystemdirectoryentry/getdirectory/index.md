---
title: "FileSystemDirectoryEntry: getDirectory() method"
short-title: getDirectory()
slug: Web/API/FileSystemDirectoryEntry/getDirectory
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryEntry.getDirectory
---

{{APIRef("File and Directory Entries API")}}

متد {{domxref("FileSystemDirectoryEntry")}} با نام **`getDirectory()`** یک شیء {{domxref("FileSystemDirectoryEntry")}} را برمی‌گرداند که متناظر با یک دایرکتوری درون زیردرخت دایرکتوری ریشه‌شده در دایرکتوری‌ای است که بر روی آن فراخوانی شده است.

## نحوه استفاده

```js-nolint
getDirectory()
getDirectory(path)
getDirectory(path, options)
getDirectory(path, options, successCallback)
getDirectory(path, options, successCallback, errorCallback)
```

### پارامترها

- `path` {{optional_inline}}
  - : یک رشته که یک مسیر مطلق یا یک مسیر نسبی نسبت به دایرکتوری‌ای که متد بر روی آن فراخوانی شده است را نشان می‌دهد و مشخص می‌کند کدام ورودی دایرکتوری برگردانده شود. مسیرهای مطلق ممکن است به دلایل امنیتی قابل استفاده نباشند.
- `options` {{optional_inline}}
  - : یک شیء که به شما امکان می‌دهد مشخص کنید آیا در صورت وجود نداشتن ورودی، آن را ایجاد کند یا خیر و آیا وجود فایل از قبل خطا محسوب می‌شود یا خیر. این گزینه‌ها در حال حاضر در بستر وب مفید نیستند. برای جزئیات بیشتر به بخش [پارامتر options](#options-parameter) مراجعه کنید.
- `successCallback` {{optional_inline}}
  - : متدی که پس از ایجاد {{domxref("FileSystemDirectoryEntry")}} فراخوانی می‌شود. این متد یک پارامتر دریافت می‌کند: شیء `FileSystemDirectoryEntry` که نمایانگر دایرکتوری مورد نظر است.
- `errorCallback` {{optional_inline}}
  - : متدی که در صورت بروز خطا فراخوانی می‌شود. به عنوان تنها پارامتر ورودی، یک شیء {{domxref("DomException")}} دریافت می‌کند که خطای رخ داده را توصیف می‌کند.

#### پارامتر `options`

شیء پارامتر `options` پارامترهای زیر را می‌پذیرد:

- `create` {{optional_inline}}
  - : اگر این ویژگی `true` باشد و دایرکتوری درخواستی وجود نداشته باشد، عامل کاربر باید آن را ایجاد کند. مقدار پیش‌فرض `false` است. دایرکتوری والد باید از قبل وجود داشته باشد.
- `exclusive` {{optional_inline}}
  - : اگر `true` باشد و همچنین گزینه `create` نیز `true` باشد، دایرکتوری نباید قبل از فراخوانی وجود داشته باشد. در عوض، باید بتوان آن را در زمان فراخوانی به صورت جدید ایجاد کرد. مقدار پیش‌فرض `false` است. اگر `create` `false` باشد، این پارامتر نادیده گرفته می‌شود.

جدول زیر نتیجه هر ترکیب ممکن از این پرچم‌ها را بسته به اینکه مسیر دایرکتوری هدف از قبل وجود داشته باشد یا خیر، توصیف می‌کند.

| گزینه `create` | گزینه `exclusive` | وضعیت مسیر                         | نتیجه                                                                                                                                                 |
| -------------- | ----------------- | ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `false`        | _نادیده گرفته شده_ | مسیر وجود دارد و یک دایرکتوری است | `successCallback` با یک {{domxref("FileSystemDirectoryEntry")}} فراخوانی می‌شود.                                                                      |
| `false`        | _نادیده گرفته شده_ | مسیر وجود دارد اما یک فایل است     | `errorCallback` با یک کد خطای مناسب فراخوانی می‌شود (اگر تابع بازگشتی ارائه شده باشد).                                                                |
| `true`         | `false`           | مسیر وجود دارد                     | دایرکتوری موجود حذف شده و با یک دایرکتوری جدید جایگزین می‌شود، سپس `successCallback` با یک {{domxref("FileSystemDirectoryEntry")}} فراخوانی می‌شود. |
| `true`         | `false`           | مسیر وجود ندارد                    | دایرکتوری ایجاد می‌شود، سپس یک {{domxref("FileSystemDirectoryEntry")}} به `successCallback` ارسال می‌شود.                                            |
| `true`         | `true`            | مسیر وجود دارد                     | `errorCallback` با یک خطای مناسب، مانند `DOMException.PATH_EXISTS_ERR`، فراخوانی می‌شود.                                                              |
| `true`         | `true`            | مسیر وجود ندارد                    | دایرکتوری ایجاد می‌شود، سپس یک {{domxref("FileSystemDirectoryEntry")}} به `successCallback` ارسال می‌شود.                                            |

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر گزینه `create` مشخص نشده باشد (یا به صورت `false` مشخص شده باشد) و دایرکتوری وجود نداشته باشد، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر به دلایل امنیتی درخواست دسترسی به دایرکتوری رد شود، پرتاب می‌شود.
- `TypeMismatchError` {{domxref("DOMException")}}
  - : اگر مسیر مشخص شده یک دایرکتوری نباشد، پرتاب می‌شود؛ احتمالاً یک فایل است، اما ممکن است یک توصیف‌کننده فایل پشتیبانی‌نشده مانند یک پایپ (pipe) باشد؛ این موضوع تا حدودی به عامل کاربر بستگی دارد.

## مثال‌ها

در این مثال، تابعی ارائه شده است که وظیفه آن یافتن یک فایل JSON حاوی دیکشنری کاربر برای یک زبان مشخص در دایرکتوری داده‌های برنامه کاربر است و سپس آن دیکشنری را بارگذاری می‌کند.

```js
let dictionary = null;

function loadDictionaryForLanguage(appDataDirEntry, lang) {
  dictionary = null;

  appDataDirEntry.getDirectory("Dictionaries", {}, (dirEntry) => {
    dirEntry.getFile(`${lang}-dict.json`, {}, (fileEntry) => {
      fileEntry.file((dictFile) => {
        let reader = new FileReader();

        reader.addEventListener("loadend", () => {
          dictionary = JSON.parse(reader.result);
        });

        reader.readAsText(dictFile);
      });
    });
  });
}
```

تابع `loadDictionaryForLanguage()` با استفاده از `getDirectory()` شروع می‌کند تا شیء {{domxref("FileSystemDirectoryEntry")}} مربوط به زیرپوشه‌ای به نام "Dictionaries" که در داخل دایرکتوری داده‌های برنامه مشخص شده قرار دارد، به دست آورد. تابع بازگشتی موفقیت این مرحله، شیء ورودی دایرکتوری حاصل را گرفته و {{domxref("FileSystemDirectoryEntry.getFile", "getFile()")}} را فراخوانی می‌کند تا یک شیء {{domxref("FileSystemFileEntry")}} مربوط به فایل دیکشنری به دست آورد. تابع بازگشتی موفقیت این مرحله نیز به نوبه خود یک {{domxref("FileReader")}} جدید ایجاد کرده و از آن برای بارگذاری محتویات فایل استفاده می‌کند. هنگامی که این بارگذاری با موفقیت انجام شود (که با فعال شدن رویداد {{domxref("FileReader/loadend_event", "loadend")}} مشخص می‌شود)، متن بارگذاری شده به {{jsxref("JSON.parse()")}} ارسال می‌شود تا به یک شیء جاوااسکریپت تبدیل شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [API ورودی‌های فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemDirectoryEntry")}}