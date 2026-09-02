---
title: "MediaError"
slug: Web/API/MediaError
page-type: web-api-interface
browser-compat: api.MediaError
---

{{APIRef("HTML DOM")}}

رابط (Interface) **`MediaError`** نشان‌دهنده‌ی خطایی است که هنگام پردازش رسانه در یک عنصر رسانه‌ای HTML مبتنی بر {{domxref("HTMLMediaElement")}} (مانند {{HTMLElement("audio")}} یا {{HTMLElement("video")}}) رخ داده است.

یک شیء `MediaError` خطا را به صورت کلی با استفاده از یک `code` عددی که نوع خطا را دسته‌بندی می‌کند و یک `message` که اطلاعات تشخیصی خاصی درباره‌ی مشکل پیش‌آمده ارائه می‌دهد، توصیف می‌کند.

## ویژگی‌های نمونه (Instance properties)

_این رابط هیچ ویژگی‌ای را به ارث نمی‌برد._

- {{domxref("MediaError.code")}}
  - : عددی که [نوع کلی خطای رخ داده](/en-US/docs/Web/API/MediaError/code#media_error_code_constants) را نشان می‌دهد.
- {{domxref("MediaError.message")}}
  - : یک رشته‌ی قابل خواندن برای انسان که _اطلاعات تشخیصی خاصی_ را برای کمک به درک شرایط خطا به خواننده ارائه می‌دهد؛ به طور خاص، این رشته خلاصه‌ای از معنای کد خطا نیست، بلکه اطلاعات تشخیصی واقعی برای کمک به فهم دقیق مشکل است. متن و قالب این رشته توسط مشخصات تعریف نشده است و از یک {{Glossary("user agent")}} به دیگری متفاوت خواهد بود. اگر اطلاعات تشخیصی در دسترس نباشد یا توضیحی قابل ارائه نباشد، این مقدار یک رشته‌ی خالی (`""`) است.

## روش‌های نمونه (Instance methods)

_این رابط هیچ روشی را پیاده‌سازی یا به ارث نمی‌برد و روش خاص خود را نیز ندارد._

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement.error")}}