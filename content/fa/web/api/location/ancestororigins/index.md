---
title: "Location: ancestorOrigins property"
short-title: ancestorOrigins
slug: Web/API/Location/ancestorOrigins
page-type: web-api-instance-property
browser-compat: api.Location.ancestorOrigins
---

{{APIRef("Location")}}

خاصیت فقط‑خواندنی **`ancestorOrigins`** از رابط {{domxref("Location")}} یک {{domxref("DOMStringList")}} ایستا است که به ترتیب معکوس، خاستگاه (origin) تمام زمینه‌های مرورگر اجداد (ancestor browsing contexts) سند مرتبط با شیء {{domxref("Location")}} داده شده را شامل می‌شود.

می‌توانید از `location.ancestorOrigins` در اسکریپت یک سند استفاده کنید تا مثلاً تشخیص دهید که آیا سند توسط سایتی که انتظارش را ندارید در یک فریم قرار گرفته است یا خیر. همچنین می‌توانید از آن برای تغییر رفتار سند بر اساس اینکه چه سایتی یا چه فهرستی از سایت‌ها آن را در فریم قرار داده‌اند، استفاده کنید.

> **یادداشت:** صفت [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/iframe#referrerpolicy) یک `<iframe>` جاساز شده روی این فهرست تأثیر می‌گذارد. تنظیم `referrerpolicy` به `no-referrer` یا به `same-origin` وقتی سند فریم‌شده cross-origin است، خاستگاه سند حاوی `<iframe>` را از فهرست `ancestorOrigins` سند فریم‌شده حذف می‌کند. خاستگاه با یک خاستگاه مبهم (opaque origin) جایگزین می‌شود که به صورت `"null"` سریال‌سازی می‌گردد.

## مقدار

یک {{domxref("DOMStringList")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}