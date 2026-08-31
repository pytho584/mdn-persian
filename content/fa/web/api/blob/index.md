---
title: "Blob"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob"
translated_by: "n8n + AI"
---

---
title: Blob
slug: Web/API/Blob
page-type: web-api-interface
browser-compat: api.Blob
---

{{APIRef("File API")}}{{AvailableInWorkers}}

رابط **`Blob`** یک blob را نشان می‌دهد، که یک شیء شبیه به فایل از داده‌های خام و تغییرناپذیر است؛ این داده‌ها می‌توانند به‌صورت متن یا داده‌های باینری خوانده شوند، یا به یک {{DOMxRef("ReadableStream")}} تبدیل شوند تا روش‌های آن برای پردازش داده‌ها استفاده شود.

Blobها می‌توانند داده‌هایی را نشان دهند که لزوماً در قالب بومی جاوااسکریپت نیستند. رابط {{DOMxRef("File")}} بر پایه `Blob` است و عملکرد blob را به ارث می‌برد و آن را برای پشتیبانی از فایل‌های موجود در سیستم کاربر گسترش می‌دهد.

## استفاده از blobs

برای ساخت یک `Blob` از سایر اشیاء و داده‌های غیر-blob، از سازنده {{DOMxRef("Blob.Blob", "Blob()")}} استفاده کنید. برای ایجاد یک blob که شامل زیرمجموعه‌ای از داده‌های blob دیگر است، از روش {{DOMxRef("Blob.slice()", "slice()")}} استفاده کنید. برای به دست آوردن یک شیء `Blob` برای یک فایل در سیستم فایل کاربر، به مستندات {{DOMxRef("File")}} مراجعه کنید.

APIهایی که اشیاء `Blob` را می‌پذیرند نیز در مستندات {{DOMxRef("File")}} فهرست شده‌اند.

## سازنده

- {{DOMxRef("Blob.Blob", "Blob()")}}
  - : یک شیء `Blob` تازه ایجاد شده را برمی‌گرداند که شامل الحاق تمام داده‌های موجود در آرایه‌ای است که به سازنده منتقل شده است.

## ویژگی‌های نمونه

- {{DOMxRef("Blob.size")}} {{ReadOnlyInline}}
  - : اندازه داده‌های موجود در شیء `Blob` به بایت.
- {{DOMxRef("Blob.type")}} {{ReadOnlyInline}}
  - : رشته‌ای که نوع MIME داده‌های موجود در `Blob` را نشان می‌دهد. اگر نوع ناشناخته باشد، این رشته خالی است.

## روش‌های نمونه

- {{DOMxRef("Blob.arrayBuffer()")}}
  - : یک promise برمی‌گرداند که با یک {{jsxref("ArrayBuffer")}} شامل کل محتویات `Blob` به‌عنوان داده باینری حل می‌شود.
- {{DOMxRef("Blob.bytes()")}}
  - : یک promise برمی‌گرداند که با یک {{jsxref("Uint8Array")}} شامل محتویات `Blob` حل می‌شود.
- {{DOMxRef("Blob.slice()")}}
  - : یک شیء `Blob` جدید برمی‌گرداند که شامل داده‌های موجود در محدوده بایت مشخص‌شده از blob است که روی آن فراخوانی می‌شود.
- {{DOMxRef("Blob.stream()")}}
  - : یک {{DOMxRef("ReadableStream")}} برمی‌گرداند که می‌تواند برای خواندن محتویات `Blob` استفاده شود.
- {{DOMxRef("Blob.text()")}}
  - : یک promise برمی‌گرداند که با یک رشته شامل کل محتویات `Blob` که به‌عنوان متن UTF-8 تفسیر شده است، حل می‌شود.

## نمونه‌ها

### ایجاد یک blob

سازنده {{DOMxRef("Blob.Blob", "Blob()")}} می‌تواند blobها را از اشیاء دیگر ایجاد کند. برای مثال، برای ساخت یک blob از یک رشته JSON:

```js
const obj = { hello: "world" };
const blob = new Blob([JSON.stringify(obj, null, 2)], {
  type: "application/json",
});
```

### ایجاد یک URL که محتویات یک typed array را نشان می‌دهد

مثال زیر یک [typed array](/en-US/docs/Web/JavaScript/Guide/Typed_arrays) جاوااسکریپت ایجاد می‌کند و یک `Blob` جدید حاوی داده‌های typed array می‌سازد. سپس {{DOMxRef("URL/createObjectURL_static", "URL.createObjectURL()")}} را برای تبدیل blob به یک {{glossary("URL")}} فراخوانی می‌کند.

```html live-sample___url-from-array
<p>
  This example creates a typed array containing the ASCII codes for the space
  character through the letter Z, then converts it to an object URL. A link to
  open that object URL is created. Click the link to see the decoded object URL.
</p>
```

بخش اصلی این کد برای اهداف مثال، تابع `typedArrayToURL()` است که یک `Blob` از typed array داده‌شده ایجاد می‌کند و یک URL شیء برای آن برمی‌گرداند. پس از تبدیل داده‌ها به یک URL شیء، می‌توان از آن به روش‌های مختلف استفاده کرد، از جمله به‌عنوان مقدار ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/img#src) عنصر {{HTMLElement("img")}} (البته به شرطی که داده‌ها حاوی یک تصویر باشند).

```js live-sample___url-from-array
function showViewLiveResultButton() {
  if (window.self !== window.top) {
    // Ensure that if our document is in a frame, we get the user
    // to first open it in its own tab or window. Otherwise, this
    // example won't work.
    const p = document.querySelector("p");
    p.textContent = "";
    const button = document.createElement("button");
    button.textContent = "View live result of the example code above";
    p.append(button);
    button.addEventListener("click", () => window.open(location.href));
    return true;
  }
  return false;
}

if (!showViewLiveResultButton()) {
  function typedArrayToURL(typedArray, mimeType) {
    return URL.createObjectURL(
      new Blob([typedArray.buffer], { type: mimeType }),
    );
  }
  const bytes = new Uint8Array(59);

  for (let i = 0; i < 59; i++) {
    bytes[i] = 32 + i;
  }

  const url = typedArrayToURL(bytes, "text/plain");
  const link = document.createElement("a");

  link.href = url;
  link.innerText = "Open the array URL";
  document.body.appendChild(link);
}
```

{{EmbedLiveSample('url-from-array', , , , , , , 'allow-popups')}}

### استخراج داده‌ها از یک blob

یکی از راه‌های خواندن محتوا از یک `Blob` استفاده از {{DOMxRef("FileReader")}} است. کد زیر محتوای یک `Blob` را به‌صورت یک typed array می‌خواند:

```js
const reader = new FileReader();
reader.addEventListener("loadend", () => {
  // reader.result contains the contents of blob as a typed array
});
reader.readAsArrayBuffer(blob);
```

راه دیگر برای خواندن محتوا از یک `Blob` استفاده از یک {{domxref("Response")}} است. کد زیر محتوای یک `Blob` را به‌صورت متن می‌خواند:

```js
const text = await new Response(blob).text();
```

یا با استفاده از {{DOMxRef("Blob.text()")}}:

```js
const text = await blob.text();
```

با استفاده از روش‌های دیگر `FileReader`، می‌توان محتویات یک Blob را به‌صورت یک رشته یا یک URL داده خواند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("FileReader")}}
- {{DOMxRef("File")}}
- {{DOMxRef("URL/createObjectURL_static", "URL.createObjectURL()")}}
- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)