---
title: "Event: currentTarget property"
short-title: currentTarget
slug: Web/API/Event/currentTarget
page-type: web-api-instance-property
browser-compat: api.Event.currentTarget
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`currentTarget`** از رابط {{domxref("Event")}}، عنصری را مشخص می‌کند که رویداد‌گردان (event handler) به آن متصل شده است.

این مقدار همیشه با عنصری که رویداد روی آن رخ داده یکسان نیست؛ زیرا ممکن است رویداد روی یک عنصر فرزند از عنصر دارای رویداد‌گردان رخ داده باشد و سپس به سمت بالا [حباب کند](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) و به عنصر دارای رویداد‌گردان برسد. عنصری که رویداد روی آن رخ داده است توسط {{domxref("Event.target")}} مشخص می‌شود.

توجه داشته باشید که مقدار `currentTarget` فقط در یک رویداد‌گردان برای آن رویداد در دسترس است. خارج از رویداد‌گردان، مقدار آن `null` خواهد بود. این بدان معناست که مثلاً اگر در داخل یک رویداد‌گردان مرجعی از شیء `Event` بگیرید و سپس به ویژگی `currentTarget` آن در خارج از رویداد‌گردان دسترسی پیدا کنید، مقدار آن `null` خواهد بود.

## مقدار

یک {{domxref("EventTarget")}} که نشان‌دهنده شیئی است که رویداد‌گردان فعلی به آن متصل شده است.

## مثال‌ها

### currentTarget در برابر target

این مثال تفاوت بین `currentTarget` و `target` را نشان می‌دهد.

#### HTML

صفحه شامل یک {{htmlelement("div")}} «والد» است که یک `<div>` «فرزند» درون آن قرار دارد.

```html
<div id="parent">
  Click parent
  <div id="child">Click child</div>
</div>

<button id="reset">Reset</button>
<pre id="output"></pre>
```

```css hidden
button,
div,
pre {
  margin: 0.5rem;
}

div {
  padding: 1rem;
  border: 1px solid black;
}
```

#### JavaScript

رویداد‌گردان به عنصر والد متصل شده است. این رویداد‌گردان مقدار `event.currentTarget` و `event.target` را ثبت می‌کند.

همچنین یک دکمه «Reset» داریم که فقط مثال را دوباره بارگذاری می‌کند.

```js
const output = document.querySelector("#output");
const parent = document.querySelector("#parent");
parent.addEventListener("click", (event) => {
  const currentTarget = event.currentTarget.getAttribute("id");
  const target = event.target.getAttribute("id");
  output.textContent = `Current target: ${currentTarget}\n`;
  output.textContent += `Target: ${target}`;
});

const reset = document.querySelector("#reset");
reset.addEventListener("click", () => document.location.reload());
```

#### نتیجه

اگر روی `<div>` فرزند کلیک کنید، `target` عنصر فرزند را مشخص می‌کند. اگر روی `<div>` والد کلیک کنید، `target` عنصر والد را مشخص می‌کند.

در هر دو حالت، `currentTarget` عنصر والد را مشخص می‌کند، زیرا این عنصری است که رویداد‌گردان به آن متصل شده است.

{{EmbedLiveSample("currentTarget versus target", 100, 250)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: حباب رویداد](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling)