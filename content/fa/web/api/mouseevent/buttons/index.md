---
title: "MouseEvent: buttons property"
short-title: buttons
slug: Web/API/MouseEvent/buttons
page-type: web-api-instance-property
browser-compat: api.MouseEvent.buttons
---

{{APIRef("Pointer Events")}}

ویژگی فقط‌خواندنی **`MouseEvent.buttons`** نشان می‌دهد که هنگام فعال شدن یک رویداد ماوس، کدام دکمه‌های ماوس (یا سایر دستگاه‌های ورودی) فشرده شده‌اند.

هر دکمه‌ای که قابل فشار دادن باشد با یک عدد مشخص نمایش داده می‌شود (در زیر آمده است).
اگر بیش از یک دکمه فشرده شده باشد، مقادیر دکمه‌ها با هم جمع می‌شوند تا عدد جدیدی به دست آید.
برای مثال، اگر دکمه فرعی (`2`) و کمکی (`4`) به طور همزمان فشرده شوند، مقدار `6` خواهد بود (یعنی `2 + 4`).

> [!NOTE]
> این ویژگی را با ویژگی {{domxref("MouseEvent.button")}} اشتباه نگیرید.
> ویژگی `MouseEvent.buttons` وضعیت دکمه‌های فشرده‌شده را در هر نوع رویداد ماوس نشان می‌دهد،
> در حالی که ویژگی {{domxref("MouseEvent.button")}} فقط برای رویدادهای ماوس که در اثر فشار دادن یا رها کردن یک یا چند دکمه رخ می‌دهند، مقدار صحیح را تضمین می‌کند.

## مقدار

عددی که یک یا چند دکمه را نشان می‌دهد.
برای فشرده شدن همزمان بیش از یک دکمه، مقادیر با هم ترکیب می‌شوند (مثلاً `3` یعنی دکمه اصلی + فرعی).

- `0`: بدون دکمه یا مقداردهی‌نشده
- `1`: دکمه اصلی (معمولاً دکمه چپ)
- `2`: دکمه فرعی (معمولاً دکمه راست)
- `4`: دکمه کمکی (معمولاً دکمه چرخ ماوس یا دکمه وسط)
- `8`: دکمه چهارم (معمولاً دکمه «بازگشت در مرورگر»)
- `16` : دکمه پنجم (معمولاً دکمه «رفتن به جلو در مرورگر»)

## مثال‌ها

این مثال وقتی رویداد {{domxref("Element/mousedown_event", "mousedown")}} را فعال می‌کنید، ویژگی `buttons` را ثبت می‌کند.

### HTML

```html
<p>هر جا با یک یا چند دکمه ماوس کلیک کنید.</p>
<pre id="log">[هنوز کلیکی انجام نشده]</pre>
```

### JavaScript

```js
const buttonNames = ["left", "right", "wheel", "back", "forward"];
function mouseButtonPressed(event, buttonName) {
  // برای بررسی فشرده شدن یک دکمه خاص از عملگر باینری `&` با توان مربوطه از 2 استفاده کنید
  return Boolean(event.buttons & (1 << buttonNames.indexOf(buttonName)));
}

function format(event) {
  const { type, buttons } = event;
  const obj = { type, buttons };
  for (const buttonName of buttonNames) {
    obj[buttonName] = mouseButtonPressed(event, buttonName);
  }
  return JSON.stringify(obj, null, 2);
}

const log = document.getElementById("log");
function logButtons(event) {
  log.textContent = format(event);
}

document.addEventListener("mouseup", logButtons);
document.addEventListener("mousedown", logButtons);
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### یادداشت‌های فایرفاکس

فایرفاکس از ویژگی `buttons` در ویندوز، لینوکس (GTK) و macOS با محدودیت‌های زیر پشتیبانی می‌کند:

- ابزارهای کاربردی امکان سفارشی‌سازی عملکرد دکمه‌ها را فراهم می‌کنند.
  بنابراین، دکمه _اصلی_ ممکن است دکمه چپ دستگاه نباشد، دکمه _فرعی_ ممکن است دکمه راست نباشد و غیره.
  همچنین، دکمه وسط (چرخ)، دکمه چهارم و دکمه پنجم ممکن است مقداری نداشته باشند، حتی زمانی که فشرده شده‌اند.
- دستگاه‌های تک‌دکمه‌ای ممکن است دکمه‌های اضافی را با ترکیبی از فشردن دکمه و کلیدهای صفحه‌کلید شبیه‌سازی کنند.
- دستگاه‌های لمسی ممکن است دکمه‌ها را با ژست‌های قابل تنظیم شبیه‌سازی کنند (مثلاً لمس یک انگشتی برای دکمه _اصلی_، لمس دو انگشتی برای دکمه _فرعی_ و غیره).
- در لینوکس (GTK)، دکمه چهارم و دکمه پنجم پشتیبانی نمی‌شوند.
  علاوه بر این، رویداد {{domxref("Element/mouseup_event", "mouseup")}} همیشه اطلاعات دکمه‌ای که رها شده را در مقدار `buttons` شامل می‌شود.
- در Mac OS X 10.5، ویژگی `buttons` همیشه `0` برمی‌گرداند، زیرا هیچ API سیستمی برای پیاده‌سازی این قابلیت وجود ندارد.

## همچنین ببینید

- {{domxref("MouseEvent")}}