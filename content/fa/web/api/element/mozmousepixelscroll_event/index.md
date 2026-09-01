---
title: "Element: MozMousePixelScroll event"
---

---
title: "Element: MozMousePixelScroll event"
short-title: MozMousePixelScroll
slug: Web/API/Element/MozMousePixelScroll_event
page-type: web-api-event
status:
  - deprecated
  - non-standard
browser-compat: api.Element.MozMousePixelScroll_event
---

{{APIRef("UI Events")}}{{deprecated_header}}{{Non-standard_header}}

رویداد **`MozMousePixelScroll`** که فقط در Firefox موجود است، _غیراستاندارد_ و _منسوخ_ است، به‌صورت ناهمزمان روی یک {{domxref("Element")}} هنگامی که چرخ ماوس یا وسیلهٔ مشابهی به‌کار گرفته می‌شود، صادر می‌شود. این رویداد توسط رابط {{ domxref("MouseScrollEvent") }} نمایش داده می‌شود.

> [!NOTE]
> از این رویداد غیراستاندارد و منسوخ استفاده نکنید. در عوض، همیشه باید از رویداد استاندارد {{domxref("Element.wheel_event", "wheel")}} استفاده کنید.

## نحو

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به‌کار ببرید، یا یک ویژگیِ کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("MozMousePixelScroll", (event) => { })

onMozMousePixelScroll = (event) => { }
```

## نوع رویداد

یک {{domxref("WheelEvent")}}. از {{domxref("MouseEvent")}}، {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("WheelEvent")}}

## دریافت فاصلهٔ پیمایش

ویژگی {{domxref("UIEvent/detail", "detail")}} رویداد، فاصلهٔ پیمایش را بر حسب خط بیان می‌کند؛ مقادیر منفی نشان می‌دهند که پیمایش به سمت پایین یا راست انجام می‌شود و مقادیر مثبت نشان می‌دهند که پیمایش به سمت بالا یا چپ است.

اگر رویدادهای بومیِ چرخ ماوس در پلتفرم، فاصلهٔ پیمایش را بر حسب خط یا صفحه اعلام کنند، مقدار `detail` با استفاده از آن مقدار و ارتفاع خط یا عرض/ارتفاع صفحهٔ نزدیک‌ترین عنصرِ والدِ قابل‌پیمایش که شامل عنصر هدف است، محاسبه می‌شود.

> [!NOTE]
> در macOS، فاصلهٔ پیمایش (و در نتیجه مقدار `detail`) بر اساس فاصلهٔ پیمایش شتاب‌دار محاسبه می‌شود.

اگر رویدادها معتبر باشند، مقدار `detail` هرگز ۰ نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseScrollEvent") }}
- رویداد قدیمی پیمایش خط یا صفحه در Gecko: `DOMMouseScroll`
- رویداد قدیمی چرخ ماوس در مرورگرهای غیر-Gecko: `mousewheel`
- رویداد استانداردشدهٔ چرخ ماوس: `wheel`