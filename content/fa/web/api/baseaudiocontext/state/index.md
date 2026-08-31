---
title: "BaseAudioContext: state property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/state"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: state property"
short-title: state
slug: Web/API/BaseAudioContext/state
page-type: web-api-instance-property
browser-compat: api.BaseAudioContext.state
---

{{ APIRef("Web Audio API") }}

خاصیت فقط خواندنی `state` از رابط {{ domxref("BaseAudioContext") }}
وضعیت فعلی `AudioContext` را برمی‌گرداند.

## مقدار

یک رشته. مقادیر ممکن عبارتند از:

- `closed`
  - : زمینه صوتی بسته شده است (با متد {{domxref("AudioContext.close()")}}).
- `interrupted`
  - : زمینه صوتی توسط رویدادی خارج از کنترل وب‌اپ قطع شده است.
- `running`
  - : زمینه صوتی به طور عادی در حال اجرا است.
- `suspended`
  - : زمینه صوتی معلق شده است (با متد {{domxref("AudioContext.suspend()")}}).

## توضیحات

خاصیت `state` یک زمینه صوتی برای نمایش وضعیت عملیاتی فعلی آن استفاده می‌شود. این کار معمولاً با پرس‌وجوی `state` در داخل یک مدیر رویداد {{domxref("BaseAudioContext.statechange_event", "statechange")}} انجام می‌شود تا بتوان به تغییرات وضعیت به طور مناسب پاسخ داد.

مقادیر `running` و `closed` بدیهی هستند – آنها نشان می‌دهند که زمینه صوتی یا به طور عادی در حال اجرا است، یا بسته شده است (از طریق متد {{domxref("AudioContext.close()")}}).

حالت‌های `interrupted` و `suspended` هر دو یک وضعیت "مکث" را نشان می‌دهند که بعداً می‌توان از سر گرفته شود، اما از نظر معنایی متفاوت هستند:

- وضعیت `suspended` نشان می‌دهد که زمینه صوتی در پاسخ به یک اقدام کاربر درون وب‌اپ، با اجرای متد {{domxref("AudioContext.suspend()")}} در داخل یک مدیر رویداد `click` (یا مشابه)، مکث شده است. در این حالت، زمینه با اجرای متد {{domxref("AudioContext.resume()")}} از حالت مکث خارج می‌شود.
- وضعیت `interrupted` نشان می‌دهد که زمینه صوتی در پاسخ به یک وقفه خارج از کنترل وب‌اپ مکث شده است. در این حالت، مرورگر تصمیم می‌گیرد که چه زمانی برنامه را مکث و از سر بگیرد. وب‌اپ می‌تواند وضعیت `interrupted` را به طور مناسب مدیریت کند، مثلاً با مکث یک جریان صوتی برای جلوگیری از هدر رفتن منابع در حالی که برنامه استفاده نمی‌شود.

وقفه‌هایی که ممکن است وضعیت `interrupted` را فعال کنند شامل موارد زیر هستند:

- یک برنامه کنفرانس یا تلفن در همان سیستم که نیاز به دسترسی انحصاری به سخت‌افزار صوتی دستگاه دارد.
- کاربر لپ‌تاپ خود را می‌بندد.
- ویژگی‌های API که برای شروع یا پاسخ به وقفه‌های صوتی طراحی شده‌اند.

> [!NOTE]
> نحوه فعال شدن وضعیت `interrupted` ممکن است بین مرورگرها متفاوت باشد.

همچنین به امکان انتقال بین حالت‌های `interrupted` و `suspended` توجه کنید:

- اگر `suspend()` روی یک زمینه صوتی در طول یک وقفه فراخوانی شود (`state` برابر `interrupted` است)، وضعیت بلافاصله به `suspended` تغییر می‌کند.
- اگر `resume()` روی یک زمینه صوتی `suspended` در طول یک وقفه فراخوانی شود، وضعیت بلافاصله به `interrupted` تغییر می‌کند.
- اگر یک وقفه در حالی که زمینه صوتی `suspended` است رخ دهد، زمینه به `interrupted` تغییر نخواهد کرد. این تغییر اتفاق نخواهد افتاد مگر اینکه `resume()` روی زمینه فراخوانی شود (همانطور که در نکته قبلی اشاره شد). این انتخاب برای جلوگیری از افشای اطلاعات بیش از حد دستگاه به صفحات وب انجام شد – برای مثال، ثبت هر بار بسته شدن لپ‌تاپ می‌تواند یک مسئله حریم خصوصی باشد.

## مثال‌ها

### مدیریت تغییرات وضعیت

برش کد زیر از [نمونه وضعیت‌های AudioContext](https://github.com/mdn/webaudio-examples) گرفته شده است ([مشاهده اجرای زنده](https://mdn.github.io/webaudio-examples/audiocontext-states/)). مدیر {{domxref("BaseAudioContext.statechange_event", "onstatechange")}} برای ثبت وضعیت فعلی در کنسول هر بار که تغییر می‌کند استفاده می‌شود.

```js
audioCtx.onstatechange = () => {
  console.log(audioCtx.state);
};
```

### از سرگیری وضعیت‌های پخش قطع شده در iOS Safari

در iOS Safari، هنگامی که کاربر صفحه را ترک می‌کند (مثلاً برگه‌ها را تغییر می‌دهد، مرورگر را کوچک می‌کند یا صفحه را خاموش می‌کند)، وضعیت زمینه صوتی به "interrupted" تغییر می‌کند و نیاز به از سرگیری دارد. برای مثال:

```js
function play() {
  if (audioCtx.state === "interrupted") {
    audioCtx.resume().then(() => play());
    return;
  }
  // rest of the play() function
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)