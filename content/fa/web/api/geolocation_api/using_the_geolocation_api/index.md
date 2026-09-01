---
title: Using the Geolocation API
slug: Web/API/Geolocation_API/Using_the_Geolocation_API
page-type: guide
---

{{DefaultAPISidebar("Geolocation API")}}

از API موقعیت‌یابی (Geolocation API) برای به‌دست‌آوردن موقعیت کاربر استفاده می‌شود. به‌طور مثال می‌توان از آن برای نمایش موقعیت کاربر روی نقشه با کمک یک API نقشه‌برداری استفاده کرد. این مقاله اصول استفاده از آن را توضیح می‌دهد.

## شیء موقعیت‌یابی (geolocation object)

[API موقعیت‌یابی](/en-US/docs/Web/API/Geolocation) از طریق شیء {{domxref("navigator.geolocation")}} در دسترس است.

اگر این شیء وجود داشته باشد، سرویس‌های موقعیت‌یابی در دسترس هستند. می‌توانید وجود موقعیت‌یابی را به این صورت بررسی کنید:

```js
if ("geolocation" in navigator) {
  /* geolocation در دسترس است */
} else {
  /* geolocation در دسترس نیست */
}
```

### به‌دست‌آوردن موقعیت فعلی

برای به‌دست‌آوردن موقعیت فعلی کاربر، می‌توانید متد {{domxref("Geolocation.getCurrentPosition","getCurrentPosition()")}} را فراخوانی کنید. این کار یک درخواست ناهمگام (asynchronous) برای تشخیص موقعیت کاربر آغاز می‌کند و از سخت‌افزار موقعیت‌یابی برای دریافت اطلاعات به‌روز استفاده می‌کند. وقتی موقعیت مشخص شد، تابع callback تعریف‌شده اجرا می‌شود. می‌توانید به‌طور اختیاری یک تابع callback دوم برای اجرا در صورت بروز خطا ارائه دهید. پارامتر سوم اختیاری، یک شیء options است که می‌توانید در آن حداکثر عمر مجاز موقعیت بازگشتی، مدت زمان انتظار برای درخواست، و دقت بالای موقعیت را تنظیم کنید.

> [!NOTE]
> به‌طور پیش‌فرض، {{domxref("Geolocation.getCurrentPosition","getCurrentPosition()")}} سعی می‌کند با یک نتیجه با دقت پایین، در سریع‌ترین زمان ممکن پاسخ دهد. اگر بدون توجه به دقت، به پاسخی سریع نیاز داشته باشید مفید است. دستگاه‌های دارای GPS، برای مثال، ممکن است یک دقیقه یا بیشتر طول بکشد تا موقعیت GPS را بگیرند، بنابراین داده‌های با دقت کمتر (موقعیت IP یا Wi-Fi) ممکن است به `getCurrentPosition()` بازگردانده شوند.

```js
navigator.geolocation.getCurrentPosition((position) => {
  doSomething(position.coords.latitude, position.coords.longitude);
});
```

مثال بالا باعث می‌شود تابع `doSomething()` هنگام به‌دست‌آمدن موقعیت اجرا شود.

### نظارت بر موقعیت فعلی

اگر داده‌های موقعیت تغییر کند (چه با حرکت دستگاه یا با رسیدن اطلاعات جغرافیایی دقیق‌تر)، می‌توانید یک تابع callback تنظیم کنید که با آن اطلاعات موقعیت به‌روز فراخوانی شود. این کار با استفاده از تابع {{domxref("Geolocation.watchPosition","watchPosition()")}} انجام می‌شود که همان پارامترهای ورودی {{domxref("Geolocation.getCurrentPosition","getCurrentPosition()")}} را دارد. تابع callback چندین بار فراخوانی می‌شود و به مرورگر اجازه می‌دهد یا موقعیت شما را هنگام حرکت به‌روز کند، یا با استفاده از تکنیک‌های مختلف موقعیت‌یابی، موقعیت دقیق‌تری ارائه دهد. تابع callback خطا که مانند `getCurrentPosition()` اختیاری است، می‌تواند چندین بار فراخوانی شود.

> [!NOTE]
> می‌توانید از {{domxref("Geolocation.watchPosition","watchPosition()")}} بدون فراخوانی اولیه {{domxref("Geolocation.getCurrentPosition","getCurrentPosition()")}} استفاده کنید.

```js
const watchID = navigator.geolocation.watchPosition((position) => {
  doSomething(position.coords.latitude, position.coords.longitude);
});
```

متد {{domxref("Geolocation.watchPosition","watchPosition()")}} یک شماره ID بازمی‌گرداند که می‌توان از آن برای شناسایی منحصربه‌فرد ناظر موقعیت درخواست‌شده استفاده کرد؛ این مقدار را در کنار متد {{domxref("Geolocation.clearWatch","clearWatch()")}} برای توقف نظارت بر موقعیت کاربر استفاده می‌کنید.

```js
navigator.geolocation.clearWatch(watchID);
```

### تنظیم دقیق پاسخ

هم {{domxref("Geolocation.getCurrentPosition","getCurrentPosition()")}} و هم {{domxref("Geolocation.watchPosition","watchPosition()")}} یک callback موفقیت، یک callback خطای اختیاری، و یک شیء options اختیاری می‌پذیرند.

این شیء به شما امکان می‌دهد مشخص کنید که آیا دقت بالا فعال شود، حداکثر عمر برای مقدار موقعیت بازگشتی (تا این سن، مقدار در حافظه نهان ذخیره و در صورت درخواست مجدد همان موقعیت استفاده مجدد می‌شود؛ پس از آن مرورگر داده‌های موقعیت جدیدی درخواست می‌کند)، و یک مقدار timeout که تعیین می‌کند مرورگر چقدر باید برای دریافت داده‌های موقعیت تلاش کند، قبل از اینکه زمان آن تمام شود.

یک فراخوانی {{domxref("Geolocation.watchPosition","watchPosition")}} می‌تواند به این شکل باشد:

```js
function success(position) {
  doSomething(position.coords.latitude, position.coords.longitude);
}

function error() {
  alert("متأسفیم، موقعیتی در دسترس نیست.");
}

const options = {
  enableHighAccuracy: true,
  maximumAge: 30000,
  timeout: 27000,
};

const watchID = navigator.geolocation.watchPosition(success, error, options);
```

## توصیف یک موقعیت

موقعیت کاربر با استفاده از یک نمونه از شیء {{domxref("GeolocationPosition")}} توصیف می‌شود که خود شامل یک نمونه از شیء {{domxref("GeolocationCoordinates")}} است.

نمونه `GeolocationPosition` فقط دو چیز دارد: یک ویژگی `coords` که شامل نمونه `GeolocationCoordinates` است، و یک ویژگی `timestamp` که شامل یک برچسب زمانی (timestamp) بر حسب میلی‌ثانیه از زمان یونیکس ({{Glossary("Unix time")}}) است که داده‌های موقعیت در آن زمان بازیابی شده‌اند.

نمونه `GeolocationCoordinates` شامل تعدادی ویژگی است، اما دو موردی که بیشتر استفاده می‌کنید `latitude` و `longitude` هستند که برای رسم موقعیت روی نقشه نیاز دارید. بنابراین بسیاری از callbackهای موفقیت موقعیت‌یابی نسبتاً ساده به نظر می‌رسند:

```js
function success(position) {
  const latitude = position.coords.latitude;
  const longitude = position.coords.longitude;

  // کار با طول و عرض جغرافیایی خود
}
```

با این حال می‌توانید اطلاعات دیگری را نیز از یک شیء `GeolocationCoordinates` به‌دست آورید، از جمله ارتفاع، سرعت، جهت دستگاه، و اندازه‌گیری دقت داده‌های ارتفاع، طول و عرض جغرافیایی.

## مدیریت خطاها

تابع callback خطا، در صورت ارائه هنگام فراخوانی `getCurrentPosition()` یا `watchPosition()`، انتظار دارد یک نمونه از شیء [`GeolocationPositionError`](/en-US/docs/Web/API/GeolocationPositionError) به عنوان اولین پارامتر خود دریافت کند. این نوع شیء شامل دو ویژگی است: یک `code` که نشان می‌دهد چه نوع خطایی بازگشته، و یک `message` قابل خواندن برای انسان که توضیح می‌دهد کد خطا به چه معناست.

می‌توانید از آن به این صورت استفاده کنید:

```js
function errorCallback(error) {
  alert(`ERROR(${error.code}): ${error.message}`);
}
```

## مثال‌ها

در مثال زیر از API موقعیت‌یابی برای بازیابی طول و عرض جغرافیایی کاربر استفاده می‌شود. در صورت موفقیت، پیوند در دسترس با یک آدرس URL `openstreetmap.org` پر می‌شود که موقعیت کاربر را نشان می‌دهد.

```css hidden
body {
  padding: 20px;
  background-color: #ffffc9;
}

button {
  margin: 0.5rem 0;
}
```

### HTML

```html
<button id="find-me">نمایش موقعیت من</button><br />
<p id="status"></p>
<a id="map-link" href="" target="_blank">موقعیت نامشخص</a>
```

### JavaScript

```js
function geoFindMe() {
  const status = document.querySelector("#status");
  const mapLink = document.querySelector("#map-link");

  mapLink.href = "";
  mapLink.textContent = "";

  function success(position) {
    const latitude = position.coords.latitude;
    const longitude = position.coords.longitude;

    status.textContent = "";
    mapLink.href = `https://www.openstreetmap.org/#map=18/${latitude}/${longitude}`;
    mapLink.textContent = `عرض جغرافیایی: ${latitude} °، طول جغرافیایی: ${longitude} °`;
  }

  function error() {
    status.textContent = "امکان بازیابی موقعیت شما وجود ندارد";
  }

  if (!navigator.geolocation) {
    status.textContent = "مرورگر شما از موقعیت‌یابی پشتیبانی نمی‌کند";
  } else {
    status.textContent = "در حال مکان‌یابی…";
    navigator.geolocation.getCurrentPosition(success, error);
  }
}

document.querySelector("#find-me").addEventListener("click", geoFindMe);
```

### نتیجه

{{EmbedLiveSample('Examples', 350, 150, "", "", "", "geolocation")}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}