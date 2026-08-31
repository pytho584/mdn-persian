---
title: "Audio Output Devices API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Audio_Output_Devices_API"
translated_by: "n8n + AI"
---

---
title: Audio Output Devices API
slug: Web/API/Audio_Output_Devices_API
page-type: web-api-overview
status:
  - experimental
browser-compat:
  - api.MediaDevices.selectAudioOutput
  - api.HTMLMediaElement.setSinkId
  - api.HTMLMediaElement.sinkId
  - http.headers.Permissions-Policy.speaker-selection
spec-urls: https://w3c.github.io/mediacapture-output/
---

{{DefaultAPISidebar("Audio Output Devices API")}}{{securecontext_header}}{{SeeCompatTable}}

API **Audio Output Devices** به برنامه‌های وب اجازه می‌دهد تا از کاربران درباره اینکه از کدام دستگاه خروجی برای پخش صدا استفاده شود، سوال کند.

## مفاهیم و کاربرد

سیستم‌های عامل معمولاً به کاربران اجازه می‌دهند تا مشخص کنند که صدا از بلندگوها، هدست بلوتوث یا برخی دستگاه‌های خروجی دیگر پخش شود. این API به برنامه‌ها اجازه می‌دهد تا همین قابلیت را درون یک صفحه وب فراهم کنند.

حتی اگر توسط یک خط مشی مجوز اجازه داده شود، دسترسی به یک دستگاه خروجی صوتی خاص همچنان نیازمند مجوز صریح کاربر است، زیرا ممکن است کاربر در مکانی باشد که پخش صدا از طریق برخی دستگاه‌های خروجی مناسب نباشد.

این API متد {{domxref("MediaDevices.selectAudioOutput()")}} را فراهم می‌کند که به کاربران اجازه می‌دهد دستگاه خروجی صوتی مورد نظر خود را از میان دستگاه‌هایی که توسط دایرکتیو [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) سربرگ HTTP {{httpheader("Permissions-Policy")}} برای سند مجاز شده‌اند، انتخاب کنند. سپس دستگاه انتخاب‌شده مجوز کاربر را دارد و می‌توان با {{domxref("MediaDevices.enumerateDevices()")}} آن را شمارش کرد و با استفاده از {{domxref("HTMLMediaElement.setSinkId()")}} به عنوان دستگاه خروجی صوتی تنظیم کرد.

دستگاه‌های صوتی ممکن است به طور دلخواه متصل و قطع شوند. برنامه‌هایی که می‌خواهند به این نوع تغییر واکنش نشان دهند می‌توانند به رویداد {{domxref("MediaDevices/devicechange_event", "devicechange")}} گوش دهند و از {{domxref("MediaDevices.enumerateDevices", "enumerateDevices()")}} برای تعیین اینکه آیا `sinkId` در دستگاه‌های بازگشتی وجود دارد استفاده کنند. این ممکن است باعث توقف یا ازسرگیری پخش شود.

## رابط‌ها

### افزونه‌هایی به رابط‌های دیگر

API Audio Output Devices API‌های زیر را گسترش می‌دهد و ویژگی‌های ذکر شده را اضافه می‌کند:

#### MediaDevices

- {{domxref("MediaDevices.selectAudioOutput()")}}
  - : این متد از کاربر می‌خواهد یک دستگاه خروجی صوتی خاص، مثلاً یک بلندگو یا هدست را انتخاب کند. انتخاب یک دستگاه به کاربر مجوز استفاده از آن دستگاه را می‌دهد و اطلاعاتی درباره دستگاه، از جمله شناسه آن، بازمی‌گرداند.

#### HTMLMediaElement

- {{domxref("HTMLMediaElement.setSinkId()")}}
  - : این متد شناسه دستگاه صوتی را که برای خروجی استفاده می‌شود تنظیم می‌کند، در صورت مجاز بودن از آن استفاده خواهد شد.
- {{domxref("HTMLMediaElement.sinkId")}}
  - : این ویژگی شناسه یکتای دستگاه صوتی مورد استفاده برای خروجی را بازمی‌گرداند، یا اگر دستگاه پیش‌فرض عامل کاربر استفاده می‌شود یک رشته خالی.

## الزامات امنیتی

دسترسی به API مشروط به محدودیت‌های زیر است:

- همه متدها و ویژگی‌ها فقط در یک [زمینه امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) قابل فراخوانی هستند.

- {{domxref("MediaDevices.selectAudioOutput()")}} مجوز کاربر را برای استفاده از یک دستگاه انتخاب‌شده به عنوان خروجی صدا اعطا می‌کند:
  - دسترسی ممکن است توسط [خط مشی مجوز](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) HTTP [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) محدود شود.
  - [فعال‌سازی موقت کاربر](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است. کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل داشته باشد تا متد فراخوانی شود.

- {{domxref("HTMLMediaElement.setSinkId()")}} یک شناسه مجاز را به عنوان خروجی صدا تنظیم می‌کند:
  - دسترسی ممکن است توسط [خط مشی مجوز](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) HTTP [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) محدود شود.
  - مجوز کاربر برای تنظیم یک شناسه دستگاه غیرپیش‌فرض الزامی است.
    - این می‌تواند از انتخاب در پنجره بازشوی راه‌اندازی‌شده توسط `MediaDevices.selectAudioOutput()` حاصل شود.
    - مجوز کاربر برای تنظیم دستگاه خروجی همچنین به طور ضمنی اعطا می‌شود اگر کاربر قبلاً مجوز استفاده از یک دستگاه ورودی رسانه در همان گروه را با {{domxref("MediaDevices.getUserMedia()")}} اعطا کرده باشد.

<!-- The line below is "true" but this is not implemented in any browser -->
<!-- The permission status can be queried using the [Permissions API](/en-US/docs/Web/API/Permissions_API) method [`navigator.permissions.query()`](/en-US/docs/Web/API/Permissions/query), passing a permission descriptor with the `speaker-selection` permission. -->

## نمونه‌ها

در اینجا مثالی از استفاده از `selectAudioOutput()`، درون یک تابع که با کلیک دکمه فعال می‌شود، و سپس تنظیم دستگاه انتخاب‌شده به عنوان خروجی صدا آورده شده است.

کد ابتدا بررسی می‌کند که آیا `selectAudioOutput()` پشتیبانی می‌شود، و اگر پشتیبانی می‌شود، از آن برای انتخاب یک خروجی و بازگرداندن [شناسه دستگاه](/en-US/docs/Web/API/MediaDeviceInfo/deviceId) استفاده می‌کند. سپس با استفاده از خروجی پیش‌فرض مقداری صدا پخش می‌کنیم و سپس `setSinkId()` را فراخوانی می‌کنیم تا به دستگاه خروجی انتخاب‌شده سوئیچ کنیم.

```js
document.querySelector("#myButton").addEventListener("click", async () => {
  if (!navigator.mediaDevices.selectAudioOutput) {
    console.log("selectAudioOutput() not supported or not in secure context.");
    return;
  }

  // Display prompt to select device
  const audioDevice = await navigator.mediaDevices.selectAudioOutput();

  // Create an audio element and start playing audio on the default device
  const audio = document.createElement("audio");
  audio.src = "https://example.com/audio.mp3";
  audio.play();

  // Change the sink to the selected audio output device.
  audio.setSinkId(audioDevice.deviceId);
});
```

توجه داشته باشید که اگر جزئیات خروجی را لاگ کنید، ممکن است چیزی شبیه به این باشد:

```js
console.log(
  `${audioDevice.kind}: ${audioDevice.label} id = ${audioDevice.deviceId}`,
);
// audiooutput: Realtek Digital Output (Realtek(R) Audio) id = 0wE6fURSZ20H0N2NbxqgowQJLWbwo+5ablCVVJwRM3k=
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}