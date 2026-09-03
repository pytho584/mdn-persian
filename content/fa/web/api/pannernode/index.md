---
title: PannerNode
slug: Web/API/PannerNode
page-type: web-api-interface
browser-compat: api.PannerNode
---

{{ APIRef("Web Audio API") }}

رابط `PannerNode` یک شیء پردازش صوتی را تعریف می‌کند که مکان، جهت و رفتار سیگنال منبع صوتی را در یک فضای فیزیکی شبیه‌سازی‌شده نشان می‌دهد. این {{domxref("AudioNode")}} از مختصات دکارتی راست‌گرد برای توصیف _موقعیت_ منبع به‌عنوان یک بردار و _جهت‌گیری_ آن به‌عنوان یک مخروط جهت‌دار سه‌بعدی استفاده می‌کند.

یک `PannerNode` همیشه دقیقاً یک ورودی و یک خروجی دارد: ورودی می‌تواند _مونو_ یا _استریو_ باشد، اما خروجی همیشه _استریو_ (۲ کانال) است؛ بدون حداقل دو کانال صوتی، افکت پننگ امکان‌پذیر نیست.

![PannerNode موقعیت و جهت فضایی یک سیگنال معین را تعریف می‌کند.](webaudiopannernode.png)

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">حالت تعداد کانال</th>
      <td><code>"clamped-max"</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال</th>
      <td><code>2</code></td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("PannerNode.PannerNode", "PannerNode()")}}
  - : یک نمونه جدید از شیء `PannerNode` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌های والد خود، {{domxref("AudioNode")}} را به ارث می‌برد._

> [!NOTE]
> مقادیر جهت‌گیری و موقعیت با نحو متفاوتی تنظیم و بازیابی می‌شوند، زیرا به‌صورت مقادیر {{domxref("AudioParam")}} ذخیره شده‌اند. بازیابی مقدار با دسترسی مستقیم انجام می‌شود، مثلاً `PannerNode.positionX`، در حالی که تنظیم همان ویژگی با `PannerNode.positionX.value` صورت می‌گیرد. به همین دلیل این مقادیر فقط‌خواندنی علامت‌گذاری نشده‌اند و به همین شکل در WebIDL ظاهر می‌شوند.

- {{domxref("PannerNode.coneInnerAngle")}}
  - : یک مقدار double که زاویه (بر حسب درجه) مخروط داخلی را توصیف می‌کند؛ در داخل این مخروط هیچ کاهش حجمی رخ نمی‌دهد.
- {{domxref("PannerNode.coneOuterAngle")}}
  - : یک مقدار double که زاویه (بر حسب درجه) مخروط بیرونی را توصیف می‌کند؛ خارج از این مخروط حجم صدا با مقدار ثابتی که توسط ویژگی `coneOuterGain` تعریف شده است کاهش می‌یابد.
- {{domxref("PannerNode.coneOuterGain")}}
  - : یک مقدار double که میزان کاهش حجم صدا را در خارج از مخروط تعریف‌شده توسط ویژگی `coneOuterAngle` توصیف می‌کند. مقدار پیش‌فرض آن `0` است، به این معنی که هیچ صدایی شنیده نمی‌شود.
- {{domxref("PannerNode.distanceModel")}}
  - : یک مقدار شمارشی که تعیین می‌کند با دور شدن منبع صوتی از شنونده، از کدام الگوریتم برای کاهش حجم صدا استفاده شود. مقادیر ممکن شامل `"linear"`، `"inverse"` و `"exponential"` است. مقدار پیش‌فرض `"inverse"` است.
- {{domxref("PannerNode.maxDistance")}}
  - : یک مقدار double که حداکثر فاصله بین منبع صوتی و شنونده را نشان می‌دهد؛ پس از این فاصله، دیگر حجم صدا کاهش نمی‌یابد.
- {{domxref("PannerNode.orientationX")}}
  - : موقعیت افقی بردار منبع صوتی را در دستگاه مختصات دکارتی راست‌گرد نشان می‌دهد. اگرچه این {{domxref("AudioParam")}} را نمی‌توان مستقیماً تغییر داد، می‌توان مقدار آن را با استفاده از ویژگی {{domxref("AudioParam.value", "value")}} آن تغییر داد. مقدار پیش‌فرض ۱ است.
- {{domxref("PannerNode.orientationY")}}
  - : موقعیت عمودی بردار منبع صوتی را در دستگاه مختصات دکارتی راست‌گرد نشان می‌دهد. اگرچه این {{domxref("AudioParam")}} را نمی‌توان مستقیماً تغییر داد، می‌توان مقدار آن را با استفاده از ویژگی {{domxref("AudioParam.value", "value")}} آن تغییر داد. مقدار پیش‌فرض ۰ است.
- {{domxref("PannerNode.orientationZ")}}
  - : موقعیت طولی (عقب و جلو) بردار منبع صوتی را در دستگاه مختصات دکارتی راست‌گرد نشان می‌دهد. اگرچه این {{domxref("AudioParam")}} را نمی‌توان مستقیماً تغییر داد، می‌توان مقدار آن را با استفاده از ویژگی {{domxref("AudioParam.value", "value")}} آن تغییر داد. مقدار پیش‌فرض ۰ است.
- {{domxref("PannerNode.panningModel")}}
  - : یک مقدار شمارشی که تعیین می‌کند برای قرار دادن صدا در فضای سه‌بعدی از کدام الگوریتم فضاسازی استفاده شود.
- {{domxref("PannerNode.positionX")}}
  - : موقعیت افقی صدا را در دستگاه مختصات دکارتی راست‌گرد نشان می‌دهد. اگرچه این {{domxref("AudioParam")}} را نمی‌توان مستقیماً تغییر داد، می‌توان مقدار آن را با استفاده از ویژگی {{domxref("AudioParam.value", "value")}} آن تغییر داد. مقدار پیش‌فرض ۰ است.
- {{domxref("PannerNode.positionY")}}
  - : موقعیت عمودی صدا را در دستگاه مختصات دکارتی راست‌گرد نشان می‌دهد. اگرچه این {{domxref("AudioParam")}} را نمی‌توان مستقیماً تغییر داد، می‌توان مقدار آن را با استفاده از ویژگی {{domxref("AudioParam.value", "value")}} آن تغییر داد. مقدار پیش‌فرض ۰ است.
- {{domxref("PannerNode.positionZ")}}
  - : موقعیت طولی (عقب و جلو) صدا را در دستگاه مختصات دکارتی راست‌گرد نشان می‌دهد. اگرچه این {{domxref("AudioParam")}} را نمی‌توان مستقیماً تغییر داد، می‌توان مقدار آن را با استفاده از ویژگی {{domxref("AudioParam.value", "value")}} آن تغییر داد. مقدار پیش‌فرض ۰ است.
- {{domxref("PannerNode.refDistance")}}
  - : یک مقدار double که فاصله مرجع برای کاهش حجم صدا را نشان می‌دهد؛ وقتی منبع صوتی از شنونده دورتر می‌شود، برای فاصله‌های بزرگ‌تر از این مقدار، حجم صدا بر اساس `rolloffFactor` و `distanceModel` کاهش می‌یابد.
- {{domxref("PannerNode.rolloffFactor")}}
  - : یک مقدار double که توصیف می‌کند با دور شدن منبع از شنونده، حجم صدا با چه سرعتی کاهش می‌یابد. این مقدار در همه مدل‌های فاصله استفاده می‌شود.

## متدهای نمونه

_متدهای والد خود، {{domxref("AudioNode")}} را به ارث می‌برد._

- {{domxref("PannerNode.setPosition()")}} {{deprecated_inline}}
  - : موقعیت منبع صوتی را نسبت به شنونده تعریف می‌کند (شنونده با یک شیء {{domxref("AudioListener")}} که در ویژگی {{domxref("BaseAudioContext.listener")}} ذخیره شده است نمایش داده می‌شود).
- {{domxref("PannerNode.setOrientation()")}} {{deprecated_inline}}
  - : جهتی که منبع صوتی در آن پخش می‌شود را تعریف می‌کند.

## مثال‌ها

برای نمونه‌کد، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)