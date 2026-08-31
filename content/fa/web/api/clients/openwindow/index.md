---
title: "Clients: openWindow() method"
short-title: openWindow()
slug: Web/API/Clients/openWindow
page-type: web-api-instance-method
browser-compat: api.Clients.openWindow
---

{{APIRef("Service Workers API")}}{{AvailableInWorkers("service")}}

متد **`openWindow()`** از رابط {{domxref("Clients")}} یک زمینهٔ مرور سطح بالا (top-level browsing context) جدید ایجاد می‌کند و یک URL مشخص را بارگذاری می‌کند. اگر اسکریپت فراخواننده اجازهٔ نمایش پنجرهٔ بازشو (popup) را نداشته باشد، `openWindow()` یک خطای `InvalidAccessError` پرتاب می‌کند.

در فایرفاکس، این متد تنها زمانی مجاز است که پنجرهٔ بازشو را نشان دهد که در نتیجهٔ یک رویداد کلیک روی اعلان (notification) فراخوانی شده باشد.

در Chrome برای اندروید، این متد ممکن است به‌جای آن URL را در یک زمینهٔ مرور موجود که توسط یک [وب‌اپلیکیشن مستقل](/en-US/docs/Web/Progressive_web_apps) که قبلاً به صفحهٔ اصلی کاربر اضافه شده فراهم شده، باز کند. اخیراً این قابلیت در Chrome برای ویندوز نیز کار می‌کند.

## نحو (Syntax)

```js-nolint
openWindow(url)
```

### پارامترها

- `url`
  - : یک رشته که URL کلاینت مورد نظر برای باز کردن در پنجره را نشان می‌دهد. به‌طور کلی این مقدار باید یک URL از همان مبدأ (same origin) اسکریپت فراخواننده باشد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک شیء {{domxref("WindowClient")}} حل می‌شود اگر URL از همان مبدأ سرویس‌ورکر باشد، در غیر این صورت به یک {{Glossary("null", "مقدار null")}} حل می‌شود.

### استثناها (Exceptions)

- `InvalidAccessError` {{domxref("DOMException")}}
  - : پرامیس با این استثنا رد می‌شود اگر هیچ‌یک از پنجره‌های مبدأ برنامه [فعال‌سازی گذرا (transient activation)](/en-US/docs/Web/Security/Defenses/User_activation) نداشته باشند.

## الزامات امنیتی

- حداقل یک پنجره در مبدأ برنامه باید [فعال‌سازی گذرا](/en-US/docs/Web/Security/Defenses/User_activation) داشته باشد.

## مثال‌ها

### باز کردن یک پنجره هنگام کلیک روی اعلان

در این مثال، یک سرویس‌ورکر یک اعلان ایجاد و نمایش می‌دهد که حاوی یک URL مرتبط است که در محدوده (scope) سرویس‌ورکر قرار دارد. وقتی کاربر روی اعلان کلیک می‌کند:

- اگر صفحه در URL اعلان از قبل باز باشد، سرویس‌ورکر آن را فوکوس می‌کند.
- در غیر این صورت، سرویس‌ورکر صفحه را در یک پنجرهٔ جدید باز می‌کند.

توجه داشته باشید که ویژگی {{domxref("Client.url")}} به‌روزرسانی نمی‌شود مگر اینکه یک صفحهٔ جدید واقعاً بارگذاری شود. این بدان معناست که اگر کاربر با استفاده از یک قطعهٔ URL (fragment) در همان صفحه پیمایش کند، یا اگر یک [برنامهٔ تک‌صفحه‌ای (SPA)](/en-US/docs/Glossary/SPA) یک رویداد پیمایش را رهگیری کند (مثلاً با استفاده از [Navigation API](/en-US/docs/Web/API/Navigation_API)) و محتوای صفحه را با کد سمت کلاینت به‌روزرسانی کند، این ویژگی به‌روزرسانی نخواهد شد. بنابراین، این تکنیک برای برنامه‌های تک‌صفحه‌ای مناسب نیست.

```js
// Create and show notification
if (self.Notification.permission === "granted") {
  const notificationObject = {
    body: "Click here to view your messages.",
    data: { url: `${self.location.origin}/some/path` },
  };
  self.registration.showNotification(
    "You've got messages!",
    notificationObject,
  );
}

// Handle notification click
self.addEventListener("notificationclick", (e) => {
  // Close the notification popout
  e.notification.close();
  e.waitUntil(
    // Get all the Window clients
    clients.matchAll({ type: "window" }).then((clientsArr) => {
      const windowToFocus = clientsArr.find(
        (windowClient) => windowClient.url === e.notification.data.url,
      );
      if (windowToFocus) {
        // If a Window tab matching the targeted URL already exists, focus that;
        windowToFocus.focus();
      } else {
        // Otherwise, open a new tab to the applicable URL and focus it.
        clients
          .openWindow(e.notification.data.url)
          .then((windowClient) => (windowClient ? windowClient.focus() : null));
      }
    }),
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}