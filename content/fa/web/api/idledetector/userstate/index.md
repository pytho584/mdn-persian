---
title: "IdleDetector: userState property"
---

---
title: "IdleDetector: userState property"
short-title: userState
slug: Web/API/IdleDetector/userState
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IdleDetector.userState
---

{{securecontext_header}}{{APIRef("Idle Detection API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط‌خواندنی **`userState`** در رابط {{domxref("IdleDetector")}} رشته‌ای را برمی‌گرداند که نشان می‌دهد آیا کاربر از زمان فراخوانی `start()` با دستگاه تعامل داشته است یا نه.

## مقدار

اگر {{domxref("IdleDetector.start()")}} فراخوانی شده باشد، مقدار یا `"active"` است یا `"idle"`، و در غیر این صورت `null` است.

## مثال‌ها

در مثال زیر، تابع callback رویداد `change`، وضعیت `userState` و `screenState` را در کنسول چاپ می‌کند.

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