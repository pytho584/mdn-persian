---
title: "ClipboardItem: ClipboardItem() constructor"
---

سازندهٔ **`ClipboardItem()`** یک شیء جدید {{domxref("ClipboardItem")}} ایجاد می‌کند که داده‌ای را برای ذخیره‌سازی یا بازیابی از طریق متدهای {{domxref("clipboard.read()")}} و {{domxref("clipboard.write()")}} از [API کلیپ‌بورد](/en-US/docs/Web/API/Clipboard_API) به ترتیب نمایش می‌دهد.

> [!NOTE]
> متدهای `read()` و `write()` را می‌توان برای کار با رشته‌های متنی و آیتم‌های داده‌ای دلخواه که توسط نمونه‌های {{domxref("Blob")}} نمایش داده می‌شوند استفاده کرد. با این حال، اگر فقط با متن کار می‌کنید، استفاده از متدهای {{domxref("Clipboard.readText()")}} و {{domxref("Clipboard.writeText()")}} راحت‌تر است.

> [!NOTE]
> پشتیبانی از فرمت تصویر در مرورگرهای مختلف متفاوت است. برای رابط `Clipboard` به [جدول سازگاری مرورگرها](/en-US/docs/Web/API/Clipboard#browser_compatibility) مراجعه کنید.

## Syntax

```js-nolint
new ClipboardItem(data)
new ClipboardItem(data, options)
```

### Parameters

- `data`
  - : یک {{jsxref("Object")}} با {{Glossary("MIME type")}} به عنوان کلید و داده به عنوان مقدار. داده می‌تواند به یکی از اشکال زیر نمایش داده شود:
    - یک {{domxref("Blob")}}
    - یک رشته
    - یک {{jsxref("Promise")}} که به یک `Blob` یا رشته حل می‌شود.
- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `presentationStyle` {{optional_inline}}
      - : یکی از سه رشته: `unspecified`، `inline` یا `attachment`. پیش‌فرض `unspecified` است.

        `inline` به برنامه‌هایی که جای‌گذاری را دریافت می‌کنند نشان می‌دهد که `ClipboardItem` باید در نقطهٔ جای‌گذاری به صورت درون‌خطی درج شود. `attachment` به برنامه‌هایی که جای‌گذاری را دریافت می‌کنند نشان می‌دهد که `ClipboardItem` باید به عنوان پیوست اضافه شود. `unspecified` هیچ اطلاعاتی به برنامه‌های دریافت‌کنندهٔ جای‌گذاری نمی‌دهد.

## Examples

نمونهٔ زیر یک تصویر PNG را با استفاده از {{domxref("Window/fetch", "fetch()")}} و به نوبهٔ خود متد {{domxref("Response.blob()")}} درخواست می‌کند تا یک {{domxref("ClipboardItem")}} جدید ایجاد کند. سپس این آیتم با استفاده از متد {{domxref("Clipboard.write()")}} در کلیپ‌بورد نوشته می‌شود.

> [!NOTE]
> شما فقط می‌توانید یک آیتم کلیپ‌بورد را در یک زمان ارسال کنید.

```js
async function writeClipImg() {
  try {
    if (ClipboardItem.supports("image/png")) {
      const imgURL = "/my-image.png";
      const data = await fetch(imgURL);
      const blob = await data.blob();
      await navigator.clipboard.write([
        new ClipboardItem({
          [blob.type]: blob,
        }),
      ]);
      console.log("Fetched image copied.");
    } else {
      console.log("image png is not supported");
    }
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [API کلیپ‌بورد](/en-US/docs/Web/API/Clipboard_API)
- [مقالهٔ پشتیبانی از تصویر در کلیپ‌بورد ناهمگام](https://web.dev/articles/async-clipboard)