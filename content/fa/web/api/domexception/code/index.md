---
title: "DOMException: code property"
short-title: code
slug: Web/API/DOMException/code
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.DOMException.code
---

{{APIRef("DOM")}}{{AvailableInWorkers}}{{deprecated_header}}

خاصیت فقط خواندنی **`code`** از رابط {{domxref("DOMException")}} یکی از [ثابت‌های کد خطا](/en-US/docs/Web/API/DOMException#error_names) قدیمی را برمی‌گرداند، یا اگر هیچ‌کدام مطابقت نداشت، `0` را برمی‌گرداند.

این فیلد به دلایل تاریخی استفاده می‌شود. استثناهای جدید DOM دیگر از این استفاده نمی‌کنند: این اطلاعات را در ویژگی {{domxref("DOMException.name")}} قرار می‌دهند.

## مقدار

یکی از [ثابت‌های کد خطا](/en-US/docs/Web/API/DOMException#error_names)، یا `0` اگر هیچ‌کدام مطابقت نداشت.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}