---
title: "NDEFRecord: lang property"
short-title: lang
slug: Web/API/NDEFRecord/lang
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NDEFRecord.lang
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

ویژگی **`lang`** در رابط {{DOMxRef("NDEFRecord")}} زبان بار متنی (textual payload) را برمی‌گرداند، یا اگر زبانی ارائه نشده باشد، مقدار `null` را برمی‌گرداند.

ممکن است رکورد برچسب زبان (language tag) نداشته باشد، برای مثال اگر اطلاعات ثبت‌شده مختص به یک منطقه (locale) خاص نباشد.

## مقدار

یک رشته (string).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ویژگی `lang` در HTML](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) که زبان محتوای سند یا عناصر آن را تعیین می‌کند
- هدرهای HTTP که زبان محتوا را اعلام می‌کنند: {{HTTPHeader("Content-Language")}} و {{HTTPHeader("Accept-Language")}}