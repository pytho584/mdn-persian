---
title: "MouseEvent: pageX property"
short-title: pageX
slug: Web/API/MouseEvent/pageX
page-type: web-api-instance-property
browser-compat: api.MouseEvent.pageX
---

{{APIRef("Pointer Events")}}

ویژگی فقط‌خواندنی **`pageX`** در رابط {{domxref("MouseEvent")}} مختصات X (افقی) را بر حسب پیکسل، در نقطه‌ای که ماوس کلیک شده است، نسبت به لبهٔ چپ کل سند برمی‌گرداند. این مقدار شامل هر بخشی از سند که در حال حاضر قابل مشاهده نیست نیز می‌شود.

از آنجا که این ویژگی بر پایهٔ لبهٔ سند محاسبه می‌شود، هرگونه اسکرول افقی صفحه را نیز در نظر می‌گیرد. برای مثال، اگر صفحه چنان اسکرول شده باشد که ۲۰۰ پیکسل از سمت چپ سند از دید خارج شده باشد و ماوس، ۱۰۰ پیکسل به سمت داخل از لبهٔ چپ نما کلیک شود، مقدار بازگشت‌داده‌شده توسط `pageX` برابر ۳۰۰ خواهد بود.

در ابتدا، این ویژگی به صورت عدد صحیح `long` تعریف شده بود. [ماژول نمای CSSOM](/en-US/docs/Web/CSS/Guides/CSSOM_view) آن را به صورت ممیز شناور `double` بازتعریف کرد. برای جزئیات، بخش [سازگاری مرورگر](#browser_compatibility) را ببینید.

برای اطلاعات بیشتر دربارهٔ مختصاتی که به این روش مشخص می‌شوند، به [سیستم‌های مختصات](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems#page) مراجعه کنید.

## مقدار

یک عدد ممیز شناور `double` شامل تعداد پیکسل‌ها از لبهٔ چپ _سند_ که ماوس در آن کلیک شده است، صرف‌نظر از هرگونه اسکرول یا موقعیت‌دهی ویوپورت (viewport) که ممکن است اعمال شده باشد.

این ویژگی در اصل در مشخصات رویدادهای لمسی (Touch Events) به صورت عدد صحیح `long` تعریف شده بود، اما در ماژول نمای CSSOM به یک عدد ممیز شناور با دقت دوگانه بازتعریف شد تا دقت زیرپیکسلی امکان‌پذیر شود. اگرچه هر دو نوع عددی در جاوااسکریپت با `Number` نمایش داده می‌شوند، ممکن است در داخل کد مرورگر به شکل متفاوتی پردازش شوند که می‌تواند تفاوت‌هایی در رفتار ایجاد کند.

برای آگاهی از مرورگرهایی که به استفاده از نوع دادهٔ بازبینی‌شده به‌روزرسانی شده‌اند، [سازگاری مرورگر](#browser_compatibility) را ببینید.

## مثال‌ها

### نمایش موقعیت ماوس نسبت به مبدأ صفحه

بیایید مثالی را بررسی کنیم که موقعیت ماوس را نسبت به مبدأ صفحه نشان می‌دهد. از آنجا که این مثال در یک {{HTMLElement("iframe")}} ارائه شده است، آن گوشهٔ بالا-چپ، گوشهٔ بالای چپ قاب است، نه پنجرهٔ مرورگر.

#### HTML

```html
<div class="box">
  <p>Move the mouse around in this box to watch its coordinates change.</p>
  <p><code>pageX</code>: <span id="x">n/a</span></p>
  <p><code>pageY</code>: <span id="y">n/a</span></p>
</div>
```

#### CSS

```css
.box {
  width: 400px;
  height: 250px;
  border: 2px solid darkblue;
  background-color: blue;
  color: white;
  font:
    16px "Zilla",
    "Open Sans",
    "Helvetica",
    "Arial",
    sans-serif;
}
```

#### JavaScript

```js
const box = document.querySelector(".box");
const pageX = document.getElementById("x");
const pageY = document.getElementById("y");

function updateDisplay(event) {
  pageX.innerText = event.pageX;
  pageY.innerText = event.pageY;
}

box.addEventListener("mousemove", updateDisplay);
box.addEventListener("mouseenter", updateDisplay);
box.addEventListener("mouseleave", updateDisplay);
```

کد جاوااسکریپت با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} تابع `updateDisplay()` را به عنوان گردانندهٔ رویداد برای رویدادهای {{domxref("Element/mousemove_event", "mousemove")}}، {{domxref("Element/mouseenter_event", "mouseenter")}} و {{domxref("Element/mouseleave_event", "mouseleave")}} ثبت می‌کند.

`updateDisplay()` محتوای عناصر {{HTMLElement("span")}} را که برای نمایش مختصات X و Y در نظر گرفته شده‌اند، با مقادیر `pageX` و {{domxref("MouseEvent.pageY", "pageY")}} جایگزین می‌کند.

#### نتیجه

می‌توانید آن را اینجا امتحان کنید:

{{EmbedLiveSample("Showing_the_mouse_position_relative_to_page_origin", 500, 300)}}

### مثال‌های بیشتر

همچنین می‌توانید مثالی را ببینید که [نحوه دسترسی به موقعیت ماوس](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems#example) را در هر یک از سیستم‌های مختصات موجود نشان می‌دهد.

## مشخصات

{{Specifications}}

پیش از افزوده‌شدن به مشخصات CSSOM View، `pageX` و `pageY` برای مدت کوتاهی در زیرمجموعه‌ای محدود از مرورگرها روی رابط {{domxref("UIEvent")}} در دسترس بودند.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MouseEvent.pageY")}}
- [سیستم‌های مختصات](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems)