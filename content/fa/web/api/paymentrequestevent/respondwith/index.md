---
title: "PaymentRequestEvent: respondWith() method"
short-title: respondWith()
slug: Web/API/PaymentRequestEvent/respondWith
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PaymentRequestEvent.respondWith
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

متد **`respondWith()`** در رابط {{domxref("PaymentRequestEvent")}} از رفتار پیش‌فرض رویداد جلوگیری می‌کند و به شما امکان می‌دهد یک {{jsxref("Promise")}} برای شیء پاسخِ پردازندهٔ پرداخت ارائه دهید.

## نحو (Syntax)

```js-nolint
respondWith(promise)
```

### پارامترها

- `promise`
  - : یک شیء پاسخِ پردازندهٔ پرداخت یا یک {{jsxref('Promise')}} که به چنین شیءای حل می‌شود. این شیء باید دارای ویژگی‌های زیر باشد:
    - `methodName`
      - : شناسهٔ روش پرداختی که کاربر برای انجام تراکنش انتخاب کرده است.
    - `details`
      - : یک شیء قابل تبدیل به JSON که حاوی پیامی مخصوص روش پرداخت است و فروشنده برای پردازش تراکنش و تعیین موفقیت‌آمیز بودن انتقال وجه از آن استفاده می‌کند. برای جزئیات بیشتر به [ویژگی `details` در بخش ۸.۱.۲](https://w3c.github.io/web-based-payment-handler/#details-attribute) مراجعه کنید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

مثال زیر از [باز کردن پنجرهٔ پردازندهٔ پرداخت برای نمایش رابط کاربری برنامهٔ پرداخت مبتنی بر وب](https://web.dev/articles/orchestrating-payment-transactions#open-payment-handler-window) گرفته شده است. برای درک زمینهٔ کد، مقاله را مطالعه کنید.

```js
self.addEventListener("paymentrequest", async (e) => {
  // Retain a promise for future resolution
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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مرور کلی برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخهٔ عمر یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)