---
title: "Document: visibilityState property"
short-title: visibilityState
slug: Web/API/Document/visibilityState
page-type: web-api-instance-property
browser-compat: api.Document.visibilityState
---

{{ApiRef("DOM")}}

خاصیت فقط خواندنی **`Document.visibilityState`** وضعیت نمایان بودن سند را برمی‌گرداند. می‌توان از آن برای بررسی اینکه آیا سند در پس‌زمینه یا در یک پنجره کمینه‌شده قرار دارد، یا به‌طور کلی برای کاربر قابل مشاهده نیست، استفاده کرد.

زمانی که مقدار این خاصیت تغییر می‌کند، رویداد {{domxref("Document/visibilitychange_event", "visibilitychange")}} به {{domxref("Document")}} ارسال می‌شود.

خاصیت {{domxref("Document.hidden")}} روش جایگزینی برای تعیین اینکه آیا صفحه پنهان است، ارائه می‌دهد.

## مقدار

یک رشته با یکی از مقادیر زیر:

- `visible`
  - : محتوای صفحه ممکن است حداقل تا حدی قابل مشاهده باشد. در عمل این به این معنی است که صفحه، زبانه پیش‌زمینه یک پنجره غیر کمینه‌شده است.
- `hidden`
  - : محتوای صفحه برای کاربر قابل مشاهده نیست. در عمل این به این معنی است که سند یا یک زبانه پس‌زمینه است یا بخشی از یک پنجره کمینه‌شده، یا قفل صفحه سیستم‌عامل فعال است.

## مثال‌ها

```js
document.addEventListener("visibilitychange", () => {
  console.log(document.visibilityState);
  // Modify behavior…
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.hidden")}}
- [Page Visibility API](/en-US/docs/Web/API/Page_Visibility_API)