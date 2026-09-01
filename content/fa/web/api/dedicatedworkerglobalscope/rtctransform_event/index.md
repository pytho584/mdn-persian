---
title: "DedicatedWorkerGlobalScope: rtctransform event"
short-title: rtctransform
slug: Web/API/DedicatedWorkerGlobalScope/rtctransform_event
page-type: web-api-event
browser-compat: api.DedicatedWorkerGlobalScope.rtctransform_event
---

{{APIRef("WebRTC")}}{{AvailableInWorkers("dedicated")}}

رویداد **`rtctransform`** روی شیء {{domxref('DedicatedWorkerGlobalScope')}} یک worker زمانی شلیک می‌شود که یک فریم ویدیویی یا صوتی کدگذاری‌شده برای پردازش توسط یک {{domxref("WebRTC API/Using Encoded Transforms", "WebRTC Encoded Transform", "", "nocode")}} در صف قرار گرفته باشد.

ویژگی {{domxref("RTCTransformEvent.transformer","transformer")}} رویداد، یک {{domxref("RTCRtpScriptTransformer")}} برمی‌گرداند که {{domxref("ReadableStream")}} را که فریم در آن صف‌بندی شده است و همچنین {{domxref("WritableStream")}} را که می‌توان فریم را در آن نوشت تا دوباره به خط لوله WebRTC تزریق شود، در دسترس قرار می‌دهد.

این رویداد لغوپذیر نیست و bubble نمی‌شود.

## نحو

برای استفاده از این رویداد، می‌توان از نام آن در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کرد یا یک ویژگی مدیریت‌کننده رویداد تنظیم کرد.

```js-nolint
addEventListener("rtctransform", (event) => { })

onrtctransform = (event) => { }
```

## نوع رویداد

یک {{domxref("RTCTransformEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("RTCTransformEvent")}}

## مثال

قطعه کد زیر یک مدیریت‌کننده برای رویداد `rtctransform` در worker را نشان می‌دهد که با استفاده از `addEventListener()` به محدوده سراسری اضافه شده است. `event.transformer` یک {{domxref("RTCRtpScriptTransformer")}} است؛ همتای سمت worker برای {{domxref("RTCRtpScriptTransform")}}.

```js
addEventListener("rtctransform", (event) => {
  let transform;
  // Select a transform based on passed options
  if (event.transformer.options.name === "senderTransform")
    transform = createSenderTransform(); // A TransformStream
  else if (event.transformer.options.name === "receiverTransform")
    transform = createReceiverTransform(); // A TransformStream
  else return;

  // Pipe frames from the readable to writeable through TransformStream
  event.transformer.readable
    .pipeThrough(transform)
    .pipeTo(event.transformer.writable);
});
```

رویداد `rtctransform` زمانی شلیک می‌شود که یک فریم کدگذاری‌شده روی {{domxref("RTCRtpScriptTransformer")}} در صف قرار می‌گیرد و فقط یکبار نیز هنگام ساخته‌شدن {{domxref("RTCRtpScriptTransformer")}} متناظر با آن، شلیک می‌شود. کد ابتدا با استفاده از مقدار `name` که در گزینه‌ها (options) ارسال شده است، مشخص می‌کند کدام تبدیل اعمال شود (این امکان را می‌دهد که نمونه‌های {{domxref("RTCRtpScriptTransform")}} اضافه‌شده به خطوط لوله ورودی و خروجی WebRTC از یک worker مشترک استفاده کنند). سپس فریم‌های کدگذاری‌شده از readable، از طریق {{domxref("TransformStream")}} انتخاب‌شده، به writeable هدایت می‌شوند. کد تبدیل واقعی در اینجا نشان داده نشده است.

توجه داشته باشید که این کد بخشی از یک مثال کامل‌تر است که در {{domxref("WebRTC API/Using Encoded Transforms", "Using WebRTC Encoded Transforms", "", "nocode")}} ارائه شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("WebRTC API/Using Encoded Transforms", "Using WebRTC Encoded Transforms", "", "nocode")}}