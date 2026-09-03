---
title: "NDEFRecord: recordType property"
---

---
title: "NDEFRecord: recordType property"
short-title: recordType
slug: Web/API/NDEFRecord/recordType
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NDEFRecord.recordType
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

**`recordType`** ویژگی از رابط {{DOMxRef("NDEFRecord")}} نوع رکورد (record) را برمیگرداند.

## مقدار

یک رشته (string) که میتواند یکی از مقادیر زیر باشد:

- `"empty"`
  - : یک رکورد NDEF خالی.
- `"text"`
  - : یک رکورد NDEF متنی.
- `"url"`
  - : یک رکورد NDEF شامل URI.
- `"smart-poster"`
  - : یک رکورد NDEF «پوستر هوشمند».
- `"absolute-url"`
  - : یک رکورد NDEF با آدرس URL مطلق.
- `"mime"`
  - : یک رکورد NDEF از نوع {{Glossary("MIME type")}}.
- `"unknown"`
  - : نوع رکورد NDEF ناشناخته است.
- نام نوع محلی (local type name)
  - : نشاندهنده یک نام نوع محلی است که معمولاً برای مشخص کردن رکورد NDEF تعبیهشده در رکوردی دیگر استفاده میشود.
- نام نوع خارجی (external type name)
  - : رشتهای سفارشی شامل نام دامنه و نام نوع سفارشی که با دو نقطه (":") از هم جدا شدهاند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}