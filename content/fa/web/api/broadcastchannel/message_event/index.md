---
title: "BroadcastChannel: message event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel/message_event"
translated_by: "n8n + AI"
---

---
title: "BroadcastChannel: message event"
short-title: message
slug: Web/API/BroadcastChannel/message_event
page-type: web-api-event
browser-compat: api.BroadcastChannel.message_event
---

{{APIRef("BroadCastChannel API")}}{{AvailableInWorkers}}

رویداد **`message`** از رابط {{domxref("BroadcastChannel")}} زمانی که پیامی روی آن کانال می‌رسد، رخ می‌دهد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("message", (event) => { })

onmessage = (event) => { }
```

## نوع رویداد

یک {{domxref("MessageEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("MessageEvent")}}

## مثال‌ها

در این مثال، یک {{HTMLElement("iframe")}} به‌عنوان «فرستنده» وجود دارد که وقتی کاربر روی دکمه کلیک می‌کند، محتویات یک {{HTMLElement("textarea")}} را پخش می‌کند. دو iframe «گیرنده» وجود دارند که به پیام پخش‌شده گوش می‌دهند و نتیجه را در یک عنصر {{HTMLElement("div")}} می‌نویسند.

### فرستنده

```html hidden
<h1>Sender</h1>
<label for="message">Type a message to broadcast:</label><br />
<textarea id="message" name="message" rows="1" cols="40">Hello</textarea>
<button id="broadcast-message" type="button">Broadcast message</button>
```

```css hidden
body {
  border: 1px solid black;
  padding: 0.5rem;
  height: 150px;
  font-family: "Fira Sans", sans-serif;
}

h1 {
  font:
    1.6em "Fira Sans",
    sans-serif;
  margin-bottom: 1rem;
}

textarea {
  padding: 0.2rem;
}

label,
br {
  margin: 0.5rem 0;
}

button {
  vertical-align: top;
  height: 1.5rem;
}
```

```js
const channel = new BroadcastChannel("example-channel");
const messageControl = document.querySelector("#message");
const broadcastMessageButton = document.querySelector("#broadcast-message");

broadcastMessageButton.addEventListener("click", () => {
  channel.postMessage(messageControl.value);
});
```

### گیرنده ۱

```html hidden
<h1>Receiver 1</h1>
<div id="received"></div>
```

```css hidden
body {
  border: 1px solid black;
  padding: 0.5rem;
  height: 100px;
  font-family: "Fira Sans", sans-serif;
}

h1 {
  font:
    1.6em "Fira Sans",
    sans-serif;
  margin-bottom: 1rem;
}
```

```js
const channel = new BroadcastChannel("example-channel");
channel.addEventListener("message", (event) => {
  received.textContent = event.data;
});
```

### گیرنده ۲

```html hidden
<h1>Receiver 2</h1>
<div id="received"></div>
```

```css hidden
body {
  border: 1px solid black;
  padding: 0.5rem;
  height: 100px;
  font-family: "Fira Sans", sans-serif;
}

h1 {
  font:
    1.6em "Fira Sans",
    sans-serif;
  margin-bottom: 1rem;
}
```

```js
const channel = new BroadcastChannel("example-channel");
channel.addEventListener("message", (event) => {
  received.textContent = event.data;
});
```

### نتیجه

{{ EmbedLiveSample('Sender', '100%', 220) }}

{{ EmbedLiveSample('Receiver_1', '100%', 160) }}

{{ EmbedLiveSample('Receiver_2', '100%', 160) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: {{domxref("BroadcastChannel/messageerror_event", "messageerror")}}.