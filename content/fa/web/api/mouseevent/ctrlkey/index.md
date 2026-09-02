---
title: "MouseEvent: ctrlKey property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent/ctrlKey"
---

---
title: "MouseEvent: ctrlKey property"
short-title: ctrlKey
slug: Web/API/MouseEvent/ctrlKey
page-type: web-api-instance-property
browser-compat: api.MouseEvent.ctrlKey
---

{{APIRef("Pointer Events")}}

ویژگی فقط‌خواندنی **`MouseEvent.ctrlKey`** یک مقدار بولی است که نشان می‌دهد آیا کلید <kbd>ctrl</kbd> هنگام وقوع یک رویداد ماوس خاص فشرده شده بود یا نه.

در صفحه‌کلیدهای Macintosh، این کلید با نام <kbd>control</kbd> شناخته می‌شود. همچنین توجه داشته باشید که در مک، کلیک همراه با کلید <kbd>control</kbd> توسط سیستم عامل رهگیری شده و برای باز کردن منوی زمینه استفاده می‌شود، بنابراین `ctrlKey` در رویدادهای کلیک قابل تشخیص نیست.

بزرگ‌نمایی با حرکت پینچ روی ترک‌پد نیز یک رویداد {{domxref("Element/wheel_event", "wheel")}} شبیه‌سازی‌شده با `ctrlKey` برابر با `true` ارسال می‌کند.

## مقدار

یک مقدار بولی، که `true` نشان می‌دهد کلید فشرده شده است و `false` نشان می‌دهد کلید _فشرده نشده_ است.

## مثال‌ها

این مثال، ویژگی `ctrlKey` را هنگام فعال‌شدن رویداد {{domxref("Element/mousemove_event", "mousemove")}} ثبت می‌کند.

### HTML

```html
<p id="log">The ctrl key was pressed while the cursor was moving: false</p>
```

### JavaScript

```js
const log = document.querySelector("#log");
window.addEventListener("mousemove", logKey);

function logKey(e) {
  log.textContent = `The ctrl key was pressed while the cursor was moving: ${e.ctrlKey}`;
}
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseEvent") }}