---
title: "BiquadFilterNode"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode"
translated_by: "n8n + AI"
---

---
title: BiquadFilterNode
slug: Web/API/BiquadFilterNode
page-type: web-api-interface
browser-compat: api.BiquadFilterNode
---

{{APIRef("Web Audio API")}}

رابطه `BiquadFilterNode` یک فیلتر ساده با مرتبه پایین را نشان می‌دهد و با استفاده از متد {{ domxref("BaseAudioContext/createBiquadFilter") }} ساخته می‌شود. این یک {{domxref("AudioNode")}} است که می‌تواند انواع مختلف فیلترها، دستگاه‌های کنترل تن و اکولایزرهای گرافیکی را نشان دهد. یک `BiquadFilterNode` همیشه دقیقاً یک ورودی و یک خروجی دارد.

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
      <td><code>2</code> (در حالت پیش‌فرض تعداد استفاده نمی‌شود)</td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("BiquadFilterNode.BiquadFilterNode", "BiquadFilterNode()")}}
  - : یک نمونه جدید از شیء `BiquadFilterNode` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌های زیر را از والد خود، {{domxref("AudioNode")}} به ارث می‌برد._

> [!NOTE]
> اگرچه اشیاء `AudioParam` برگشتی فقط‌خواندنی هستند، مقادیری که نشان می‌دهند فقط‌خواندنی نیستند.

- {{domxref("BiquadFilterNode.frequency")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} با [a-rate](/en-US/docs/Web/API/AudioParam#a-rate)، یک عدد اعشاری (double) که فرکانس را در الگوریتم فیلتر فعلی بر حسب هرتز (Hz) نشان می‌دهد.
- {{domxref("BiquadFilterNode.detune")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} با [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) که انحراف فرکانس را بر حسب [سنت](https://en.wikipedia.org/wiki/Cent_%28music%29) نشان می‌دهد.
- {{domxref("BiquadFilterNode.Q")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} با [a-rate](/en-US/docs/Web/API/AudioParam#a-rate)، یک عدد اعشاری که نمایانگر [ضریب Q](https://en.wikipedia.org/wiki/Q_factor) یا _عامل کیفیت_ است.
- {{domxref("BiquadFilterNode.gain")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioParam")}} با [a-rate](/en-US/docs/Web/API/AudioParam#a-rate)، یک عدد اعشاری که نمایانگر [بهره (gain)](https://en.wikipedia.org/wiki/Gain) استفاده‌شده در الگوریتم فیلتر فعلی است.
- {{domxref("BiquadFilterNode.type")}}
  - : یک مقدار رشته‌ای که نوع الگوریتم فیلتری را که گره پیاده‌سازی می‌کند تعریف می‌کند.

    <table class="standard-table">
      <caption>
        معنای پارامترهای مختلف بسته به نوع فیلتر (detune صرف‌نظر از نوع، معنی یکسانی دارد، بنابراین در زیر فهرست نشده است)
      </caption>
      <thead>
        <tr>
          <th scope="row"><code>type</code></th>
          <th scope="col">توضیحات</th>
          <th scope="col"><code>frequency</code></th>
          <th scope="col"><code>Q</code></th>
          <th scope="col"><code>gain</code></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row"><code>lowpass</code></th>
          <td>
            فیلتر پایین‌گذر رزونانسی استاندارد مرتبه دوم با شیب 12dB/اکتاو.
            فرکانس‌های پایین‌تر از cutoff عبور می‌کنند؛ فرکانس‌های بالاتر از آن تضعیف می‌شوند.
          </td>
          <td>فرکانس cutoff.</td>
          <td>
            نشان می‌دهد که فرکانس در اطراف cutoff چقدر قله‌دار است. هرچه مقدار بیشتر باشد، قله بزرگ‌تر است.
          </td>
          <td><em>استفاده نشده</em></td>
        </tr>
        <tr>
          <th scope="row"><code>highpass</code></th>
          <td>
            فیلتر بالاگذر رزونانسی استاندارد مرتبه دوم با شیب 12dB/اکتاو.
            فرکانس‌های پایین‌تر از cutoff تضعیف می‌شوند؛ فرکانس‌های بالاتر از آن عبور می‌کنند.
          </td>
          <td>فرکانس cutoff.</td>
          <td>
            نشان می‌دهد که فرکانس در اطراف cutoff چقدر قله‌دار است. هرچه مقدار بیشتر باشد، قله بزرگ‌تر است.
          </td>
          <td><em>استفاده نشده</em></td>
        </tr>
        <tr>
          <th scope="row"><code>bandpass</code></th>
          <td>
            فیلتر میان‌گذر استاندارد مرتبه دوم. فرکانس‌های خارج از محدوده داده‌شده تضعیف می‌شوند؛ فرکانس‌های داخل آن عبور می‌کنند.
          </td>
          <td>مرکز محدوده فرکانس‌ها.</td>
          <td>
            عرض باند فرکانس را کنترل می‌کند. هرچه مقدار <code>Q</code> بزرگ‌تر باشد، باند فرکانس کوچک‌تر است.
          </td>
          <td><em>استفاده نشده</em></td>
        </tr>
        <tr>
          <th scope="row"><code>lowshelf</code></th>
          <td>
            فیلتر قفسه پایین استاندارد مرتبه دوم. فرکانس‌های پایین‌تر از فرکانس تقویت یا تضعیف می‌شوند؛ فرکانس‌های بالاتر از آن بدون تغییر باقی می‌مانند.
          </td>
          <td>
            حد بالایی فرکانس‌هایی که تقویت یا تضعیف می‌شوند.
          </td>
          <td><em>استفاده نشده</em></td>
          <td>
            تقویت بر حسب دسیبل که اعمال می‌شود؛ اگر منفی باشد، تضعیف خواهد بود.
          </td>
        </tr>
        <tr>
          <th scope="row"><code>highshelf</code></th>
          <td>
            فیلتر قفسه بالا استاندارد مرتبه دوم. فرکانس‌های بالاتر از فرکانس تقویت یا تضعیف می‌شوند؛ فرکانس‌های پایین‌تر از آن بدون تغییر باقی می‌مانند.
          </td>
          <td>
            حد پایینی فرکانس‌هایی که تقویت یا تضعیف می‌شوند.
          </td>
          <td><em>استفاده نشده</em></td>
          <td>
            تقویت بر حسب دسیبل که اعمال می‌شود؛ اگر منفی باشد، تضعیف خواهد بود.
          </td>
        </tr>
        <tr>
          <th scope="row"><code>peaking</code></th>
          <td>
            فرکانس‌های داخل محدوده تقویت یا تضعیف می‌شوند؛ فرکانس‌های خارج از آن بدون تغییر باقی می‌مانند.
          </td>
          <td>
            وسط محدوده فرکانسی که تقویت یا تضعیف می‌شود.
          </td>
          <td>
            عرض باند فرکانس را کنترل می‌کند. هرچه مقدار <code>Q</code> بزرگ‌تر باشد، باند فرکانس کوچک‌تر است.
          </td>
          <td>
            تقویت بر حسب دسیبل که اعمال می‌شود؛ اگر منفی باشد، تضعیف خواهد بود.
          </td>
        </tr>
        <tr>
          <th scope="row"><code>notch</code></th>
          <td>
            فیلتر استاندارد [نچ (notch)](https://en.wikipedia.org/wiki/Band-stop_filter)، همچنین به‌عنوان فیلتر _باند-ایست_ یا _باند-رد_ نامیده می‌شود. این برعکس فیلتر میان‌گذر است: فرکانس‌های خارج از محدوده داده‌شده عبور می‌کنند؛ فرکانس‌های داخل آن تضعیف می‌شوند.
          </td>
          <td>مرکز محدوده فرکانس‌ها.</td>
          <td>
            عرض باند فرکانس را کنترل می‌کند. هرچه مقدار <code>Q</code> بزرگ‌تر باشد، باند فرکانس کوچک‌تر است.
          </td>
          <td><em>استفاده نشده</em></td>
        </tr>
        <tr>
          <th scope="row"><code>allpass</code></th>
          <td>
            فیلتر استاندارد [تمام‌گذر (allpass)](https://en.wikipedia.org/wiki/All-pass_filter#Digital_Implementation) مرتبه دوم. این فیلتر اجازه عبور همه فرکانس‌ها را می‌دهد، اما رابطه فاز بین فرکانس‌های مختلف را تغییر می‌دهد.
          </td>
          <td>
            فرکانسی با حداکثر [تأخیر گروهی](https://en.wikipedia.org/wiki/Group_delay_and_phase_delay)، یعنی فرکانسی که مرکز انتقال فاز در آن رخ می‌دهد.
          </td>
          <td>
            کنترل می‌کند که انتقال در فرکانس میانی چقدر تیز باشد. هرچه این پارامتر بزرگ‌تر باشد، انتقال تیزتر و بزرگ‌تر خواهد بود.
          </td>
          <td><em>استفاده نشده</em></td>
        </tr>
      </tbody>
    </table>

## روش‌های نمونه

_روش‌های زیر را از والد خود، {{domxref("AudioNode")}} به ارث می‌برد._

- {{domxref("BiquadFilterNode.getFrequencyResponse()")}}
  - : از تنظیمات فعلی پارامترهای فیلتر، این روش پاسخ فرکانسی را برای فرکانس‌های مشخص‌شده در آرایه فرکانس‌های داده‌شده محاسبه می‌کند.

## مثال

برای مثال کدی که نحوه استفاده از `AudioContext` برای ایجاد گره فیلتر Biquad را نشان می‌دهد، به [`AudioContext.createBiquadFilter`](/en-US/docs/Web/API/BaseAudioContext/createBiquadFilter#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)