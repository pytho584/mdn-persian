---
title: "Document: timeline property"
short-title: timeline
slug: Web/API/Document/timeline
page-type: web-api-instance-property
browser-compat: api.Document.timeline
---

{{ APIRef("Web Animations") }}

ویژگی فقط‌خواندنی `timeline` در رابط {{domxref("Document")}}، خط‌زمان پیش‌فرض سند جاری را نشان می‌دهد. این خط‌زمان یک نمونهٔ ویژه از {{domxref("DocumentTimeline")}} است.

این خط‌زمان منحصر به هر `document` است و در تمام طول عمر آن سند، از جمله در فراخوانی‌های {{domxref("Document.open()")}}، پابرجا می‌ماند.

این خط‌زمان زمان را بر حسب میلی‌ثانیه از {{domxref("Performance.timeOrigin")}} بیان می‌کند. پیش از مبدأ زمان، خط‌زمان غیرفعال است و {{domxref("AnimationTimeline.currentTime","currentTime")}} آن `null` است.

> [!NOTE]
> خط‌زمان سندی که با یک سند غیرفعال مرتبط باشد (یک {{domxref("Document")}} که با {{domxref("Window")}}، {{htmlelement("iframe")}} یا {{htmlelement("frame")}} مرتبط نیست) نیز غیرفعال در نظر گرفته می‌شود.

## Value

یک شیء {{domxref("DocumentTimeline")}}.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationTimeline")}}
- {{domxref("AnimationTimeline.currentTime")}}
- {{domxref("DocumentTimeline")}}