---
title: "Element: DOMMouseScroll event"
short-title: DOMMouseScroll
slug: Web/API/Element/DOMMouseScroll_event
page-type: web-api-event
status:
  - deprecated
  - non-standard
browser-compat: api.Element.DOMMouseScroll_event
---

{{APIRef}}{{Deprecated_Header}}{{Non-standard_header}}

رویداد `DOMMouseScroll` در DOM به‌صورت ناهمگام (asynchronous) زمانی پرتاب می‌شود که چرخ ماوس یا وسیله‌ای مشابه عمل کند و میزان انباشته‌شدهٔ پیمایش از آخرین رویداد، بیش از ۱ خط یا ۱ صفحه باشد. این رویداد توسط رابط {{ domxref("MouseScrollEvent") }} نمایش داده می‌شود. این رویداد فقط توسط فایرفاکس پیاده‌سازی شده بود. به‌جای آن باید از رویداد استاندارد {{domxref("Element.wheel_event", "wheel")}} استفاده کنید.

اگر می‌خواهید از اقدام پیش‌فرض رویدادهای چرخ ماوس جلوگیری کنید، در Gecko کافی نیست که فقط این رویداد را مدیریت کنید؛ زیرا اگر مقدار پیمایش توسط یک رویداد بومی چرخ ماوس کمتر از ۱ خط (یا کمتر از ۱ صفحه، زمانی که تنظیمات سیستم بر اساس پیمایش صفحه‌ای باشد) باشد، ممکن است رویدادهای چرخ ماوس دیگری بدون پرتاب این رویداد رخ دهند.

در Gecko 17 (فایرفاکس 17) یا بالاتر، باید `preventDefault()` رویدادهای `wheel` را فراخوانی کنید، زیرا این رویدادها باید برای هر رویداد بومی پرتاب شوند.

در صورت در دسترس بودن، از رویداد استاندارد {{domxref("Element/wheel_event","wheel")}} استفاده کنید.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("DOMMouseScroll", (event) => { })

onDOMMouseScroll = (event) => { }
```

## نوع رویداد

یک {{domxref("WheelEvent")}}. از {{domxref("MouseEvent")}}، {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("WheelEvent")}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseScrollEvent") }}
- رویداد پیمایش پیکسلی قدیمی Gecko: `MozMousePixelScroll`
- رویداد چرخ ماوس قدیمی مرورگرهای غیر-Gecko: `mousewheel`
- رویداد استاندارد چرخ: `wheel`