---
title: "HTMLMediaElement: readyState property"
short-title: readyState
slug: Web/API/HTMLMediaElement/readyState
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.readyState
---

{{APIRef("HTML DOM")}}

خاصیت **`HTMLMediaElement.readyState`** وضعیت آمادگی رسانه را نشان می‌دهد.

## مقدار

عددی که یکی از پنج ثابت وضعیت ممکن تعریف‌شده در واسط {{domxref("HTMLMediaElement")}} است:

- `HTMLMediaElement.HAVE_NOTHING` (0)
  - : هیچ اطلاعاتی درباره منبع رسانه در دسترس نیست.
- `HTMLMediaElement.HAVE_METADATA` (1)
  - : به اندازه کافی از منبع رسانه دریافت شده است که ویژگی‌های فراداده مقداردهی اولیه شوند. جستجو دیگر خطا ایجاد نخواهد کرد.
- `HTMLMediaElement.HAVE_CURRENT_DATA` (2)
  - : داده‌هایی برای موقعیت پخش کنونی در دسترس است، اما به اندازه‌ای نیست که بتوان بیش از یک فریم را پخش کرد.
- `HTMLMediaElement.HAVE_FUTURE_DATA` (3)
  - : داده‌هایی برای موقعیت پخش کنونی و همچنین برای حداقل کمی از زمان آینده در دسترس است (به عبارت دیگر، حداقل دو فریم از ویدیو، به عنوان مثال).
- `HTMLMediaElement.HAVE_ENOUGH_DATA` (4)
  - : داده‌های کافی در دسترس است – و نرخ دانلود به اندازه کافی بالا است – که رسانه می‌تواند بدون وقفه تا انتها پخش شود.

## مثال‌ها

این مثال گوش می‌دهد تا داده‌های صوتی برای عنصر `example` بارگذاری شوند. سپس بررسی می‌کند که آیا حداقل موقعیت پخش کنونی بارگذاری شده است. اگر بارگذاری شده باشد، صدا پخش خواهد شد.

```html
<audio id="example" preload="auto">
  <source src="sound.ogg" type="audio/ogg" />
</audio>
```

```js
const obj = document.getElementById("example");

obj.addEventListener("loadeddata", () => {
  if (obj.readyState >= HTMLMediaElement.HAVE_CURRENT_DATA) {
    obj.play();
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: واسطی که برای تعریف خاصیت `HTMLMediaElement.readyState` استفاده شده است.