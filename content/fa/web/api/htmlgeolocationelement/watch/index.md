---
title: "HTMLGeolocationElement: watch property"
short-title: watch
slug: Web/API/HTMLGeolocationElement/watch
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.watch
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

ویژگی **`watch`** در واسط {{domxref("HTMLGeolocationElement")}} یک مقدار بولی را دریافت و تنظیم می‌کند که نشان می‌دهد مرورگر باید هر بار که موقعیت دستگاه کاربر تغییر می‌کند، داده‌های موقعیت را به‌طور پیوسته به‌روزرسانی کند یا فقط یک بار آن را بازیابی کند.

این ویژگی مقدار صفت [`watch`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#watch) عنصر `<geolocation>` را منعکس می‌کند.

## مقدار

یک مقدار بولی:

- اگر `true` باشد، داده‌های موقعیت به‌طور پیوسته درخواست می‌شوند، مانند حالتی که متد {{domxref("Geolocation.watchPosition()")}} فراخوانی شده باشد.
- اگر `false` باشد، داده‌های موقعیت فقط یک بار درخواست می‌شوند، مانند حالتی که متد {{domxref("Geolocation.getCurrentPosition()")}} فراخوانی شده باشد.

مقدار پیش‌فرض `false` است.

## مثال‌ها

### استفادهٔ پایه

```html
<geolocation watch></geolocation>
```

```js
const geo = document.querySelector("geolocation");
console.log(geo.watch); // true
```

### بازیابی پیوستهٔ داده‌های موقعیت

در این مثال، داده‌های موقعیت را به‌طور پیوسته بازیابی کرده و در صفحه چاپ می‌کنیم.

#### HTML

ما یک عنصر {{htmlelement("geolocation")}} با صفت `watch` تنظیم‌شده روی آن قرار می‌دهیم. هنگامی که کاربر روی دکمهٔ حاصل از این عنصر کلیک می‌کند و اجازهٔ استفاده از قابلیت `geolocation` را می‌دهد، مرورگر هر بار که موقعیت دستگاه کاربر تغییر کند، شروع به درخواست پیوستهٔ داده‌های موقعیت می‌کند. همچنین یک عنصر {{htmlelement("p")}} اضافه می‌کنیم تا داده‌های موقعیت و خطاها در آن نمایش داده شود.

```html
<geolocation watch></geolocation>
<p id="output"></p>
```

#### جاوااسکریپت

در جاوااسکریپت، ابتدا ارجاع‌هایی به پاراگراف خروجی و عنصر `<geolocation>` می‌گیریم و مقدار ویژگی `watch` را با دسترسی به خاصیت `watch` بررسی می‌کنیم.

```js
const outputElem = document.querySelector("#output");
const geo = document.querySelector("geolocation");
console.log(geo.watch); // true
```

سپس یک شنوندهٔ رویداد {{domxref("HTMLGeolocationElement.location_event", "location")}} به شیء `HTMLGeolocationElement` حاصل اضافه می‌کنیم تا زمانی که درخواست دادهٔ موقعیت بازگردانده می‌شود را تشخیص دهیم. اگر داده با موفقیت بازگردانده شود، از طریق ویژگی {{domxref("HTMLGeolocationElement.position")}} به آن دسترسی پیدا کرده و مقادیر عرض و طول جغرافیایی را در پاراگراف خروجی چاپ می‌کنیم. اگر درخواست داده ناموفق باشد، خطا را از طریق ویژگی {{domxref("HTMLGeolocationElement.error")}} دریافت کرده و پیام خطا را در پاراگراف خروجی چاپ می‌کنیم.

```js
geo.addEventListener("location", () => {
  if (geo.position) {
    outputElem.textContent += `(${geo.position.coords.latitude},${geo.position.coords.longitude}), `;
  } else if (geo.error) {
    outputElem.textContent += `${geo.error.message}, `;
  }
});
```

#### نتیجه

این کد را به‌صورت [اجرای زنده](https://mdn.github.io/dom-examples/geolocation-element/basic-watch-example/) ([کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/basic-watch-example)) ببینید. کد کامل همچنین شامل یک راه‌حل جایگزین (fallback) برای مرورگرهایی است که عنصر `<geolocation>` را پشتیبانی نمی‌کنند.

در صورت امکان، نمایش را در یک مرورگر پشتیبانی‌شده و یک مرورگر پشتیبانی‌نشده ببینید و به تفاوت در روند نمایش گفتگوی مجوز هنگامی که انتخاب می‌کنید اجازهٔ استفاده از `geolocation` را بدهید یا رد کنید، توجه کنید.

همچنین توجه داشته باشید که چون صفت `watch` عنصر `<geolocation>` روی `true` تنظیم شده است، داده‌های موقعیت درخواست می‌شوند و رویداد `location` هر بار که کاربر مکان خود را تغییر می‌دهد، به‌طور پیوسته رخ می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}