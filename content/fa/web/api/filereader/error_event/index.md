---
title: "FileReader: error event"
---

---
title: "FileReader: error event"
short-title: error
slug: Web/API/FileReader/error_event
page-type: web-api-event
browser-compat: api.FileReader.error_event
---

{{APIRef("File API")}}{{AvailableInWorkers}}

رویداد **`error`** از رابط {{domxref("FileReader")}} زمانی رخ می‌دهد که خواندن فایل به دلیل یک خطا با شکست مواجه شود (برای مثال، به این دلیل که فایل پیدا نشده یا قابل خواندن نیست).

این رویداد قابل لغو نیست و bubble نمی‌شود (حباب نمی‌زند).

## نحو

برای گوش دادن به این رویداد، می‌توانید از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("error", (event) => { })

onerror = (event) => { }
```

## نوع رویداد

یک {{domxref("ProgressEvent")}}. این رویداد از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("ProgressEvent")}}

## مثال‌ها

```js
const fileInput = document.querySelector('input[type="file"]');
const reader = new FileReader();

function handleSelected(e) {
  const selectedFile = fileInput.files[0];
  if (selectedFile) {
    reader.addEventListener("error", () => {
      console.error(`Error occurred reading file: ${selectedFile.name}`);
    });

    reader.addEventListener("load", () => {
      console.log(`File: ${selectedFile.name} read successfully`);
    });

    reader.readAsDataURL(selectedFile);
  }
}

fileInput.addEventListener("change", handleSelected);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: {{domxref("FileReader.loadstart_event", "loadstart")}}, {{domxref("FileReader.loadend_event", "loadend")}}, {{domxref("FileReader.progress_event", "progress")}}, {{domxref("FileReader.load_event", "load")}}, {{domxref("FileReader.abort_event", "abort")}}