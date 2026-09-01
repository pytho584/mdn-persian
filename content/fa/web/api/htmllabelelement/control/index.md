---
title: "HTMLLabelElement: control property"
short-title: control
slug: Web/API/HTMLLabelElement/control
page-type: web-api-instance-property
browser-compat: api.HTMLLabelElement.control
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`HTMLLabelElement.control`** ارجاعی به کنترل (در قالب یک شیء از نوع {{domxref("HTMLElement")}} یا یکی از مشتقات آن) که عنصر {{HTMLElement("label")}} با آن مرتبط است، برمی‌گرداند. اگر برچسب با هیچ کنترلی مرتبط نباشد، مقدار `null` برمی‌گرداند.

## مقدار

یک شیء مشتق‌شده از {{domxref("HTMLElement")}} که کنترلی را نشان می‌دهد که {{HTMLElement("label")}} با آن مرتبط است؛ یا اگر برچسب به تنهایی باشد، مقدار `null`.

> [!NOTE]
> اگر این ویژگی مقداری داشته باشد و {{domxref("HTMLLabelElement.htmlFor")}} نیز مقداری داشته باشد، ویژگی {{domxref("HTMLLabelElement.htmlFor")}} باید به همان کنترل ارجاع دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLLabelElement")}}
- {{domxref("HTMLElement")}}
- {{HTMLElement("label")}}
- [راهنمای فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)