---
title: "Element: fullscreenchange event"
short-title: fullscreenchange
slug: Web/API/Element/fullscreenchange_event
page-type: web-api-event
browser-compat: api.Element.fullscreenchange_event
---

{{APIRef("Fullscreen API")}}

رویداد **`fullscreenchange`** بلافاصله پس از اینکه یک {{domxref("Element")}} به حالت تمام‌صفحه وارد یا از آن خارج می‌شود، فعال می‌گردد.

این رویداد به همان `Element` که در حال ورود به حالت تمام‌صفحه یا خروج از آن است ارسال می‌شود.

برای اینکه بفهمید `Element` در حال ورود به حالت تمام‌صفحه است یا خروج از آن، مقدار {{domxref("Document.fullscreenElement")}} را بررسی کنید: اگر این مقدار `null` باشد، عنصر در حال خروج از حالت تمام‌صفحه است و در غیر این صورت، در حال ورود به حالت تمام‌صفحه می‌باشد.

این رویداد قابل لغو (cancelable) نیست.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("fullscreenchange", (event) => { })

onfullscreenchange = (event) => { }
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

در این مثال، یک handler برای رویداد `fullscreenchange` به عنصری که `id` آن `fullscreen-div` است اضافه شده است.

اگر کاربر روی دکمه «Toggle Fullscreen Mode» کلیک کند، handler مربوط به `click` حالت تمام‌صفحه را برای آن `div` تغییر می‌دهد. اگر `document.fullscreenElement` مقداری داشته باشد، از حالت تمام‌صفحه خارج می‌شود. در غیر این صورت، `div` به حالت تمام‌صفحه وارد می‌شود.

به خاطر داشته باشید که تا زمانی که رویداد `fullscreenchange` مدیریت می‌شود، وضعیت عنصر قبلاً تغییر کرده است. بنابراین اگر تغییر به سمت حالت تمام‌صفحه باشد، `document.fullscreenElement` به عنصری اشاره می‌کند که اکنون در حالت تمام‌صفحه است. از سوی دیگر، اگر `document.fullscreenElement` برابر با `null` باشد، حالت تمام‌صفحه لغو شده است.

این یعنی در کد مثال، اگر عنصری در حال حاضر در حالت تمام‌صفحه باشد، handler رویداد `fullscreenchange` مقدار `id` عنصر تمام‌صفحه را در کنسول ثبت می‌کند. اگر `document.fullscreenElement` برابر `null` باشد، کد پیامی ثبت می‌کند که تغییر به سمت خروج از حالت تمام‌صفحه است.

### HTML

```html
<h1>fullscreenchange event example</h1>
<div id="fullscreen-div">
  <button id="toggle-fullscreen">Toggle Fullscreen Mode</button>
</div>
```

### JavaScript

```js
function fullscreenchangeHandler(event) {
  // document.fullscreenElement will point to the element that
  // is in fullscreen mode if there is one. If not, the value
  // of the property is null.
  if (document.fullscreenElement) {
    console.log(
      `Element: ${document.fullscreenElement.id} entered fullscreen mode.`,
    );
  } else {
    console.log("Leaving fullscreen mode.");
  }
}

const el = document.getElementById("fullscreen-div");

el.addEventListener("fullscreenchange", fullscreenchangeHandler);
// or
el.onfullscreenchange = fullscreenchangeHandler;

// When the toggle button is clicked, enter/exit fullscreen
document
  .getElementById("toggle-fullscreen")
  .addEventListener("click", (event) => {
    if (document.fullscreenElement) {
      // exitFullscreen is only available on the Document object.
      document.exitFullscreen();
    } else {
      el.requestFullscreen();
    }
  });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Document: fullscreenchange event](/en-US/docs/Web/API/Document/fullscreenchange_event)
- [Element: fullscreenerror event](/en-US/docs/Web/API/Element/fullscreenerror_event)
- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- [Guide to the Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide)