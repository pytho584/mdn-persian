---
title: "MouseEvent: initMouseEvent() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent/initMouseEvent"
---

---
title: "MouseEvent: initMouseEvent() method"
short-title: initMouseEvent()
slug: Web/API/MouseEvent/initMouseEvent
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.MouseEvent.initMouseEvent
---

{{APIRef("Pointer Events")}}{{deprecated_header}}

متد **`MouseEvent.initMouseEvent()`** مقدار یک رویداد ماوس را پس از ایجاد آن (معمولاً با متد {{domxref("Document.createEvent()")}}) مقداردهی می‌کند.

> [!WARNING]
> دیگر از این متد استفاده نکنید زیرا منسوخ شده است.
>
> در عوض، از سازنده‌های رویداد خاص مانند {{domxref("MouseEvent.MouseEvent", "MouseEvent()")}} استفاده کنید.
> بخش [ایجاد و ارسال رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) اطلاعات بیشتری درباره نحوه استفاده از این‌ها ارائه می‌دهد.

رویدادهایی که به این روش مقداردهی می‌شوند باید با متد {{domxref("Document.createEvent()")}} ایجاد شده باشند.
این متد باید قبل از ارسال رویداد، با استفاده از {{ domxref("EventTarget.dispatchEvent()") }} فراخوانی شود تا رویداد تنظیم گردد.

## نحو (Syntax)

```js-nolint
initMouseEvent(type, canBubble, cancelable, view,
                     detail, screenX, screenY, clientX, clientY,
                     ctrlKey, altKey, shiftKey, metaKey,
                     button, relatedTarget)
```

### پارامترها

- `type`
  - : رشته‌ای که {{domxref("Event.type", "type")}} رویداد را تنظیم می‌کند. انواع ممکن
    برای رویدادهای ماوس عبارت‌اند از: `click`، `mousedown`،
    `mouseup`، `mouseover`، `mousemove`،
    `mouseout`.
- `canBubble`
  - : مشخص می‌کند که آیا رویداد می‌تواند حباب بزند یا خیر. مقدار {{domxref("Event.bubbles")}} را تنظیم می‌کند.
- `cancelable`
  - : مشخص می‌کند که آیا می‌توان از اقدام پیش‌فرض رویداد جلوگیری کرد یا خیر. مقدار
    {{domxref("Event.cancelable")}} را تنظیم می‌کند.
- `view`
  - : AbstractView رویداد. باید شیء {{domxref("window")}} را اینجا ارسال کنید.
    مقدار {{domxref("UIEvent.view")}} را تنظیم می‌کند.
- `detail`
  - : تعداد کلیک‌های ماوس رویداد. مقدار {{domxref("UIEvent.detail")}} را تنظیم می‌کند.
- `screenX`
  - : مختصات x صفحه رویداد. مقدار
    {{domxref("MouseEvent.screenX")}} را تنظیم می‌کند.
- `screenY`
  - : مختصات y صفحه رویداد. مقدار
    {{domxref("MouseEvent.screenY")}} را تنظیم می‌کند.
- `clientX`
  - : مختصات x سمت کلاینت رویداد. مقدار
    {{domxref("MouseEvent.clientX")}} را تنظیم می‌کند.
- `clientY`
  - : مختصات y سمت کلاینت رویداد. مقدار
    {{domxref("MouseEvent.clientY")}} را تنظیم می‌کند.
- `ctrlKey`
  - : مشخص می‌کند که آیا کلید <kbd>کنترل</kbd> در طول رویداد فشار داده شده بود یا خیر. مقدار
    {{domxref("MouseEvent.ctrlKey")}} را تنظیم می‌کند.

- `altKey`
  - : مشخص می‌کند که آیا کلید <kbd>alt</kbd> در طول رویداد فشار داده شده بود یا خیر. مقدار
    {{domxref("MouseEvent.altKey")}} را تنظیم می‌کند.

- `shiftKey`
  - : مشخص می‌کند که آیا کلید <kbd>shift</kbd> در طول رویداد فشار داده شده بود یا خیر. مقدار
    {{domxref("MouseEvent.shiftKey")}} را تنظیم می‌کند.

- `metaKey`
  - : مشخص می‌کند که آیا کلید <kbd>meta</kbd> در طول رویداد فشار داده شده بود یا خیر. مقدار
    {{domxref("MouseEvent.metaKey")}} را تنظیم می‌کند.

- `button`
  - : {{domxref("MouseEvent.button", "دکمه")}} ماوس رویداد.
- `relatedTarget`
  - : [EventTarget مرتبط](/en-US/docs/Web/API/MouseEvent/relatedTarget) رویداد. فقط با
    برخی از انواع رویداد استفاده می‌شود (مثلاً `mouseover` و `mouseout`). در
    سایر موارد، `null` را ارسال کنید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const event = document.createEvent("MouseEvents");
event.initMouseEvent(
  "click",
  true,
  true,
  window,
  0,
  0,
  0,
  80,
  20,
  false,
  false,
  false,
  false,
  0,
  null,
);
document.body.dispatchEvent(event);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سازنده {{domxref("MouseEvent.MouseEvent()","MouseEvent()")}}، روش مدرن و استاندارد
  برای ایجاد یک {{domxref("MouseEvent")}}
- {{domxref("Event.initEvent()")}} متد ساده‌تری است که هدف مشابهی دارد. این متد
  نیز منسوخ شده است و نباید دیگر استفاده شود.