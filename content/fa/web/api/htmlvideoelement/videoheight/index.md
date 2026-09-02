---
title: "HTMLVideoElement: videoHeight property"
---

---
title: "HTMLVideoElement: videoHeight property"
short-title: videoHeight
slug: Web/API/HTMLVideoElement/videoHeight
page-type: web-api-instance-property
browser-compat: api.HTMLVideoElement.videoHeight
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`videoHeight`** در رابط {{domxref("HTMLVideoElement")}}، [ارتفاع ذاتی](#about_intrinsic_width_and_height) ویدیو را بر حسب پیکسل‌های CSS بیان می‌کند. به زبان ساده، این ارتفاع رسانه در اندازه طبیعی آن است.

## Value

یک مقدار صحیح که ارتفاع ذاتی ویدیو را بر حسب پیکسل‌های CSS مشخص می‌کند. اگر {{domxref("HTMLMediaElement.readyState", "readyState")}} عنصر برابر با `HTMLMediaElement.HAVE_NOTHING` باشد، مقدار این ویژگی ۰ است، زیرا هنوز اطلاعاتی درباره اندازه ویدیو یا فریم پوستر در دسترس نیست.

### About intrinsic width and height

یک {{Glossary("user agent")}} عرض و ارتفاع ذاتی رسانهٔ عنصر را با شروع از عرض و ارتفاع پیکسلی خام رسانه محاسبه می‌کند و سپس عواملی مانند موارد زیر را در نظر می‌گیرد:

- {{glossary("aspect ratio")}} رسانه.
- دیافراگم تمیز (clean aperture) رسانه (زیر-مستطیلی در مرکز رسانه که با نسبت ابعاد هدف مطابقت دارد).
- وضوح (resolution) دستگاه هدف.
- هر عامل دیگری که قالب رسانه ایجاب کند.

اگر عنصر در حال حاضر به جای ویدیوی رندر شده، فریم پوستر را نمایش دهد، اندازه ذاتی فریم پوستر به‌عنوان اندازه عنصر `<video>` در نظر گرفته می‌شود.

اگر در هر زمان اندازه ذاتی رسانه تغییر کند و {{domxref("HTMLMediaElement.readyState", "readyState")}} عنصر برابر با `HAVE_NOTHING` نباشد، یک رویداد {{domxref("HTMLVideoElement.resize_event", "resize")}} به عنصر `<video>` ارسال می‌شود. این اتفاق می‌تواند زمانی رخ دهد که عنصر از نمایش فریم پوستر به نمایش محتوای ویدیویی تغییر وضعیت دهد، یا زمانی که ترک ویدیویی در حال نمایش تغییر کند.

## Examples

این مثال یک کنترل‌کننده برای رویداد {{domxref("HTMLVideoElement.resize_event", "resize")}} ایجاد می‌کند که عنصر {{HTMLElement("video")}} را به‌گونه‌ای تغییر اندازه می‌دهد که با اندازه ذاتی محتوای آن مطابقت داشته باشد.

```js
let v = document.getElementById("myVideo");

v.addEventListener("resize", (ev) => {
  let w = v.videoWidth;
  let h = v.videoHeight;

  if (w && h) {
    v.style.width = w;
    v.style.height = h;
  }
});
```

توجه داشته باشید که این تغییر فقط زمانی اعمال می‌شود که هر دو مقدار `videoWidth` و `videoHeight` غیرصفر باشند. این کار از اعمال تغییرات نامعتبر زمانی که هنوز اطلاعات دقیقی برای ابعاد در دسترس نیست، جلوگیری می‌کند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}