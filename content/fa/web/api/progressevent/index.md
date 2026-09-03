---
title: ProgressEvent
slug: Web/API/ProgressEvent
page-type: web-api-interface
browser-compat: api.ProgressEvent
---

{{APIRef("XMLHttpRequest API")}}{{AvailableInWorkers}}

رابط **`ProgressEvent`** نمایانگر رویدادهایی است که پیشرفت یک فرایند در حال انجام را اندازه‌گیری می‌کنند؛ مانند یک درخواست HTTP (مثلاً یک `XMLHttpRequest` یا بارگذاری منبعِ مرتبط با یک {{HTMLElement("img")}}، {{HTMLElement("audio")}}، {{HTMLElement("video")}}، {{HTMLElement("style")}} یا {{HTMLElement("link")}}).

{{InheritanceDiagram}}

## سازنده

- {{domxref("ProgressEvent.ProgressEvent", "ProgressEvent()")}}
  - : یک رویداد `ProgressEvent` را با پارامترهای داده‌شده می‌سازد.

## ویژگی‌های نمونه

_ویژگی‌های والد خود، یعنی {{domxref("Event")}} را نیز به ارث می‌برد._

- {{domxref("ProgressEvent.lengthComputable")}} {{ReadOnlyInline}}
  - : یک پرچم بولی که نشان می‌دهد آیا نسبت بین حجم داده‌هایِ منتقل‌شده یا پردازش‌شده (`loaded`) و حجم کل داده‌ها (`total`) قابل محاسبه است یا نه. به عبارت دیگر، مشخص می‌کند که آیا پیشرفت قابل اندازه‌گیری است یا خیر.
- {{domxref("ProgressEvent.loaded")}} {{ReadOnlyInline}}
  - : عددی که حجم داده‌های ارسال‌شده یا پردازش‌شده را نشان می‌دهد. برای یک `ProgressEvent` که مرورگر در پیام‌های HTTP ارسال می‌کند، این مقدار به حجم بدنه پیام (body) بر حسب بایت اشاره دارد و هدرها و سایر سربارها را شامل نمی‌شود. در پیام‌های فشرده‌ای که حجم کل آن‌ها نامعلوم است، مقدار `loaded` بسته به مرورگر ممکن است به حجم داده فشرده یا حجم داده فشرده‌نشده اشاره کند. از سال ۲۰۲۴، این مقدار در فایرفاکس حجم داده فشرده و در کروم حجم داده فشرده‌نشده است. اگر خودتان یک `ProgressEvent` بسازید، می‌توانید هر مقدار عددی را به `loaded` اختصاص دهید که میزان کار انجام‌شده را نسبت به مقدار `total` نشان دهد.
- {{domxref("ProgressEvent.total")}} {{ReadOnlyInline}}
  - : عددی که حجم کل داده‌های در حال انتقال یا پردازش را نشان می‌دهد. برای رویدادهای `ProgressEvent` که مرورگر در پیام‌های HTTP ارسال می‌کند، این مقدار به حجم یک منبع بر حسب بایت اشاره دارد و از هدر `Content-Length` به دست می‌آید. اگر خودتان یک `ProgressEvent` بسازید و نگران افشای حجم دقیق بایت‌های یک منبع هستید، می‌توانید مقدار `total` را به مقداری مانند `100` یا `1` نرمال‌سازی کنید. برای مثال، اگر مقدار کل `1` باشد، آنگاه `loaded` یک مقدار اعشاری بین `0` و `1` خواهد بود.

## متدهای نمونه

_متدهایی را از والد خود، یعنی {{domxref("Event")}}، به ارث می‌برد._

## مثال‌ها

### نمایش وضعیت یک درخواست

مثال زیر یک `ProgressEvent` را به یک {{domxref("XMLHttpRequest")}} جدید اضافه می‌کند و از آن برای نمایش وضعیت درخواست استفاده می‌کند.

```js
const progressBar = document.getElementById("p"),
  client = new XMLHttpRequest();
client.open("GET", "magical-unicorns");
client.onprogress = (pe) => {
  if (pe.lengthComputable) {
    progressBar.max = pe.total;
    progressBar.value = pe.loaded;
  }
};
client.onloadend = (pe) => {
  progressBar.value = pe.loaded;
};
client.send();
```

### استفاده از اعداد کسری در ProgressEvent

حجم کل یک منبع بر حسب بایت ممکن است اطلاعات زیادی درباره آن منبع فاش کند؛ بنابراین می‌توان به‌جای آن از عددی بین ۰ و ۱ در یک {{domxref("ProgressEvent.ProgressEvent", "ProgressEvent()")}} استفاده کرد:

```js
function updateProgress(loaded, total) {
  const progressEvent = new ProgressEvent("progress", {
    lengthComputable: true,
    loaded,
    total,
  });

  document.dispatchEvent(progressEvent);
}

document.addEventListener("progress", (event) => {
  console.log(`Progress: ${event.loaded}/${event.total}`);
});

updateProgress(0.123456, 1);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط پایه {{domxref("Event")}}