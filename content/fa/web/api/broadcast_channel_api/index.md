---
title: "Broadcast Channel API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API"
translated_by: "n8n + AI"
---

---
title: Broadcast Channel API
slug: Web/API/Broadcast_Channel_API
page-type: web-api-overview
browser-compat: api.BroadcastChannel
---

{{DefaultAPISidebar("Broadcast Channel API")}} {{AvailableInWorkers}}

**API Broadcast Channel** امکان ارتباط ساده بین {{glossary("browsing context", "زمینه‌های مرور")}} (یعنی _پنجره‌ها_, _زبانه‌ها_, _فریم‌ها_, یا _ایفریم‌ها_) و کارگران در یک {{glossary("origin", "مبدأ")}} را فراهم می‌کند.

> [!NOTE]
> در واقع، ارتباط بین زمینه‌های مرور که از [ذخیره‌سازی یکسان](/en-US/docs/Web/Privacy/Guides/State_Partitioning) استفاده می‌کنند مجاز است. ذخیره‌سازی ابتدا بر اساس سایت‌های سطح بالا تقسیم‌بندی می‌شود—به عنوان مثال، اگر یک صفحه در `a.com` باز داشته باشید که یک iframe از `b.com` را جاسازی کرده است، و صفحه دیگری به `b.com` باز شده باشد، آنگاه iframe نمی‌تواند با صفحه دوم ارتباط برقرار کند، با وجود اینکه از نظر فنی همان مبدأ هستند. با این حال، اگر صفحه اول نیز در `b.com` باشد، آنگاه iframe می‌تواند با صفحه دوم ارتباط برقرار کند.

با ایجاد یک شیء {{domxref("BroadcastChannel")}}، می‌توانید هر پیامی که به آن ارسال می‌شود را دریافت کنید. نیازی به نگه داشتن ارجاع به فریم‌ها یا کارگرانی که می‌خواهید با آنها ارتباط برقرار کنید ندارید: آنها می‌توانند با ساختن {{domxref("BroadcastChannel")}} خود با همان نام، در یک کانال خاص «مشترک» شوند و ارتباط دوطرفه بین همه آنها برقرار کنند.

![The principle of the Broadcast Channel API](broadcastchannel.png)

## رابط Broadcast Channel

### ایجاد یا پیوستن به یک کانال

یک مشتری با ایجاد یک شیء {{domxref("BroadcastChannel")}} به یک کانال پخش می‌پیوندد. [سازنده](/en-US/docs/Web/API/BroadcastChannel/BroadcastChannel) آن یک پارامتر واحد دریافت می‌کند: _نام_ کانال. اگر اولین بار باشد که به آن نام کانال پخش متصل می‌شود، کانال زمینه‌ای ایجاد می‌شود.

```js
// Connection to a broadcast channel
const bc = new BroadcastChannel("test_channel");
```

### ارسال پیام

کافی است متد {{domxref("BroadcastChannel.postMessage", "postMessage()")}} را روی شیء `BroadcastChannel` ایجاد شده فراخوانی کنید، که هر شیئی را به عنوان آرگومان می‌پذیرد. یک نمونه پیام رشته‌ای:

```js
// Example of sending of a very simple message
bc.postMessage("This is a test message.");
```

داده‌های ارسال شده به کانال با استفاده از [الگوریتم شبیه‌سازی ساختاریافته](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) سریال‌سازی می‌شوند. این بدان معناست که می‌توانید انواع مختلفی از اشیاء داده را بدون نیاز به سریال‌سازی خودتان به صورت ایمن ارسال کنید.

API هیچ معنایی به پیام‌ها نسبت نمی‌دهد، بنابراین این به عهده کد است که بداند چه نوع پیام‌هایی را انتظار داشته باشد و با آنها چه کند.

### دریافت پیام

وقتی پیامی ارسال می‌شود، یک رویداد [`message`](/en-US/docs/Web/API/BroadcastChannel/message_event) به هر شیء {{domxref("BroadcastChannel")}} متصل به این کانال ارسال می‌شود. یک تابع می‌تواند برای این رویداد با استفاده از کنترل‌کننده رویداد {{domxref("BroadcastChannel/message_event", "onmessage")}} اجرا شود:

```js
// A handler that only logs the event to the console:
bc.onmessage = (event) => {
  console.log(event);
};
```

### قطع اتصال از یک کانال

برای ترک یک کانال، متد {{domxref("BroadcastChannel.close", "close()")}} را روی شیء فراخوانی کنید. این کار شیء را از کانال زمینه‌ای جدا می‌کند و امکان جمع‌آوری زباله را فراهم می‌کند.

```js
// Disconnect the channel
bc.close();
```

## نتیجه‌گیری

رابط خودکفای API Broadcast Channel امکان ارتباط بین زمینه‌ای را فراهم می‌کند. می‌توان از آن برای تشخیص اقدامات کاربر در زبانه‌های دیگر در یک مبدأ استفاده کرد، مانند زمانی که کاربر وارد یا خارج می‌شود.

پروتکل پیام‌رسانی تعریف نشده است و زمینه‌های مرور مختلف باید خودشان آن را پیاده‌سازی کنند؛ هیچ مذاکره یا الزامی از سوی مشخصات وجود ندارد.

## Interfaces

- {{domxref("BroadcastChannel")}}
  - : نشان‌دهنده یک کانال نام‌گذاری شده است که هر {{glossary("browsing context", "زمینه مرور")}} از یک {{glossary("origin", "مبدأ")}} مشخص می‌تواند در آن مشترک شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("BroadcastChannel")}}، رابطی که آن را پیاده‌سازی می‌کند.