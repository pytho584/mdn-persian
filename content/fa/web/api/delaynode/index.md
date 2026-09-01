---
title: DelayNode
slug: Web/API/DelayNode
page-type: web-api-interface
browser-compat: api.DelayNode
---

{{APIRef("Web Audio API")}}

اینترفیس **`DelayNode`** یک [خط تأخیر](https://en.wikipedia.org/wiki/Digital_delay_line) را نمایش می‌دهد؛ یک ماژول پردازش صوتی {{domxref("AudioNode")}} که بین رسیدن داده ورودی و انتشار آن به خروجی، تأخیر ایجاد می‌کند.

یک `DelayNode` همیشه دقیقاً یک ورودی و یک خروجی دارد و هر دو تعداد کانال‌های یکسانی دارند.

![DelayNode به‌عنوان یک خط تأخیر عمل می‌کند، در اینجا با مقدار ۱ ثانیه.](webaudiodelaynode.png)

هنگام ایجاد یک گراف دارای چرخه، وجود حداقل یک `DelayNode` در چرخه الزامی است؛ در غیر این صورت، گره‌های شرکت‌کننده در چرخه بی‌صدا خواهند شد.

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

- {{domxref("DelayNode.DelayNode", "DelayNode()")}}
  - : یک نمونه جدید از شیء DelayNode ایجاد می‌کند. به‌عنوان گزینه جایگزین، می‌توانید از روش کارخانه‌ای {{domxref("BaseAudioContext.createDelay()")}} استفاده کنید؛ به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## ویژگی‌های نمونه

ویژگی‌هایی را از والد خود، {{domxref("AudioNode")}} به ارث می‌برد.

- {{domxref("DelayNode.delayTime")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} از نوع [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) که میزان تأخیر اعمال‌شده را بر حسب ثانیه نشان می‌دهد.

## روش‌های نمونه

روش خاصی ندارد؛ روش‌ها را از والد خود، {{domxref("AudioNode")}} به ارث می‌برد.

## مثال

برای کد مثال، به [`BaseAudioContext.createDelay()`](/en-US/docs/Web/API/BaseAudioContext/createDelay#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)