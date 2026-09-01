---
title: "GeolocationCoordinates: longitude property"
---

---
title: "GeolocationCoordinates: longitude property"
short-title: longitude
slug: Web/API/GeolocationCoordinates/longitude
page-type: web-api-instance-property
browser-compat: api.GeolocationCoordinates.longitude
---

{{securecontext_header}}{{APIRef("Geolocation API")}}

ویژگی فقط‌خواندنی **`longitude`** از رابط {{domxref("GeolocationCoordinates")}} عددی است که طول جغرافیایی یک موقعیت را بر حسب درجه‌های اعشاری نشان می‌دهد. این شیء به همراه یک برچسب زمانی که به صورت {{Glossary("Unix time")}} بر حسب میلی‌ثانیه داده می‌شود و زمان اندازه‌گیری را نشان می‌دهد، بخشی از رابط {{domxref("GeolocationPosition")}} است؛ نوع شیئی که توابع Geolocation API برای دریافت و بازگرداندن یک موقعیت جغرافیایی برمی‌گردانند.

## مقدار

مقدار در `longitude` طول جغرافیایی مکان روی زمین است که توسط شیء `Coordinates` توصیف شده و به درجه‌های اعشاری بیان می‌شود. این مقدار مطابق مشخصات سیستم ژئودتیک جهانی ۱۹۸۴ (WGS 84) تعریف شده است.

> [!NOTE]
> نصف‌النهار مبدأ (که به‌عنوان نصف‌النهار نخست یا نصف‌النهار مرجع نیز شناخته می‌شود) دقیقاً همان نصف‌النهار گرینویچ نیست که بیشتر مردم تصور می‌کنند. بلکه [نصف‌النهار مرجع IERS](https://en.wikipedia.org/wiki/IERS_Reference_Meridian) است که در فاصله ۵٫۳ [ثانیه قوسی](https://en.wikipedia.org/wiki/Arcseconds) (۱۰۲ متر / ۳۳۵ فوت) به سمت شرق [نصف‌النهار گرینویچ](https://en.wikipedia.org/wiki/Greenwich_meridian) قرار دارد. این همان استانداردی است که توسط [سامانه موقعیت‌یاب جهانی](https://en.wikipedia.org/wiki/Global_Positioning_System) (GPS) استفاده می‌شود.

## مثال‌ها

در این مثال ساده، موقعیت کاربر را دریافت کرده و پس از بازگشت، مختصات حاصل را نمایش می‌دهیم.

### JavaScript

کد جاوااسکریپت زیر یک شنونده رویداد ایجاد می‌کند تا وقتی کاربر روی دکمه کلیک می‌کند، اطلاعات موقعیت دریافت و نمایش داده شود.

```js
let button = document.getElementById("get-location");
let latText = document.getElementById("latitude");
let longText = document.getElementById("longitude");

button.addEventListener("click", () => {
  navigator.geolocation.getCurrentPosition((position) => {
    let lat = position.coords.latitude;
    let long = position.coords.longitude;

    latText.innerText = lat.toFixed(2);
    longText.innerText = long.toFixed(2);
  });
});
```

پس از تعریف متغیرها برای ارجاع آسان‌تر به عنصر دکمه و دو عنصری که عرض و طول جغرافیایی در آن‌ها نمایش داده می‌شود، شنونده رویداد با فراخوانی {{domxref("EventTarget.addEventListener", "addEventListener()")}} روی عنصر {{HTMLElement("button")}} ایجاد می‌شود. وقتی کاربر دکمه را کلیک کند، اطلاعات موقعیت را دریافت و نمایش می‌دهیم.

پس از دریافت رویداد {{domxref("Element/click_event", "click")}}، تابع {{domxref("Geolocation.getCurrentPosition", "getCurrentPosition()")}} را برای درخواست موقعیت فعلی دستگاه فراخوانی می‌کنیم. این یک درخواست ناهمگام است، بنابراین یک تابع بازخورد (callback) ارائه می‌دهیم که یک شیء {{domxref("GeolocationPosition")}} را به‌عنوان ورودی دریافت می‌کند و موقعیت تعیین‌شده را توصیف می‌کند.

از شیء `GeolocationPosition`، عرض و طول جغرافیایی کاربر را با استفاده از {{domxref("GeolocationCoordinates/latitude", "position.coords.latitude")}} و `position.coords.longitude` به دست می‌آوریم تا مختصات نمایش‌داده‌شده را به‌روز کنیم. دو عنصر {{HTMLElement("span")}} پس از تبدیل مقدار به عددی با دو رقم اعشار، به‌روز می‌شوند تا مقادیر مربوطه را نمایش دهند.

### HTML

HTML مورد استفاده برای نمایش نتایج به این صورت است:

```html
<p>
  Your location is <span id="latitude">0.00</span>° latitude by
  <span id="longitude">0.00</span>° longitude.
</p>
<button id="get-location">Get My Location</button>
```

### نتیجه

این مثال را می‌توانید اینجا آزمایش کنید:

{{EmbedLiveSample("Examples", 600, 120)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Geolocation API](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- رابط {{domxref("GeolocationCoordinates")}} که این ویژگی به آن تعلق دارد.
- رابط {{domxref("GeolocationPosition")}} که رابط سطح بالایی است که برای بازگرداندن داده‌های موقعیت‌یابی از توابع Geolocation API، یعنی {{domxref("Geolocation.getCurrentPosition()")}} و {{domxref("Geolocation.watchPosition", "watchPosition()")}} استفاده می‌شود.