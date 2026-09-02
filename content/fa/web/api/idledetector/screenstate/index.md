---
title: "IdleDetector: screenState property"
---

---
title: "IdleDetector: screenState property"
short-title: screenState
slug: Web/API/IdleDetector/screenState
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IdleDetector.screenState
---

{{securecontext_header}}{{APIRef("Idle Detection API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`screenState`** از رابط {{domxref("IdleDetector")}} رشته‌ای برمی‌گرداند که نشان می‌دهد آیا صفحه قفل است، یکی از مقادیر `"locked"` یا `"unlocked"`.

## مقدار

اگر {{domxref("IdleDetector.start()")}} فراخوانی شده باشد، یکی از مقادیر `"locked"` یا `"unlocked"` است، در غیر این صورت `null`.

## مثال‌ها

در مثال زیر، تابعی که به رویداد `change` متصل شده، وضعیت `userState` و `screenState` را در کنسول چاپ می‌کند.

```js
idleDetector.addEventListener("change", () => {
  const userState = idleDetector.userState;
  const screenState = idleDetector.screenState;
  console.log(`Idle change: ${userState}, ${screenState}.`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}