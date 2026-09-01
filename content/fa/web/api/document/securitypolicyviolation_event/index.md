---
title: "Document: securitypolicyviolation event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Document/securitypolicyviolation_event"
short-title: securitypolicyviolation
slug: Web/API/Document/securitypolicyviolation_event
page-type: web-api-event
browser-compat: api.Document.securitypolicyviolation_event
---

{{APIRef("Reporting API")}}

رویداد **`securitypolicyviolation`** زمانی رخ می‌دهد که یک [سیاست امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) نقض شود.

این رویداد زمانی روی سند (document) رخ می‌دهد که سیاست CSP مربوط به سند نقض شود (و ممکن است از عناصر داخل سند نیز به سمت بالا منتشر شود).

این رویداد [انتشار می‌یابد](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) و به شیء {{domxref("Window")}} می‌رسد و [ترکیب‌پذیر (composed)](/en-US/docs/Web/API/Event/composed) است.

> [!NOTE]
> معمولاً باید کنترل‌کننده این رویداد را روی یک شیء سطح بالا (مانند {{domxref("Window")}} یا {{domxref("Document")}}) قرار دهید.
> اگرچه عناصر HTML از نظر فنی می‌توانند هدف رویداد `securitypolicyviolation` باشند، اما در عمل این رویداد روی آن‌ها رخ نمی‌دهد؛ برای مثال، یک منبع `<img>` مسدودشده مستقیماً این رویداد را با هدف `document` فعال می‌کند، نه اینکه از عنصر `<img>` به سمت بالا منتشر شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("securitypolicyviolation", (event) => { })

onsecuritypolicyviolation = (event) => { }
```

## نوع رویداد

یک {{domxref("SecurityPolicyViolationEvent")}}. به ارث‌رسیده از {{domxref("Event")}}.

{{InheritanceDiagram("SecurityPolicyViolationEvent")}}

## مثال‌ها

کد زیر نشان می‌دهد که چگونه می‌توانید یک تابع کنترل‌کننده رویداد را با استفاده از ویژگی `onsecuritypolicyviolation` یا `addEventListener()` روی `Document` اضافه کنید.

```js
document.onsecuritypolicyviolation = (e) => {
  // مدیریت SecurityPolicyViolationEvent در اینجا
};

document.addEventListener("securitypolicyviolation", (e) => {
  // مدیریت SecurityPolicyViolationEvent در اینجا
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Element/securitypolicyviolation_event", "securitypolicyviolation")}} در رابط {{domxref("Element")}}
- رویداد {{domxref("WorkerGlobalScope/securitypolicyviolation_event", "securitypolicyviolation")}} در رابط {{domxref("WorkerGlobalScope")}}
- [HTTP > سیاست امنیت محتوا](/en-US/docs/Web/HTTP/Guides/CSP)