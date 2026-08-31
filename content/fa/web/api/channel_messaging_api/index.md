---
title: Channel Messaging API
slug: Web/API/Channel_Messaging_API
page-type: web-api-overview
browser-compat:
  - api.MessageChannel
  - api.MessagePort
spec-urls: https://html.spec.whatwg.org/multipage/web-messaging.html#channel-messaging
---

{{DefaultAPISidebar("Channel Messaging API")}} {{AvailableInWorkers}}

**Channel Messaging API** به دو اسکریپت جداگانه که در زمینه‌های مرور متفاوتی اجرا می‌شوند و به سند یکسانی متصل هستند (مثلاً دو IFrame، یا سند اصلی و یک IFrame، دو سند از طریق یک {{domxref("SharedWorker")}} یا دو worker) اجازه می‌دهد مستقیماً با یکدیگر ارتباط برقرار کنند و پیام‌ها را از طریق کانال‌های دوسویه (یا لوله‌هایی) که در هر انتهایشان یک پورت قرار دارد، جابه‌جا کنند.

## مفاهیم و کاربرد

یک کانال پیام با استفاده از سازندهٔ {{domxref("MessageChannel.MessageChannel", "MessageChannel()")}} ساخته می‌شود. پس از ایجاد، می‌توان از طریق ویژگی‌های {{domxref("MessageChannel.port1")}} و {{domxref("MessageChannel.port2")}} به دو پورت کانال دسترسی یافت (هر دو شیء {{domxref("MessagePort")}} برمی‌گردانند). برنامه‌ای که کانال را ایجاد کرده از `port1` استفاده می‌کند و برنامه‌ای که در انتهای دیگر پورت قرار دارد از `port2` — شما به `port2` پیام می‌فرستید و پورت را با استفاده از {{domxref("window.postMessage")}} همراه با دو آرگومان (پیامی که باید ارسال شود و شیئی که قرار است مالکیت آن منتقل شود؛ در اینجا خودِ پورت) به زمینهٔ مرور دیگر منتقل می‌کنید.

وقتی این اشیاء قابل انتقال (transferable) منتقل می‌شوند، دیگر در زمینه‌ای که قبلاً به آن تعلق داشتند قابل استفاده نیستند. یک پورت پس از ارسال، دیگر نمی‌تواند توسط زمینهٔ اصلی استفاده شود.

زمینهٔ مرور دیگر می‌تواند با استفاده از {{domxref("MessagePort.message_event", "onmessage")}} به پیام گوش دهد و محتوای پیام را از طریق ویژگی `data` رویداد دریافت کند. سپس می‌توانید با ارسال پیام به سند اصلی با استفاده از {{domxref("MessagePort.postMessage")}} پاسخ دهید.

وقتی می‌خواهید ارسال پیام در طول کانال را متوقف کنید، می‌توانید با فراخوانی {{domxref("MessagePort.close")}} پورت‌ها را ببندید.

برای کسب اطلاعات بیشتر دربارهٔ نحوه استفاده از این API به [استفاده از پیام‌رسانی کانالی](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging) مراجعه کنید.

## رابط‌ها

- {{domxref("MessageChannel")}}
  - : یک کانال پیام جدید برای ارسال پیام‌ها ایجاد می‌کند.
- {{domxref("MessagePort")}}
  - : پورت‌های کانال پیام را کنترل می‌کند و امکان ارسال پیام از یک پورت و گوش‌دادن به رسیدن آن‌ها در پورت دیگر را فراهم می‌کند.

## مثال‌ها

- ما یک [نمونهٔ سادهٔ پیام‌رسانی کانالی](https://github.com/mdn/dom-examples/tree/main/channel-messaging-basic) را در GitHub منتشر کرده‌ایم ([اجرای آنلاین آن](https://mdn.github.io/dom-examples/channel-messaging-basic/)) که انتقال یک پیام بسیار ساده را بین یک صفحه و یک {{htmlelement("iframe")}} توکار نشان می‌دهد.
- همچنین می‌توانید [نمونهٔ چندپیامی](https://github.com/mdn/dom-examples/tree/main/channel-messaging-multimessage) را ببینید ([اجرای آنلاین](https://mdn.github.io/dom-examples/channel-messaging-multimessage/)) که تنظیمات کمی پیچیده‌تری را نشان می‌دهد و می‌تواند چند پیام را بین صفحهٔ اصلی و IFrame ارسال کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از پیام‌رسانی کانالی](/en-US/docs/Web/API/Channel_Messaging_API/Using_channel_messaging)
- [Web Workers API](/en-US/docs/Web/API/Web_Workers_API)
- [Broadcast Channel API](/en-US/docs/Web/API/Broadcast_Channel_API)