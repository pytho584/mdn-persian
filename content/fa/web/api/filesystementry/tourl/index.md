---
title: "FileSystemEntry: toURL() method"
short-title: toURL()
slug: Web/API/FileSystemEntry/toURL
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.FileSystemEntry.toURL
---

{{APIRef("File and Directory Entry API")}}{{Deprecated_Header}}{{Non-standard_Header}}

متد **`toURL()`** در اینترفیس {{domxref("FileSystemEntry")}} رشته‌ای حاوی URL می‌سازد و آن را بازمی‌گرداند که می‌توان از آن برای شناسایی ورودیِ سیستم فایل استفاده کرد. این کار با معرفی یک طرح URL جدید به نام `filesystem:` انجام می‌شود که می‌توان آن را به‌عنوان مقدار ویژگی‌های `src` و `href` به کار برد.

## نحو

```js-nolint
toURL()
toURL(mimeType)
```

### پارامترها

- `mimeType` {{optional_inline}}
  - : یک رشته اختیاری که نوع MIME مورد استفاده برای تفسیر فایل را مشخص می‌کند. از این پارامتر می‌توان برای مدیریت فایل‌هایی استفاده کرد که نوع آن‌ها به‌طور خودکار توسط عامل کاربر (user agent) شناسایی نمی‌شود. اگر این پارامتر حذف شود، عامل کاربر از الگوریتم‌های استاندارد خود برای شناسایی فایل استفاده می‌کند.

### مقدار بازگشتی

یک رشته حاوی URL که سپس می‌تواند به‌عنوان ارجاعی به سند در محتوای HTML استفاده شود؛ یا اگر URL قابل تولید نباشد (مثلاً اگر پیاده‌سازی سیستم فایل از `toURL()` پشتیبانی نکند)، یک رشته خالی.

## مثال‌ها

اگر یک {{domxref("FileSystemFileEntry")}} متناظر با یک فایل تصویری در سیستم فایلی که در اختیار وب‌سایت یا برنامه شماست داشته باشید، می‌توانید `toURL()` را برای دریافت URL آن و استفاده در HTML فراخوانی کنید. اگر سایت شما در آدرس `http://my-awesome-website.woot` باشد و یک سیستم فایل موقت حاوی فایل تصویری به نام `awesome-sauce.jpg` داشته باشید، URL بازگردانده‌شده توسط `toURL()` بسته به پیاده‌سازی مرورگر می‌تواند چیزی شبیه به `"filesystem:http://my-awesome-website.woot/temporary/awesome-sauce.jpg"` باشد.

کدی که از این قابلیت استفاده می‌کند می‌تواند به شکل زیر باشد:

```js
const img = document.createElement("img");
img.src = imageFileEntry.toURL();
img.alt = "";
document.body.appendChild(img);
```

با فرض سناریویی که پیش از کد ذکر شد، نتیجه، HTML ای خواهد بود که به انتهای سند افزوده می‌شود و به این صورت است:

```html
<img
  src="filesystem:http://my-awesome-website.woot/temporary/awesome-sauce.jpg"
  alt="" />
```

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API ورودی‌های فایل و دایرکتوری](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("FileSystemDirectoryEntry.removeRecursively()")}}