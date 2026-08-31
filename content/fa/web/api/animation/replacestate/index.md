---
title: "Animation: replaceState property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/replaceState"
translated_by: "n8n + AI"
---

---
title: "Animation: replaceState property"
short-title: replaceState
slug: Web/API/Animation/replaceState
page-type: web-api-instance-property
browser-compat: api.Animation.replaceState
---

{{ APIRef("Web Animations") }}

ویژگی فقط‌خواندنی **`Animation.replaceState`** از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) نشان می‌دهد که آیا انیمیشن پس از جایگزین‌شدن با انیمیشن دیگر، [به‌طور خودکار توسط مرورگر حذف شده است](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#automatically_removing_filling_animations) یا خیر.

## مقدار

یک رشته که وضعیت جایگزینی انیمیشن را نشان می‌دهد. مقدار می‌تواند یکی از موارد زیر باشد:

- `active`
  - : مقدار اولیه وضعیت جایگزینی انیمیشن هنگام ایجاد آن.
- `persisted`
  - : انیمیشن به‌طور صریح با فراخوانی {{domxref("Animation.persist()")}} بر روی آن ماندگار شده است.
- `removed`
  - : انیمیشن به‌طور خودکار توسط مرورگر حذف شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}
- رویداد {{domxref("Animation.remove_event","remove")}}
- {{domxref("Animation.persist()")}}