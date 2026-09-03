---
title: "NDEFMessage: records property"
short-title: records
slug: Web/API/NDEFMessage/records
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NDEFMessage.records
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

ویژگی `records` در رابط {{DOMxRef("NDEFMessage")}} فهرستی از {{DOMxRef("NDEFRecord")}}هایی را نشان می‌دهد که در پیام NDEF وجود دارند.

## مقدار

فهرستی از اشیاء {{DOMxRef("NDEFRecord")}} که داده‌های ثبت‌شده در پیام را نمایش می‌دهند.

## مثال‌ها

مثال زیر نحوه خواندن محتویات یک پیام NDEF را نشان می‌دهد. ابتدا یک کنترل‌کننده رویداد برای {{domxref("NDEFReader.reading_event", "onreading")}} تنظیم می‌شود که یک نمونه از {{domxref("NDEFReadingEvent")}} دریافت می‌کند. یک شیء `NDEFMessage` از {{domxref("NDEFReadingEvent.message")}} بازگردانده می‌شود. سپس روی `message.records` حلقه زده و هر رکورد بر اساس نوع پیام آن پردازش می‌شود. عضو `data` یک {{jsxref("DataView")}} است که امکان پردازش داده‌های رمزگذاری‌شده با {{glossary("UTF-16")}} را فراهم می‌کند.

```js
ndefReaderInst.onreading = (event) => {
  const ndefMessage = event.message;
  for (const record of ndefMessage.records) {
    console.log(`Record type:  ${record.recordType}`);
    console.log(`MIME type:    ${record.mediaType}`);
    console.log(`Record id:    ${record.id}`);
    switch (record.recordType) {
      case "text":
        // TODO: Read text record with record data, lang, and encoding.
        break;
      case "url":
        // TODO: Read URL record with record data.
        break;
      default:
      // TODO: Handle other records with record data.
    }
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}