---
title: "InputDeviceCapabilities: InputDeviceCapabilities() constructor"
short-title: InputDeviceCapabilities()
slug: Web/API/InputDeviceCapabilities/InputDeviceCapabilities
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.InputDeviceCapabilities.InputDeviceCapabilities
---

{{APIRef("Input Device Capabilities API")}}{{SeeCompatTable}}

سازندهٔ `InputDeviceCapabilities()` یک شیء جدید از {{domxref("InputDeviceCapabilities")}} می‌سازد که اطلاعاتی دربارهٔ دستگاه فیزیکی مسئول تولید یک رویداد لمسی فراهم می‌کند.

## سینتکس

```js-nolint
new InputDeviceCapabilities()
new InputDeviceCapabilities(InputDeviceCapabilitiesInit)
```

### پارامترها

- `InputDeviceCapabilitiesInit` {{optional_inline}}
  - : یک شیء دیکشنری شامل مجموعه‌ای از قابلیت‌های دستگاه. این شیء دارای ویژگی زیر است.
    - `fireTouchEvents`: یک مقدار بولی (Boolean) که نشان می‌دهد آیا دستگاه رویدادهای لمسی را ارسال می‌کند یا نه.

### مقدار بازگشتی

یک نمونه از رابط (interface) {{domxref("InputDeviceCapabilities")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}