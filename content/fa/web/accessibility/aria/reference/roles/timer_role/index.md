---
title: "ARIA: timer role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/timer_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: timer role"
short-title: timer
slug: Web/Accessibility/ARIA/Reference/Roles/timer_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#timer
sidebar: accessibilitysidebar
---

نقش **`timer`** به فناوری‌های کمکی اعلام می‌کند که یک عنصر شمارشگر عددی است که مقدار زمان سپری‌شده از یک نقطه شروع یا زمان باقی‌مانده تا یک نقطه پایان را فهرست می‌کند. فناوری‌های کمکی به‌روزرسانی‌های تایمر را اعلام نمی‌کنند، زیرا مقدار ضمنی [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) آن `off` است.

```html
<div role="timer" id="eggtimer">0</div>
```

این عنصر `div` را به‌عنوان یک تایمر بدون زمان باقی‌مانده تعریف می‌کند.

## توضیحات

نقش `timer` به فناوری‌های کمکی اعلام می‌کند که این بخش از محتوای وب یک ناحیه زنده (live region) است که شامل یک تایمر فهرست‌کننده زمان باقی‌مانده یا زمان سپری‌شده است. متن داخلی تایمر باید یک اندازه‌گیری زمانی فعلی باشد که به‌روزرسانی می‌شود. هرچند مقدار لزوماً نباید قابل تجزیه ماشینی باشد، اما باید به‌طور مداوم در فواصل منظم به‌روزرسانی شود، مگر اینکه تایمر متوقف شده یا به نقطه پایان خود رسیده باشد.

نقش `timer` همراه با نقش‌های [`alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role)، [`log`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role)، [`marquee`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role) و [`status`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role) یک ناحیه زنده است و می‌تواند توسط ویژگی‌های [ناحیه زنده](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) تغییر کند.

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : برخی از صفحه‌خوان‌ها نام یک عنصر تایمر را قبل از اعلام محتویات آن اعلام می‌کنند. اگر نامی قابل مشاهده است، با استفاده از `aria-labelledby` به آن ارجاع دهید. گنجاندن `aria-label` روشی برای پیشوند کردن محتوای قابل مشاهده یک عنصر تایمر با متنی فراهم می‌کند که هنگام خواندن محتوا توسط صفحه‌خوان نمایش داده نمی‌شود. نام‌گذاری تایمر الزامی نیست، بنابراین اگر چیز مناسبی وجود ندارد، هر دو ویژگی را می‌توان حذف کرد.

- [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)
  - : عناصر با نقش `timer` دارای مقدار ضمنی `aria-live` برابر با `off` هستند.

## نگرانی‌های دسترس‌پذیری

اگر نیاز به یک محدودیت زمانی وجود داشته باشد، مثلاً به دلایل امنیتی، کاربر باید گزینه خاموش کردن یا تمدید آن را داشته باشد. این محدودیت در مواردی که محدودیت زمانی به دلیل یک رویداد زنده مانند مزایده یا بازی باشد، یا زمانی که زمان تکمیل فرم برای یک ارسال معتبر ضروری است، اعمال نمی‌شود.

## مثال‌ها

### یک تایمر پایه

این مثال دارای یک تایمر است که از ۳۰ ثانیه به ۰ ثانیه شمارش معکوس می‌کند. کل ناحیه نمایش زمان دارای `role="timer"` و همچنین [`aria-atomic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-atomic) است تا نشان دهد ناحیه باید به‌طور کامل اعلام شود، نه فقط بخش‌های تغییر یافته. به دلیل `aria-live="off"` ضمنی، تغییرات به‌طور پیش‌فرض اعلام نمی‌شوند؛ ما به‌صورت دستی نقش را وقتی تایمر به ۱۰ ثانیه باقی‌مانده می‌رسد به `"alert"` تغییر می‌دهیم تا یک بار اعلام شود.

```html
<div id="countdown" role="timer" aria-atomic="true">
  <span id="number">30</span> seconds left!
</div>
```

```css
html {
  font-size: 50px;
  text-align: center;
  margin-top: 1em;
  font-family: sans-serif;
}

#number {
  font-family: monospace;
  color: #cc0000;
  font-weight: bold;
  font-size: 1.25em;
  vertical-align: middle;
}
```

```js
const numElement = document.getElementById("number");
const liveRegion = document.getElementById("countdown");
let startTime = new Date().getTime();

function decrement() {
  const timeNow = new Date().getTime();
  const elapsedTime = Math.floor((timeNow - startTime) / 1000);
  let newNumber = 30 - elapsedTime;

  if (newNumber >= 0) {
    numElement.textContent = newNumber;
  }

  if (newNumber === 10) {
    liveRegion.setAttribute("role", "alert");
    setTimeout(() => {
      liveRegion.setAttribute("role", "timer");
    }, 999);
  }
}

window.setInterval(() => {
  decrement();
}, 500);
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش ARIA: `alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role)
- [نقش ARIA: `log`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/log_role)
- [نقش ARIA: `marquee`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/marquee_role)
- [نقش ARIA: `status`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role)
- [نواحی زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)