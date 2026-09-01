---
title: "HTMLElement: load event"
short-title: load
slug: Web/API/HTMLElement/load_event
page-type: web-api-event
browser-compat: api.HTMLElement.load_event
---

{{APIRef("HTML DOM")}}

وقتی منبع یک عنصر با موفقیت بارگذاری میشود، رویداد **`load`** برای آن عنصر فعال میشود. در حال حاضر، عناصر HTML پشتیبانیشده عبارتاند از: {{HTMLElement("body")}}، {{HTMLElement("embed")}}، {{HTMLElement("iframe")}}، {{HTMLElement("img")}}، {{HTMLElement("link")}}، {{HTMLElement("object")}}، {{HTMLElement("script")}}، {{HTMLElement("style")}} و {{HTMLElement("track")}}.

> [!NOTE]
> رویداد `load` روی {{domxref("HTMLBodyElement#event_handlers", "HTMLBodyElement")}} در واقع نام مستعار رویداد {{domxref("Window/load_event", "window.onload")}} است. بنابراین، رویداد `load` تنها زمانی روی عنصر `<body>` فعال میشود که تمام منابع سند بارگذاری شده یا با خطا مواجه شده باشند. با این حال، برای وضوح بیشتر، توصیه میشود که مدیریتکننده رویداد مستقیماً به شیء `window` متصل شود، نه به `HTMLBodyElement`.

این رویداد قابل لغو نیست و رویداد حبابی (bubble) ندارد.

## Syntax

از نام رویداد در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریتکننده رویداد تنظیم کنید.

```js-nolint
addEventListener("load", (event) => { })

onload = (event) => { }
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

این مثال هر بار که عنصر {{HtmlElement("img")}} منبع خود را با موفقیت بارگذاری میکند، پیامی را روی صفحه نمایش میدهد.

### HTML

```html
<img
  id="image"
  src="/shared-assets/images/examples/favicon144.png"
  alt="MDN logo"
  width="72" />
<div><button>Reload</button></div>
```

### JavaScript

```js
const image = document.getElementById("image");
image.onload = () => {
  document.body.appendChild(document.createElement("div")).textContent =
    "loaded!";
};

document.querySelector("button").addEventListener("click", reload);

function reload() {
  image.src = "/shared-assets/images/examples/favicon144.png";
}
```

### Result

{{EmbedLiveSample("Example", "100%", "200")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رویدادهای مرتبط
  - Window: رویداد {{domxref("Window/load_event", "load")}}
  - Window: رویداد {{domxref("Window/error_event", "error")}}