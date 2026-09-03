---
title: PerformanceEventTiming
slug: Web/API/PerformanceEventTiming
page-type: web-api-interface
browser-compat: api.PerformanceEventTiming
---

{{APIRef("Performance API")}}

رابط `PerformanceEventTiming` از Event Timing API اطلاعاتی درباره تأخیر (latency) انواع خاصی از رویدادهای ناشی از تعامل کاربر فراهم می‌کند.

## توضیحات

این API با ارائه زمان‌وقوع و مدت‌زمان برخی انواع رویداد (به [رویدادهای ارائه‌شده](#events_exposed) در ادامه مراجعه کنید)، امکان مشاهده رویدادهای کُند را می‌دهد. برای مثال، می‌توانید زمان بین اقدام کاربر و شروع اجرای مدیریت‌کننده رویداد (event handler) یا مدت‌زمان اجرای مدیریت‌کننده رویداد را پایش کنید.

این API به‌ویژه برای اندازه‌گیری {{Glossary("Interaction to Next Paint")}} (INP) مفید است: بلندترین مدت‌زمان (به‌جز برخی مقادیر پرت) از لحظه‌ای که کاربر با برنامه شما تعامل برقرار می‌کند تا لحظه‌ای که مرورگر واقعاً بتواند به آن تعامل پاسخ دهد.

معمولاً با ساختن یک نمونه از {{domxref("PerformanceObserver")}} و سپس فراخوانی متد [`observe()`](/en-US/docs/Web/API/PerformanceObserver/observe) روی آن، با آبجکت‌های `PerformanceEventTiming` کار می‌کنید؛ مقدار [`type`](/en-US/docs/Web/API/PerformanceEntry/entryType) را روی `"event"` یا `"first-input"` قرار می‌دهید. سپس callback آبجکت `PerformanceObserver` با فهرستی از آبجکت‌های `PerformanceEventTiming` فراخوانی می‌شود که می‌توانید آن‌ها را تحلیل کنید. برای جزئیات بیشتر به [مثال زیر](#getting_event_timing_information) مراجعه کنید.

به‌صورت پیش‌فرض، ورودی‌های `PerformanceEventTiming` زمانی ارائه می‌شوند که `duration` آن‌ها ۱۰۴ میلی‌ثانیه یا بیشتر باشد. پژوهش‌ها نشان می‌دهد که ورودی کاربر که در کمتر از ۱۰۰ میلی‌ثانیه پردازش نشود، کُند تلقی می‌شود و ۱۰۴ میلی‌ثانیه نخستین مضرب ۸ بزرگ‌تر از ۱۰۰ است (به دلایل امنیتی، مقادیر این API به نزدیک‌ترین مضرب ۸ میلی‌ثانیه گرد می‌شوند).
البته می‌توانید با استفاده از گزینه `durationThreshold` در متد [`observe()`](/en-US/docs/Web/API/PerformanceObserver/observe)، آستانه متفاوتی برای {{domxref("PerformanceObserver")}} تعیین کنید.

این رابط، متدها و ویژگی‌های والد خود، {{domxref("PerformanceEntry")}} را به ارث می‌برد:

{{InheritanceDiagram}}

### رویدادهای ارائه‌شده

انواع رویداد زیر توسط Event Timing API ارائه می‌شوند:

<table>
  <tbody>
    <tr>
      <th scope="row">رویدادهای کلیک</th>
      <td>
        {{domxref("Element/auxclick_event", "auxclick")}},
        {{domxref("Element/click_event", "click")}},
        {{domxref("Element/contextmenu_event", "contextmenu")}},
        {{domxref("Element/dblclick_event", "dblclick")}}
      </td>
    </tr>
    <tr>
      <th scope="row">رویدادهای ترکیب</th>
      <td>
        {{domxref("Element/compositionend_event", "compositionend")}},
        {{domxref("Element/compositionstart_event", "compositionstart")}},
        {{domxref("Element/compositionupdate_event", "compositionupdate")}}
      </td>
    </tr>
    <tr>
      <th scope="row">رویدادهای کشیدن و رها کردن (drag &amp; drop)</th>
      <td>
        {{domxref("HTMLElement/dragend_event", "dragend")}},
        {{domxref("HTMLElement/dragenter_event", "dragenter")}},
        {{domxref("HTMLElement/dragleave_event", "dragleave")}},
        {{domxref("HTMLElement/dragover_event", "dragover")}},
        {{domxref("HTMLElement/dragstart_event", "dragstart")}},
        {{domxref("HTMLElement/drop_event", "drop")}}
      </td>
    </tr>
    <tr>
      <th scope="row">رویدادهای ورودی</th>
      <td>
        {{domxref("Element/beforeinput_event", "beforeinput")}},
        {{domxref("Element/input_event", "input")}}
      </td>
    </tr>
    <tr>
      <th scope="row">رویدادهای صفحه‌کلید</th>
      <td>
        {{domxref("Element/keydown_event", "keydown")}},
        {{domxref("Element/keypress_event", "keypress")}},
        {{domxref("Element/keyup_event", "keyup")}}
      </td>
    </tr>
    <tr>
      <th scope="row">رویدادهای ماوس</th>
      <td>
        {{domxref("Element/mousedown_event", "mousedown")}},
        {{domxref("Element/mouseenter_event", "mouseenter")}},
        {{domxref("Element/mouseleave_event", "mouseleave")}},
        {{domxref("Element/mouseout_event", "mouseout")}},
        {{domxref("Element/mouseover_event", "mouseover")}},
        {{domxref("Element/mouseup_event", "mouseup")}}
      </td>
    </tr>
    <tr>
      <th scope="row">رویدادهای اشاره‌گر</th>
      <td>
        {{domxref("Element/pointerover_event", "pointerover")}},
        {{domxref("Element/pointerenter_event", "pointerenter")}},
        {{domxref("Element/pointerdown_event", "pointerdown")}},
        {{domxref("Element/pointerup_event", "pointerup")}},
        {{domxref("Element/pointercancel_event", "pointercancel")}},
        {{domxref("Element/pointerout_event", "pointerout")}},
        {{domxref("Element/pointerleave_event", "pointerleave")}},
        {{domxref("Element/gotpointercapture_event", "gotpointercapture")}},
        {{domxref("Element/lostpointercapture_event", "lostpointercapture")}}
      </td>
    </tr>
    <tr>
      <th scope="row">رویدادهای لمسی</th>
      <td>
        {{domxref("Element/touchstart_event", "touchstart")}},
        {{domxref("Element/touchend_event", "touchend")}},
        {{domxref("Element/touchcancel_event", "touchcancel")}}
      </td>
    </tr>
  </tbody>
</table>

توجه داشته باشید که رویدادهای زیر در این فهرست گنجانده نشده‌اند، زیرا رویدادهای پیوسته‌ای هستند و در این مرحله نمی‌توان شمارش معنادار رویداد یا معیارهای عملکردی از آن‌ها به دست آورد: {{domxref("Element/mousemove_event", "mousemove")}}, {{domxref("Element/pointermove_event", "pointermove")}}, {{domxref("Element/pointerrawupdate_event", "pointerrawupdate")}}, {{domxref("Element/touchmove_event", "touchmove")}}, {{domxref("Element/wheel_event", "wheel")}}, {{domxref("HTMLElement/drag_event", "drag")}}.

برای دریافت فهرست همه رویدادهای ارائه‌شده، می‌توانید کلیدهای موجود در نگاشت {{domxref("performance.eventCounts")}} را نیز بررسی کنید:

```js
const exposedEventsList = [...performance.eventCounts.keys()];
```

## سازنده

این رابط به‌تنهایی سازنده‌ای ندارد. برای روش معمول دریافت اطلاعاتی که رابط `PerformanceEventTiming` در خود نگه می‌دارد، به [مثال زیر](#getting_event_timing_information) مراجعه کنید.

## خصوصیات نمونه

این رابط، ویژگی‌های زیر از {{domxref("PerformanceEntry")}} را برای انواع ورودی‌های performance مربوط به زمان‌بندی رویداد به شکل زیر بازتعریف می‌کند:

- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که مدت‌زمان از `startTime` تا رندرِ بعدی (rendering paint) را نشان می‌دهد (به نزدیک‌ترین ۸ میلی‌ثانیه گرد شده است).
- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}}
  - : مقدار `"event"` (برای رویدادهای طولانی) یا `"first-input"` (برای نخستین تعامل کاربر) را برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}}
  - : نوع رویداد مرتبط را برمی‌گرداند.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که ویژگی [`timestamp`](/en-US/docs/Web/API/Event/timeStamp) رویداد مرتبط را نشان می‌دهد. این زمان، زمانِ ایجاد رویداد است و می‌توان آن را به‌عنوان برآوردی از زمان رخ دادن تعامل کاربر در نظر گرفت.

این رابط همچنین از ویژگی‌های زیر پشتیبانی می‌کند:

- {{domxref("PerformanceEventTiming.cancelable")}} {{ReadOnlyInline}}
  - : ویژگی [`cancelable`](/en-US/docs/Web/API/Event/cancelable) رویداد مرتبط را برمی‌گرداند.
- {{domxref("PerformanceEventTiming.interactionId")}} {{ReadOnlyInline}}
  - : شناسه‌ای را برمی‌گرداند که تعامل کاربرِ محرکِ رویداد مرتبط را به‌شکلی یکتا شناسایی می‌کند.
- {{domxref("PerformanceEventTiming.processingStart")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان آغاز ارسال (dispatch) رویداد را نشان می‌دهد. برای اندازه‌گیری زمان بین اقدام کاربر و زمانی که مدیریت‌کننده رویداد شروع به اجرا می‌کند، `processingStart-startTime` را محاسبه کنید.
- {{domxref("PerformanceEventTiming.processingEnd")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} برمی‌گرداند که زمان پایان ارسال رویداد را نشان می‌دهد. برای اندازه‌گیری مدت‌زمان اجرای مدیریت‌کننده رویداد، `processingEnd-processingStart` را محاسبه کنید.
- {{domxref("PerformanceEventTiming.target")}} {{ReadOnlyInline}}
  - : آخرین هدف (target) رویداد مرتبط را برمی‌گرداند، اگر حذف نشده باشد.

## متدهای نمونه

- {{domxref("PerformanceEventTiming.toJSON()")}}
  - : یک نمایش JSON از آبجکت `PerformanceEventTiming` برمی‌گرداند.

## مثال‌ها

### دریافت اطلاعات زمان‌بندی رویداد

برای دریافت اطلاعات زمان‌بندی رویداد، یک نمونه از {{domxref("PerformanceObserver")}} بسازید و سپس متد [`observe()`](/en-US/docs/Web/API/PerformanceObserver/observe) را با مقدار `"event"` یا `"first-input"` برای [`type`](/en-US/docs/Web/API/PerformanceEntry/entryType) صدا بزنید. همچنین باید `buffered` را روی `true` قرار دهید تا به رویدادهایی که عامل کاربر هنگام ساخت سند در بافر قرار داده است دسترسی داشته باشید. سپس callback آبجکت `PerformanceObserver` با فهرستی از آبجکت‌های `PerformanceEventTiming` فراخوانی می‌شود که می‌توانید آن‌ها را تحلیل کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    // Full duration
    const duration = entry.duration;

    // Input delay (before processing event)
    const delay = entry.processingStart - entry.startTime;

    // Synchronous event processing time
    // (between start and end dispatch)
    const eventHandlerTime = entry.processingEnd - entry.processingStart;
    console.log(`Total duration: ${duration}`);
    console.log(`Event delay: ${delay}`);
    console.log(`Event handler duration: ${eventHandlerTime}`);
  });
});

// Register the observer for events
observer.observe({ type: "event", buffered: true });
```

همچنین می‌توانید [`durationThreshold`](/en-US/docs/Web/API/PerformanceObserver/observe#durationthreshold) متفاوتی تعیین کنید. مقدار پیش‌فرض ۱۰۴ میلی‌ثانیه است و کمترین آستانه ممکن ۱۶ میلی‌ثانیه است.

```js
observer.observe({ type: "event", durationThreshold: 16, buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API)
- [Page Visibility API](/en-US/docs/Web/API/Page_Visibility_API)