---
title: "KeyframeEffect: iterationComposite property"
short-title: iterationComposite
slug: Web/API/KeyframeEffect/iterationComposite
page-type: web-api-instance-property
browser-compat: api.KeyframeEffect.iterationComposite
---

{{ APIRef("Web Animations") }}

ویژگی **`iterationComposite`** در یک {{domxref("KeyframeEffect")}} مشخص می‌کند که تغییرات مقدار ویژگی انیمیشن، در هر تکرار (iteration) چگونه روی یکدیگر انباشته می‌شوند یا یکدیگر را بازنویسی می‌کنند.

## مقدار

یکی از موارد زیر:

- `replace`
  - : مقدار تولیدشدهٔ `keyframeEffect` مستقل از تکرار فعلی است.
- `accumulate`
  - : تکرارهای بعدیِ `keyframeEffect` بر اساس مقدار نهایی تکرار قبلی ساخته می‌شوند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- ویژگی اشیاء {{domxref("KeyframeEffect")}}