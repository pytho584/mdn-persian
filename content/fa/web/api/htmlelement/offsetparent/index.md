---
title: "HTMLElement: offsetParent property"
---

---
title: "HTMLElement: offsetParent property"
short-title: offsetParent
slug: Web/API/HTMLElement/offsetParent
page-type: web-api-instance-property
browser-compat: api.HTMLElement.offsetParent
---

{{ APIRef("HTML DOM") }}

ویژگی فقطخواندنی **`HTMLElement.offsetParent`** ارجاعی به عنصری برمی‌گرداند که نزدیک‌ترین جدِ دارای موقعیت (positioned ancestor) است؛ یعنی نزدیک‌ترین عنصر در زنجیرهٔ دربرگیری والدها.

یک جدِ موقعیت‌دار می‌تواند یکی از موارد زیر باشد:

- یک [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block#identifying_the_containing_block) برای عناصر دارای موقعیت مطلق (absolutely positioned)
- عنصری که مقدار [zoom](/en-US/docs/Web/CSS/Reference/Properties/zoom) مؤثر آن (یعنی حاصل‌ضرب تمام مقیاس‌های zoom والدهایش) با مقدار zoom این عنصر متفاوت باشد
- عناصر `td`، `th` یا `table` در صورتی که خودِ عنصر دارای موقعیت static باشد

اگر هیچ عنصر جدِ موقعیت‌داری وجود نداشته باشد، عنصر `body` برگردانده می‌شود.

> [!NOTE]
> `offsetParent` در شرایط زیر مقدار `null` برمی‌گرداند:
>
> - عنصر یا هر یک از اجدادش، ویژگی `display` را روی `none` تنظیم کرده باشد.
> - عنصر ویژگی `position` را روی `fixed` داشته باشد و containing block آن، viewport باشد.
>   اگر containing block، viewport نباشد، `offsetParent` نزدیک‌ترین جدی را برمی‌گرداند که یک containing block تشکیل می‌دهد؛ مثلاً جدی که استایل‌های `transform`، `perspective` یا `filter` روی آن تنظیم شده است.
> - عنصر، `<body>` یا `<html>` باشد.

`offsetParent` مفید است، زیرا {{domxref("HTMLElement.offsetTop","offsetTop")}} و {{domxref("HTMLElement.offsetLeft","offsetLeft")}} نسبت به لبهٔ padding عنصر `offsetParent` سنجیده می‌شوند.

## مقدار

یک ارجاع شیء به عنصری که عنصر فعلی نسبت به آن آفست (offset) شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}