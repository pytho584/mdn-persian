---
title: "AudioScheduledSourceNode"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioScheduledSourceNode"
translated_by: "n8n + AI"
---

---
title: AudioScheduledSourceNode
slug: Web/API/AudioScheduledSourceNode
page-type: web-api-interface
browser-compat: api.AudioScheduledSourceNode
---

{{APIRef("Web Audio API")}}

رابط `AudioScheduledSourceNode` — بخشی از Web Audio API — یک رابط والد برای چندین نوع رابط گره منبع صوتی است که توانایی شروع و توقف را، به‌طور اختیاری در زمان‌های مشخص، به اشتراک می‌گذارند. به‌طور خاص، این رابط متدهای {{domxref("AudioScheduledSourceNode.start", "start()")}} و {{domxref("AudioScheduledSourceNode.stop", "stop()")}} و همچنین رویداد {{domxref("AudioScheduledSourceNode.ended_event", "ended")}} را تعریف می‌کند.

> [!NOTE]
> شما نمی‌توانید یک شیء `AudioScheduledSourceNode` را مستقیماً ایجاد کنید. در عوض، از رابطی استفاده کنید که آن را گسترش می‌دهد، مانند {{domxref("AudioBufferSourceNode")}}، {{domxref("OscillatorNode")}} یا {{domxref("ConstantSourceNode")}}.

مگر در غیر این صورت ذکر شده باشد، گره‌های مبتنی بر `AudioScheduledSourceNode` هنگام عدم پخش (یعنی قبل از فراخوانی `start()` و بعد از فراخوانی `stop()`) خروجی سکوت تولید می‌کنند. سکوت، همان‌طور که همیشه مرسوم است، با جریانی از نمونه‌ها با مقدار صفر (0) نشان داده می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از رابط والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

## متدهای نمونه

_متدها را از رابط والد خود، {{domxref("AudioNode")}}، به ارث می‌برد و متدهای زیر را اضافه می‌کند:_

- {{domxref("AudioScheduledSourceNode.start", "start()")}}
  - : شروع پخش صدای ثابت را در زمان مشخص‌شده زمان‌بندی می‌کند. اگر زمانی مشخص نشود، گره بلافاصله پخش را آغاز می‌کند.
- {{domxref("AudioScheduledSourceNode.stop", "stop()")}}
  - : توقف پخش گره را در زمان مشخص‌شده زمان‌بندی می‌کند. اگر زمانی مشخص نشود، گره بلافاصله پخش را متوقف می‌کند.

## رویدادها

به این رویدادها با استفاده از [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) گوش دهید، یا با انتساب یک شنونده رویداد به ویژگی `oneventname` این رابط.

- [`ended`](/en-US/docs/Web/API/AudioScheduledSourceNode/ended_event)
  - : زمانی رخ می‌دهد که گره منبع پخش را متوقف کرده باشد؛ چه به دلیل رسیدن به زمان توقف از پیش تعیین‌شده، چه به دلیل اجرای کامل مدت‌زمان صدا، یا به دلیل پخش کل بافر.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("AudioNode")}}