---
title: DirectoryEntrySync
slug: Web/API/DirectoryEntrySync
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.DirectoryEntrySync
---

{{APIRef("File and Directory Entries API")}}{{Non-standard_Header}}{{Deprecated_Header}}

رابط `DirectoryEntrySync` یک دایرکتوری در یک سیستم فایل را نشان می‌دهد. این شامل روش‌هایی برای ایجاد، خواندن، جستجو و حذف بازگشتی فایل‌ها در یک دایرکتوری است.

> [!WARNING]
> این رابط منسوخ شده است و دیگر در مسیر استاندارد قرار ندارد. _دیگر از آن استفاده نکنید._ به جای آن از [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API) استفاده کنید.

## مفاهیم پایه

اگر می‌خواهید زیردایرکتوری‌هایی ایجاد کنید، باید هر زیردایرکتوری را به ترتیب ایجاد کنید. اگر تلاش کنید با یک مسیر کامل که شامل دایرکتوری‌های والد است که هنوز وجود ندارند، یک دایرکتوری ایجاد کنید، با خطا مواجه می‌شوید. بنابراین سلسله‌مراتب را با ایجاد بازگشتی مسیر جدید پس از ایجاد دایرکتوری والد ایجاد کنید.

### مثال

متد `getFile()` یک `FileEntrySync` برمی‌گرداند که یک فایل در سیستم فایل را نشان می‌دهد. دستور زیر یک فایل خالی به نام `logs.txt` در دایرکتوری ریشه ایجاد می‌کند.

```js
const fileEntry = fs.root.getFile("logs.txt", { create: true });
```

متد `getDirectory()` یک `DirectoryEntrySync` برمی‌گرداند که یک دایرکتوری در سیستم فایل را نشان می‌دهد. دستور زیر یک دایرکتوری جدید به نام `project_dir` در دایرکتوری ریشه ایجاد می‌کند.

```js
const dirEntry = fs.root.getDirectory("project_dir", { create: true });
```

## نمای کلی متدها

- <a href="#createreader">createReader()</a>
- <a href="#getfile">getFile()</a>
- <a href="#getdirectory">getDirectory()</a>
- <a href="#removerecursively">removeRecursively()</a>

## متدهای نمونه

### createReader()

یک `DirectoryReaderSync` جدید برای خواندن ورودی‌ها از این دایرکتوری ایجاد می‌کند.

#### Syntax

```js-nolint
createReader()
```

##### پارامترها

هیچکدام.

##### مقدار برگشتی

یک شیء [`DirectoryReaderSync`](/en-US/docs/Web/API/DirectoryReaderSync) که یک دایرکتوری در سیستم فایل را نشان می‌دهد.

##### استثناها

این متد می‌تواند یک {{domxref("DOMException")}} با کدهای زیر ایجاد کند:

| استثنا            | توضیحات                                                                              |
| ----------------- | ------------------------------------------------------------------------------------ |
| `NOT_FOUND_ERR`   | دایرکتوری وجود ندارد.                                                                |
| `SECURITY_ERR`    | مرورگر تشخیص داد که جستجوی فراداده ایمن نیست. [ توضیح: دلیل را توضیح دهید ]           |

### getFile()

بسته به نحوه تنظیم پارامتر `options`، این متد یا یک فایل ایجاد می‌کند یا یک فایل موجود را جستجو می‌کند.

#### Syntax

```js-nolint
getFile(path)
getFile(path, options)
```

##### پارامترها

- `path`
  - : یا یک مسیر مطلق یا یک مسیر نسبی از دایرکتوری به فایلی که باید جستجو یا ایجاد شود. نمی‌توانید فایلی ایجاد کنید که والد بلافصل آن وجود نداشته باشد. ابتدا دایرکتوری والد را ایجاد کنید.
- `options`
  - : (اختیاری) یک لیترال شیء که رفتار متد را توصیف می‌کند. اگر فایل وجود نداشته باشد، ایجاد می‌شود.

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">لیترال شیء</th>
      <th scope="col">شرط</th>
      <th scope="col">نتیجه</th>
    </tr>
    <tr>
      <td><code>create: true</code><br /><code>exclusive: true</code></td>
      <td>مسیر از قبل وجود دارد</td>
      <td>یک خطا ایجاد می‌شود.</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>create: true</code><br /><code>exclusive: false</code></td>
      <td>مسیر وجود ندارد و خطای دیگری رخ نمی‌دهد</td>
      <td>یک فایل ایجاد می‌شود. اگر فایل از قبل وجود داشته باشد، خطایی ایجاد نمی‌شود.</td>
    </tr>
    <tr>
      <td>
        <code>create: false</code><br />(<code>exclusive</code> نادیده گرفته می‌شود)
      </td>
      <td>مسیر وجود دارد</td>
      <td>فایل برگردانده می‌شود.</td>
    </tr>
    <tr>
      <td>
        <code>create: false</code><br />(<code>exclusive</code> نادیده گرفته می‌شود)
      </td>
      <td>مسیر وجود ندارد</td>
      <td>یک خطا ایجاد می‌شود.</td>
    </tr>
    <tr>
      <td>
        <code>create: false</code><br />(<code>exclusive</code> نادیده گرفته می‌شود)
      </td>
      <td>مسیر وجود دارد، اما یک دایرکتوری است</td>
      <td>یک خطا ایجاد می‌شود.</td>
    </tr>
  </tbody>
</table>

##### مقدار برگشتی

یک شیء [`FileEntrySync`](/en-US/docs/Web/API/FileEntrySync) که یک فایل در سیستم فایل را نشان می‌دهد.

##### استثناها

این متد می‌تواند یک {{domxref("DOMException")}} با کدهای زیر ایجاد کند:

| استثنا                       | توضیحات                                                                                              |
| ---------------------------- | ---------------------------------------------------------------------------------------------------- |
| `ENCODING_ERR`               | مسیر ارائه‌شده نامعتبر است.                                                                          |
| `NOT_FOUND_ERR`              | مسیر از نظر ساختاری صحیح است، اما به منبعی اشاره دارد که وجود ندارد.                                 |
| `NO_MODIFICATION_ALLOWED_ERR`| این یک مشکل مجوز است. دایرکتوری یا فایل هدف قابل نوشتن نیست.                                          |
| `PATH_EXISTS_ERR`            | فایل از قبل وجود دارد. نمی‌توانید فایل دیگری با همان مسیر ایجاد کنید.                                 |
| `QUOTA_EXCEEDED_ERROR`       | این عملیات باعث می‌شود برنامه از سهمیه ذخیره‌سازی خود تجاوز کند.                                     |
| `SECURITY_ERR`               | برنامه مجوز دسترسی به عنصر اشاره‌شده توسط مسیر را ندارد. [ توضیح: دلیل را توضیح دهید ]                |
| `TYPE_MISMATCH_ERR`          | مسیر ارائه‌شده وجود دارد، اما یک دایرکتوری نیست.                                                     |

### getDirectory()

یک دایرکتوری ایجاد یا جستجو می‌کند. این متد مشابه `getFile()` است با این تفاوت که `DirectoryEntrySync` به جای آن برگردانده می‌شود.

#### Syntax

```js-nolint
getDirectory(path)
getDirectory(path, options)
```

##### پارامترها

- `path`
  - : یا یک مسیر مطلق یا یک مسیر نسبی از دایرکتوری به فایلی که باید جستجو یا ایجاد شود. نمی‌توانید فایلی ایجاد کنید که والد بلافصل آن وجود نداشته باشد. ابتدا دایرکتوری والد را ایجاد کنید.
- `options`
  - : (اختیاری) یک لیترال شیء که رفتار متد را در صورت وجود نداشتن فایل توصیف می‌کند.

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">لیترال شیء</th>
      <th scope="col">شرط</th>
      <th scope="col">نتیجه</th>
    </tr>
    <tr>
      <td><code>create: true</code><br /><code>exclusive: true</code></td>
      <td>مسیر از قبل وجود دارد</td>
      <td>یک خطا ایجاد می‌شود.</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>create: true</code><br /><code>exclusive: false</code></td>
      <td>مسیر وجود ندارد و خطای دیگری رخ نمی‌دهد</td>
      <td>
        یک دایرکتوری ایجاد می‌شود. اگر فایل از قبل وجود داشته باشد، خطایی ایجاد نمی‌شود.
      </td>
    </tr>
    <tr>
      <td>
        <code>create: false</code><br />(<code>exclusive</code> نادیده گرفته می‌شود)
      </td>
      <td>مسیر وجود دارد</td>
      <td>دایرکتوری برگردانده می‌شود.</td>
    </tr>
    <tr>
      <td>
        <code>create: false</code><br />(<code>exclusive</code> نادیده گرفته می‌شود)
      </td>
      <td>مسیر وجود ندارد</td>
      <td>یک خطا ایجاد می‌شود.</td>
    </tr>
    <tr>
      <td>
        <code>create: false</code><br />(<code>exclusive</code> نادیده گرفته می‌شود)
      </td>
      <td>مسیر وجود دارد، اما یک دایرکتوری است</td>
      <td>یک خطا ایجاد می‌شود.</td>
    </tr>
  </tbody>
</table>

##### مقدار برگشتی

یک شیء [`DirectoryEntrySync`](/en-US/docs/Web/API/DirectoryReaderSync) که یک دایرکتوری در سیستم فایل را نشان می‌دهد.

##### استثناها

این متد می‌تواند یک {{domxref("DOMException")}} با کدهای زیر ایجاد کند:

| استثنا                       | توضیحات                                                                                              |
| ---------------------------- | ---------------------------------------------------------------------------------------------------- |
| `ENCODING_ERR`               | مسیر ارائه‌شده نامعتبر است.                                                                          |
| `NOT_FOUND_ERR`              | مسیر از نظر ساختاری صحیح است، اما به منبعی اشاره دارد که وجود ندارد.                                 |
| `NO_MODIFICATION_ALLOWED_ERR`| این یک مشکل مجوز است. دایرکتوری یا فایل هدف قابل نوشتن نیست.                                          |
| `PATH_EXISTS_ERR`            | فایل از قبل وجود دارد. نمی‌توانید فایل دیگری با همان مسیر ایجاد کنید.                                 |
| `QUOTA_EXCEEDED_ERROR`       | این عملیات باعث می‌شود برنامه از سهمیه ذخیره‌سازی خود تجاوز کند.                                     |
| `SECURITY_ERR`               | برنامه مجوز دسترسی به عنصر اشاره‌شده توسط مسیر را ندارد. [ توضیح: دلیل را توضیح دهید ]                |
| `TYPE_MISMATCH_ERR`          | مسیر ارائه‌شده وجود دارد، اما یک دایرکتوری نیست.                                                     |

### removeRecursively()

یک دایرکتوری و تمام محتویات آن را حذف می‌کند. نمی‌توانید دایرکتوری ریشه یک سیستم فایل را حذف کنید.

اگر دایرکتوری‌ای را حذف کنید که شامل فایلی است که قابل حذف نیست یا اگر در حین حذف خطایی رخ دهد، ممکن است برخی از محتویات حذف نشوند. این موارد را با فراخوانی‌های خطا بگیرید و حذف را دوباره امتحان کنید.

#### Syntax

```js-nolint
removeRecursively()
```

##### پارامترها

هیچکدام.

##### مقدار برگشتی

{{jsxref('undefined')}}

##### استثناها

این متد می‌تواند یک {{domxref("DOMException")}} با کدهای زیر ایجاد کند:

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">استثنا</th>
      <th scope="col">توضیحات</th>
    </tr>
    <tr>
      <td><code>NOT_FOUND_ERR</code></td>
      <td>دایرکتوری هدف وجود ندارد.</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>INVALID_STATE_ERR</code></td>
      <td>
        این دایرکتوری به دلیلی غیر از حذف شدن دیگر معتبر نیست.
        <p>[ توضیح: بیشتر توضیح دهید ]</p>
      </td>
    </tr>
    <tr>
      <td><code>NO_MODIFICATION_ALLOWED_ERR</code></td>
      <td>
        یکی از موارد زیر قابل نوشتن نیست: دایرکتوری، دایرکتوری والد آن، یا برخی از محتویات دایرکتوری.
      </td>
    </tr>
    <tr>
      <td><code>SECURITY_ERR</code></td>
      <td>
        برنامه مجوز دسترسی به دایرکتوری هدف، والد آن یا برخی از محتویات آن را ندارد.
      </td>
    </tr>
  </tbody>
</table>

## مشخصات

این ویژگی بخشی از هیچ مشخصات فعلی نیست. دیگر در مسیر تبدیل شدن به یک استاندارد قرار ندارد. به جای آن از [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API) استفاده کنید.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)