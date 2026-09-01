---
title: "Element: securitypolicyviolation event"
short-title: securitypolicyviolation
slug: Web/API/Element/securitypolicyviolation_event
page-type: web-api-event
browser-compat: api.Element.securitypolicyviolation_event
---

{{APIRef("Reporting API")}}

رویداد **`securitypolicyviolation`** زمانی پرتاب می‌شود که [خط مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) نقض شود.

این رویداد زمانی روی عنصر پرتاب می‌شود که نقضی در خط مشی CSP رخ دهد.

این رویداد [حباب می‌زند](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) و به شیء {{domxref("Window")}} می‌رسد و [ترکیب‌پذیر (composed)](/en-US/docs/Web/API/Event/composed) است.

> [!NOTE]
> معمولاً باید مدیریت‌کننده این رویداد را روی یک شیء سطح بالا (یعنی {{domxref("Window")}} یا {{domxref("Document")}}) تنظیم کنید.
> اگرچه عناصر HTML از نظر فنی می‌توانند هدف رویداد `securitypolicyviolation` باشند، اما در عمل این رویداد روی آن‌ها پرتاب نمی‌شود — برای مثال، یک منبع `<img>` مسدودشده مستقیماً این رویداد را با هدف `document` پرتاب می‌کند، نه اینکه از عنصر `<img>` حباب بزند.

## نحو (Syntax)

برای استفاده از نام رویداد، می‌توانید از روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("securitypolicyviolation", (event) => { })

onsecuritypolicyviolation = (event) => { }
```

## نوع رویداد

یک {{domxref("SecurityPolicyViolationEvent")}} که از {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("SecurityPolicyViolationEvent")}}

## مثال‌ها

### گوش دادن به رویداد securitypolicyviolation روی Window

کد زیر نشان می‌دهد که چگونه می‌توانید یک تابع مدیریت‌کننده رویداد را با استفاده از ویژگی مدیریت‌کننده رویداد سراسری `onsecuritypolicyviolation` یا `addEventListener()` روی `Window` سطح بالا اضافه کنید (می‌توانید دقیقاً از همان روش روی `Document` نیز استفاده کنید).

```js
window.onsecuritypolicyviolation = (e) => {
  // مدیریت SecurityPolicyViolationEvent در اینجا
};

window.addEventListener("securitypolicyviolation", (e) => {
  // مدیریت SecurityPolicyViolationEvent در اینجا
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Document/securitypolicyviolation_event", "securitypolicyviolation")}} در رابط {{domxref("Document")}}
- رویداد {{domxref("WorkerGlobalScope/securitypolicyviolation_event", "securitypolicyviolation")}} در رابط {{domxref("WorkerGlobalScope")}}
- [HTTP > خط مشی امنیت محتوا](/en-US/docs/Web/HTTP/Guides/CSP)