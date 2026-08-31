---
title: CropTarget
slug: Web/API/CropTarget
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CropTarget
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}

**`CropTarget`** از رابط‌های {{domxref("Screen Capture API", "Screen Capture API", "", "nocode")}} یک متد ایستا به نام {{domxref("CropTarget.fromElement_static", "fromElement()")}} ارائه می‌دهد که یک نمونه از `CropTarget` برمی‌گرداند. از این نمونه می‌توان برای برش دادن یک ویدئوی ضبط‌شده به ناحیه‌ای که یک عنصر مشخص در آن رندر می‌شود استفاده کرد.

{{InheritanceDiagram}}

## متدهای ایستا

- {{domxref("CropTarget.fromElement_static", "fromElement()")}} {{Experimental_Inline}}
  - : یک نمونه `CropTarget` برمی‌گرداند که می‌توان از آن برای برش دادن یک ویدئوی ضبط‌شده به ناحیه‌ای که یک عنصر مشخص در آن رندر می‌شود استفاده کرد.

## مثال‌ها

```js
// گزینه‌های مربوط به getDisplayMedia()
const displayMediaOptions = {
  preferCurrentTab: true,
};

// ایجاد target برش از روی عنصر DOM
const demoElem = document.querySelector("#demo");
const cropTarget = await CropTarget.fromElement(demoElem);

// دریافت جریان ویدئو از وب‌کم کاربر و جدا کردن track ویدئو
const stream =
  await navigator.mediaDevices.getDisplayMedia(displayMediaOptions);
const [track] = stream.getVideoTracks();

// برش دادن track ویدئو
await track.cropTo(cropTarget);

// پخش جریان برش‌خورده در عنصر <video>
videoElem.srcObject = stream;
```

برای مشاهده کد مثال در بافت واقعی، به [استفاده از APIهای Element Capture و Region Capture](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [استفاده از APIهای Element Capture و Region Capture](/en-US/docs/Web/API/Screen_Capture_API/Element_Region_Capture)