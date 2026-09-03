---
title: "PresentationRequest: start() method"
---

---
title: "PresentationRequest: start() method"
short-title: start()
slug: Web/API/PresentationRequest/start
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PresentationRequest.start
---

{{APIRef("Presentation API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`start()`** در {{domxref("PresentationRequest")}} یک {{jsxref("Promise")}} برمی‌گرداند که پس از آنکه عامل کاربر (user agent) از کاربر می‌خواهد یک نمایشگر را انتخاب کند و اجازه استفاده از آن را بدهد، با یک {{domxref("PresentationConnection")}} resolve می‌شود.

## نحو

```js-nolint
start()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک {{domxref("PresentationConnection")}} resolve می‌شود.

## امنیت

[فعال‌سازی گذرای کاربر](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این قابلیت کار کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}