---
title: "BroadcastChannel"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel"
translated_by: "n8n + AI"
---

---
title: BroadcastChannel
slug: Web/API/BroadcastChannel
page-type: web-api-interface
browser-compat: api.BroadcastChannel
---

{{APIRef("Broadcast Channel API")}} {{AvailableInWorkers}}

رابط **`BroadcastChannel`** یک کانال نامگذاری‌شده را نمایش می‌دهد که هر {{glossary("browsing context")}} از یک {{glossary("origin")}} معین می‌تواند در آن مشترک شود. این امکان ارتباط بین اسناد مختلف (در پنجره‌ها، تب‌ها، فریم‌ها یا iframe های مختلف) از همان origin را فراهم می‌کند. پیام‌ها از طریق یک رویداد {{domxref("BroadcastChannel/message_event", "message")}} که بر روی تمام اشیاء `BroadcastChannel` در حال گوش دادن به کانال، به‌جز شیءای که پیام را ارسال کرده است، پخش می‌شوند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("BroadcastChannel.BroadcastChannel", "BroadcastChannel()")}}
  - : یک شیء مرتبط با کانال نامگذاری‌شده ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌ها را از والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("BroadcastChannel.name")}} {{ReadOnlyInline}}
  - : یک رشته، نام کانال را برمی‌گرداند.

## روش‌های نمونه

_این رابط همچنین روش‌ها را از والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("BroadcastChannel.postMessage()")}}
  - : پیام را، از هر نوع شیء، به هر شیء `BroadcastChannel` که به همان کانال گوش می‌دهد، ارسال می‌کند.
- {{domxref("BroadcastChannel.close()")}}
  - : شیء کانال را می‌بندد، نشان می‌دهد که پیام جدیدی دریافت نخواهد کرد و به آن اجازه می‌دهد تا در نهایت، بازیافت حافظه (Garbage Collection) شود.

## رویدادها

_این رابط همچنین رویدادها را از والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("BroadcastChannel/message_event", "message")}}
  - : زمانی که یک پیام به کانال می‌رسد، فعال می‌شود. همچنین از طریق ویژگی `onmessage` در دسترس است.
- {{domxref("BroadcastChannel/messageerror_event", "messageerror")}}
  - : زمانی که پیامی می‌رسد که نمی‌تواند از حالت سریال خارج شود (deserialize)، فعال می‌شود. همچنین از طریق ویژگی `onmessageerror` در دسترس است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- راه دیگری (سنگین‌تر) برای ارتباط بین زمینه‌های مرورگر: {{domxref("ServiceWorker")}}.
- [نمای کلی Broadcast Channel API](/en-US/docs/Web/API/Broadcast_Channel_API)