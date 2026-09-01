---
title: "Element: pointercancel event"
short-title: pointercancel
slug: Web/API/Element/pointercancel_event
page-type: web-api-event
browser-compat: api.Element.pointercancel_event
---

{{APIRef("Pointer Events")}}

رویداد **`pointercancel`** زمانی به وقوع می‌پیوندد که مرورگر تشخیص دهد احتمالاً رویدادهای اشاره‌ای دیگری رخ نخواهند داد، یا اگر پس از رویداد {{domxref("Element/pointerdown_event", "pointerdown")}}، اشاره‌گر برای دستکاری نمای دید (viewport) از طریق پیمایش (panning)، بزرگ‌نمایی یا اسکرول استفاده شود.

چند نمونه از موقعیت‌هایی که می‌توانند رویداد `pointercancel` را تحریک کنند:

- رخ دادن یک رویداد سخت‌افزاری که فعالیت‌های اشاره‌گر را لغو می‌کند. این می‌تواند برای مثال شامل این باشد که کاربر با استفاده از رابط تعویض برنامه‌ها، برنامه را تغییر دهد یا دکمه «خانه» را در یک دستگاه همراه فشار دهد.
- تغییر جهت صفحه‌نمایش دستگاه در حالی که اشاره‌گر فعال است.
- مرورگر تصمیم بگیرد که کاربر ورودی اشاره را به‌طور تصادفی شروع کرده است. این می‌تواند برای مثال زمانی رخ دهد که سخت‌افزار از قابلیت رد کف دست پشتیبانی می‌کند تا از ایجاد رویدادهای تصادفی هنگام استراحت دست روی نمایشگر در زمان استفاده از قلم جلوگیری کند.
- ویژگی CSS {{cssxref("touch-action")}} از ادامه یافتن ورودی جلوگیری کند.
- وقتی کاربر همزمان با تعداد زیادی اشاره‌گر تعامل داشته باشد، مرورگر می‌تواند این رویداد را برای همه اشاره‌گرهای موجود شلیک کند (حتی اگر کاربر همچنان صفحه را لمس کرده باشد).

> [!NOTE]
> پس از شلیک رویداد `pointercancel`، مرورگر همچنین {{domxref("Element/pointerout_event", "pointerout")}} و به دنبال آن {{domxref("Element/pointerleave_event", "pointerleave")}} را ارسال خواهد کرد.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی پردازنده رویداد را تنظیم کنید.

```js-nolint
addEventListener("pointercancel", (event) => { })

onpointercancel = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}}. به ارث‌برده از {{domxref("Event")}}.

{{InheritanceDiagram("PointerEvent")}}

## مثال‌ها

استفاده از `addEventListener()`:

```js
const para = document.querySelector("p");

para.addEventListener("pointercancel", (event) => {
  console.log("Pointer event cancelled");
});
```

استفاده از ویژگی پردازنده رویداد `onpointercancel`:

```js
const para = document.querySelector("p");

para.onpointercancel = (event) => {
  console.log("Pointer event cancelled");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط
  - {{domxref('Element/gotpointercapture_event', 'gotpointercapture')}}
  - {{domxref('Element/lostpointercapture_event', 'lostpointercapture')}}
  - {{domxref('Element/pointerover_event', 'pointerover')}}
  - {{domxref('Element/pointerenter_event', 'pointerenter')}}
  - {{domxref('Element/pointerdown_event', 'pointerdown')}}
  - {{domxref('Element/pointermove_event', 'pointermove')}}
  - {{domxref('Element/pointerup_event', 'pointerup')}}
  - {{domxref('Element/pointerout_event', 'pointerout')}}
  - {{domxref('Element/pointerleave_event', 'pointerleave')}}
  - {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}}