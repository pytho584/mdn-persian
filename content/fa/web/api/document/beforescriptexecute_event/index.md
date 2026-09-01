---
title: "Document: beforescriptexecute event"
short-title: beforescriptexecute
slug: Web/API/Document/beforescriptexecute_event
page-type: web-api-event
status:
  - deprecated
  - non-standard
browser-compat: api.Document.beforescriptexecute_event
---

{{APIRef("DOM")}}{{non-standard_header}}{{deprecated_header}}

رویداد `beforescriptexecute` زمانی رخ می‌دهد که یک {{HTMLElement("script")}} ایستا (static) در آستانهٔ اجرا قرار می‌گیرد. اگر عنصر به‌صورت پویا اضافه شود، مانند استفاده از {{domxref("Node.appendChild()", "appendChild()")}}، این رویداد فعال نمی‌شود.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به‌کار ببرید یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("beforescriptexecute", (event) => { })

onbeforescriptexecute = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## نمونه‌ها

```js
function starting(e) {
  logMessage(`Starting script with ID: ${e.target.id}`);
}

document.addEventListener("beforescriptexecute", starting);
// or
document.onbeforescriptexecute = starting;
```

[مشاهدهٔ مثال زنده](https://mdn.dev/archives/media/samples/html/currentScript.html)

## مشخصات

بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Document.afterscriptexecute_event", "afterscriptexecute")}} از `Document`
- {{domxref("Document.currentScript")}}