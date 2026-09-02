---
title: "MessageEvent: ports property"
short-title: ports
slug: Web/API/MessageEvent/ports
page-type: web-api-instance-property
browser-compat: api.MessageEvent.ports
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`ports`** در رابط {{domxref("MessageEvent")}} آرایه‌ای از اشیاء {{domxref("MessagePort")}} است که همهٔ اشیاء {{domxref("MessagePort")}} ارسال‌شده به‌همراه پیام را به‌ترتیب دربرمی‌گیرد.

## مقدار

آرایه‌ای از اشیاء {{domxref("MessagePort")}}.

## مثال‌ها

```js
onconnect = (e) => {
  const port = e.ports[0];

  port.addEventListener("message", (e) => {
    const workerResult = `Result: ${e.data[0] * e.data[1]}`;
    port.postMessage(workerResult);
  });

  port.start(); // Required when using addEventListener. Otherwise called implicitly by onmessage setter.
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ExtendableMessageEvent")}} — مشابه همین رابط است؛ با این تفاوت که در رابط‌هایی استفاده می‌شود که نیاز است انعطاف‌پذیری بیشتری را در اختیار نویسندگان قرار دهند.