---
title: "IntersectionObserverEntry: boundingClientRect property"
short-title: boundingClientRect
slug: Web/API/IntersectionObserverEntry/boundingClientRect
page-type: web-api-instance-property
browser-compat: api.IntersectionObserverEntry.boundingClientRect
---

{{APIRef("Intersection Observer API")}}

ویژگی فقط‌خواندنی **`boundingClientRect`** در رابط {{domxref("IntersectionObserverEntry")}} یک {{domxref("DOMRectReadOnly")}} برمی‌گرداند که در اصل کوچک‌ترین مستطیلی را توصیف می‌کند که کل عنصر هدف را در بر می‌گیرد.

## مقدار

یک {{domxref("DOMRectReadOnly")}} که کوچک‌ترین مستطیلِ دربرگیرندهٔ تمام بخش‌های عنصر هدف را توصیف می‌کند؛ یعنی عنصری که تغییر تقاطع آن در حال توصیف است. این مقدار با استفاده از همان الگوریتم {{domxref("Element.getBoundingClientRect()")}} به دست می‌آید؛ بنابراین برای اطلاع از جزئیات دقیق چگونگی محاسبهٔ این مستطیل و اینکه چه چیزهایی در مرزهای آن قرار می‌گیرند یا نمی‌گیرند، به آن مقاله مراجعه کنید.

با این حال، در حالت کلی می‌توانید با خیال راحت آن را به‌عنوان مستطیل مرزیِ عنصر هدف در نظر بگیرید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}