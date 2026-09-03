---
title: "PushManager: getSubscription() method"
short-title: getSubscription()
slug: Web/API/PushManager/getSubscription
page-type: web-api-instance-method
browser-compat: api.PushManager.getSubscription
---

{{ApiRef("Push API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

متد **`PushManager.getSubscription()`** از رابط {{domxref("PushManager")}} یک اشتراک push موجود را بازیابی می‌کند.

این متد یک {{jsxref("Promise")}} برمی‌گرداند که به یک شیء {{domxref("PushSubscription")}} حاوی جزئیات اشتراک موجود تبدیل می‌شود. اگر هیچ اشتراکی وجود نداشته باشد، این Promise به مقدار `null` تبدیل می‌شود.

## نحو (Syntax)

```js-nolint
getSubscription()
```

### پارامترها

هیچکدام.

### مقدار برگشتی

یک {{jsxref("Promise")}} که به یک شیء {{domxref("PushSubscription")}} یا `null` تبدیل می‌شود.

## مثال‌ها

این قطعه کد از یک [نمونه پیام‌رسانی و اعلان‌های push](https://github.com/GoogleChrome/samples/tree/gh-pages/push-messaging-and-notifications) گرفته شده است. (هیچ نسخه نمایشی زنده‌ای در دسترس نیست.)

```js
// We need the service worker registration to check for a subscription
navigator.serviceWorker.ready.then((serviceWorkerRegistration) => {
  // Do we already have a push message subscription?
  serviceWorkerRegistration.pushManager
    .getSubscription()
    .then((subscription) => {
      // Enable any UI which subscribes / unsubscribes from
      // push messages.
      const pushButton = document.querySelector(".js-push-button");
      pushButton.disabled = false;

      if (!subscription) {
        // We aren't subscribed to push, so set UI
        // to allow the user to enable push
        return;
      }

      // Keep your server in sync with the latest subscriptionId
      sendSubscriptionToServer(subscription);

      showCurlCommand(subscription);

      // Set your UI to show they have subscribed for
      // push messages
      pushButton.textContent = "Disable Push Messages";
      isPushEnabled = true;
    })
    .catch((err) => {
      console.error(`Error during getSubscription(): ${err}`);
    });
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}