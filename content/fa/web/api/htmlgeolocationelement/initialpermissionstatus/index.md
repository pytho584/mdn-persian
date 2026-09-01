---
title: "HTMLGeolocationElement: initialPermissionStatus property"
short-title: initialPermissionStatus
slug: Web/API/HTMLGeolocationElement/initialPermissionStatus
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.initialPermissionStatus
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

خاصیت فقطخواندنی **`initialPermissionStatus`** از رابط {{domxref("HTMLGeolocationElement")}} یک مقدار شمارشی برمی‌گرداند که وضعیت مجوز قابلیت `geolocation` را هنگام بارگذاری اولیهٔ صفحه نشان می‌دهد.

اگر می‌خواهید به وضعیت فعلی مجوز قابلیت `geolocation` دسترسی داشته باشید، از خاصیت {{domxref("HTMLGeolocationElement.permissionStatus")}} استفاده کنید.

## مقدار

یک مقدار شمارشی که می‌تواند یکی از موارد زیر باشد:

- `granted`
  - : کاربر قبلاً به مرورگر اجازهٔ استفاده از قابلیت `geolocation` را داده است، چه از طریق عنصر {{htmlelement("geolocation")}} و چه از طریق سازوکاری دیگر. هنگام استفاده از عنصر `<geolocation>`، این بدان معناست که کاربر قبلاً دکمهٔ رندرشده را فشار داده و گزینهٔ «allow» (اجازه) را انتخاب کرده است.

    اگر عنصر `<geolocation>` ویژگی [`autolocate`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#autolocate) را با مقدار `true` داشته باشد و مجوز قبلاً داده شده باشد، مرورگر به محض بارگذاری صفحه شروع به درخواست داده‌های موقعیت مکانی می‌کند، بدون اینکه کاربر نیازی به فشار دادن دکمه داشته باشد.

- `denied`
  - : کاربر قبلاً اجازهٔ استفاده از قابلیت `geolocation` را به مرورگر رد کرده است، چه از طریق عنصر `<geolocation>` و چه از طریق سازوکاری دیگر. هنگام استفاده از عنصر `<geolocation>`، این بدان معناست که کاربر قبلاً دکمهٔ رندرشده را فشار داده و گزینهٔ «don't allow» (عدم اجازه) را انتخاب کرده است.

- `prompt`
  - : کاربر قبلاً اجازهٔ استفاده از قابلیت `geolocation` را نه داده و نه رد کرده است. هنگام استفاده از عنصر `<geolocation>`، این بدان معناست که کاربر قبلاً دکمهٔ رندرشده را فشار نداده است.

## مثال‌ها

### استفادهٔ پایه

```html
<geolocation></geolocation>
```

```js
const geo = document.querySelector("geolocation");
console.log(geo.initialPermissionStatus);
// "granted" if the user previously granted permission before reloading the page
```

### استفاده از وضعیت مجوز اولیه برای اطلاع‌رسانی به کاربر هنگام بارگذاری صفحه

در این مثال، از وضعیت مجوز اولیه استفاده می‌کنیم تا پیام مناسبی روی صفحه چاپ کنیم و به کاربر اطلاع دهیم که دکمهٔ {{htmlelement("geolocation")}} چه اقدامی انجام خواهد داد.

#### HTML

ما یک عنصر `<geolocation>` و دو عنصر {{htmlelement("p")}} قرار می‌دهیم؛ یکی برای خروجی پیام‌های وضعیت مجوز و دیگری برای خروجی داده‌های موقعیت مکانی.

```html
<geolocation>
  Your browser doesn't support the <code>&lt;geolocation&gt;</code> element.
</geolocation>
<p id="status"></p>
<p id="output"></p>
```

#### JavaScript

در جاوااسکریپت خود، ابتدا به هر سه عنصر HTML اشاره (reference) می‌گیریم:

```js
const statusElem = document.querySelector("#status");
const outputElem = document.querySelector("#output");
const geo = document.querySelector("geolocation");
```

در مرحلهٔ بعد، یک ساختار `if...else if` قرار می‌دهیم که مقدار `initialPermissionStatus` را بررسی می‌کند و یک پیام وضعیت روی صفحه چاپ می‌کند تا به کاربر اطلاع دهد وضعیت فعلی چیست، برای استفاده از برنامه چه کاری باید انجام دهد، و دکمه هنگام فشار دادن چه کاری انجام خواهد داد.

```js
if (geo.initialPermissionStatus === "prompt") {
  statusElem.textContent =
    "Please press the button to allow access to your location data and start requesting it.";
} else if (geo.initialPermissionStatus === "denied") {
  statusElem.textContent =
    "Permission previously denied. Please press the button to allow access to your location data and start requesting it.";
} else if (geo.initialPermissionStatus === "granted") {
  statusElem.textContent =
    "Permission previously granted. Please press the button to start requesting location data.";
}
```

در نهایت، یک شنوندهٔ رویداد (event listener) برای رویداد {{domxref("HTMLGeolocationElement.location_event", "location")}} به شیء `HTMLGeolocationElement` اضافه می‌کنیم تا وقتی درخواست دادهٔ موقعیت مکانی برگردانده شد، آن را تشخیص دهیم. اگر داده با موفقیت برگردانده شود، از طریق خاصیت {{domxref("HTMLGeolocationElement.position")}} به آن دسترسی پیدا می‌کنیم و مقادیر طول و عرض جغرافیایی را در پاراگراف خروجی چاپ می‌کنیم. اگر درخواست داده با شکست مواجه شود، خطا را از طریق خاصیت {{domxref("HTMLGeolocationElement.error")}} دریافت و آن را در پاراگراف خروجی چاپ می‌کنیم.

```js
geo.addEventListener("location", () => {
  statusElem.textContent = "Data requested";
  if (geo.position) {
    outputElem.textContent += `(${geo.position.coords.latitude},${geo.position.coords.longitude}), `;
  } else if (geo.error) {
    outputElem.textContent += `${geo.error.message}, `;
  }
});
```

#### نتیجه

نمونهٔ [اجرای زنده](https://mdn.github.io/dom-examples/geolocation-element/initial-permission-status/) را ببینید ([کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/initial-permission-status)). چند بار دکمهٔ `<geolocation>` را انتخاب کنید و هر بار گزینهٔ متفاوتی را از کادر محاوره‌ای ظاهر شده برگزینید و صفحه را دوباره بارگذاری کنید تا ببینید پیام خروجی چگونه برای انعکاس وضعیت تغییر می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر {{htmlelement("geolocation")}}