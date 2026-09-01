---
title: "Gamepad: connected property"
---

---
title: "Gamepad: connected property"
short-title: connected
slug: Web/API/Gamepad/connected
page-type: web-api-instance-property
browser-compat: api.Gamepad.connected
---

{{APIRef("Gamepad API")}}

ویژگی **`Gamepad.connected`** از رابط {{domxref("Gamepad") }} یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا گیمپد همچنان به سیستم متصل است یا خیر.

اگر گیمپد متصل باشد، مقدار `true` است؛ در غیر این صورت، مقدار `false` است.

## مقدار

یک مقدار بولین.

## مثال‌ها

```js
const gp = navigator.getGamepads()[0];
console.log(gp.connected);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

[استفاده از Gamepad API](/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API)