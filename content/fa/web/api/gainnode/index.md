---
title: "GainNode"
---

---
title: GainNode
slug: Web/API/GainNode
page-type: web-api-interface
browser-compat: api.GainNode
---

{{ APIRef("Web Audio API") }}

رابطه `GainNode` تغییر در حجم صدا را نشان می‌دهد. این یک ماژول پردازش صوتی {{domxref("AudioNode")}} است که باعث می‌شود یک بهره (gain) معین به داده ورودی اعمال شود و سپس به خروجی منتقل شود. یک `GainNode` همیشه دقیقاً یک ورودی و یک خروجی دارد، هر دو با تعداد کانال‌های یکسان.

بهره یک مقدار بدون واحد است که با زمان تغییر می‌کند و در هر نمونه متناظر از تمام کانال‌های ورودی ضرب می‌شود. اگر تغییر داده شود، بهره جدید بلافاصله اعمال می‌شود که باعث ایجاد «کلیک»های ناخوشایند در صدای حاصل می‌شود. برای جلوگیری از این اتفاق، هرگز مقدار را مستقیماً تغییر ندهید؛ بلکه از روش‌های درون‌یابی نمایی در رابط {{domxref("AudioParam")}} استفاده کنید.

![The GainNode is increasing the gain of the output.](webaudiogainnode.png)

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
      <td><code>"max"</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال</th>
      <td><code>2</code> (در حالت پیش‌فرض تعداد کانال استفاده نمی‌شود)</td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("GainNode.GainNode", "GainNode()")}}
  - : یک شیء `GainNode` جدید ایجاد کرده و آن را برمی‌گرداند. به عنوان جایگزین، می‌توانید از متد کارخانه‌ای {{domxref("BaseAudioContext.createGain()")}} استفاده کنید؛ به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

- {{domxref("GainNode.gain")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} از نوع [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) که میزان بهره مورد اعمال را نشان می‌دهد. برای تغییر اثر بهره، باید {{domxref("AudioParam.value")}} را تنظیم کنید یا از روش‌های `AudioParam` استفاده کنید.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

## مثال

برای مشاهده کد نمونه‌ای که نحوه استفاده از یک `AudioContext` برای ایجاد یک `GainNode` را نشان می‌دهد، به [`BaseAudioContext.createGain()`](/en-US/docs/Web/API/BaseAudioContext/createGain#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)