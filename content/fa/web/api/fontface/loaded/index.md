---
title: "FontFace: loaded property"
short-title: loaded
slug: Web/API/FontFace/loaded
page-type: web-api-instance-property
browser-compat: api.FontFace.loaded
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

خاصیت‌ی فقط‌خواندنی **`loaded`** در رابط {{domxref("FontFace")}} یک {{jsxref('Promise')}} برمی‌گرداند که وقتی فونت مشخص‌شده در سازندهٔ شیء بارگذاری شود، با همان شیء `FontFace` فعلی resolve می‌شود، یا در صورت بروز خطا، با یک `SyntaxError` reject می‌شود.

## مقدار

یک {{jsxref('Promise')}} که با شیء `FontFace` فعلی resolve می‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}