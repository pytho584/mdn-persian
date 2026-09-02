---
title: "MutationRecord: attributeNamespace property"
short-title: attributeNamespace
slug: Web/API/MutationRecord/attributeNamespace
page-type: web-api-instance-property
browser-compat: api.MutationRecord.attributeNamespace
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`attributeNamespace`** از {{domxref("MutationRecord")}}، فضای نام (namespace) صفت تغییریافته در {{domxref("MutationRecord")}} است که توسط یک {{domxref("MutationObserver")}} مشاهده شده است.

## مقدار

اگر [`type`](/en-US/docs/Web/API/MutationRecord/type) رکورد برابر با `attributes` باشد، این ویژگی رشته‌ای است که فضای نام صفت تغییریافتهٔ هدف جهش (mutation target) را نشان می‌دهد. در غیر این صورت مقدار آن `null` است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
