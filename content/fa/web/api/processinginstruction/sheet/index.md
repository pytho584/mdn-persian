---
title: "ProcessingInstruction: sheet property"
short-title: sheet
slug: Web/API/ProcessingInstruction/sheet
page-type: web-api-instance-property
browser-compat: api.ProcessingInstruction.sheet
---

{{ApiRef("DOM")}}

ویژگی فقط‌خواندنی **`sheet`** در رابط {{domxref("ProcessingInstruction")}} شامل شیوه‌نامه‌ای است که به این `ProcessingInstruction` مرتبط شده است.

دستور پردازشی `xml-stylesheet` برای مرتبط‌سازی یک شیوه‌نامه در یک فایل XML استفاده می‌شود.

## مقدار

شیء {{DOMxref("Stylesheet")}} مرتبط، یا اگر وجود نداشته باشد `null`.

## مثال

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/css" href="rule.css"?>
…
```

ویژگی `sheet` در دستور پردازشی، شیء {{domxref("StyleSheet")}} مربوط به `rule.css` را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [DOM API](/en-US/docs/Web/API/Document_Object_Model)