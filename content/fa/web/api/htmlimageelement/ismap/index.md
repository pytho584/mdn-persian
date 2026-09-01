---
title: "HTMLImageElement: isMap property"
short-title: isMap
slug: Web/API/HTMLImageElement/isMap
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.isMap
---

{{APIRef("HTML DOM")}}

ویژگی **`isMap`** در رابط {{domxref("HTMLImageElement")}} نشان می‌دهد که تصویر بخشی از یک [نقشه سمت سرور](https://en.wikipedia.org/wiki/Image_map#Server-side) است. اگر چنین باشد، مختصاتی که کاربر روی تصویر کلیک کرده به سرور ارسال می‌شود. این ویژگی منعکس‌کنندهٔ ویژگی محتوایی [`ismap`](/en-US/docs/Web/HTML/Reference/Elements/img#ismap) عنصر `<img>` است. این ویژگی فقط زمانی مجاز است که عنصر `<img>` از نوادگان یک عنصر {{htmlelement("a")}} با ویژگی [`href`](/en-US/docs/Web/HTML/Reference/Elements/a#href) معتبر باشد.

> [!NOTE]
> به دلایل دسترس‌پذیری، معمولاً باید از استفاده از نقشه‌های تصویری سمت سرور خودداری کنید، زیرا آن‌ها به استفاده از ماوس نیاز دارند. در عوض از [نقشه تصویری سمت کلاینت](/en-US/docs/Web/HTML/How_to/Add_a_hit_map_on_top_of_an_image) استفاده کنید.

## مقدار

یک مقدار بولی که اگر تصویر برای نقشه تصویری سمت سرور استفاده شود `true` است؛ در غیر این صورت مقدار `false` است.

## نکات استفاده

وقتی روی تصویری که به عنوان بخشی از نقشه تصویری سمت سرور علامت‌گذاری شده کلیک می‌شود، مرورگر رشتهٔ «?x,y» را می‌سازد که در آن x و y مختصات نقطه‌ای را نشان می‌دهند که ماوس در آن کلیک شده است و به صورت فاصله از گوشهٔ بالا-چپ تصویر و بر حسب پیکسل‌های CSS مشخص می‌شوند.

سپس مرورگر آن URL را از سرور دریافت می‌کند و بسته به مقدار ویژگی [`download`](/en-US/docs/Web/HTML/Reference/Elements/a#download) آن را نمایش می‌دهد یا دانلود می‌کند.

برخلاف نقشه‌های تصویری سمت سرور، نقشه‌های تصویری سمت کلاینت باعث نمی‌شوند که عنصر {{HTMLElement("img")}} حالت محتوای تعاملی را اتخاذ کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}