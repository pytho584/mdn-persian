---
title: "HTMLElement: autofocus property"
short-title: autofocus
slug: Web/API/HTMLElement/autofocus
page-type: web-api-instance-property
browser-compat: api.HTMLElement.autofocus
---

{{APIRef("HTML DOM")}}

ویژگی **`autofocus`** در رابط {{domxref("HTMLElement")}} یک مقدار بولی است که ویژگی سراسری HTML [`autofocus`](/en-US/docs/Web/HTML/Reference/Global_attributes/autofocus) را بازتاب می‌دهد. این ویژگی مشخص می‌کند که آیا عنصر باید هنگام بارگذاری صفحه فوکوس بگیرد یا اگر درون یک عنصر {{htmlelement("dialog")}} یا [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) تو در تو قرار گرفته باشد، وقتی آن `<dialog>` یا popover نمایش داده می‌شود فوکوس بگیرد.

فقط یک عنصر در یک سند، عنصر `<dialog>` یا popover می‌تواند این ویژگی را داشته باشد. اگر روی چند عنصر اعمال شود، اولین عنصر قابل فوکوس، فوکوس را دریافت می‌کند.

> [!NOTE]
> تنظیم این ویژگی باعث نمی‌شود که فوکوس روی عنصر مرتبط قرار گیرد؛ فقط به مرورگر می‌گوید که وقتی _عنصر در سند درج می‌شود_ آن را فوکوس کند. تنظیم آن پس از درج، یعنی معمولاً پس از بارگذاری سند، هیچ اثر قابل مشاهده‌ای ندارد.

## مقدار

یک مقدار بولی.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}