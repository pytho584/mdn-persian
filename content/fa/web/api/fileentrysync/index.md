---
title: "FileEntrySync"
---

---
title: FileEntrySync
slug: Web/API/FileEntrySync
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.FileEntrySync
---

{{APIRef("File and Directory Entries API")}} {{Non-standard_header}}{{Deprecated_Header}}

رابط `FileEntrySync` یک فایل را در سیستم فایل نمایش می‌دهد و به شما امکان می‌دهد محتوایی را در یک فایل بنویسید.

> [!WARNING]
> این رابط منسوخ شده است و دیگر در مسیر استاندارد قرار ندارد.
> _دیگر از آن استفاده نکنید._ در عوض از [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API) استفاده کنید.

## مفاهیم پایه

برای نوشتن محتوا در فایل، با فراخوانی [`createWriter()`](#createwriter) یک شیء `FileWriter` بسازید.

## نمای کلی متدها

<table class="standard-table">
  <tbody>
    <tr>
      <td>
        <code>FileWriterSync <a href="#createwriter">createWriter</a> ();</code>
      </td>
    </tr>
    <tr>
      <td>
        <code>File <a href="#file">file</a> ();</code>
      </td>
    </tr>
  </tbody>
</table>

## متدهای نمونه

### createWriter()

یک `FileWriter` جدید مرتبط با فایلِ متناظر با این `FileEntry` می‌سازد.

```js-nolint
createWriter()
```

#### پارامترها

هیچ.

#### مقدار بازگشتی

یک شیء `FileWriterSync`.

#### استثناها

این متد می‌تواند یک [DOMException](/en-US/docs/Web/API/DOMException) با کدهای زیر ایجاد کند:

| Exception           | توضیحات                                                                    |
| ------------------- | ------------------------------------------------------------------------------ |
| `NOT_FOUND_ERR`     | فایل وجود ندارد.                                                       |
| `INVALID_STATE_ERR` | فایل به دلایلی غیر از حذف‌شدن، دیگر معتبر نیست. |

### file()

یک `File` برمی‌گرداند که وضعیت فعلی فایلِ متناظر با این `FileEntry` را نشان می‌دهد.

```js-nolint
file()
```

#### پارامترها

هیچ.

#### مقدار بازگشتی

یک شیء `File`.

#### استثناها

این متد می‌تواند یک [DOMException](/en-US/docs/Web/API/DOMException) با کدهای زیر ایجاد کند:

| Exception           | توضیحات                                                                    |
| ------------------- | ------------------------------------------------------------------------------ |
| `NOT_FOUND_ERR`     | فایل وجود ندارد.                                                       |
| `INVALID_STATE_ERR` | فایل به دلایلی غیر از حذف‌شدن، دیگر معتبر نیست. |

## مشخصات

این ویژگی دیگر بخشی از هیچ مشخصاتی نیست و دیگر در مسیر استاندارد شدن قرار ندارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)