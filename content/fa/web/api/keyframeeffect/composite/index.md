```markdown
---
title: "KeyframeEffect: composite property"
short-title: composite
slug: Web/API/KeyframeEffect/composite
page-type: web-api-instance-property
browser-compat: api.KeyframeEffect.composite
---

{{ APIRef("Web Animations") }}

خاصیت **`composite`** در {{domxref("KeyframeEffect")}} مشخص می‌کند که انیمیشن یک عنصر چگونه بر مقادیر ویژگی‌های زیربنایی آن اثر می‌گذارد.

## مقدار

برای درک این مقادیر، مثال یک `keyframeEffect` با مقدار `blur(2)` را در نظر بگیرید که روی مقدار ویژگی زیربنایی `blur(3)` اعمال می‌شود.

- `replace`
  - : `keyframeEffect` مقدار زیربنایی را که با آن ترکیب می‌شود **بازنویسی** می‌کند: `blur(2)` جایگزین `blur(3)` می‌شود.
- `add`
  - : `keyframeEffect` به مقدار زیربنایی که با آن ترکیب می‌شود **اضافه** می‌شود (یا به عبارت دیگر _افزایشی_): `blur(2) blur(3)`.
- `accumulate`
  - : `keyframeEffect` روی مقدار زیربنایی **انباشته** می‌شود: `blur(5)`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- ویژگی مربوط به اشیاء {{domxref("KeyframeEffect")}}
- {{Glossary("Composite operation")}}
```