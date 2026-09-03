---
title: "PaymentRequestEvent: openWindow() method"
short-title: openWindow()
slug: Web/API/PaymentRequestEvent/openWindow
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PaymentRequestEvent.openWindow
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

متد **`openWindow()`** از رابط {{domxref("PaymentRequestEvent")}} نشانی وب مشخص‌شده را در یک پنجرهٔ جدید باز می‌کند، فقط به شرطی که آن نشانی وب هم‌مبدأ با صفحهٔ فراخوان باشد. این متد یک {{jsxref("Promise")}} برمی‌گرداند که با ارجاعی به یک {{domxref("WindowClient")}} resolve می‌شود.

## Syntax

```js-nolint
openWindow(url)
```

### Parameters

- `url`
  - : نشانی وب موردنظر برای باز شدن در پنجرهٔ جدید. این نشانی باید هم‌مبدأ با صفحهٔ فراخوان باشد.

### Return value

یک {{jsxref("Promise")}} که با ارجاعی به یک {{domxref("WindowClient")}} resolve می‌شود.

## Examples

```js
self.addEventListener("paymentrequest", async (e) => {
  // …
  // Retain a promise for future resolution
  // Polyfill for PromiseResolver at link below.
  resolver = new PromiseResolver();

  // Pass a promise that resolves when payment is done.
  e.respondWith(resolver.promise);
  // Open the checkout page.
  try {
    // Open the window and preserve the client
    client = await e.openWindow(checkoutURL);
    if (!client) {
      // Reject if the window fails to open
      throw new Error("Failed to open window");
    }
  } catch (err) {
    // Reject the promise on failure
    resolver.reject(err);
  }
});
```

برای جزئیات بیشتر در مورد نحوهٔ استفاده از این قابلیت، به [Open the payment handler window to display the web-based payment app frontend](https://web.dev/articles/orchestrating-payment-transactions#open-payment-handler-window) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Web-based payment apps overview](https://web.dev/articles/web-based-payment-apps-overview)
- [Setting up a payment method](https://web.dev/articles/setting-up-a-payment-method)
- [Life of a payment transaction](https://web.dev/articles/life-of-a-payment-transaction)
- [Using the Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [Payment processing concepts](/en-US/docs/Web/API/Payment_Request_API/Concepts)