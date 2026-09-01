---
title: "HTMLMediaElement: setSinkId() method"
short-title: setSinkId()
slug: Web/API/HTMLMediaElement/setSinkId
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.setSinkId
---

{{APIRef("Audio Output Devices API")}}{{securecontext_header}}

متد **`setSinkId()`** در واسط {{domxref("HTMLMediaElement")}} شناسهٔ دستگاه صوتی مورد استفاده برای خروجی را تنظیم می‌کند و یک {{jsxref("Promise")}} برمی‌گرداند.

این کار تنها زمانی کار می‌کند که به برنامه اجازه داده شده باشد از دستگاه مشخص‌شده استفاده کند. برای اطلاعات بیشتر به [نیازمندی‌های امنیتی](#security_requirements) در زیر مراجعه کنید.

## نحو (Syntax)

```js-nolint
setSinkId(sinkId)
```

### پارامترها

- `sinkId`
  - : {{domxref("MediaDeviceInfo.deviceId")}} دستگاه خروجی صوتی.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به {{jsxref("undefined")}} تحقق می‌یابد.

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) با [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) برای مسدود کردن استفاده از خروجی‌های صوتی استفاده شود، بازگردانده می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر `deviceId` با هیچ دستگاه خروجی صوتی مطابقت نداشته باشد، بازگردانده می‌شود.
- `AbortError` {{domxref("DOMException")}}
  - : اگر تعویض دستگاه خروجی صوتی به دستگاه جدید ناموفق باشد، بازگردانده می‌شود.

## نیازمندی‌های امنیتی

دسترسی به این API مشروط به محدودیت‌های زیر است:

- متد باید در یک [بافت امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) فراخوانی شود.
- دسترسی ممکن است توسط [Permission Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) HTTP با [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) محدود شود.
- برای دسترسی به دستگاهی غیر از دستگاه پیش‌فرض، اجازهٔ کاربر لازم است. کاربر با انتخاب دستگاهی که شناسهٔ آن در اعلان نمایش‌داده‌شده توسط {{domxref("MediaDevices.selectAudioOutput()")}} مرتبط است، اجازه می‌دهد.

## مثال‌ها

این مثال نشان می‌دهد که چگونه یک دستگاه خروجی صوتی را از آرایهٔ بازگردانده‌شده توسط {{domxref("MediaDevices.enumerateDevices()")}} انتخاب کرده و آن را به عنوان خروجی صدا تنظیم کنید. توجه داشته باشید که نتیجهٔ `enumerateDevices()` فقط شامل دستگاه‌هایی می‌شود که اجازهٔ کاربر برای آن‌ها لازم نیست یا قبلاً داده شده است.

```js
const devices = await navigator.mediaDevices.enumerateDevices();
const audioDevice = devices.find((device) => device.kind === "audiooutput");
const audio = document.createElement("audio");
await audio.setSinkId(audioDevice.deviceId);
console.log(`Audio is being output on ${audio.sinkId}`);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Audio Output Devices API](/en-US/docs/Web/API/Audio_Output_Devices_API)
- {{domxref("MediaDevices.selectAudioOutput()")}}
- {{domxref("HTMLMediaElement.sinkId")}}