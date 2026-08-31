---
title: ChannelSplitterNode
slug: Web/API/ChannelSplitterNode
page-type: web-api-interface
browser-compat: api.ChannelSplitterNode
---

{{APIRef("Web Audio API")}}

رابط `ChannelSplitterNode` که اغلب در کنار نقطه‌ی مقابل آن، یعنی {{domxref("ChannelMergerNode")}} استفاده می‌شود، کانال‌های مختلف یک منبع صوتی را به مجموعه‌ای از خروجی‌های تک‌کاناله (mono) جدا می‌کند. این کار برای دسترسی جداگانه به هر کانال مفید است؛ مثلاً برای انجام میکس کانال زمانی که باید بهره (gain) هر کانال به‌صورت جداگانه کنترل شود.

![گره تقسیم‌کننده کانال پیش‌فرض با یک ورودی که به ۶ خروجی تک‌کاناله تقسیم می‌شود.](webaudiosplitter.png)

اگر `ChannelSplitterNode` شما همیشه فقط یک ورودی داشته باشد، تعداد خروجی‌ها توسط یک پارامتر در سازنده‌ی آن و در فراخوانی {{domxref("BaseAudioContext/createChannelSplitter", "AudioContext.createChannelSplitter()")}} تعیین می‌شود. اگر مقداری داده نشود، پیش‌فرض آن `6` خواهد بود. اگر تعداد کانال‌های ورودی کمتر از تعداد خروجی‌ها باشد، خروجی‌های اضافی بی‌صدا خواهند بود.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td>متغیر؛ پیش‌فرض <code>6</code>.</td>
    </tr>
    <tr>
      <th scope="row">حالت تعداد کانال</th>
      <td>
        <code>"explicit"</code>. پیاده‌سازی‌های قدیمی‌تر، طبق نسخه‌های قبلی
        مشخصات، از <code>"max"</code> استفاده می‌کنند.
      </td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال</th>
      <td>
        ثابت و برابر با تعداد خروجی‌ها. پیاده‌سازی‌های قدیمی‌تر، طبق نسخه‌های
        قبلی مشخصات، از <code>2</code> استفاده می‌کنند (در حالت تعداد پیش‌فرض
        استفاده نمی‌شود).
      </td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال</th>
      <td><code>"discrete"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("ChannelSplitterNode.ChannelSplitterNode()","ChannelSplitterNode()")}}
  - : یک نمونه‌ی جدید از شیء `ChannelSplitterNode` می‌سازد.

## ویژگی‌های نمونه

_ویژگی خاصی ندارد؛ ویژگی‌ها را از والد خود، {{domxref("AudioNode")}} به ارث می‌برد._

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از والد خود، {{domxref("AudioNode")}} به ارث می‌برد._

## مثال

برای کد مثال، [`BaseAudioContext.createChannelSplitter()`](/en-US/docs/Web/API/BaseAudioContext/createChannelSplitter#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)