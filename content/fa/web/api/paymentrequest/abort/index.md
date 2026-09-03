---
title: "PaymentRequest: abort() method"
short-title: abort()
slug: Web/API/PaymentRequest/abort
page-type: web-api-instance-method
browser-compat: api.PaymentRequest.abort
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

متد `PaymentRequest.abort()` از رابط {{domxref('PaymentRequest')}} باعث می‌شود که عامل کاربر (user agent) درخواست پرداخت را پایان دهد و هر رابط کاربری‌ای را که ممکن است نمایش داده شده باشد حذف کند.

## نحو

```js-nolint
abort()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref('undefined')}}).

## مثال‌ها

مثال زیر یک تایمر (timeout) تنظیم می‌کند تا درخواست پرداختی را که ممکن است رها شده یا نادیده گرفته شده باشد لغو کند.

```js
const request = new PaymentRequest(supportedInstruments, details, options);

const paymentTimeout = setTimeout(
  () => {
    clearTimeout(paymentTimeout);
    request
      .abort()
      .then(() => {
        print("Payment timed out after 20 minutes.");
      })
      .catch(() => {
        print(
          "Unable to abort, because the user is currently in the process " +
            "of paying.",
        );
      });
  },
  20 * 60 * 1000,
); /* 20 minutes */
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}