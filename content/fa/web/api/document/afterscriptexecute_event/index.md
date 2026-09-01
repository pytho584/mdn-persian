---
title: "Document: afterscriptexecute event"
short-title: afterscriptexecute
slug: Web/API/Document/afterscriptexecute_event
page-type: web-api-event
status:
  - deprecated
  - non-standard
browser-compat: api.Document.afterscriptexecute_event
---

{{APIRef("DOM")}}{{non-standard_header}}{{deprecated_header}}

رویداد `afterscriptexecute` زمانی رخ می‌دهد که یک عنصر ایستای {{HTMLElement("script")}} اجرای اسکریپت خود را به پایان برساند. اگر عنصر به‌صورت پویا اضافه شود، مثلاً با استفاده از {{domxref("Node.appendChild()", "appendChild()")}}، این رویداد رخ نمی‌دهد.

## سینتکس

برای استفاده از این رویداد، نام آن را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی کنترل‌کنندهٔ رویداد را تنظیم کنید.

```js-nolint
addEventListener("afterscriptexecute", (event) => { })

onafterscriptexecute = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
function finished(e) {
  logMessage(`Finished script with ID: ${e.target.id}`);
}

document.addEventListener("afterscriptexecute", finished);
// or
document.onafterscriptexecute = finished;
```

[مشاهدهٔ مثال زنده](https://mdn.dev/archives/media/samples/html/currentScript.html)

## مشخصات

بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Document.beforescriptexecute_event", "beforescriptexecute")}} از `Document`
- {{domxref("Document.currentScript")}}