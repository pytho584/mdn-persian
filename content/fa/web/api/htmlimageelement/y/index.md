---
title: "HTMLImageElement: y property"
short-title: y
slug: Web/API/HTMLImageElement/y
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.y
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`y`** از رابط {{domxref("HTMLImageElement")}}، مختصات y لبه بالایی حاشیه عنصر {{HTMLElement("img")}} را نسبت به مبدأ عنصر ریشه نشان می‌دهد.

## مقدار

یک مقدار صحیح که فاصله را بر حسب پیکسل از لبه بالایی نزدیک‌ترین عنصر ریشه عنصر تا لبه بالایی جعبه مرزی (border box) عنصر {{HTMLElement("img")}} نشان می‌دهد. نزدیک‌ترین عنصر ریشه، بیرونی‌ترین عنصر {{HTMLElement("html")}} است که تصویر را در بر می‌گیرد. اگر تصویر در یک {{HTMLElement("iframe")}} قرار داشته باشد، مقدار `y` نسبت به همان قاب محاسبه می‌شود.

در نمودار زیر، لبه بالایی حاشیه، لبه بالایی ناحیه آبی padding است. بنابراین مقدار بازگشتی `y` فاصله از آن نقطه تا لبه بالایی ناحیه محتوا خواهد بود.

![نموداری که رابطه بین جعبه‌های مختلف مرتبط با یک عنصر را نشان می‌دهد](boxmodel-3.png)

## مثال‌ها

برای مثال‌ها، صفحه ویژگی {{domxref("HTMLImageElement.x", "x")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLImageElement.x")}}