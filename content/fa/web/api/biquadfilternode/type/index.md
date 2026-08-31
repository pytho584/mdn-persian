---
title: "BiquadFilterNode: type property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode/type"
translated_by: "n8n + AI"
---

---
title: "BiquadFilterNode: type property"
short-title: type
slug: Web/API/BiquadFilterNode/type
page-type: web-api-instance-property
browser-compat: api.BiquadFilterNode.type
---

{{ APIRef("Web Audio API") }}

ویژگی `type` در رابط {{ domxref("BiquadFilterNode") }} یک رشته (enum) است که نوع الگوریتم فیلتر مورد استفاده توسط گره را تعریف می‌کند.

## مقدار

یک رشته (enum) که نمایانگر [BiquadFilterType](https://webaudio.github.io/web-audio-api/#idl-def-BiquadFilterType) است.

## مقادیر `type` و معنای آن‌ها

<table class="standard-table">
  <tbody>
    <tr>
      <th scope="row"><code>type</code></th>
      <th scope="col">توضیحات</th>
      <th scope="col"><code>frequency</code></th>
      <th scope="col"><code>Q</code></th>
      <th scope="col"><code>gain</code></th>
    </tr>
    <tr>
      <th scope="row"><code>lowpass</code></th>
      <td>
        فیلتر پایین‌گذر تشدیدی استاندارد مرتبه دوم با شیب 12 دسی‌بل بر اکتاو.
        فرکانس‌های پایین‌تر از فرکانس قطع عبور می‌کنند؛ فرکانس‌های بالاتر از آن تضعیف می‌شوند.
      </td>
      <td>فرکانس قطع.</td>
      <td>
        نشان‌دهنده میزان قله‌دار بودن فرکانس در اطراف فرکانس قطع است. هرچه مقدار بزرگ‌تر باشد، قله بزرگ‌تر است.
      </td>
      <td><em>استفاده نشده</em></td>
    </tr>
    <tr>
      <th scope="row"><code>highpass</code></th>
      <td>
        فیلتر بالاگذر تشدیدی استاندارد مرتبه دوم با شیب 12 دسی‌بل بر اکتاو.
        فرکانس‌های پایین‌تر از فرکانس قطع تضعیف می‌شوند؛ فرکانس‌های بالاتر از آن عبور می‌کنند.
      </td>
      <td>فرکانس قطع.</td>
      <td>
        نشان‌دهنده میزان قله‌دار بودن فرکانس در اطراف فرکانس قطع است. هرچه مقدار بزرگ‌تر باشد، قله بزرگ‌تر است.
      </td>
      <td><em>استفاده نشده</em></td>
    </tr>
    <tr>
      <th scope="row"><code>bandpass</code></th>
      <td>
        فیلتر میان‌گذر استاندارد مرتبه دوم. فرکانس‌های خارج از محدوده معین تضعیف می‌شوند؛ فرکانس‌های داخل آن عبور می‌کنند.
      </td>
      <td>مرکز محدوده فرکانس‌ها.</td>
      <td>
        عرض باند فرکانسی را کنترل می‌کند. هرچه مقدار <code>Q</code> بزرگ‌تر باشد، باند فرکانسی بزرگ‌تر است.
      </td>
      <td><em>استفاده نشده</em></td>
    </tr>
    <tr>
      <th scope="row"><code>lowshelf</code></th>
      <td>
        فیلتر قفسه پایین استاندارد مرتبه دوم. فرکانس‌های پایین‌تر از فرکانس موردنظر تقویت یا تضعیف می‌شوند؛ فرکانس‌های بالاتر از آن بدون تغییر می‌مانند.
      </td>
      <td>
        حد بالای فرکانس‌هایی که تقویت یا تضعیف می‌شوند.
      </td>
      <td><em>استفاده نشده</em></td>
      <td>
        میزان تقویت بر حسب دسی‌بل؛ اگر منفی باشد، به‌صورت تضعیف اعمال می‌شود.
      </td>
    </tr>
    <tr>
      <th scope="row"><code>highshelf</code></th>
      <td>
        فیلتر قفسه بالا استاندارد مرتبه دوم. فرکانس‌های بالاتر از فرکانس موردنظر تقویت یا تضعیف می‌شوند؛ فرکانس‌های پایین‌تر از آن بدون تغییر می‌مانند.
      </td>
      <td>
        حد پایین فرکانس‌هایی که تقویت یا تضعیف می‌شوند.
      </td>
      <td><em>استفاده نشده</em></td>
      <td>
        میزان تقویت بر حسب دسی‌بل؛ اگر منفی باشد، به‌صورت تضعیف اعمال می‌شود.
      </td>
    </tr>
    <tr>
      <th scope="row"><code>peaking</code></th>
      <td>
        فرکانس‌های داخل محدوده تقویت یا تضعیف می‌شوند؛ فرکانس‌های خارج از آن بدون تغییر می‌مانند.
      </td>
      <td>
        وسط محدوده فرکانسی که تقویت یا تضعیف می‌شود.
      </td>
      <td>
        عرض باند فرکانسی را کنترل می‌کند. هرچه مقدار <code>Q</code> بزرگ‌تر باشد، باند فرکانسی بزرگ‌تر است.
      </td>
      <td>
        میزان تقویت بر حسب دسی‌بل؛ اگر منفی باشد، به‌صورت تضعیف اعمال می‌شود.
      </td>
    </tr>
    <tr>
      <th scope="row"><code>notch</code></th>
      <td>
        فیلتر
        <a href="https://en.wikipedia.org/wiki/Band-stop_filter">نچ</a>
        استاندارد، همچنین به نام فیلتر <em>باند-ایست</em> یا
        <em>باند-رد</em> شناخته می‌شود. این فیلتر برعکس فیلتر میان‌گذر عمل می‌کند:
        فرکانس‌های خارج از محدوده معین عبور می‌کنند؛ فرکانس‌های داخل آن تضعیف می‌شوند.
      </td>
      <td>مرکز محدوده فرکانس‌ها.</td>
      <td>
        عرض باند فرکانسی را کنترل می‌کند. هرچه مقدار <code>Q</code> بزرگ‌تر باشد، باند فرکانسی بزرگ‌تر است.
      </td>
      <td><em>استفاده نشده</em></td>
    </tr>
    <tr>
      <th scope="row"><code>allpass</code></th>
      <td>
        فیلتر
        <a
          href="https://en.wikipedia.org/wiki/All-pass_filter#Digital_Implementation"
          >تمام‌گذر</a
        >
        استاندارد مرتبه دوم. این فیلتر همه فرکانس‌ها را عبور می‌دهد، اما
        رابطه فاز بین فرکانس‌های مختلف را تغییر می‌دهد.
      </td>
      <td>
        فرکانس با حداکثر
        <a href="https://en.wikipedia.org/wiki/Group_delay_and_phase_delay"
          >تأخیر گروهی</a
        >، یعنی فرکانسی که مرکز انتقال فاز در آن رخ می‌دهد.
      </td>
      <td>
        میزان تیزی انتقال در فرکانس میانی را کنترل می‌کند. هرچه این پارامتر بزرگ‌تر باشد، انتقال تیزتر و بزرگ‌تر خواهد بود.
      </td>
      <td><em>استفاده نشده</em></td>
    </tr>
  </tbody>
</table>

## مثال‌ها

مثال زیر کاربرد پایه‌ای AudioContext را برای ایجاد یک گره فیلتر Biquad نشان می‌دهد.
برای مثال‌ها/اطلاعات کاربردی کامل‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (برای کد مرتبط به [app.js خطوط ۱۰۸–۱۹۳](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) مراجعه کنید).

```js
const audioCtx = new AudioContext();

// Set up the different audio nodes we will use for the app
const analyser = audioCtx.createAnalyser();
const distortion = audioCtx.createWaveShaper();
const gainNode = audioCtx.createGain();
const biquadFilter = audioCtx.createBiquadFilter();
const convolver = audioCtx.createConvolver();

// Connect the nodes together

source = audioCtx.createMediaStreamSource(stream);
source.connect(analyser);
analyser.connect(distortion);
distortion.connect(biquadFilter);
biquadFilter.connect(convolver);
convolver.connect(gainNode);
gainNode.connect(audioCtx.destination);

// Manipulate the Biquad filter

biquadFilter.type = "lowshelf";
biquadFilter.frequency.value = 1000;
biquadFilter.gain.value = 25;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)