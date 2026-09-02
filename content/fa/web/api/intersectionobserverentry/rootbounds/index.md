---
title: "IntersectionObserverEntry: rootBounds property"
short-title: rootBounds
slug: Web/API/IntersectionObserverEntry/rootBounds
page-type: web-api-instance-property
browser-compat: api.IntersectionObserverEntry.rootBounds
---

{{APIRef("Intersection Observer API")}}

ویژگی فقط-خواندنی **`rootBounds`** از رابط {{domxref("IntersectionObserverEntry")}} یک {{domxref("DOMRectReadOnly")}} است که معادل مستطیل تقاطع ریشه (root intersection rectangle) هدف ({{domxref("IntersectionObserverEntry.target", "target")}}) می‌باشد، که در صورت مشخص شدن مقدار {{domxref("IntersectionObserver.rootMargin")}}، توسط آن افست (offset) شده است.

## مقدار

یک {{domxref("DOMRectReadOnly")}} که مستطیل تقاطع ریشه را توصیف می‌کند. برای ریشه‌هایی که viewport سند ({{domxref("Document")}}) هستند، این مستطیل، مستطیل مرزهای (bounds rectangle) کل سند است. در غیر این صورت، مرزهای عنصر ریشه است. این مستطیل توسط مقادیر موجود در {{domxref("IntersectionObserver.rootMargin")}} افست می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}