---
title: "MediaKeys: createSession() method"
short-title: createSession()
slug: Web/API/MediaKeys/createSession
page-type: web-api-instance-method
browser-compat: api.MediaKeys.createSession
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

متد `createSession()` از رابط {{domxref("MediaKeys")}} یک شیء جدید {{domxref("MediaKeySession")}} برمی‌گرداند که نمایانگر زمینه‌ای برای تبادل پیام با ماژول رمزگشایی محتوا (CDM) است.

## سینتکس

```js-nolint
createSession()
createSession(mediaKeySessionType)
```

### پارامترها

- `mediaKeySessionType` {{optional_inline}}
  - : یک رشته؛ مقدار آن «temporary» یا «persistent-license» است. مقدار پیش‌فرض «temporary» است.

### مقدار بازگشتی

یک شیء جدید {{domxref("MediaKeySession")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}