---
title: "Document: fullscreenchange event"
short-title: fullscreenchange
slug: Web/API/Document/fullscreenchange_event
page-type: web-api-event
browser-compat: api.Document.fullscreenchange_event
---

{{APIRef("Fullscreen API")}}

رویداد **`fullscreenchange`** بلافاصله پس از اینکه مرورگر به حالت تمام‌صفحه وارد می‌شود یا از آن خارج می‌شود، شلیک می‌شود.

این رویداد به `Element` (عنصر) ارسال می‌شود که در حال ورود به حالت تمام‌صفحه یا خروج از آن است و سپس این رویداد به سمت بالا حباب می‌زند و به `Document` می‌رسد.

برای اینکه بفهمید `Element` در حال ورود به حالت تمام‌صفحه است یا خروج از آن، مقدار {{domxref("Document.fullscreenElement")}} را بررسی کنید: اگر این مقدار `null` باشد، عنصر در حال خروج از حالت تمام‌صفحه است؛ در غیر این صورت، در حال ورود به حالت تمام‌صفحه است.

این رویداد قابل لغو (cancelable) نیست.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی event handler تنظیم کنید.

```js-nolint
addEventListener("fullscreenchange", (event) => { })

onfullscreenchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### ثبت رویدادهای `fullscreenchange`

در این مثال، یک مدیر رویداد برای رویداد `fullscreenchange` به {{domxref("Document")}} اضافه شده است.

اگر کاربر روی دکمه «Toggle Fullscreen Mode» کلیک کند، مدیر رویداد `click` حالت تمام‌صفحه را برای `div` تغییر می‌دهد (toggle). اگر `document.fullscreenElement` مقداری داشته باشد، از حالت تمام‌صفحه خارج می‌شود؛ در غیر این صورت، div به حالت تمام‌صفحه درمی‌آید.

به خاطر داشته باشید که تا زمانی که رویداد `fullscreenchange` پردازش می‌شود، وضعیت عنصر قبلاً تغییر کرده است. بنابراین اگر تغییر به سمت حالت تمام‌صفحه باشد، `document.fullscreenElement` به عنصری اشاره می‌کند که اکنون در حالت تمام‌صفحه است. از طرف دیگر، اگر `document.fullscreenElement` برابر `null` باشد، حالت تمام‌صفحه لغو شده است.

معنای این موضوع برای کد مثال این است که اگر عنصری در حال حاضر در حالت تمام‌صفحه باشد، مدیر رویداد `fullscreenchange` مقدار `id` عنصر تمام‌صفحه را در کنسول ثبت می‌کند. اگر `document.fullscreenElement` برابر `null` باشد، کد پیامی ثبت می‌کند که تغییر به سمت خروج از حالت تمام‌صفحه است.

#### HTML

```html
<h1>fullscreenchange event example</h1>
<div id="fullscreen-div">
  <button id="toggle-fullscreen">Toggle Fullscreen Mode</button>
  <pre id="logger"></pre>
</div>
```

#### CSS

```css
* {
  box-sizing: border-box;
}

#fullscreen-div {
  height: 150px;
  padding: 1rem;
  background-color: pink;
}

#logger {
  height: 80px;
  padding: 0 0.5rem;
  background-color: white;
  overflow: scroll;
}
```

#### JavaScript

```js
const logger = document.querySelector("#logger");
const fullScreenElement = document.querySelector("#fullscreen-div");

function log(message) {
  logger.textContent = `${logger.textContent}\n${message}`;
}

function fullscreenchangeHandler(event) {
  // document.fullscreenElement will point to the element that
  // is in fullscreen mode if there is one. If there isn't one,
  // the value of the property is null.
  if (document.fullscreenElement) {
    log(`Element: ${document.fullscreenElement.id} entered fullscreen mode.`);
  } else {
    log("Leaving fullscreen mode.");
  }
}

document.addEventListener("fullscreenchange", fullscreenchangeHandler);

// When the toggle button is clicked, enter/exit fullscreen
document.getElementById("toggle-fullscreen").addEventListener("click", () => {
  if (document.fullscreenElement) {
    // exitFullscreen is only available on the Document object.
    document.exitFullscreen();
  } else {
    fullScreenElement.requestFullscreen();
  }
});
```

{{EmbedLiveSample("ثبت رویدادهای fullscreenchange", 640, 250, "", "", "", "fullscreen")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document/fullscreenerror_event", "fullscreenerror")}}
- {{domxref("Element")}}: رویداد {{domxref("Element/fullscreenchange_event", "fullscreenchange")}}
- [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API)
- [راهنمای Fullscreen API](/en-US/docs/Web/API/Fullscreen_API/Guide)