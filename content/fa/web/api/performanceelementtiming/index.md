---
title: PerformanceElementTiming
slug: Web/API/PerformanceElementTiming
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PerformanceElementTiming
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

رابط **`PerformanceElementTiming`** حاوی اطلاعات زمان‌بندی رندر برای عناصر تصویر و گره‌های متنی است که توسعه‌دهنده با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) آن‌ها را برای مشاهده علامت‌گذاری کرده است.

## توضیحات

هدف API زمان‌بندی عنصر (Element Timing API) این است که به توسعه‌دهندگان وب یا ابزارهای تحلیلی امکان اندازه‌گیری زمان‌های رندر عناصر حیاتی در یک صفحه را بدهد.

این API از اطلاعات زمان‌بندی برای عناصر زیر پشتیبانی می‌کند:

- عناصر {{htmlelement("img")}}
- عناصر {{SVGElement("image")}} درون یک {{SVGElement("svg")}}
- تصاویر [پوستر](/en-US/docs/Web/HTML/Reference/Elements/video#poster) عناصر {{htmlelement("video")}}
- عناصری که دارای ویژگی {{cssxref("background-image")}} با مقدار URL برای یک منبع موجود هستند
- گروه‌هایی از گره‌های متنی، مانند یک {{htmlelement("p")}}

نویسنده با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) به عنصر، آن را برای مشاهده علامت‌گذاری می‌کند.

`PerformanceElementTiming` از {{domxref("PerformanceEntry")}} ارث‌بری می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط به طور مستقیم ویژگی‌های زیر را تعریف می‌کند:

- {{domxref("PerformanceElementTiming.element")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("Element")}} که عنصری را که در مورد آن اطلاعات بازگردانده می‌شود، نشان می‌دهد.
- {{domxref("PerformanceElementTiming.id")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته که [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) عنصر است.
- {{domxref("PerformanceElementTiming.identifier")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته که مقدار ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/for) روی عنصر است.
- {{domxref("PerformanceElementTiming.intersectionRect")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMRectReadOnly")}} که مستطیل عنصر درون نمای دید (viewport) است.
- {{domxref("PerformanceElementTiming.loadTime")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} با زمان بارگذاری عنصر.
- {{domxref("PerformanceElementTiming.naturalHeight")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک عدد صحیح ۳۲ بیتی بدون علامت (unsigned long) که ارتفاع ذاتی تصویر است اگر برای یک تصویر اعمال شود، و برای متن ۰ است.
- {{domxref("PerformanceElementTiming.naturalWidth")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک عدد صحیح ۳۲ بیتی بدون علامت (unsigned long) که عرض ذاتی تصویر است اگر برای یک تصویر اعمال شود، و برای متن ۰ است.
- {{domxref("PerformanceElementTiming.paintTime")}} {{experimental_inline}}
  - : {{domxref("DOMHighResTimeStamp","timestamp")}} زمانی که فاز رندر به پایان رسید و فاز نقاشی (paint) شروع شد را بازمی‌گرداند.
- {{domxref("PerformanceElementTiming.presentationTime")}} {{experimental_inline}}
  - : {{domxref("DOMHighResTimeStamp","timestamp")}} زمانی که عنصر واقعاً روی صفحه رسم شد را بازمی‌گرداند.
- {{domxref("PerformanceElementTiming.renderTime")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} با زمان رندر عنصر.
- {{domxref("PerformanceElementTiming.url")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک رشته که URL اولیه درخواست منابع برای تصاویر است، و برای متن ۰ است.

همچنین ویژگی‌های زیر را از {{domxref("PerformanceEntry")}} به ارث برده و آن‌ها را به شرح زیر محدود و واجد شرایط می‌کند:

- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : همیشه `0` را برمی‌گرداند زیرا `duration` برای این رابط کاربردی ندارد.
- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : همیشه `"element"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : برای تصاویر `"image-paint"` و برای متن `"text-paint"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مقدار {{domxref("PerformanceElementTiming.renderTime", "renderTime")}} این ورودی را اگر `0` نباشد، در غیر این صورت مقدار {{domxref("PerformanceElementTiming.loadTime", "loadTime")}} این ورودی را برمی‌گرداند.

## روش‌های نمونه

- {{domxref("PerformanceElementTiming.toJSON()")}} {{Experimental_Inline}}
  - : یک نمایش JSON از شیء `PerformanceElementTiming` برمی‌گرداند.

## مثال‌ها

### مشاهده زمان رندر عناصر خاص

در این مثال دو عنصر با افزودن ویژگی [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) تحت مشاهده قرار می‌گیرند. یک {{domxref("PerformanceObserver")}} برای دریافت تمام ورودی‌های عملکرد از نوع `"element"` ثبت می‌شود و از پرچم `buffered` برای دسترسی به داده‌های قبل از ایجاد observer استفاده می‌شود.

```html
<img src="image.jpg" elementtiming="big-image" />
<p elementtiming="text" id="text-id">text here</p>
```

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry);
  });
});
observer.observe({ type: "element", buffered: true });
```

دو ورودی در کنسول نمایش داده خواهد شد. اولی شامل جزئیات تصویر و دومی شامل جزئیات گره متنی است.

### مشاهده زمان‌بندی‌های جداگانه نقاشی و نمایش

ویژگی‌های `paintTime` و `presentationTime` به شما امکان می‌دهند زمان‌بندی‌های خاصی را برای شروع فاز نقاشی و رسم عنصر روی صفحه دریافت کنید. `paintTime` به طور کلی بین مرورگرها یکسان است، در حالی که `presentationTime` وابسته به پیاده‌سازی است.

این مثال از یک `PerformanceObserver` برای مشاهده تمام ورودی‌های عملکرد از نوع `"element"` استفاده می‌کند (به یاد داشته باشید که برای مشاهده، عناصر باید ویژگی‌های `elementtimity` روی آن‌ها تنظیم شده باشد). ما پشتیبانی از `paintTime` و `presentationTime` را بررسی می‌کنیم و در صورت وجود آن مقادیر را بازیابی می‌کنیم. در مرورگرهایی که از آن‌ها پشتیبانی نمی‌کنند، کد بسته به پشتیبانی، `renderTime` یا `loadTime` را بازیابی می‌کند.

```js
const observer = new PerformanceObserver((list) => {
  const entries = list.getEntries();
  entries.forEach((entry) => {
    if (entry.presentationTime) {
      console.log(
        "Element paintTime:",
        entry.paintTime,
        "Element presentationTime:",
        entry.presentationTime,
      );
    } else if (entry.paintTime) {
      console.log("Element paintTime:", entry.paintTime);
    } else if (entry.renderTime) {
      console.log("Element renderTime:", entry.renderTime);
    } else {
      console.log("Element loadTime", entry.loadTime);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی HTML [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming)