---
title: "DocumentTimeline"
---

---
title: DocumentTimeline
slug: Web/API/DocumentTimeline
page-type: web-api-interface
browser-compat: api.DocumentTimeline
---

{{ APIRef("Web Animations") }}

رابط **`DocumentTimeline`** در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) نشاندهندهٔ خط‌های زمانی انیمیشن است، از جمله خط زمانی پیش‌فرض سند (که از طریق {{domxref("Document.timeline")}} قابل دسترسی است).

{{InheritanceDiagram}}

## سازنده

- {{domxref("DocumentTimeline.DocumentTimeline", "DocumentTimeline()")}}
  - : یک شیء `DocumentTimeline` جدید مرتبط با سند فعالِ بافتار مرور فعلی ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط ویژگی خود را از والد خود، {{domxref("AnimationTimeline")}}، به ارث می‌برد._

- {{domxref("AnimationTimeline.currentTime")}}
  - : مقدار زمان را بر حسب میلی‌ثانیه برای این خط زمانی برمی‌گرداند، یا اگر غیرفعال باشد، `null` را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationTimeline")}}
- {{domxref("AnimationTimeline.currentTime")}}
- {{domxref("Document.timeline")}}
- {{domxref("DocumentTimeline.DocumentTimeline", "DocumentTimeline()")}}