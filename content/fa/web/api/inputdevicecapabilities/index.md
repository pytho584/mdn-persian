---
title: "InputDeviceCapabilities"
---

---
title: InputDeviceCapabilities
slug: Web/API/InputDeviceCapabilities
page-type: web-api-interface
status:
  - experimental
browser-compat: api.InputDeviceCapabilities
---

{{APIRef("Input Device Capabilities API")}}{{SeeCompatTable}}

رابط **`InputDeviceCapabilities`** از {{domxref("InputDeviceCapabilities API", "Input Device Capabilities API", "", "nocode")}} اطلاعاتی درباره دستگاه فیزیکی یا گروهی از دستگاه‌های مرتبط که مسئول تولید رویدادهای ورودی هستند، فراهم می‌کند. رویدادهایی که توسط یک دستگاه ورودی فیزیکی یکسان ایجاد می‌شوند، نمونه یکسانی از این شیء دریافت می‌کنند، اما عکس این موضوع درست نیست. به‌عنوان مثال، دو ماوس با قابلیت‌های یکسان در یک سیستم ممکن است به‌صورت یک نمونه `InputDeviceCapabilities` ظاهر شوند.

در برخی موارد، `InputDeviceCapabilities` قابلیت‌های دستگاه‌های منطقی را به‌جای دستگاه‌های فیزیکی نشان می‌دهد. این امکان را فراهم می‌کند که برای مثال، صفحه‌کلیدهای لمسی و صفحه‌کلیدهای فیزیکی وقتی ورودی یکسانی تولید می‌کنند، به یک شکل نمایش داده شوند.

## سازنده‌ها

- {{domxref("InputDeviceCapabilities.InputDeviceCapabilities", "InputDeviceCapabilities()")}} {{Experimental_Inline}}
  - : یک شیء `InputDeviceCapabilities` می‌سازد.

## ویژگی‌های نمونه

- {{DOMxRef("InputDeviceCapabilities.firesTouchEvents")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{JSxRef("Boolean")}} که نشان می‌دهد آیا دستگاه رویدادهای لمسی را ارسال می‌کند یا خیر.

## روش‌های نمونه

هیچ‌کدام.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}