---
title: "HTMLFormElement: length property"
short-title: length
slug: Web/API/HTMLFormElement/length
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.length
---

{{APIRef("HTML DOM")}}

خاصیت فقط‌خواندنی **`HTMLFormElement.length`** تعداد کنترل‌ها در عنصر {{HTMLElement("form")}} را برمی‌گرداند.

می‌توانید فهرست کنترل‌های فرم را با استفاده از خاصیت {{domxref("HTMLFormElement.elements", "elements")}} به دست آورید.

این تعداد شامل هم عناصری می‌شود که فرزندان عنصر `<form>` هستند و هم عناصری که با استفاده از خاصیت `form` خود به عضویت فرم درآمده‌اند.

عناصری که برای این خاصیت در نظر گرفته می‌شوند عبارت‌اند از: {{HTMLElement("button")}}، {{HTMLElement("fieldset")}}، {{HTMLElement("input")}} (به استثنای آن‌هایی که نوعشان «image» است و به دلایل تاریخی حذف شده‌اند)، {{HTMLElement("object")}}، {{HTMLElement("output")}}، {{HTMLElement("select")}} و {{HTMLElement("textarea")}}.

## مقدار

یک عدد.

## مثال‌ها

```js
if (document.getElementById("form1").length > 1) {
  // more than one form control here
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}