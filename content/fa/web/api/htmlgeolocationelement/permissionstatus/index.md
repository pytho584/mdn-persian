---
title: "HTMLGeolocationElement: permissionStatus property"
short-title: permissionStatus
slug: Web/API/HTMLGeolocationElement/permissionStatus
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.permissionStatus
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

ویژگی فقط‑خواندنی **`permissionStatus`** از رابط {{domxref("HTMLGeolocationElement")}} یک مقدار شمارشی برمی‌گرداند که وضعیت مجوز فعلی برای ویژگی `geolocation` را نشان می‌دهد.

اگر می‌خواهید به وضعیت مجوز اولیه برای ویژگی `geolocation` در زمان بارگذاری اولیه صفحه دسترسی داشته باشید، از ویژگی {{domxref("HTMLGeolocationElement.initialPermissionStatus", "initialPermissionStatus")}} استفاده کنید.

## مقدار

یک مقدار شمارشی که می‌تواند یکی از موارد زیر باشد:

- `granted`
  - : کاربر به مرورگر اجازه استفاده از ویژگی `geolocation` را داده است، چه از طریق عنصر {{htmlelement("geolocation")}} و چه از طریق مکانیزم دیگری. هنگام استفاده از عنصر `<geolocation>`، این بدان معناست که کاربر دکمه رندر شده را فشار داده و گزینه «allow» (اجازه) را انتخاب کرده است، و در این مرحله مرورگر شروع به درخواست داده‌های موقعیت مکانی می‌کند.
- `denied`
  - : کاربر از دادن اجازه به مرورگر برای استفاده از ویژگی `geolocation` خودداری کرده است، چه از طریق عنصر `<geolocation>` و چه از طریق مکانیزم دیگری. هنگام استفاده از عنصر `<geolocation>`، این بدان معناست که کاربر دکمه رندر شده را فشار داده و گزینه «don't allow» (اجازه نده) را انتخاب کرده است، و در این مرحله مرورگر تا زمانی که کاربر دوباره دکمه رندر شده را فشار دهد و گزینه «allow» را انتخاب کند، داده‌های موقعیت مکانی را درخواست نخواهد کرد.
- `prompt`
  - : کاربر به طور خاص به مرورگر اجازه استفاده از ویژگی `geolocation` را نداده یا آن را رد نکرده است، یعنی مرورگر تا زمانی که کاربر مجوز ندهد، داده‌های موقعیت مکانی را درخواست نخواهد کرد. هنگام استفاده از عنصر `<geolocation>`، این بدان معناست که کاربر هنوز دکمه رندر شده را فشار نداده است. وقتی این کار را انجام دهد، گزینه اعطا یا رد مجوز برای درخواست داده‌های موقعیت مکانی به او ارائه می‌شود.

وضعیت مجوز بین بارگذاری‌های صفحه پایدار می‌ماند. اگر عنصر `<geolocation>` دارای ویژگی [`autolocate`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#autolocate) با مقدار `true` باشد و مجوز قبلاً اعطا شده باشد، مرورگر به محض رندر شدن عنصر `<geolocation>` بدون نیاز به فشار دادن دکمه توسط کاربر، شروع به درخواست داده‌های موقعیت مکانی می‌کند.

## مثال‌ها

### استفاده پایه

```html
<geolocation></geolocation>
```

```js
const geo = document.querySelector("geolocation");
console.log(geo.permissionStatus);
// "prompt" اگر اولین بار است که کاربر به این صفحه دسترسی پیدا می‌کند
```

### استفاده از وضعیت مجوز برای اطلاع‌رسانی به کاربر

در مثال [نقشه تعبیه‌شده](https://mdn.github.io/dom-examples/geolocation-element/embedded-map/) ما ([کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/embedded-map))، یک شنونده رویداد {{domxref("HTMLGeolocationElement.promptaction_event", "promptaction")}} به شیء `HTMLGeolocationElement` که عنصر `<geolocation>` ما را نشان می‌دهد، اضافه می‌کنیم.

```js
geo.addEventListener("promptaction", notifyUserGrantPermission);
```

در تابع `notifyUserGrantPermission()` ارجاع‌شده، از ویژگی `permissionStatus` برای بررسی اینکه آیا وضعیت مجوز `denied` یا `prompt` است استفاده می‌کنیم و اگر چنین بود، از کاربر می‌خواهیم دوباره دکمه را فشار دهد و موقعیت مکانی را مجاز کند. اگر کاربر مجوز بدهد نیازی به این درخواست نیست.

```js
function notifyUserGrantPermission() {
  if (geo.permissionStatus === "denied" || geo.permissionStatus === "prompt") {
    statusElem.textContent =
      'لطفاً دوباره دکمه "Use location" را فشار دهید و موقعیت مکانی را برای این سایت مجاز کنید.';
  }
}
```

برای توضیح کامل این مثال به صفحه اصلی {{domxref("HTMLGeolocationElement")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}