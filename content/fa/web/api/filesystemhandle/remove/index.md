---
title: "FileSystemHandle: remove() method"
short-title: remove()
slug: Web/API/FileSystemHandle/remove
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.FileSystemHandle.remove
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}{{SeeCompatTable}}{{Non-standard_header}}

متد **`remove()`** از رابط {{domxref("FileSystemHandle")}} درخواست حذف ورودی (entry) مربوط به این handle را از سیستم فایل زیرین می‌دهد.

متد `remove()` به شما امکان می‌دهد یک فایل یا دایرکتوری را مستقیماً از طریق handle آن حذف کنید. بدون این متد، باید handle دایرکتوری والد را به دست آورید و سپس متد {{domxref("FileSystemDirectoryHandle.removeEntry()")}} را روی آن فراخوانی کنید تا حذف انجام شود.

همچنین می‌توانید `remove()` را روی دایرکتوری ریشه [سیستم فایل خصوصی مبدأ (Origin Private File System)](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) فراخوانی کنید تا محتویات آن پاک شود. پس از آن، یک OPFS خالی جدید ایجاد می‌شود.

## نحو (Syntax)

```js-nolint
remove()
remove(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء که گزینه‌های حذف را مشخص می‌کند. ویژگی‌های احتمالی به شرح زیر است:
    - `recursive` {{optional_inline}}
      - : یک مقدار بولین که پیش‌فرض آن `false` است. اگر روی `true` تنظیم شود و ورودی یک دایرکتوری باشد، محتویات آن به صورت بازگشتی حذف خواهند شد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با مقدار `undefined` حل می‌شود.

### استثناها (Exceptions)

- `InvalidModificationError` {{domxref("DOMException")}}
  - : اگر `recursive` روی `false` تنظیم شده باشد و ورودی مورد نظر برای حذف یک دایرکتوری دارای زیرشاخه باشد، پرتاب می‌شود.
- `NoModificationAllowedError` {{domxref("DOMException")}}
  - : اگر مرورگر نتواند یک قفل انحصاری (exclusive lock) روی ورودی به دست آورد، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus')}} برابر `granted` نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی پیدا نشود، پرتاب می‌شود.

## مثال‌ها

[نمونه `FileSystemHandle.remove()`](https://mdn.github.io/dom-examples/file-system-api/filesystemhandle-remove/) (مشاهده [کد منبع](https://github.com/mdn/dom-examples/tree/main/file-system-api/filesystemhandle-remove)) یک برنامه ایجاد فایل است. می‌توانید متن را درون {{htmlelement("textarea")}} وارد کنید و دکمه «ذخیره فایل» ({{htmlelement("button")}}) را فشار دهید. برنامه یک پنجره انتخاب فایل باز می‌کند تا بتوانید آن متن را به صورت یک فایل متنی در سیستم فایل محلی خود ذخیره کنید. همچنین می‌توانید فایل‌هایی که ایجاد کرده‌اید را حذف کنید.

این برنامه به شما اجازه مشاهده محتوای فایل‌های ایجاد شده را نمی‌دهد و با بارگذاری مجدد صفحه یا بستن آن، با سیستم فایل زیرین همگام نمی‌ماند. یعنی فایل‌هایی که توسط برنامه ایجاد شده‌اند، اگر قبل از بارگذاری مجدد یا بستن تب، آن‌ها را حذف نکنید، همچنان در سیستم فایل باقی می‌مانند.

انتخاب‌گر فایل، handle فایل و خود فایل (اگر فایل جدیدی ایجاد می‌کنید) با استفاده از {{domxref("window.showSaveFilePicker()")}} ایجاد می‌شوند. متن از طریق {{domxref("FileSystemFileHandle.createWritable()")}} در فایل نوشته می‌شود.

هنگامی که یک فایل در سیستم فایل ایجاد می‌شود، یک ورودی در برنامه ایجاد می‌شود (به تابع `processNewFile()` در کد منبع مراجعه کنید):

- یک ارجاع به handle فایل در آرایه‌ای به نام `savedFileRefs` ذخیره می‌شود تا بعداً به راحتی قابل ارجاع باشد.
- یک آیتم لیست در زیر عنوان «فایل‌های ذخیره شده» در رابط کاربری اضافه می‌شود که نام فایل به همراه یک دکمه «حذف» در کنار آن نمایش داده می‌شود.

هنگامی که دکمه «حذف» فشار داده می‌شود، تابع `deleteFile()` اجرا می‌شود که به صورت زیر است:

```js
async function deleteFile(e) {
  for (const handle of savedFileRefs) {
    if (handle.name === `${e.target.id}.txt`) {
      await handle.remove();
      savedFileRefs = savedFileRefs.filter(
        (handle) => handle.name !== `${e.target.id}.txt`,
      );
      e.target.parentElement.parentElement.removeChild(e.target.parentElement);
    }
  }
}
```

شرح این کد:

1. برای هر handle فایل ذخیره شده در آرایه `savedFileRefs`، نام آن را بررسی می‌کنیم تا ببینیم آیا با ویژگی `id` دکمه‌ای که رویداد را فعال کرده مطابقت دارد یا خیر.
2. هنگامی که تطبیقی پیدا شد، `FileSystemHandle.remove()` را روی آن handle اجرا می‌کنیم تا فایل از سیستم فایل زیرین حذف شود.
3. همچنین handle مطابقت داده شده را از آرایه `savedFileRefs` حذف می‌کنیم.
4. در نهایت، آیتم لیست مربوط به آن فایل را در رابط کاربری حذف می‌کنیم.

## مشخصات

این ویژگی بخشی از هیچ مشخصاتی نیست، اما ممکن است در آینده استاندارد شود. برای جزئیات به [_whatwg/fs#9_](https://github.com/whatwg/fs/pull/9) مراجعه کنید.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)