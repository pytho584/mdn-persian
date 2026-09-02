---
title: "MouseEvent: button property"
short-title: button
slug: Web/API/MouseEvent/button
page-type: web-api-instance-property
browser-compat: api.MouseEvent.button
---

{{APIRef("Pointer Events")}}

ویژگی فقط‌خواندنی **`MouseEvent.button`** نشان می‌دهد کدام دکمهٔ ماوس برای به‌وجود آمدن رویداد فشرده یا رها شده است.

این ویژگی فقط تضمین می‌کند که در رویدادهای ناشی از فشردن یا رها کردن یک یا چند دکمه، مشخص کند کدام دکمه‌ها فشرده یا رها شده‌اند. بنابراین، برای رویدادهایی مانند {{domxref("Element/mouseenter_event", "mouseenter")}}، {{domxref("Element/mouseleave_event", "mouseleave")}}، {{domxref("Element/mouseover_event", "mouseover")}}، {{domxref("Element/mouseout_event", "mouseout")}} یا {{domxref("Element/mousemove_event", "mousemove")}} قابل‌اعتماد نیست.

کاربران ممکن است پیکربندی دکمه‌های دستگاه اشاره‌گر خود را تغییر دهند؛ بنابراین اگر ویژگی button یک رویداد صفر باشد، ممکن است آن رویداد توسط دکمه‌ای که از نظر فیزیکی در سمت چپ دستگاه اشاره‌گر قرار دارد ایجاد نشده باشد. اما باید رفتاری داشته باشد که گویی در چیدمان استاندارد دکمه‌ها، دکمهٔ چپ کلیک شده است.

> [!NOTE]
> این ویژگی را با ویژگی {{domxref("MouseEvent.buttons")}} اشتباه نگیرید؛ ویژگی اخیر مشخص می‌کند در همهٔ انواع رویدادهای ماوس کدام دکمه‌ها فشرده شده‌اند.

## مقدار

عددی که نمایانگر یک دکمهٔ مشخص است:

- `0`: دکمهٔ اصلی، معمولاً دکمهٔ چپ یا حالت مقداردهی‌نشده
- `1`: دکمهٔ کمکی، معمولاً دکمهٔ چرخ یا دکمهٔ وسط (در صورت وجود)
- `2`: دکمهٔ ثانویه، معمولاً دکمهٔ راست
- `3`: دکمهٔ چهارم، معمولاً دکمهٔ _بازگشت در مرورگر_
- `4`: دکمهٔ پنجم، معمولاً دکمهٔ _رفتن به جلو در مرورگر_

همانطور که در بالا اشاره شد، ممکن است دکمه‌ها برخلاف چیدمان استاندارد «چپ به راست» پیکربندی شده باشند. ماوسی که برای استفاده با دست چپ تنظیم شده باشد ممکن است عملکرد دکمه‌ها را معکوس کرده باشد. برخی دستگاه‌های اشاره‌گر فقط یک دکمه دارند و برای نشان دادن دکمهٔ اصلی، ثانویه، کمکی و غیره از صفحه‌کلید یا سایر سازوکارهای ورودی استفاده می‌کنند. برخی دیگر ممکن است دکمه‌های زیادی داشته باشند که به عملکردها و مقادیر دکمه‌های مختلف نگاشته شده‌اند.

## نمونه‌ها

### HTML

```html
<button id="button">Click here with your mouse…</button>
<p id="log"></p>
```

### جاوااسکریپت

```js
const button = document.querySelector("#button");
const log = document.querySelector("#log");
button.addEventListener("mouseup", (e) => {
  switch (e.button) {
    case 0:
      log.textContent = "Left button clicked.";
      break;
    case 1:
      log.textContent = "Middle button clicked.";
      break;
    case 2:
      log.textContent = "Right button clicked.";
      break;
    default:
      log.textContent = `Unknown button code: ${e.button}`;
  }
});
button.addEventListener("contextmenu", (e) => {
  e.preventDefault();
});
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MouseEvent")}}