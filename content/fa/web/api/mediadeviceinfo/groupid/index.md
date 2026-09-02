---
title: "MediaDeviceInfo: groupId property"
short-title: groupId
slug: Web/API/MediaDeviceInfo/groupId
page-type: web-api-instance-property
browser-compat: api.MediaDeviceInfo.groupId
---

{{APIRef("Media Capture and Streams")}}{{securecontext_header}}

ویژگی فقطخواندنی **`groupId`** در رابط {{domxref("MediaDeviceInfo")}} یک رشته برمی‌گرداند که شناسهٔ گروه است.

اگر دو دستگاه به یک دستگاه فیزیکی واحد تعلق داشته باشند، شناسهٔ گروه یکسانی دارند؛ برای مثال، یک مانیتور که هم دوربین داخلی دارد و هم میکروفون داخلی.

## مقدار

رشته‌ای که گروه دستگاه‌های مرتبطی را که این دستگاه به آن تعلق دارد، به‌صورت یکتا شناسایی می‌کند.

## مثال‌ها

در این مثال، فهرستی از دستگاه‌هایی می‌سازیم که در همان گروهِ یک دستگاه مشخص قرار دارند. این کار ممکن است برای تولید رابط کاربری استفاده شود که دستگاه‌های مرتبط را برای نمایش در کنار هم جمع می‌کند، یا به کاربر امکان می‌دهد به‌سادگی دوربین و میکروفون داخلیِ همان نمایشگر را هم‌زمان انتخاب کند.

```js
const getDeviceGroup = (mainDevInfo) => {
  let devList = [];

  navigator.mediaDevices.enumerateDevices().then((devices) => {
    devices.forEach((device) => {
      if (device.groupId === mainDevInfo.groupId) {
        devList.push(device);
      }
    });
  });

  return devList;
};
```

تابع `getDeviceGroup()` یک شیء `MediaDeviceInfo` را به‌عنوان ورودی می‌گیرد که دستگاهی را توصیف می‌کند که باید فهرست گروهش ساخته شود. این تابع ابتدا آرایهٔ نتیجه، `devList`، را با یک آرایهٔ خالی مقداردهی می‌کند.

سپس برای دریافت فهرست همهٔ دستگاه‌های رسانه‌ای، متد {{domxref("MediaDevices.enumerateDevices", "navigator.mediaDevices.enumerateDevices()")}} فراخوانی می‌شود. وقتی پرامیسی که این متد برمی‌گرداند برآورده شد (resolve)، فهرست را با استفاده از {{jsxref("Array.forEach", "forEach()")}} پیمایش می‌کنیم. برای هر دستگاه، اگر `groupId` آن با `groupId` دستگاه اصلی یکی باشد، شیء {{domxref("MediaDeviceInfo")}} را به فهرست اضافه می‌کنیم.

در پایان، فهرست که اکنون برای هر دستگاهِ همان گروه یک شیء `MediaDeviceInfo` دارد، به فراخواننده بازگردانده می‌شود.

به‌سادگی می‌توان این تابع را تغییر داد تا دستگاهِ داده‌شده را از فهرست برگشتی حذف کند یا آن را در بالای فهرست قرار دهد؛ این کار با مقایسهٔ مقادیر {{domxref("MediaDeviceInfo.deviceId", "deviceId")}} دو شیء انجام می‌شود و فقط وقتی دستگاه به فهرست نتیجه اضافه می‌شود که این مقدار یکسان نباشد.

این نسخه از مثال، دستگاهِ داده‌شده را در بالای فهرست نتیجه قرار می‌دهد و سپس هر عضو دیگری از گروه را که پیدا شود به آن اضافه می‌کند:

```js
const getDeviceGroup = (mainDevInfo) => {
  let devList = [mainDevInfo];

  navigator.mediaDevices.enumerateDevices().then((devices) => {
    devices.forEach((device) => {
      if (
        device.groupId === mainDevInfo.groupId &&
        device.deviceId !== mainDevInfo.deviceId
      ) {
        devList.push(device);
      }
    });
  });

  return devList;
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}