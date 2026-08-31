---
title: ConstantSourceNode
slug: Web/API/ConstantSourceNode
page-type: web-api-interface
browser-compat: api.ConstantSourceNode
---

{{APIRef("Web Audio API")}}

رابط `ConstantSourceNode` — بخشی از Web Audio API — یک منبع صوتی (بر اساس {{domxref("AudioScheduledSourceNode")}}) را نشان می‌دهد که خروجی آن یک مقدار ثابت و بدون تغییر است. این ویژگی آن را برای مواردی که نیاز به یک مقدار ثابت از یک منبع صوتی دارید مفید می‌سازد. علاوه بر این، می‌توان از آن مانند یک {{domxref("AudioParam")}} قابل ساخت استفاده کرد، با خودکار کردن مقدار {{domxref("ConstantSourceNode.offset", "offset")}} یا با اتصال یک گره دیگر به آن؛ به [کنترل پارامترهای متعدد با ConstantSourceNode](/en-US/docs/Web/API/Web_Audio_API/Controlling_multiple_parameters_with_ConstantSourceNode) مراجعه کنید.

یک `ConstantSourceNode` هیچ ورودی ندارد و دقیقاً یک خروجی مونورال (تک‌کاناله) دارد. مقدار خروجی همیشه با مقدار پارامتر {{domxref("ConstantSourceNode.offset", "offset")}} یکسان است.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>0</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("ConstantSourceNode.ConstantSourceNode", "ConstantSourceNode()")}}
  - : یک نمونه جدید از `ConstantSourceNode` ایجاد و برمی‌گرداند، و به صورت اختیاری می‌توان یک شیء که مقادیر اولیه ویژگی‌های آن را تعیین می‌کند مشخص کرد. به عنوان جایگزین، می‌توانید از روش کارخانه‌ای {{domxref("BaseAudioContext.createConstantSource()")}} استفاده کنید؛ به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## ویژگی‌های نمونه

ویژگی‌ها را از رابط والد خود، {{domxref("AudioScheduledSourceNode")}}، به ارث می‌برد و ویژگی‌های زیر را اضافه می‌کند:

- {{domxref("ConstantSourceNode.offset", "offset")}}
  - : یک {{domxref("AudioParam")}} که مقدار خروجی پیوسته این منبع را مشخص می‌کند. مقدار پیش‌فرض 1.0 است.

### رویدادها

رویدادها را از رابط والد خود، {{domxref("AudioScheduledSourceNode")}}، به ارث می‌برد.

> [!NOTE] پیاده‌سازی برخی مرورگرها از این رویدادها بخشی از رابط {{domxref("AudioScheduledSourceNode")}} است.

- {{domxref("AudioScheduledSourceNode.ended_event","ended")}}
  - : زمانی که داده‌های `ConstantSourceNode` پخش را متوقف کرده است، شلیک می‌شود.

## روش‌های نمونه

متدها را از رابط والد خود، {{domxref("AudioScheduledSourceNode")}}، به ارث می‌برد.

> [!NOTE] پیاده‌سازی برخی مرورگرها از این متدها بخشی از رابط {{domxref("AudioScheduledSourceNode")}} است.

- {{domxref("AudioScheduledSourceNode.start", "start()")}}
  - : پخش یک صدا را در زمان دقیق برنامه‌ریزی می‌کند.
- {{domxref("AudioScheduledSourceNode.stop", "stop()")}}
  - : توقف پخش یک صدا را در زمان دقیق برنامه‌ریزی می‌کند.

## مثال

در مقاله [کنترل پارامترهای متعدد با ConstantSourceNode](/en-US/docs/Web/API/Web_Audio_API/Controlling_multiple_parameters_with_ConstantSourceNode)، یک `ConstantSourceNode` ایجاد شده است تا یک کنترل لغزنده بتواند بهره (gain) دو {{domxref("GainNode")}} را تغییر دهد. سه گره به این صورت تنظیم می‌شوند:

```js
gainNode2 = context.createGain();
gainNode3 = context.createGain();
gainNode2.gain.value = gainNode3.gain.value = 0.5;
volumeSliderControl.value = gainNode2.gain.value;

constantNode = context.createConstantSource();
constantNode.connect(gainNode2.gain);
constantNode.connect(gainNode3.gain);
constantNode.start();

gainNode2.connect(context.destination);
gainNode3.connect(context.destination);
```

این کد با ایجاد گره‌های بهره و تنظیم آن‌ها و کنترل لغزنده که مقدار آن‌ها را به 0.5 تنظیم می‌کند شروع می‌شود. سپس `ConstantSourceNode` با فراخوانی {{domxref("BaseAudioContext/createConstantSource", "AudioContext.createConstantSource()")}} ایجاد می‌شود، و پارامترهای بهره هر یک از دو گره بهره به `ConstantSourceNode` متصل می‌شوند. پس از شروع منبع ثابت با فراخوانی متد {{domxref("AudioScheduledSourceNode.start", "start()")}} آن. در نهایت، دو گره بهره به مقصد صوتی (معمولاً بلندگوها یا هدفون) متصل می‌شوند.

اکنون، هر زمان که مقدار {{domxref("ConstantSourceNode.offset", "constantNode.offset")}} تغییر کند، بهره در هر دو `gainNode2` و `gainNode3` به همان مقدار تغییر خواهد کرد.

برای مشاهده این مثال در عمل و همچنین خواندن بقیه کدهایی که این قطعات از آن گرفته شده‌اند، به [کنترل پارامترهای متعدد با ConstantSourceNode](/en-US/docs/Web/API/Web_Audio_API/Controlling_multiple_parameters_with_ConstantSourceNode) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("AudioScheduledSourceNode")}}
- {{domxref("AudioNode")}}