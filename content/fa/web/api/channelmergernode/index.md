---
title: "ChannelMergerNode"
slug: Web/API/ChannelMergerNode
page-type: web-api-interface
browser-compat: api.ChannelMergerNode
---

{{APIRef("Web Audio API")}}

رابط `ChannelMergerNode` که اغلب همراه با رابط مخالف آن، یعنی {{domxref("ChannelSplitterNode")}} استفاده می‌شود، ورودی‌های مونو (تک‌کاناله) مختلف را در یک خروجی واحد ترکیب می‌کند. هر ورودی برای پر کردن یک کانال از خروجی استفاده می‌شود. این کار برای دسترسی جداگانه به هر کانال مفید است، برای مثال برای انجام میکس کانال که در آن بهره باید به‌طور جداگانه روی هر کانال کنترل شود.

![گره ادغام‌کننده کانال پیش‌فرض با شش ورودی مونو که یک خروجی واحد را تشکیل می‌دهند.](webaudiomerger.png)

`ChannelMergerNode` یک خروجی واحد دارد، اما به تعداد کانال‌هایی که باید ادغام شوند ورودی دارد؛ تعداد ورودی‌ها به عنوان پارامتر سازنده آن و فراخوانی {{domxref("BaseAudioContext/createChannelMerger", "AudioContext.createChannelMerger()")}} تعریف می‌شود. در صورتی که مقداری داده نشود، پیش‌فرض آن `6` خواهد بود.

با استفاده از `ChannelMergerNode` می‌توان خروجی‌هایی با تعداد کانال‌های بیشتر از آنچه سخت‌افزار رندرینگ قادر به پردازش است ایجاد کرد. در این حالت، هنگامی که سیگنال به شیء {{domxref("BaseAudioContext/listener", "AudioContext.listener")}} ارسال می‌شود، کانال‌های اضافی نادیده گرفته می‌شوند.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td>متغیر؛ پیش‌فرض <code>6</code>.</td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">حالت تعداد کانال‌ها</th>
      <td><code>"explicit"</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال‌ها</th>
      <td><code>2</code> (در حالت تعداد پیش‌فرض استفاده نمی‌شود)</td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("ChannelMergerNode.ChannelMergerNode()", "ChannelMergerNode()")}}
  - : یک نمونه جدید از شیء `ChannelMergerNode` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی خاصی ندارد؛ ویژگی‌ها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

## مثال

برای کد مثال، به [`BaseAudioContext.createChannelMerger()`](/en-US/docs/Web/API/BaseAudioContext/createChannelMerger#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)