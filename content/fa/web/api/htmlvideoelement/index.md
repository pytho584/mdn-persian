---
title: HTMLVideoElement
slug: Web/API/HTMLVideoElement
page-type: web-api-interface
browser-compat: api.HTMLVideoElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLVideoElement`** توسط عنصر {{HTMLElement("video")}} پیاده‌سازی می‌شود و ویژگی‌ها و روش‌های خاصی برای کار با اشیاء ویدئویی فراهم می‌کند. این رابط همچنین ویژگی‌ها و روش‌های {{domxref("HTMLMediaElement")}} و {{domxref("HTMLElement")}} را به ارث می‌برد.

فهرست [فرمت‌های رسانه‌ای پشتیبانی‌شده](/en-US/docs/Web/Media/Guides/Formats) از مرورگری به مرورگر دیگر متفاوت است. شما باید ویدئوی خود را یا در قالبی واحد که همه مرورگرهای مرتبط از آن پشتیبانی می‌کنند ارائه دهید، یا چندین منبع ویدئویی با فرمت‌های مختلف به اندازه کافی فراهم کنید تا همه مرورگرهایی که باید پشتیبانی کنید پوشش داده شوند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از رابط والد خود، {{domxref("HTMLMediaElement")}} و {{domxref("HTMLElement")}} به ارث می‌برد._

- {{DOMxRef("HTMLVideoElement.disablePictureInPicture")}}
  - : نشان می‌دهد که آیا عامل کاربر باید حالت تصویر در تصویر را به کاربران پیشنهاد دهد یا خیر.
- {{domxref("HTMLVideoElement.height")}}
  - : یک رشته که ویژگی HTML [`height`](/en-US/docs/Web/HTML/Reference/Elements/video#height) را منعکس می‌کند و ارتفاع ناحیه نمایش را بر حسب پیکسل‌های CSS مشخص می‌کند.
- {{domxref("HTMLVideoElement.poster")}}
  - : یک رشته که ویژگی HTML [`poster`](/en-US/docs/Web/HTML/Reference/Elements/video#poster) را منعکس می‌کند و تصویری را مشخص می‌کند که تا زمانی که داده ویدئویی در دسترس نباشد نمایش داده شود.
- {{domxref("HTMLVideoElement.videoHeight")}} {{ReadOnlyInline}}
  - : یک مقدار عدد صحیح بدون علامت (unsigned integer) برمی‌گرداند که ارتفاع ذاتی منبع را بر حسب پیکسل‌های CSS نشان می‌دهد، یا اگر هنوز رسانه‌ای در دسترس نباشد ۰ را برمی‌گرداند.
- {{domxref("HTMLVideoElement.videoWidth")}} {{ReadOnlyInline}}
  - : یک مقدار عدد صحیح بدون علامت (unsigned integer) برمی‌گرداند که عرض ذاتی منبع را بر حسب پیکسل‌های CSS نشان می‌دهد، یا اگر هنوز رسانه‌ای در دسترس نباشد ۰ را برمی‌گرداند.
- {{domxref("HTMLVideoElement.width")}}
  - : یک رشته که ویژگی HTML [`width`](/en-US/docs/Web/HTML/Reference/Elements/video#width) را منعکس می‌کند و عرض ناحیه نمایش را بر حسب پیکسل‌های CSS مشخص می‌کند.

### ویژگی‌های مختص فایرفاکس

- {{domxref("HTMLVideoElement.mozParsedFrames")}} {{Non-standard_Inline}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : یک `unsigned long` با تعداد فریم‌های ویدئویی که از منبع رسانه تجزیه شده‌اند برمی‌گرداند.
- {{domxref("HTMLVideoElement.mozDecodedFrames")}} {{Non-standard_Inline}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : یک `unsigned long` با تعداد فریم‌های ویدئویی تجزیه‌شده که به تصویر رمزگشایی شده‌اند برمی‌گرداند.
- {{domxref("HTMLVideoElement.mozPresentedFrames")}} {{Non-standard_Inline}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : یک `unsigned long` با تعداد فریم‌های رمزگشایی‌شده که به خط لوله رندر برای نقاشی ارائه شده‌اند برمی‌گرداند.
- {{domxref("HTMLVideoElement.mozPaintedFrames")}} {{Non-standard_Inline}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : یک `unsigned long` با تعداد فریم‌های ارائه‌شده که روی صفحه نقاشی شده‌اند برمی‌گرداند.
- {{domxref("HTMLVideoElement.mozFrameDelay")}} {{Non-standard_Inline}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : یک `double` با مدت زمانی (بر حسب ثانیه) که آخرین فریم ویدئوی نقاشی‌شده با تأخیر بوده است برمی‌گرداند.
- {{domxref("HTMLVideoElement.mozHasAudio")}} {{Non-standard_Inline}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : یک مقدار بولی (boolean) برمی‌گرداند که نشان می‌دهد آیا صدایی با ویدئو مرتبط است یا خیر.

## روش‌های نمونه

_روش‌ها را از رابط والد خود، {{domxref("HTMLMediaElement")}} و {{domxref("HTMLElement")}} به ارث می‌برد._

- {{DOMxRef("HTMLVideoElement.cancelVideoFrameCallback()")}}
  - : یک فراخوان فریم ویدئویی که قبلاً ثبت شده است را لغو می‌کند (به {{DOMxRef("HTMLVideoElement.requestVideoFrameCallback", "requestVideoFrameCallback()")}} مراجعه کنید).
- {{domxref("HTMLVideoElement.getVideoPlaybackQuality()")}}
  - : یک شی {{domxref("VideoPlaybackQuality")}} برمی‌گرداند که معیارهای پخش جاری را شامل می‌شود. این اطلاعات شامل مواردی مانند تعداد فریم‌های افتاده یا خراب و همچنین تعداد کل فریم‌ها است.
- {{DOMxRef("HTMLVideoElement.requestPictureInPicture()")}}
  - : درخواست می‌کند که عامل کاربر ویدئو را وارد حالت تصویر در تصویر کند.
- {{DOMxRef("HTMLVideoElement.requestVideoFrameCallback()")}}
  - : یک تابع فراخوان ثبت می‌کند که وقتی یک فریم ویدئویی جدید به ترکیب‌کننده (compositor) ارسال می‌شود اجرا می‌شود. این به توسعه‌دهندگان امکان می‌دهد تا عملیات کارآمدی را روی هر فریم ویدئو انجام دهند.

## رویدادها

_رویدادها را از رابط والد خود، {{domxref("HTMLMediaElement")}} و {{domxref("HTMLElement")}} به ارث می‌برد._

با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با انتساب یک شنونده رویداد به ویژگی `oneventname` این رابط به این رویدادها گوش دهید.

- {{DOMxRef("HTMLVideoElement.enterpictureinpicture_event", "enterpictureinpicture")}}
  - : زمانی فعال می‌شود که `HTMLVideoElement` با موفقیت وارد حالت تصویر در تصویر شود.
- {{DOMxRef("HTMLVideoElement.leavepictureinpicture_event", "leavepictureinpicture")}}
  - : زمانی فعال می‌شود که `HTMLVideoElement` با موفقیت از حالت تصویر در تصویر خارج شود.
- {{DOMxRef("HTMLVideoElement.resize_event", "resize")}}
  - : زمانی فعال می‌شود که یک یا هر دو ویژگی {{domxref("HTMLVideoElement.videoWidth", "videoWidth")}} و {{domxref("HTMLVideoElement.videoHeight", "videoHeight")}} به‌روزرسانی شده‌اند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML پیاده‌ساز این رابط: {{HTMLElement("video")}}.
- [فرمت‌های رسانه‌ای پشتیبانی‌شده](/en-US/docs/Web/Media/Guides/Formats)