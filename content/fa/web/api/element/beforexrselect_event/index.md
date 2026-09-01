---
title: "Element: beforexrselect event"
short-title: beforexrselect
slug: Web/API/Element/beforexrselect_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.Element.beforexrselect_event
---

{{APIRef("WebXR Device API")}}{{SeeCompatTable}}

رویداد **`beforexrselect`** پیش از ارسال رویدادهای انتخاب WebXR ({{domxref("XRSession/select_event", "select")}}، {{domxref("XRSession/selectstart_event", "selectstart")}} و {{domxref("XRSession/selectend_event", "selectend")}}) پرتاب می‌شود. می‌توان از آن برای سرکوب رویدادهای ورودی دنیای XR در حالی که کاربر با یک رابط کاربری رویه‌ای (overlay) در DOM تعامل دارد، استفاده کرد.

این رویداد [حباب می‌زند](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling)، [قابل لغو است](/en-US/docs/Web/API/Event/cancelable) و [ترکیب‌شده است](/en-US/docs/Web/API/Event/composed).

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("beforexrselect", (event) => { })

onbeforexrselect = (event) => { }
```

## نوع رویداد

یک {{domxref("XRSessionEvent")}}. به ارث‌برده از {{domxref("Event")}}.

{{InheritanceDiagram("XRSessionEvent")}}

## دسترس‌پذیری رویداد

رویداد **`beforexrselect`** یک رویداد سراسری است و برای رابط‌های زیر در دسترس است:

- {{domxref("Window")}}
- {{domxref("Document")}}
- {{domxref("HTMLElement")}}
- {{domxref("SVGElement")}}
- {{domxref("MathMLElement")}}

## مثال‌ها

برای سرکوب رویدادهای انتخاب WebXR ({{domxref("XRSession/select_event", "select")}}، {{domxref("XRSession/selectstart_event", "selectstart")}} و {{domxref("XRSession/selectend_event", "selectend")}})، یک برنامه می‌تواند به رویداد `beforexrselect` گوش دهد. این رویداد حباب می‌زند، بنابراین فراخوانی {{domxref("Event/preventDefault", "preventDefault()")}} روی عنصر رویه‌ای DOM باعث می‌شود هر رویداد انتخاب WebXR درون این ظرف جلوگیری شود و تعامل با عنصر DOM ممکن شود و از ورودی تکراری رویداد به دنیای XR جلوگیری کند.

```js
document
  .getElementById("xr-overlay")
  .addEventListener("beforexrselect", (ev) => ev.preventDefault());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("XRSession/select_event", "select")}}
- رویداد {{domxref("XRSession/selectstart_event", "selectstart")}}
- رویداد {{domxref("XRSession/selectend_event", "selectend")}}
- شبه‌کلاس {{cssxref(":xr-overlay")}}