---
title: "FetchLaterResult: activated property"
short-title: activated
slug: Web/API/FetchLaterResult/activated
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.FetchLaterResult.activated
---

{{APIRef("fetchLater API")}}{{SeeCompatTable}}

خاصیت فقط خواندنی **`activated`** از رابط {{domxref("FetchLaterResult")}} یک مقدار بولی (boolean) برمی‌گرداند که مشخص می‌کند آیا درخواست واکشی به تعویق افتاده (deferred fetch) ارسال شده است یا خیر.

## مقدار

یک {{jsxref('Boolean')}}.

## مثال‌ها

### یک درخواست `POST` را برای حدود یک دقیقه به تعویق بیندازید و تابعی برای بررسی ارسال آن ایجاد کنید

```js
const result = fetchLater("https://report.example.com", {
  method: "POST",
  body: JSON.stringify(myReport),
  activateAfter: 60000 /* 1 minute */,
});

function checkIfFetched() {
  return result.activated;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}