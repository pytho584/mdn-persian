---
title: "CreateMonitor: downloadprogress event"
short-title: downloadprogress
slug: Web/API/CreateMonitor/downloadprogress_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.CreateMonitor.downloadprogress_event
---

{{APIRef("Summarizer API")}}{{SeeCompatTable}}{{securecontext_header}}

رویداد **`downloadprogress`** از رابط {{domxref("CreateMonitor")}} زمانی رخ می‌دهد که پیشرفتی در دانلود مدل هوش مصنوعی حاصل شود.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم یک ویژگی مدیریت‌کننده رویداد، به صورت زیر عمل کنید:

```js-nolint
addEventListener("downloadprogress", (event) => { })

ondownloadprogress = (event) => { }
```

## نوع رویداد

یک {{domxref("ProgressEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("ProgressEvent")}}

## مثال‌ها

برای مشاهده مثال، به صفحه اصلی {{domxref("CreateMonitor")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Summarizer API](/en-US/docs/Web/API/Summarizer_API/Using)
- [دموهای وب AI](https://chrome.dev/web-ai-demos/) در chrome.dev.