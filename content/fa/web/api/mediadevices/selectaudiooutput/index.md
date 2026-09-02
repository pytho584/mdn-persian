---
title: "MediaDevices: selectAudioOutput() method"
short-title: selectAudioOutput()
slug: Web/API/MediaDevices/selectAudioOutput
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.MediaDevices.selectAudioOutput
---

{{APIRef("Audio Output Devices API")}}{{securecontext_header}}{{SeeCompatTable}}

متد **`selectAudioOutput()`** از رابط {{domxref("MediaDevices")}} کاربر را به انتخاب یک دستگاه خروجی صدا (مانند بلندگو یا هدفون) ترغیب می‌کند. اگر کاربر دستگاهی را انتخاب کند، این متد مجوز استفاده از آن دستگاه را به عنوان خروجی صدا اعطا می‌کند.

پس از انتخاب، اگر دستگاه در دسترس باشد، می‌توان با استفاده از {{domxref("MediaDevices.enumerateDevices()")}} آن را فهرست کرد و با استفاده از {{domxref("HTMLMediaElement.setSinkId()")}} به عنوان خروجی صدا تنظیم کرد.

در صورت موفقیت، {{jsxref("Promise")}} بازگشتی با یک {{domxref("MediaDeviceInfo")}} که دستگاه انتخاب‌شده را توصیف می‌کند، حل می‌شود.

## نحو

```js-nolint
selectAudioOutput()
selectAudioOutput(options)
```

### پارامترها

- `options` {{Optional_Inline}}
  - : یک شیء که پیکربندی می‌کند چه دستگاه‌هایی ممکن است در اعلان کاربر ارائه شوند.
    - `deviceId` {{Optional_Inline}}
      - : یک رشته که شناسه یک دستگاه قبلاً نمایش داده‌شده/مجاز را نشان می‌دهد.
        اگر تنظیم نشود، اعلانی با تمام دستگاه‌های خروجی صدا در دسترس نمایش داده خواهد شد.

        این گزینه برای برنامه‌هایی در نظر گرفته شده است که می‌خواهند یک شناسه دستگاه را ذخیره کنند تا همان دستگاه در جلسات آینده به‌طور پیش‌فرض استفاده شود.
        توجه داشته باشید که این متد ممکن است یک شناسه جدید برای همان دستگاه بازگرداند، و شناسه‌های ذخیره‌شده _باید_ با موفقیت از طریق `selectAudioOutput()` عبور کنند تا با {{domxref("HTMLMediaElement.setSinkId","setSinkId()")}} کار کنند.

        > [!NOTE]
        > یک عامل کاربر ممکن است انتخاب کند که در صورت مشخص شدن یک شناسه غیر null که قبلاً در یک جلسه قبلی توسط `selectAudioOutput()` به کاربر نمایش داده شده است، از اعلان به کاربر صرف‌نظر کند.
        > در این حالت، عامل کاربر ممکن است به سادگی با این شناسه دستگاه، یا یک شناسه جدید برای همان دستگاه در صورت تغییر، حل شود.
        > اگر مجوز دستگاه مشخص‌شده قبلاً اعطا شده اما بعداً لغو شده باشد، عامل کاربر ممکن است تمام دستگاه‌های مجاز را نمایش دهد و دستگاهی را که با شناسه مشخص‌شده مطابقت دارد برجسته کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء {{domxref("MediaDeviceInfo")}} که دستگاه خروجی صدا انتخاب‌شده توسط کاربر را توصیف می‌کند، برآورده می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورت استفاده از [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) [سیاست مجوز](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) برای مسدود کردن استفاده از خروجی‌های صدا (علاوه بر این، پنجره بازشو برای انتخاب خروجی صدا نمایش داده نمی‌شود) یا کاربر بدون انتخاب دستگاه، پنجره انتخاب را بسته است، بازگردانده می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : در صورت عدم وجود دستگاه‌های خروجی صدا در دسترس، بازگردانده می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورت عدم وجود {{Glossary("transient activation")}} (باید آن را از نوعی رویداد UI فعال کنید)، بازگردانده می‌شود.

## الزامات امنیتی

دسترسی به API مشروط به محدودیت‌های زیر است:

- متد باید در یک [زمینه امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) فراخوانی شود.
- [فعال‌سازی موقت کاربر](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است.
  کاربر باید با صفحه یا یک عنصر UI تعامل داشته باشد تا این ویژگی کار کند.
- دسترسی ممکن است توسط [سیاست مجوز](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) HTTP [`speaker-selection`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/speaker-selection) محدود شود.

وضعیت مجوز را می‌توان با استفاده از متد {{domxref("Permissions.query", "navigator.permissions.query()")}} از [API مجوزها](/en-US/docs/Web/API/Permissions_API) پرس‌وجو کرد، و یک توصیف‌گر مجوز با مجوز `speaker-selection` عبور داد.

## مثال‌ها

در اینجا یک مثال از استفاده از `selectAudioOutput()`، در داخل یک تابع که با کلیک دکمه فعال می‌شود، آورده شده است.
این تابع {{domxref("MediaDeviceInfo.deviceId", "شناسه‌های دستگاه", "", "nocode")}} و برچسب‌های انتخاب‌شده (در صورت وجود) یا یک پیام خطا را خروجی می‌دهد.

```js
document.querySelector("#myButton").addEventListener("click", () => {
  if (!navigator.mediaDevices.selectAudioOutput) {
    console.log("selectAudioOutput() not supported.");
    return;
  }

  // نمایش اعلان و ثبت دستگاه انتخاب‌شده یا خطا
  navigator.mediaDevices
    .selectAudioOutput()
    .then((device) => {
      console.log(`${device.kind}: ${device.label} id = ${device.deviceId}`);
    })
    .catch((err) => {
      console.error(`${err.name}: ${err.message}`);
    });
});
```

پس از انتخاب یک خروجی، این ممکن است تولید کند:

```bash
audiooutput: Realtek Digital Output (Realtek(R) Audio) id = 0wE6fURSZ20H0N2NbxqgowQJLWbwo+5ablCVVJwRM3k=
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement.setSinkId()")}}
- {{domxref("HTMLMediaElement.sinkId")}}
- [WebRTC](/en-US/docs/Web/API/WebRTC_API) - صفحه مقدماتی API