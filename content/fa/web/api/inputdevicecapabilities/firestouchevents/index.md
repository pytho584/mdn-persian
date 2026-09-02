---
title: "InputDeviceCapabilities: firesTouchEvents property"
---

---
title: "InputDeviceCapabilities: firesTouchEvents property"
short-title: firesTouchEvents
slug: Web/API/InputDeviceCapabilities/firesTouchEvents
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.InputDeviceCapabilities.firesTouchEvents
---

{{APIRef("Input Device Capabilities API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`firesTouchEvents`** از رابط {{domxref("InputDeviceCapabilities")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا دستگاه رویدادهای لمسی را ارسال می‌کند یا نه.

می‌توانید از این ویژگی برای تشخیص رویدادهای ماوس استفاده کنید که نشان‌دهندهٔ عملی هستند که احتمالاً از قبل توسط مدیریت‌کننده‌های رویداد لمسی رسیدگی شده‌اند. این لزوماً به این معنا نیست که دستگاه یک صفحهٔ لمسی است. برای مثال، دستگاه‌های قلمی (stylus) و ماوس معمولاً در مرورگرهای موبایل رویدادهای لمسی تولید می‌کنند.

## مقدار

یک {{jsxref('Boolean')}}

## مثال

```js
myButton.addEventListener("mousedown", (e) => {
  if (!e.sourceCapabilities.firesTouchEvents) myButton.classList.add("pressed");
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}