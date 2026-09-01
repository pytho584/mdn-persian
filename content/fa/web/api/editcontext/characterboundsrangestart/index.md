---
title: "EditContext: characterBoundsRangeStart property"
short-title: characterBoundsRangeStart
slug: Web/API/EditContext/characterBoundsRangeStart
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.EditContext.characterBoundsRangeStart
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`characterBoundsRangeStart`** از رابط {{domxref("EditContext")}}، شاخص کاراکتری را در محتوای متنی قابل ویرایش نشان می‌دهد که با اولین آیتم در آرایه {{domxref("EditContext.characterBounds()", "characterBounds")}} مطابقت دارد.

برای مثال، اگر `EditContext` شامل کاراکترهای `abc` باشد و `characterBoundsRangeStart` برابر با `1` باشد، اولین آیتم در آرایه `characterBounds` شامل مرزهای کاراکتر `b` خواهد بود.

## مقدار

یک {{jsxref("Number")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}