---
title: "NDEFReader: write() method"
short-title: write()
slug: Web/API/NDEFReader/write
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.NDEFReader.write
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

متد `write()` در رابط {{DOMxRef("NDEFReader")}} تلاش می‌کند یک پیام NDEF را روی یک تگ بنویسد و یک {{jsxref("Promise")}} برمی‌گرداند که یا زمانی که پیام با موفقیت نوشته شد حل می‌شود (resolve) یا در صورت بروز خطای سخت‌افزاری یا مجوز، رد می‌شود (reject). اگر مجوز «nfc» قبلاً داده نشده باشد، این متد یک پنجرهٔ درخواست مجوز (permission prompt) نمایش می‌دهد.

## Syntax

```js-nolint
write(message)
write(message, options)
```

### Parameters

- `message`
  - : پیامی که باید نوشته شود؛ می‌تواند یک رشته (string)، یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یک {{jsxref("DataView")}} یا یک آرایه از رکوردها باشد. هر رکورد شامل اعضای زیر است:
    - `data` {{optional_inline}}
      - : داده‌ای که باید ارسال شود؛ یک رشته، یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یک {{jsxref("DataView")}} یا آرایه‌ای از رکوردهای تو در تو.
    - `encoding` {{optional_inline}}
      - : رشته‌ای که encoding رکورد را مشخص می‌کند.
    - `id` {{optional_inline}}
      - : شناسه‌ای تعریف‌شده توسط توسعه‌دهنده برای رکورد.
    - `lang` {{optional_inline}}
      - : یک {{glossary("BCP 47 language tag")}} معتبر.
    - `mediaType` {{optional_inline}}
      - : یک [MIME type](/en-US/docs/Web/HTTP/Guides/MIME_types) معتبر.
    - `recordType`
      - : رشته‌ای که نوع دادهٔ ذخیره‌شده در `data` را مشخص می‌کند. باید یکی از مقادیر زیر باشد:
        - `"absolute-url"`
          - : یک URL مطلق برای داده.
        - `"empty"`
          - : یک {{domxref("NDEFRecord")}} خالی.
        - `"mime"`
          - : یک [MIME type](/en-US/docs/Web/HTTP/Guides/MIME_types) معتبر.
        - `"smart-poster"`
          - : پوستر هوشمند (smart poster) طبق تعریف مشخصات [NDEF-SMARTPOSTER](https://w3c.github.io/web-nfc/#bib-ndef-smartposter).
        - `"text"`
          - : متن طبق تعریف مشخصات [NDEF-TEXT](https://w3c.github.io/web-nfc/#bib-ndef-text).
        - `"unknown"`
          - : نوع رکورد ناشناخته است.
        - `"URL"`
          - : یک URL طبق تعریف مشخصات [NDEF-URI](https://w3c.github.io/web-nfc/#bib-ndef-uri).

- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `overwrite`
      - : یک مقدار بولین که مشخص می‌کند آیا رکوردهای موجود در صورت وجود، بازنویسی شوند یا خیر.
    - `signal` {{optional_inline}}
      - : یک {{DOMxRef("AbortSignal")}} که امکان لغو عملیات نوشتن فعلی را فراهم می‌کند.

### Return value

یک {{JSxRef("Promise")}} که یا زمانی که پیام روی تگ نوشته شد حل می‌شود یا در صورت بروز خطای سخت‌افزاری یا مجوز، رد می‌شود.

### Exceptions

این متد استثنا پرتاب نمی‌کند؛ در عوض، پرامیسی که برمی‌گرداند را رد می‌کند و یک {{domxref("DOMException")}} به آن می‌دهد که `name` آن یکی از مقادیر زیر است:

- `AbortError`
  - : عملیات اسکن با استفاده از {{DOMxRef("AbortSignal")}} که در آرگومان `options` داده شده بود، لغو شد.
- `NotAllowedError`
  - : مجوز این عملیات رد شد یا `overwrite` برابر `false` است و از قبل رکوردهایی روی تگ وجود دارد.
- `NotSupportedError`
  - : هیچ آداپتور NFC سازگار با Web NFC وجود ندارد، یا آداپتور NFC موجود از ارسال پیام پشتیبانی نمی‌کند، یا امکان برقراری اتصال وجود ندارد.
- `NotReadableError`
  - : مرورگر (UA) مجاز به دسترسی به آداپتور NFC زیرین نیست (مثلاً به دلیل ترجیحات کاربر).
- `NetworkError`
  - : انتقال پس از شروع، شکست خورد (مثلاً تگ از خواننده خارج شد).

## Examples

### نوشتن یک رشته متنی

مثال زیر نحوه نوشتن یک رشته روی تگ NFC و مدیریت خطاهای احتمالی را نشان می‌دهد.

```js
const ndef = new NDEFReader();
ndef
  .write("Hello World")
  .then(() => {
    console.log("Message written.");
  })
  .catch((error) => {
    console.log(`Write failed :-( try again: ${error}.`);
  });
```

### نوشتن یک URL

مثال زیر نحوه نوشتن یک شیء رکورد (که در بالا توضیح داده شد) روی تگ NFC و مدیریت خطاهای احتمالی را نشان می‌دهد.

```js
const ndef = new NDEFReader();
try {
  await ndef.write({
    records: [{ recordType: "url", data: "http://example.com/" }],
  });
} catch {
  console.log("Write failed :-( try again.");
}
```

### زمان‌بندی نوشتن با محدودیت زمانی

گاهی اوقات مفید است که برای عملیات نوشتن یک محدودیت زمانی تعیین کنید. مثلاً از کاربر می‌خواهید تگی را لمس کند، اما در مدت زمان معینی تگی پیدا نمی‌شود و سپس عملیات منقضی می‌شود.

```js
const ndef = new NDEFReader();
ndef.onreading = (event) => console.log("We read a tag!");

function write(data, { timeout } = {}) {
  return new Promise((resolve, reject) => {
    const controller = new AbortController();
    controller.signal.onabort = () =>
      reject(new Error("Time is up, bailing out!"));
    setTimeout(() => controller.abort(), timeout);

    ndef.addEventListener(
      "reading",
      (event) => {
        ndef.write(data, { signal: controller.signal }).then(resolve, reject);
      },
      { once: true },
    );
  });
}

await ndef.scan();
try {
  // فقط ۵ ثانیه صبر می‌کنیم.
  await write("Hello World", { timeout: 5_000 });
} catch (err) {
  console.error("Something went wrong", err);
} finally {
  console.log("We wrote to a tag!");
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}