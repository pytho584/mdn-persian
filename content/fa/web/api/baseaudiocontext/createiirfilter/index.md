---
title: "BaseAudioContext: createIIRFilter() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createIIRFilter"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createIIRFilter() method"
short-title: createIIRFilter()
slug: Web/API/BaseAudioContext/createIIRFilter
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createIIRFilter
---

{{ APIRef("Web Audio API") }}

روش **`createIIRFilter()`** از رابط {{domxref("BaseAudioContext")}} یک {{ domxref("IIRFilterNode") }} می‌سازد که نمایانگر یک فیلتر **[پاسخ ضربه بینهایت](https://en.wikipedia.org/wiki/Infinite_impulse_response)** (IIR) عمومی است که می‌تواند به عنوان انواع مختلف فیلتر پیکربندی شود.

> [!NOTE]
> سازنده {{domxref("IIRFilterNode.IIRFilterNode", "IIRFilterNode()")}} روش توصیه‌شده برای ایجاد یک {{domxref("IIRFilterNode")}} است؛ به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## Syntax

```js-nolint
createIIRFilter(feedforward, feedback)
```

### Parameters

- `feedforward`
  - : آرایه‌ای از مقادیر ممیز شناور که ضرایب پیش‌خور (صورت) را برای تابع انتقال فیلتر IIR مشخص می‌کند. حداکثر طول این آرایه ۲۰ است و حداقل یک مقدار باید غیرصفر باشد.
- `feedback`
  - : آرایه‌ای از مقادیر ممیز شناور که ضرایب بازخورد (مخرج) را برای تابع انتقال فیلتر IIR مشخص می‌کند. این آرایه می‌تواند تا ۲۰ عضو داشته باشد که اولین آنها نباید صفر باشد.

### Return value

یک {{domxref("IIRFilterNode")}} که فیلتر را با آرایه‌های ضرایب بازخورد و پیش‌خور مشخص‌شده پیاده‌سازی می‌کند.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر تمام ضرایب `feedforward` صفر باشند، یا اگر اولین ضریب `feedback` صفر باشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر یکی یا هر دو آرایه ورودی بیش از ۲۰ عضو داشته باشند، پرتاب می‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("IIRFilterNode")}}
- {{domxref("AudioNode")}}