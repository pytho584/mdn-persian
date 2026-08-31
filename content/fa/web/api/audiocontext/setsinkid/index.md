---
title: "AudioContext: setSinkId() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/setSinkId"
translated_by: "n8n + AI"
---

---
title: "AudioContext: setSinkId() method"
short-title: setSinkId()
slug: Web/API/AudioContext/setSinkId
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.AudioContext.setSinkId
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`setSinkId()`** در رابط {{domxref("AudioContext")}} دستگاه خروجی صوتی را برای `AudioContext` تنظیم می‌کند. اگر شناسه خروجی (sink ID) به‌صورت صریح تنظیم نشود، از دستگاه خروجی صدای پیش‌فرض سیستم استفاده خواهد شد.

برای تنظیم دستگاه صوتی به دستگاهی غیر از دستگاه پیش‌فرض، توسعه‌دهنده به مجوز دسترسی به دستگاه‌های صوتی نیاز دارد. در صورت نیاز، می‌توان با یک فراخوانی {{domxref("MediaDevices.getUserMedia()")}} از کاربر خواست تا مجوز لازم را صادر کند.

علاوه بر این، این ویژگی ممکن است توسط یک [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شود.

## نحوهٔ استفاده

```js-nolint
setSinkId(sinkId)
```

### پارامترها

- `sinkId`
  - : شناسه خروجی دستگاهی است که می‌خواهید به‌عنوان دستگاه خروجی صوتی تنظیم کنید. این می‌تواند یکی از انواع مقدار زیر باشد:
    - String
      - : رشته‌ای که شناسه خروجی را نشان می‌دهد، مثلاً از طریق ویژگی `deviceId` اشیاء {{domxref("MediaDeviceInfo")}} که توسط {{domxref("MediaDevices.enumerateDevices()")}} بازگردانده می‌شوند، به دست می‌آید.
    - `AudioSinkOptions`
      - : شیءای که گزینه‌های مختلفی را برای یک شناسه خروجی نشان می‌دهد. در حال حاضر این یک ویژگی واحد به نام `type` با مقدار `none` را می‌پذیرد. تنظیم این پارامتر باعث می‌شود صدا بدون پخش شدن از هیچ دستگاه خروجی صوتی پردازش شود. این گزینه برای کاهش مصرف انرژی زمانی که به پخش هم‌زمان با پردازش نیاز ندارید، مفید است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با مقدار `undefined` تکمیل می‌شود.

تلاش برای تنظیم شناسه خروجی به مقدار فعلی آن (یعنی مقداری که توسط {{domxref("AudioContext.sinkId")}} بازگردانده شده است)، هیچ خطایی ایجاد نمی‌کند، اما فرآیند را بلافاصله متوقف می‌کند.

### استثناها

- `InvalidAccessError` {{domxref("DOMException")}}
  - : اگر دسترسی به دستگاه خروجی صوتی انتخاب‌شده ناموفق باشد پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر مرورگر مجوز دسترسی به دستگاه‌های صوتی را نداشته باشد پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر `sinkId` ارسال‌شده با هیچ دستگاه صوتی موجود در سیستم مطابقت نداشته باشد پرتاب می‌شود.

## مثال‌ها

در [SetSinkId test example](https://mdn.github.io/dom-examples/audiocontext-setsinkid/) (به [source code](https://github.com/mdn/dom-examples/tree/main/audiocontext-setsinkid) مراجعه کنید)، یک گراف صوتی ایجاد می‌کنیم که یک انفجار سه‌ثانیه‌ای نویز سفید را از طریق یک {{domxref("AudioBufferSourceNode")}} تولید می‌کند؛ همچنین آن را از یک {{domxref("GainNode")}} عبور می‌دهیم تا صدا کمی ملایم‌تر شود.

```js
mediaDeviceBtn.addEventListener("click", async () => {
  if ("setSinkId" in AudioContext.prototype) {
    selectDiv.textContent = "";

    const stream = await navigator.mediaDevices.getUserMedia({
      audio: true,
    });
    const devices = await navigator.mediaDevices.enumerateDevices();

    // Most of the DOM scripting to generate the dropdown cut out for brevity

    const audioOutputs = devices.filter(
      (device) =>
        device.kind === "audiooutput" && device.deviceId !== "default",
    );

    audioOutputs.forEach((device) => {
      const option = document.createElement("option");
      option.value = device.deviceId;
      option.textContent = device.label;
      select.appendChild(option);
    });

    const option = document.createElement("option");
    option.value = "none";
    option.textContent = "None";
    select.appendChild(option);

    select.addEventListener("change", async () => {
      if (select.value === "none") {
        await audioCtx.setSinkId({ type: "none" });
      } else {
        await audioCtx.setSinkId(select.value);
      }
    });
  }
});
```

ما همچنین یک منوی کشویی در اختیار کاربر قرار می‌دهیم تا بتواند دستگاه خروجی صوتی را در لحظه تغییر دهد. برای انجام این کار:

1. دکمه‌ای برای پر کردن منوی کشویی فراهم می‌کنیم. ابتدا {{domxref("MediaDevices.getUserMedia()")}} را فراخوانی می‌کنیم تا درخواست مجوز مورد نیاز برای اجازه دادن به شمارش دستگاه‌ها را فعال کنیم، سپس از {{domxref("MediaDevices.enumerateDevices()")}} برای دریافت همه دستگاه‌های موجود استفاده می‌کنیم. روی دستگاه‌های مختلف حلقه می‌زنیم و هر کدام را به‌عنوان یک گزینه در یک عنصر {{htmlelement("select")}} در دسترس قرار می‌دهیم. همچنین یک گزینه `"None"` برای حالتی ایجاد می‌کنیم که نمی‌خواهید صدای خود را در هیچ خروجی پخش کنید.
2. یک شنونده رویداد {{domxref("HTMLElement/change_event", "change")}} به عنصر {{htmlelement("select")}} اضافه می‌کنیم تا وقتی مقدار جدیدی انتخاب می‌شود، شناسه خروجی و بنابراین دستگاه خروجی صوتی تغییر کند. اگر `"None"` در منوی کشویی انتخاب شود، `setSinkId()` را با پارامتر شیء `{ type : 'none' }` فراخوانی می‌کنیم تا هیچ دستگاه صوتی انتخاب نشود؛ در غیر این صورت، آن را با شناسه دستگاه صوتی موجود در ویژگی `value` عنصر `<select>` به‌عنوان پارامتر اجرا می‌کنیم.

دستگاه خروجی را می‌توان در حین پخش صدا، همچنین قبل از پخش یا بین پخش‌ها تغییر داد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Change the destination output device in Web Audio](https://developer.chrome.com/blog/audiocontext-setsinkid/)
- {{domxref("AudioContext.sinkId")}}
- {{domxref("AudioContext/sinkchange_event", "sinkchange")}}