---
title: "NDEFRecord: mediaType property"
---

---
title: "NDEFRecord: mediaType property"
short-title: mediaType
slug: Web/API/NDEFRecord/mediaType
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NDEFRecord.mediaType
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

خاصیت **`mediaType`** از رابط {{DOMxRef("NDEFRecord")}}، {{Glossary("MIME type")}} رکورد را برمی‌گرداند. اگر `recordType` برابر با `"mime"` نباشد، این مقدار `null` خواهد بود.

## مقدار

یک رشته است که شامل {{Glossary("MIME type")}} بار (payload) رکورد می‌شود.

## مثال‌ها

مثال زیر رکوردهای داخل یک شیء {{domxref("NDEFMessage")}} را پیمایش می‌کند که از {{domxref("NDEFReadingEvent.message")}} گرفته شده است. سپس از خاصیت `mediaType` برای تعیین اینکه کدام‌یک از رکوردها باید پردازش شوند استفاده می‌کند.

```js
const ndef = new NDEFReader();
await ndef.scan();
ndef.onreading = (event) => {
  const decoder = new TextDecoder();
  for (const record of event.message.records) {
    if (record.mediaType === "application/json") {
      const json = JSON.parse(decoder.decode(record.data));
      const article = /^[aeio]/i.test(json.title) ? "an" : "a";
      console.log(`${json.name} is ${article} ${json.title}`);
    }
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}