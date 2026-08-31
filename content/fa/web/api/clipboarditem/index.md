---
title: ClipboardItem
slug: Web/API/ClipboardItem
page-type: web-api-interface
browser-compat: api.ClipboardItem
---

{{APIRef("Clipboard API")}}{{SecureContext_Header}}

رابط **`ClipboardItem`** از [API کلیپ‌بورد](/en-US/docs/Web/API/Clipboard_API) یک قالب واحد را نشان می‌دهد که هنگام خواندن یا نوشتن داده‌های کلیپ‌بورد با استفاده از {{domxref("Clipboard.read()")}} و {{domxref("Clipboard.write()")}} به‌کار می‌رود.

رابط **`ClipboardItem`** به توسعه‌دهندگان امکان می‌دهد تا با یک نوع واحد، طیفی از قالب‌های داده‌ای مختلف را نمایش دهند.

> [!NOTE]
> متدهای `read()` و `write()` برای کار با رشته‌های متنی و آیتم‌های داده‌ای دلخواه که توسط نمونه‌های {{domxref("Blob")}} نمایش داده می‌شوند، قابل استفاده هستند. با این حال، اگر تنها با متن کار می‌کنید، استفاده از متدهای {{domxref("Clipboard.readText()")}} و {{domxref("Clipboard.writeText()")}} راحت‌تر است.

## سازنده

- {{domxref("ClipboardItem.ClipboardItem", "ClipboardItem()")}}
  - : یک شیء جدید **`ClipboardItem`** می‌سازد که در آن {{Glossary("MIME type")}} به عنوان کلید و داده به عنوان مقدار استفاده می‌شود.

## ویژگی‌های نمونه

- {{domxref("ClipboardItem.types", "types")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Array")}} از انواع MIME موجود در **`ClipboardItem`** را برمی‌گرداند.
- {{domxref("ClipboardItem.presentationStyle", "presentationStyle")}} {{ReadOnlyInline}}
  - : یکی از مقادیر `"unspecified"`، `"inline"` یا `"attachment"` را برمی‌گرداند.

## روش‌های ایستا

- {{domxref("ClipboardItem.supports_static", "ClipboardItem.supports()")}}
  - : بررسی می‌کند که آیا یک {{Glossary("MIME type")}} معین توسط کلیپ‌بورد پشتیبانی می‌شود یا خیر. این امکان را به وب‌سایت می‌دهد تا قبل از تلاش برای نوشتن داده، از پشتیبانی نوع MIME مطلع شود.

## روش‌های نمونه

- {{domxref("ClipboardItem.getType", "getType()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{domxref("Blob")}} از نوع {{Glossary("MIME type")}} درخواستی حل می‌شود، یا در صورت یافت نشدن آن نوع MIME خطا برمی‌گرداند.

## نمونه‌ها

### نوشتن متن در کلیپ‌بورد

در این مثال ابتدا دو ثابت شامل ارجاع به یک عنصر {{htmlelement("p")}} حاوی متن و یک عنصر {{htmlelement("button")}} تعریف می‌کنیم.

سپس تابعی به نام `copyToClipboard()` تعریف می‌کنیم. این تابع ابتدا نوع MIME `"text/plain"` را در یک ثابت ذخیره می‌کند، سپس یک شیء به نام `clipboardItemData` می‌سازد که شامل یک ویژگی با کلید برابر نوع MIME و مقدار برابر متنی است که می‌خواهیم به کلیپ‌بورد کپی کنیم (در اینجا محتوای عنصر `<p>`). از آنجا که با متن کار می‌کنیم، می‌توانیم آن را مستقیماً ارسال کنیم بدون نیاز به ایجاد یک {{domxref("Blob")}}.

یک شیء `ClipboardItem` جدید با استفاده از سازنده {{domxref("ClipboardItem.ClipboardItem", "ClipboardItem()")}} می‌سازیم و آن را به متد {{domxref("Clipboard.write()")}} می‌دهیم تا متن در کلیپ‌بورد کپی شود.

در نهایت، یک شنونده رویداد به `<button>` اضافه می‌کنیم تا هنگام کلیک تابع اجرا شود.

```js
const textSource = document.querySelector("p");
const copyBtn = document.querySelector("button");

async function copyToClipboard() {
  const type = "text/plain";
  const clipboardItemData = {
    [type]: textSource.textContent,
  };
  const clipboardItem = new ClipboardItem(clipboardItemData);
  await navigator.clipboard.write([clipboardItem]);
}

copyBtn.addEventListener("click", copyToClipboard);
```

### نوشتن یک تصویر در کلیپ‌بورد

در اینجا از {{domxref("ClipboardItem.supports_static", "supports()")}} استفاده می‌کنیم تا بررسی کنیم آیا نوع داده MIME `image/svg+xml` پشتیبانی می‌شود یا خیر. اگر پشتیبانی شود، یک تصویر SVG را با استفاده از [API Fetch](/en-US/docs/Web/API/Fetch_API) دریافت می‌کنیم و سپس آن را به صورت یک {{domxref("Blob")}} می‌خوانیم که می‌توانیم از آن برای ایجاد یک `ClipboardItem` استفاده کنیم و آن را در کلیپ‌بورد بنویسیم.

```js
async function writeClipImg() {
  try {
    if (ClipboardItem.supports("image/svg+xml")) {
      const imgURL = "/my-image.svg";
      const data = await fetch(imgURL);
      const blob = await data.blob();
      await navigator.clipboard.write([
        new ClipboardItem({
          [blob.type]: blob,
        }),
      ]);
      console.log("Fetched image copied.");
    } else {
      console.log("SVG images are not supported by the clipboard.");
    }
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

### خواندن از کلیپ‌بورد

در اینجا تمام آیتم‌های موجود در کلیپ‌بورد را از طریق متد {{domxref("clipboard.read()")}} برمی‌گردانیم. سپس از ویژگی {{domxref("ClipboardItem.types")}} برای تنظیم آرگومان {{domxref("ClipboardItem.getType", "getType()")}} و دریافت شیء blob متناظر استفاده می‌کنیم.

```js
async function getClipboardContents() {
  try {
    const clipboardItems = await navigator.clipboard.read();

    for (const clipboardItem of clipboardItems) {
      for (const type of clipboardItem.types) {
        const blob = await clipboardItem.getType(type);
        // اکنون می‌توانیم از blob در اینجا استفاده کنیم
      }
    }
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ClipboardChangeEvent")}}
- [API کلیپ‌بورد](/en-US/docs/Web/API/Clipboard_API)
- [مقاله پشتیبانی از تصویر در کلیپ‌بورد ناهمگام](https://web.dev/articles/async-clipboard)