---
title: "Document: compatMode property"
short-title: compatMode
slug: Web/API/Document/compatMode
page-type: web-api-instance-property
browser-compat: api.Document.compatMode
---

{{ ApiRef("DOM") }}

ویژگی فقط‌خواندنی **`Document.compatMode`** نشان می‌دهد که سند در [حالت Quirks](/en-US/docs/Web/HTML/Guides/Quirks_mode_and_standards_mode) رندر می‌شود یا در حالت استاندارد (Standards mode).

## مقدار

یک رشته که یکی از مقادیر زیر است:

- `"BackCompat"` اگر سند در حالت quirks باشد.
- `"CSS1Compat"` اگر سند در حالت بدون quirks (که به آن حالت «استاندارد» نیز گفته می‌شود) یا حالت quirks محدود (که به آن «تقریباً استاندارد» نیز گفته می‌شود) باشد.

> [!NOTE]
> همه این حالت‌ها اکنون استاندارد شده‌اند، بنابراین نام‌های قدیمی «استاندارد» و «تقریباً استاندارد» بی‌معنی هستند و دیگر در استانداردها استفاده نمی‌شوند.

## مثال‌ها

```js
if (document.compatMode === "BackCompat") {
  // در حالت Quirks
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}