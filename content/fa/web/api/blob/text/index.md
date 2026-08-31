---
title: "Blob: text() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob/text"
translated_by: "n8n + AI"
---

---
title: "Blob: text() method"
short-title: text()
slug: Web/API/Blob/text
page-type: web-api-instance-method
browser-compat: api.Blob.text
---

{{APIRef("File API")}}{{AvailableInWorkers}}

متد **`text()`** از رابط {{domxref("Blob")}} یک {{jsxref("Promise")}} برمی‌گرداند که با رشته‌ای حاوی محتویات blob، که به‌صورت UTF-8 تفسیر شده است، resolve می‌شود.

## نحو

```js-nolint
text()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک Promise که با رشته‌ای حاوی داده‌های blob به‌صورت متن resolve می‌شود. داده‌ها _همیشه_ به‌صورت UTF-8 فرض می‌شوند.

## نکات استفاده

متد {{domxref("FileReader")}} به نام {{domxref("FileReader.readAsText", "readAsText()")}} یک متد قدیمی‌تر است که عملکرد مشابهی دارد. این متد هم روی `Blob` و هم روی اشیاء {{domxref("File")}} کار می‌کند. دو تفاوت کلیدی وجود دارد:

- `Blob.text()` یک Promise برمی‌گرداند، در حالی که `FileReader.readAsText()` یک API مبتنی بر رویداد است.
- `Blob.text()` همیشه از UTF-8 به‌عنوان رمزگذاری استفاده می‌کند، در حالی که `FileReader.readAsText()` بسته به نوع blob و نام رمزگذاری مشخص‌شده می‌تواند از رمزگذاری دیگری استفاده کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Response.text()")}}
- [Streams API](/en-US/docs/Web/API/Streams_API)
- {{domxref("FileReader.readAsText()")}}