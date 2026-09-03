---
title: OverconstrainedError
slug: Web/API/OverconstrainedError
page-type: web-api-interface
browser-compat: api.OverconstrainedError
---

{{APIRef("Media Capture and Streams")}}

رابط **`OverconstrainedError`** از [API ضبط و جریان‌های رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API) نشان می‌دهد که مجموعه قابلیت‌های مورد نظر برای {{domxref('MediaStreamTrack')}} فعلی در حال حاضر قابل برآورده شدن نیست. هنگامی که این رویداد روی یک `MediaStreamTrack` صادر می‌شود، آن مسیر تا زمانی که محدودیت‌های فعلی قابل اعمال شوند یا محدودیت‌های قابل قبولی اعمال شوند، بی‌صدا می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("OverconstrainedError.OverconstrainedError", "OverconstrainedError()")}}
  - : یک شیء جدید `OverconstrainedError` ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌هایی را از رابط والد خود، {{domxref('DOMException')}}، به ارث می‌برد._

- {{domxref("OverconstrainedError.constraint")}} {{ReadOnlyInline}}
  - : محدودیتی را که در سازنده ارائه شده بود، یعنی محدودیتی که برآورده نشده است، برمی‌گرداند.

## روش‌های نمونه

_همچنین روش‌هایی را از رابط والد خود، {{domxref('DOMException')}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}