---
title: "FileSystemDirectoryEntry: getFile() method"
---

---
title: "FileSystemDirectoryEntry: getFile() method"
short-title: getFile()
slug: Web/API/FileSystemDirectoryEntry/getFile
page-type: web-api-instance-method
browser-compat: api.FileSystemDirectoryEntry.getFile
---

{{APIRef("File and Directory Entries API")}}

متد **`getFile()`** از رابط {{domxref("FileSystemDirectoryEntry")}} یک شیء {{domxref("FileSystemFileEntry")}} برمی‌گرداند که با فایلی در زیردرخت دایرکتوریِ مورد نظر (دایرکتوری‌ای که متد روی آن فراخوانی شده است) متناظر است.

## Syntax

```js-nolint
getFile()
getFile(path)
getFile(path, options)
getFile(path, options, successCallback)
getFile(path, options, successCallback, errorCallback)
```

### Parameters

- `path` {{optional_inline}}
  - : رشته‌ای است که مسیر فایل مورد نظر را نسبت به دایرکتوری‌ای که متد روی آن فراخوانی می‌شود مشخص می‌کند. این مسیر تعیین می‌کند که ورودیِ کدام فایل بازگردانده شود.
- `options` {{optional_inline}}
  - : شیئی که به شما امکان می‌دهد مشخص کنید در صورتی که ورودی وجود نداشته باشد آن را بسازید یا نه، و همچنین آیا وجودِ از پیشِ فایل یک خطا محسوب می‌شود یا نه. این گزینه‌ها در حال حاضر در بستر وب کاربردی ندارند. برای جزئیات بیشتر بخش [پارامتر options](#options_parameter) را ببینید.
- `successCallback` {{optional_inline}}
  - : متدی که پس از ایجاد شدن {{domxref("FileSystemFileEntry")}} فراخوانی می‌شود. این متد یک پارامتر واحد دریافت می‌کند: شیء `FileSystemFileEntry` که نمایانگر فایل مورد نظر است.
- `errorCallback` {{optional_inline}}
  - : متدی که در صورت بروز خطا فراخوانی می‌شود. تنها پارامتر ورودی آن یک شیء {{domxref("DOMException")}} است که خطای روی‌داده را توصیف می‌کند.

#### پارامتر `options`

شیء پارامتر `options` پارامترهای زیر را می‌پذیرد:

- `create` {{optional_inline}}
  - : اگر این ویژگی `true` باشد و فایل درخواستی وجود نداشته باشد، عامل کاربر (user agent) باید آن را ایجاد کند. مقدار پیش‌فرض `false` است. دایرکتوری والد باید از قبل وجود داشته باشد.
- `exclusive` {{optional_inline}}
  - : اگر `true` باشد و گزینه `create` نیز `true` باشد، فایل نباید پیش از صدور فراخوانی وجود داشته باشد؛ بلکه باید بتوان آن را به‌تازگی هنگام فراخوانی ایجاد کرد. مقدار پیش‌فرض `false` است. اگر `create` برابر `false` باشد، این پارامتر نادیده گرفته می‌شود.

جدول زیر نتیجه هر ترکیب ممکن از این پرچم‌ها را بسته به اینکه مسیر فایل هدف از قبل وجود داشته باشد یا نه، توصیف می‌کند.

| گزینه `create` | گزینه `exclusive` | شرط مسیر                 | نتیجه                                                                                                                                    |
| --------------- | ------------------ | ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `false`         | _نادیده گرفته می‌شود_          | مسیر موجود است و فایل است      | `successCallback` با یک {{domxref("FileSystemFileEntry")}} فراخوانی می‌شود.                                                                |
| `false`         | _نادیده گرفته می‌شود_          | مسیر موجود است اما دایرکتوری است | `errorCallback` با کد خطای مناسب فراخوانی می‌شود (اگر تابع بازخورد ارائه شده باشد).                                              |
| `true`          | `false`            | مسیر موجود است                    | فایل موجود حذف و با فایل جدید جایگزین می‌شود، سپس `successCallback` با یک {{domxref("FileSystemFileEntry")}} فراخوانی می‌شود. |
| `true`          | `false`            | مسیر وجود ندارد             | فایل ایجاد می‌شود و سپس یک {{domxref("FileSystemFileEntry")}} به `successCallback` ارسال می‌شود.                                        |
| `true`          | `true`             | مسیر موجود است                    | `errorCallback` با خطای مناسب، مانند `DOMException.PATH_EXISTS_ERR` فراخوانی می‌شود.                                          |
| `true`          | `true`             | مسیر وجود ندارد             | فایل ایجاد می‌شود و سپس یک {{domxref("FileSystemFileEntry")}} به `successCallback` ارسال می‌شود.                                        |

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `NotFoundError` {{domxref("DOMException")}}
  - : وقتی پرتاب می‌شود که گزینه `create` مشخص نشده باشد (یا `false` باشد) و فایل وجود نداشته باشد.
- `SecurityError` {{domxref("DOMException")}}
  - : وقتی پرتاب می‌شود که درخواست دسترسی به فایل به دلایل امنیتی رد شده باشد.
- `TypeMismatchError` {{domxref("DOMException")}}
  - : وقتی پرتاب می‌شود که مسیر مشخص‌شده یک فایل نباشد؛ احتمالاً دایرکتوری است، اما ممکن است یک توصیفگر فایل (file descriptor) پشتیبانی‌نشده مانند pipe باشد؛ این موضوع تا حدی به عامل کاربر بستگی دارد.

## Examples

در این مثال، تابعی ارائه شده است که وظیفه آن یافتن یک فایل JSON حاوی دیکشنری کاربر برای یک زبان مشخص در دایرکتوری داده‌های برنامه (app data) کاربر است و سپس بارگذاری آن دیکشنری.

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

تابع `loadDictionaryForLanguage()` ابتدا با استفاده از `getDirectory()` شیء {{domxref("FileSystemDirectoryEntry")}} را به‌دست می‌آورد که نمایانگر زیرپوشه‌ای به نام «Dictionaries» در داخل دایرکتوری داده برنامه مشخص‌شده است. تابع بازخورد موفقیت این مرحله، شیء ورودی دایرکتوری به‌دست‌آمده را می‌گیرد و `getFile()` را برای دریافت یک شیء {{domxref("FileSystemFileEntry")}} که نمایانگر فایل دیکشنری است فراخوانی می‌کند. تابع بازخورد موفقیت این مرحله نیز به نوبه خود یک {{domxref("FileReader")}} جدید می‌سازد و از آن برای بارگذاری محتویات فایل استفاده می‌کند. وقتی بارگذاری با موفقیت انجام شود (که با رویداد {{domxref("FileReader/loadend_event", "loadend")}} نشان داده می‌شود)، متن بارگذاری‌شده به {{jsxref("JSON.parse()")}} داده می‌شود تا دوباره به یک شیء جاوااسکریپتی تبدیل شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemFileEntry")}}