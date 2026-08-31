---
title: "AudioListener"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener"
translated_by: "n8n + AI"
---

{{ APIRef("Web Audio API") }}

رابط `AudioListener` موقعیت و جهت شخصی را که به صحنه صوتی گوش میدهد، نشان میدهد و در [مکانمندی صوتی](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics) استفاده میشود. همه {{domxref("PannerNode")}}ها در رابطه با `AudioListener` ذخیره‌شده در ویژگی {{domxref("BaseAudioContext.listener")}} مکانمند می‌شوند.

توجه به این نکته مهم است که فقط یک شنونده برای هر زمینه وجود دارد و آن یک {{domxref("AudioNode")}} نیست.

![We see the position, up and front vectors of an AudioListener, with the up and front vectors at 90° from the other.](webaudiolistenerreduced.png)

## ویژگی‌های نمونه

> [!NOTE]
> مقادیر موقعیت، رو به جلو و بالا با استفاده از نحوهای متفاوت تنظیم و بازیابی می‌شوند. بازیابی، برای مثال، با دسترسی به `AudioListener.positionX` انجام می‌شود، در حالی که تنظیم همان ویژگی با `AudioListener.positionX.value` انجام می‌شود. به همین دلیل این مقادیر فقط خواندنی علامت‌گذاری نشده‌اند، همان‌طور که در IDL مشخصات ظاهر می‌شوند.

- {{domxref("AudioListener.positionX")}}
  - : موقعیت افقی شنونده را در یک دستگاه مختصات دکارتی راست‌دست نشان می‌دهد. مقدار پیش‌فرض 0 است.
- {{domxref("AudioListener.positionY")}}
  - : موقعیت عمودی شنونده را در یک دستگاه مختصات دکارتی راست‌دست نشان می‌دهد. مقدار پیش‌فرض 0 است.
- {{domxref("AudioListener.positionZ")}}
  - : موقعیت طولی (جلو و عقب) شنونده را در یک دستگاه مختصات دکارتی راست‌دست نشان می‌دهد. مقدار پیش‌فرض 0 است.
- {{domxref("AudioListener.forwardX")}}
  - : موقعیت افقی جهت رو به جلوی شنونده را در همان دستگاه مختصات دکارتی مقادیر موقعیت (`positionX`، `positionY` و `positionZ`) نشان می‌دهد. مقادیر رو به جلو و بالا به صورت خطی از یکدیگر مستقل هستند. مقدار پیش‌فرض 0 است.
- {{domxref("AudioListener.forwardY")}}
  - : موقعیت عمودی جهت رو به جلوی شنونده را در همان دستگاه مختصات دکارتی مقادیر موقعیت (`positionX`، `positionY` و `positionZ`) نشان می‌دهد. مقادیر رو به جلو و بالا به صورت خطی از یکدیگر مستقل هستند. مقدار پیش‌فرض 0 است.
- {{domxref("AudioListener.forwardZ")}}
  - : موقعیت طولی (جلو و عقب) جهت رو به جلوی شنونده را در همان دستگاه مختصات دکارتی مقادیر موقعیت (`positionX`، `positionY` و `positionZ`) نشان می‌دهد. مقادیر رو به جلو و بالا به صورت خطی از یکدیگر مستقل هستند. مقدار پیش‌فرض 1- است.
- {{domxref("AudioListener.upX")}}
  - : موقعیت افقی بالای سر شنونده را در همان دستگاه مختصات دکارتی مقادیر موقعیت (`positionX`، `positionY` و `positionZ`) نشان می‌دهد. مقادیر رو به جلو و بالا به صورت خطی از یکدیگر مستقل هستند. مقدار پیش‌فرض 0 است.
- {{domxref("AudioListener.upY")}}
  - : موقعیت عمودی بالای سر شنونده را در همان دستگاه مختصات دکارتی مقادیر موقعیت (`positionX`، `positionY` و `positionZ`) نشان می‌دهد. مقادیر رو به جلو و بالا به صورت خطی از یکدیگر مستقل هستند. مقدار پیش‌فرض 1 است.
- {{domxref("AudioListener.upZ")}}
  - : موقعیت طولی (جلو و عقب) بالای سر شنونده را در همان دستگاه مختصات دکارتی مقادیر موقعیت (`positionX`، `positionY` و `positionZ`) نشان می‌دهد. مقادیر رو به جلو و بالا به صورت خطی از یکدیگر مستقل هستند. مقدار پیش‌فرض 0 است.

## روش‌های نمونه

- {{domxref("AudioListener.setOrientation()")}} {{deprecated_inline}}
  - : جهت شنونده را تنظیم می‌کند.
- {{domxref("AudioListener.setPosition()")}} {{deprecated_inline}}
  - : موقعیت شنونده را تنظیم می‌کند.

> [!NOTE]
> اگرچه این روش‌ها منسوخ شده‌اند، اما در حال حاضر تنها راه تنظیم جهت و موقعیت در فایرفاکس هستند (به [باگ 1283029 فایرفاکس](https://bugzil.la/1283029) مراجعه کنید).

## ویژگی‌های منسوخ

روش‌های `setOrientation()` و `setPosition()` با تنظیم معادل‌های ویژگی آن‌ها جایگزین شده‌اند. برای مثال، `setPosition(x, y, z)` را می‌توان با تنظیم `positionX.value`، `positionY.value` و `positionZ.value` به ترتیب به دست آورد.

## مثال

برای کد مثال به [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)