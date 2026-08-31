---
title: "AudioWorkletNode: port property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletNode/port"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletNode: port property"
short-title: port
slug: Web/API/AudioWorkletNode/port
page-type: web-api-instance-property
browser-compat: api.AudioWorkletNode.port
---

{{APIRef("Web Audio API")}}{{SecureContext_Header}}

ویژگی‌ی فقط‌خواندنی **`port`** از رابط {{domxref("AudioWorkletNode")}}، {{domxref("MessagePort")}} مرتبط را بازمی‌گرداند. از آن می‌توان برای برقراری ارتباط بین گره و {{domxref("AudioWorkletProcessor")}} مرتبط با آن استفاده کرد.

> [!NOTE]
> پورت در انتهای دیگر کانال، در ویژگی {{domxref("AudioWorkletProcessor.port", "port")}} پردازنده در دسترس است.

## مقدار

شیء {{domxref("MessagePort")}} که `AudioWorkletNode` و `AudioWorkletProcessor` مرتبط با آن را به هم متصل می‌کند.

## مثال‌ها

برای نشان دادن قابلیت‌های ارتباطی دوطرفه، یک `AudioWorkletProcessor` ایجاد می‌کنیم که خروجی‌اش سکوت است و به درخواست‌های پینگ از `AudioWorkletNode` پاسخ می‌دهد.

ابتدا باید یک `AudioWorkletProcessor` سفارشی تعریف و آن را ثبت کنیم. توجه داشته باشید که این کار باید در یک فایل جداگانه انجام شود.

```js
// ping-pong-processor.js
class PingPongProcessor extends AudioWorkletProcessor {
  constructor(...args) {
    super(...args);
    this.port.onmessage = (e) => {
      console.log(e.data);
      this.port.postMessage("pong");
    };
  }
  process(inputs, outputs, parameters) {
    return true;
  }
}

registerProcessor("ping-pong-processor", PingPongProcessor);
```

حالا در فایل اسکریپت اصلی خود، پردازنده را بارگذاری می‌کنیم، نمونه‌ای از `AudioWorkletNode` با نام پردازنده ایجاد می‌کنیم و گره را به یک گراف صوتی متصل می‌کنیم.

```js
const audioContext = new AudioContext();
await audioContext.audioWorklet.addModule("ping-pong-processor.js");
const pingPongNode = new AudioWorkletNode(audioContext, "ping-pong-processor");
// ارسال پیام حاوی رشته 'ping'
// از AudioWorkletNode به AudioWorkletProcessor هر ثانیه
setInterval(() => pingPongNode.port.postMessage("ping"), 1000);
pingPongNode.port.onmessage = (e) => console.log(e.data);
pingPongNode.connect(audioContext.destination);
```

این کار رشته‌های `"ping"` و `"pong"` را هر ثانیه در کنسول چاپ می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)