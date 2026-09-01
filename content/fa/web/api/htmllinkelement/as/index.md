---
title: "HTMLLinkElement: as property"
short-title: as
slug: Web/API/HTMLLinkElement/as
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.as
---

{{APIRef("HTML DOM")}}

خاصیت **`as`** از رابط {{domxref("HTMLLinkElement")}} یک رشته را برمی‌گرداند که نشان‌دهنده نوع محتوایی است که توسط یک عنصر پیوند (link) از پیش بارگیری می‌شود (preload).

خاصیت `as` برای عناصر پیوندی که [`rel="preload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) دارند باید مقدار داشته باشد، در غیر این صورت منبع واکشی نخواهد شد. همچنین می‌تواند برای عناصر پیوندی با [`rel="modulepreload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/modulepreload) به کار رود، اما در صورت حذف، مقدار پیش‌فرض آن `script` خواهد بود. این خاصیت نباید برای انواع دیگر عناصر پیوند، مانند `rel="prefetch"` تنظیم شود.

این خاصیت منعکس‌کننده مقدار [`as` attribute](/en-US/docs/Web/HTML/Reference/Elements/link#as) المان HTML [`<link>`](/en-US/docs/Web/HTML/Reference/Elements/link) است.

## مقدار

یک رشته با مقادیر مجاز زیر: `"audio"`، `"document"`، `"embed"`، `"fetch"`، `"font"`، `"image"`، `"object"`، `"script"`، `"style"`، `"track"`، `"video"`، `"worker"`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}