---
title: Using channel messaging
slug: Web/API/Channel_Messaging_API/Using_channel_messaging
page-type: guide
browser-compat:
  - api.MessageChannel
  - api.MessagePort
---

{{DefaultAPISidebar("Channel Messaging API")}} {{AvailableInWorkers}}

[Channel Messaging API](/en-US/docs/Web/API/Channel_Messaging_API) به دو اسکریپت مجزا که در زمینه‌های مرورگری متفاوتِ متصل به یک سند واحد اجرا می‌شوند (مثلاً دو عنصر {{HTMLElement("iframe")}}، سند اصلی و یک {{HTMLElement("iframe")}}، یا دو سند از طریق یک {{domxref("SharedWorker")}}) اجازه می‌دهد مستقیماً با یکدیگر ارتباط برقرار کنند و پیام‌ها را از طریق کانال‌های دوطرفه (یا لوله‌ها) که در هر انتها یک پورت دارند، بین خود رد و بدل کنند.

در این مقاله، اصول اولیه استفاده از این فناوری را بررسی خواهیم کرد.

## موارد استفاده

پیام‌رسانی کانال عمدتاً در مواردی مفید است که یک سایت اجتماعی قابلیت‌هایی را از سایت‌های دیگر از طریق iframe در رابط اصلی خود جاسازی می‌کند، مانند بازی‌ها، دفترچه‌های آدرس یا یک پخش‌کننده صوتی با انتخاب‌های موسیقی شخصی‌سازی‌شده. وقتی این‌ها به‌عنوان واحدهای مستقل عمل می‌کنند، همه‌چیز روبهراه است؛ اما وقتی می‌خواهید بین سایت اصلی و عناصر {{HTMLElement("iframe")}} یا بین عناصر مختلف {{HTMLElement("iframe")}} تعامل برقرار کنید، کار دشوار می‌شود. مثلاً اگر بخواهید از سایت اصلی یک مخاطب به دفترچه آدرس اضافه کنید، امتیازهای بالای بازیتان را به پروفایل اصلی خود بیفزایید، یا انتخاب‌های موسیقی پس‌زمینه جدیدی از پخش‌کننده صوتی به بازی اضافه کنید، چه؟ چنین کارهایی با فناوری مرسوم وب چندان آسان نیستند، زیرا مدل‌های امنیتی‌ای که وب استفاده می‌کند، ایجاب می‌کند به این بیندیشید که آیا مبدأها (origins) به یکدیگر اعتماد دارند و پیام‌ها چگونه رد و بدل می‌شوند.

از سوی دیگر، کانال‌های پیام می‌توانند یک کانال امن فراهم کنند که به شما امکان می‌دهد داده‌ها را بین زمینه‌های مرورگری مختلف رد و بدل کنید.

> [!NOTE]
> برای اطلاعات و ایده‌های بیشتر، بخش [Ports as the basis of an object-capability model on the Web](https://html.spec.whatwg.org/multipage/comms.html#ports-as-the-basis-of-an-object-capability-model-on-the-web) از مشخصات مرجع، مطالعه مفیدی است.

## مثال‌های ساده

برای شروع، چند دمو در GitHub منتشر کرده‌ایم. اول، [دموی پایه پیام‌رسانی کانال](https://github.com/mdn/dom-examples/tree/main/channel-messaging-basic) را ببینید ([و به‌صورت زنده هم اجرایش کنید](https://mdn.github.io/dom-examples/channel-messaging-basic/)) که یک انتقال ساده تک‌پیام بین یک صفحه و یک {{htmlelement("iframe")}} تعبیه‌شده را نشان می‌دهد.

دوم، به [دموی چندپیامه](https://github.com/mdn/dom-examples/tree/main/channel-messaging-multimessage) ما نگاهی بیندازید ([آن را به‌صورت زنده اجرا کنید](https://mdn.github.io/dom-examples/channel-messaging-multimessage/)) که یک ساختار کمی پیچیده‌تر را نشان می‌دهد و می‌تواند چندین پیام را بین صفحه اصلی و یک IFrame ارسال کند.

در این مقاله روی همین مثال دوم تمرکز خواهیم کرد که به این شکل است:

![Demo with "Hello this is my demo" sent as five separate messages. The messages are displayed as a bulleted list.](channel-messaging-demo.png)

## ایجاد کانال

در صفحه اصلی دمو، یک فرم ساده با یک فیلد متنی برای وارد کردن پیام‌هایی که قرار است به یک {{htmlelement("iframe")}} ارسال شوند داریم. همچنین یک پاراگراف داریم که بعداً از آن برای نمایش پیام‌های تأییدی که از {{htmlelement("iframe")}} دریافت خواهیم کرد استفاده می‌کنیم.

```js
const input = document.getElementById("message-input");
const output = document.getElementById("message-output");
const button = document.querySelector("button");
const iframe = document.querySelector("iframe");

const channel = new MessageChannel();
const port1 = channel.port1;

// Wait for the iframe to load
iframe.addEventListener("load", onLoad);

function onLoad() {
  // Listen for button clicks
  button.addEventListener("click", onClick);

  // Listen for messages on port1
  port1.onmessage = onMessage;

  // Transfer port2 to the iframe
  iframe.contentWindow.postMessage("init", "*", [channel.port2]);
}

// Post a message on port1 when the button is clicked
function onClick(e) {
  e.preventDefault();
  port1.postMessage(input.value);
}

// Handle messages received on port1
function onMessage(e) {
  output.innerHTML = e.data;
  input.value = "";
}
```

ما با استفاده از سازنده {{domxref("MessageChannel.MessageChannel","MessageChannel()")}} یک کانال پیام جدید می‌سازیم.

وقتی IFrame بارگذاری شد، یک کنترل‌کننده `onclick` برای دکمه و یک کنترل‌کننده `onmessage` برای {{domxref("MessageChannel.port1")}} ثبت می‌کنیم. در نهایت، {{domxref("MessageChannel.port2")}} را با استفاده از متد {{domxref("window.postMessage")}} به IFrame منتقل می‌کنیم.

بیایید دقیق‌تر ببینیم خط `iframe.contentWindow.postMessage` چگونه کار می‌کند. این خط سه آرگومان می‌گیرد:

1. پیامی که ارسال می‌شود. برای این انتقال اولیه پورت، این پیام می‌تواند یک رشته خالی باشد، اما در این مثال روی `'init'` تنظیم شده است.
2. مبدأ (origin) مقصدی که پیام باید به آن ارسال شود. `*` به معنای «هر مبدأی» است.
3. یک شیء که مالکیت آن به زمینه مرورگر دریافت‌کننده منتقل می‌شود. در این مورد، ما {{domxref("MessageChannel.port2")}} را به IFrame منتقل می‌کنیم تا بتوان از آن برای برقراری ارتباط با صفحه اصلی استفاده کرد.

وقتی دکمه ما کلیک می‌شود، از ارسال عادی فرم جلوگیری می‌کنیم و سپس مقدار واردشده در فیلد متنی را از طریق {{domxref("MessageChannel")}} به IFrame ارسال می‌کنیم.

## دریافت پورت و پیام در IFrame

در عناصر {{HTMLElement("iframe")}}، کد جاوااسکریپت زیر را داریم:

```js
const list = document.querySelector("ul");
let port2;

// Listen for the initial port transfer message
window.addEventListener("message", initPort);

// Setup the transferred port
function initPort(e) {
  port2 = e.ports[0];
  port2.onmessage = onMessage;
}

// Handle messages received on port2
function onMessage(e) {
  const listItem = document.createElement("li");
  listItem.textContent = e.data;
  list.appendChild(listItem);
  port2.postMessage(`Message received by IFrame: "${e.data}"`);
}
```

وقتی پیام اولیه از صفحه اصلی از طریق متد {{domxref("window.postMessage")}} دریافت می‌شود، تابع `initPort` را اجرا می‌کنیم. این تابع پورت منتقل‌شده را ذخیره می‌کند و یک کنترل‌کننده `onmessage` ثبت می‌کند که هر بار یک پیام از طریق {{domxref("MessageChannel")}} عبور کند فراخوانی می‌شود.

هنگامی که پیامی از صفحه اصلی دریافت می‌شود، یک آیتم فهرست (list item) می‌سازیم و آن را در فهرست نامرتب درج می‌کنیم و {{domxref("Node.textContent","textContent")}} آیتم فهرست را برابر ویژگی `data` رویداد قرار می‌دهیم (این ویژگی شامل خود پیام است).

سپس، با فراخوانی {{domxref("MessagePort.postMessage")}} روی {{domxref("MessageChannel.port2")}} که ابتدا به iframe منتقل شده بود، یک پیام تأیید از طریق کانال پیام به صفحه اصلی ارسال می‌کنیم.

## دریافت تأییدیه در صفحه اصلی

با بازگشت به صفحه اصلی، اکنون نگاهی به تابع کنترل‌کننده `onmessage` می‌اندازیم.

```js
// Handle messages received on port1
function onMessage(e) {
  output.innerHTML = e.data;
  input.value = "";
}
```

وقتی پیامی از IFrame دریافت می‌شود که تأیید می‌کند پیام اصلی با موفقیت دریافت شده است، این تابع تأییدیه را در یک پاراگراف نمایش می‌دهد و فیلد متنی را برای ارسال پیام بعدی خالی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Channel Messaging API](/en-US/docs/Web/API/Channel_Messaging_API)
- [Web Workers API](/en-US/docs/Web/API/Web_Workers_API)
- [Broadcast Channel API](/en-US/docs/Web/API/Broadcast_Channel_API)