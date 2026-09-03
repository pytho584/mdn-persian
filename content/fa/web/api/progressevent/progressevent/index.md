---
title: "ProgressEvent: ProgressEvent() constructor"
short-title: ProgressEvent()
slug: Web/API/ProgressEvent/ProgressEvent
page-type: web-api-constructor
browser-compat: api.ProgressEvent.ProgressEvent
---

{{APIRef("XMLHttpRequest API")}}{{AvailableInWorkers}}

سازندهٔ **`ProgressEvent()`** یک شیء جدید از نوع {{domxref("ProgressEvent")}} می‌سازد و آن را برمی‌گرداند. این شیء میزان تکمیل فعلی یک فرایند طولانی را نشان می‌دهد.

## دستور زبان

```js-nolint
new ProgressEvent(type)
new ProgressEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای شامل نام رویداد. این مقدار به بزرگی و کوچکی حروف حساس است (case-sensitive) و مرورگرها آن را روی یکی از مقادیر `loadstart`، `progress`، `abort`، `error`، `load`، `timeout` یا `loadend` قرار می‌دهند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `lengthComputable` {{optional_inline}}
      - : یک مقدار بولین که مشخص می‌کند آیا مجموع کاری که باید انجام شود و میزان کاری که تاکنون توسط فرایند زیرین انجام شده است، قابل محاسبه هستند یا خیر. به عبارت دیگر، می‌گوید که آیا پیشرفت قابل اندازه‌گیری است یا نه. مقدار پیش‌فرض آن `false` است.
    - `loaded` {{optional_inline}}
      - : عددی که میزان کاری را که فرایند زیرین تاکنون انجام داده است نشان می‌دهد. برای یک `ProgressEvent` که مرورگر در پیام‌های HTTP ارسال می‌کند، این مقدار به اندازهٔ بدنهٔ پیام بر حسب بایت اشاره دارد و سرآیندها (headers) و سایر سربارها (overhead) را شامل نمی‌شود. در یک `ProgressEvent` که خودتان می‌سازید، می‌توانید هر مقدار عددی را به `loaded` اختصاص دهید که نسبت به مقدار `total`، میزان کارِ تکمیل‌شده را بیان کند. مقدار پیش‌فرض آن `0` است.
    - `total` {{optional_inline}}
      - : عددی که اندازهٔ کل داده‌های در حال انتقال یا پردازش را نشان می‌دهد. برای `ProgressEvent`هایی که مرورگر در پیام‌های HTTP ارسال می‌کند، این مقدار به اندازهٔ یک منبع بر حسب بایت اشاره دارد و از هدر پاسخ `Content-Length` به دست می‌آید. در یک `ProgressEvent` که خودتان می‌سازید، اگر نگران این هستید که تعداد دقیق بایت‌های یک منبع فاش شود، می‌توانید `total` را به مقداری مانند `100` یا `1` نرمال‌سازی کنید. برای نمونه، اگر از `1` به‌عنوان مقدار `total` استفاده کنید، آنگاه `loaded` باید یک مقدار اعشاری بین 0 و 1 باشد. مقدار پیش‌فرض آن `0` است.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("ProgressEvent")}}.

## مثال

### بارگذاری فایل

این مثال نشان می‌دهد که چگونه یک `ProgressEvent` با استفاده از سازندهٔ آن ساخته می‌شود. این کار به‌ویژه برای ردیابی پیشرفت فرایندهایی مانند بارگذاری فایل، بارگیری فایل یا هر کار طولانی‌مدت دیگری مفید است.

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

updateProgress(50, 100);
```

### استفاده از کسرها در ProgressEvent

تعداد کل بایت‌های یک منبع ممکن است اطلاعات زیادی دربارهٔ یک بارگیری فاش کند؛ بنابراین می‌توان به‌جای آن از عددی بین 0 و 1 استفاده کرد:

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

- رابط {{domxref("ProgressEvent")}} که این سازنده به آن تعلق دارد.