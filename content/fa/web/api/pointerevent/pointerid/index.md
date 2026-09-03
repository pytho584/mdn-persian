---
title: "PointerEvent: pointerId property"
short-title: pointerId
slug: Web/API/PointerEvent/pointerId
page-type: web-api-instance-property
browser-compat: api.PointerEvent.pointerId
---

{{ APIRef("Pointer Events") }}

ویژگی فقط‌خواندنی **`pointerId`** در رابط {{domxref("PointerEvent")}}، شناسه‌ای است که به وسیلهٔ اشاره‌گرِ رویداد را فعال کرده اختصاص داده می‌شود. این شناسه یکتا است و با شناسه‌های همهٔ رویدادهای اشاره‌گر فعال دیگر متفاوت است.

مقدار `1-` نشان می‌دهد که PointerEvent توسط یک دستگاه اشاره‌گر تولید نشده است. (مثلاً رویداد {{domxref("Element/click_event", "click")}} که بر روی دکمه‌ای فعال‌شده با صفحه‌کلید رخ می‌دهد.) در غیر این صورت، مقدار ممکن است به‌صورت تصادفی تولید شده باشد و نباید برای انتقال اطلاعات خاصی دربارهٔ دستگاه به آن تکیه کرد. این مقدار فقط تضمین می‌شود که برای طول عمر صفحه یا نشست پایدار بماند.

> [!NOTE]
> ویژگی `pointerId` در مرورگرهای مختلف به‌طور ناسازگاری پیاده‌سازی شده است و همیشه برای هر ضربه قلم یا تعامل با صفحه‌نمایش پایدار نمی‌ماند. برای روشی مطمئن برای شناسایی همزمان چند دستگاه اشاره‌گر روی صفحه‌نمایش، به {{domxref("PointerEvent.persistentDeviceId")}} مراجعه کنید.

## مقدار

یک عدد.

## مثال‌ها

قطعه کد زیر یک `pointerId` ذخیره‌شده قبلی را با `pointerId` رویداد {{domxref("Element/pointerdown_event", "pointerdown")}} که به‌تازگی رخ داده مقایسه می‌کند.

```js
let id; // بگذارید فرض کنیم این یک pointerId ذخیره‌شده قبلی است

target.addEventListener("pointerdown", (event) => {
  // شناسه رویداد قبلی را که کش شده بود
  // با شناسه رویداد فعلی مقایسه و بر اساس آن عمل کنید
  if (id === event.pointerId) process_event(event);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
