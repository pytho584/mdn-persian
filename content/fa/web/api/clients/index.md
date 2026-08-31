---
title: Clients
slug: Web/API/Clients
page-type: web-api-interface
browser-compat: api.Clients
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

رابط `Clients` دسترسی به اشیاء {{domxref("Client")}} را فراهم می‌کند. می‌توانید از طریق `{{domxref("ServiceWorkerGlobalScope", "self")}}.clients` در یک [service worker](/en-US/docs/Web/API/Service_Worker_API) به آن دسترسی پیدا کنید.

## روش‌های نمونه

- {{domxref("Clients.get()")}}
  - : یک {{jsxref("Promise")}} برای یک {{domxref("Client")}} مطابق با {{domxref("Client.id", "id")}} مشخص برمی‌گرداند.
- {{domxref("Clients.matchAll()")}}
  - : یک {{jsxref("Promise")}} برای آرایه‌ای از اشیاء {{domxref("Client")}} برمی‌گرداند. یک آرگومان options به شما امکان می‌دهد انواع کلاینت‌های بازگردانده‌شده را کنترل کنید.
- {{domxref("Clients.openWindow()")}}
  - : یک پنجره مرورگر جدید برای یک URL مشخص باز می‌کند و یک {{jsxref("Promise")}} برای {{domxref("WindowClient")}} جدید برمی‌گرداند.
- {{domxref("Clients.claim()")}}
  - : به یک service worker فعال اجازه می‌دهد خود را به عنوان {{domxref("ServiceWorkerContainer.controller", "controller")}} برای همه کلاینت‌های درون {{domxref("ServiceWorkerRegistration.scope", "scope")}} خود تنظیم کند.

## مثال‌ها

مثال زیر یک پنجره چت موجود را نشان می‌دهد یا زمانی که کاربر روی یک اعلان کلیک می‌کند، پنجره جدیدی ایجاد می‌کند.

```js
addEventListener("notificationclick", (event) => {
  event.waitUntil(
    (async () => {
      const allClients = await clients.matchAll({
        includeUncontrolled: true,
      });

      let chatClient;

      // ببینیم آیا از قبل پنجره چت باز داریم:
      for (const client of allClients) {
        const url = new URL(client.url);

        if (url.pathname === "/chat/") {
          // عالی است، از آن استفاده می‌کنیم!
          client.focus();
          chatClient = client;
          break;
        }
      }

      // اگر پنجره چت موجود پیدا نکردیم،
      // یک پنجره جدید باز کن:
      chatClient ??= await clients.openWindow("/chat/");

      // به کلاینت پیام بده:
      chatClient.postMessage("New chat messages!");
    })(),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)