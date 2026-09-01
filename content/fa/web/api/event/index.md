---
title: Event
slug: Web/API/Event
page-type: web-api-interface
browser-compat: api.Event
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

رابط (interface) **`Event`** نشان‌دهندهٔ رویدادی است که روی یک [`EventTarget`](/en-US/docs/Web/API/EventTarget) رخ می‌دهد.

یک رویداد می‌تواند توسط اقدام کاربر مانند کلیک کردن دکمهٔ ماوس یا فشردن کلید صفحه‌کلید ایجاد شود، یا توسط APIها برای نمایش پیشرفت یک کار ناهمگام (asynchronous) تولید شود. همچنین می‌توان آن را به صورت برنامه‌نویسی شده (programmatically) فعال کرد، مانند فراخوانی متد [`HTMLElement.click()`](/en-US/docs/Web/API/HTMLElement/click) یک عنصر، یا با تعریف رویداد و سپس ارسال آن به یک هدف مشخص با استفاده از [`EventTarget.dispatchEvent()`](/en-US/docs/Web/API/EventTarget/dispatchEvent).

انواع مختلفی از رویدادها وجود دارند که برخی از آن‌ها از رابط‌های دیگری مبتنی بر رابط اصلی `Event` استفاده می‌کنند. خود `Event` شامل ویژگی‌ها و روش‌هایی است که در همهٔ رویدادها مشترک هستند.

بسیاری از عناصر DOM را می‌توان طوری تنظیم کرد که این رویدادها را بپذیرند (یا «گوش دهند») و در پاسخ به پردازش (یا «مدیریت») آن‌ها کد اجرا کنند. مدیریت‌کننده‌های رویداد (event-handlers) معمولاً با استفاده از [`EventTarget.addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) به عناصر مختلف [HTML](/en-US/docs/Web/HTML/Reference/Elements) (مانند `<button>`، `<div>`، `<span>` و غیره) متصل می‌شوند و این کار عموماً جایگزین استفاده از [ویژگی‌های مدیریت‌کننده رویداد](/en-US/docs/Web/HTML/Reference/Global_attributes) قدیمی HTML می‌شود. علاوه بر این، پس از اضافه شدن صحیح، در صورت نیاز می‌توان این مدیریت‌کننده‌ها را با استفاده از [`removeEventListener()`](/en-US/docs/Web/API/EventTarget/removeEventListener) جدا کرد.

> [!NOTE]
> یک عنصر می‌تواند چندین مدیریت‌کننده از این دست داشته باشد، حتی برای دقیقاً همان رویداد—به‌ویژه اگر ماژول‌های کد جداگانه و مستقل آن‌ها را متصل کنند، هر کدام برای اهداف مستقل خود. (مثلاً یک صفحه وب با یک ماژول تبلیغاتی و یک ماژول آمار که هر دو تماشای ویدیو را نظارت می‌کنند.)

وقتی عناصر تودرتو (nested) زیادی وجود دارند که هر کدام مدیریت‌کننده(های) خود را دارند، پردازش رویداد می‌تواند بسیار پیچیده شود—به‌ویژه جایی که یک عنصر والد دقیقاً همان رویداد عناصر فرزند خود را دریافت می‌کند زیرا از نظر «مکانی» هم‌پوشانی دارند بنابراین رویداد از نظر فنی در هر دو رخ می‌دهد، و ترتیب پردازش چنین رویدادهایی به تنظیمات [حباب زدن رویداد (Event bubbling)](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) هر مدیریت‌کننده‌ای که فعال می‌شود بستگی دارد.

## رابط‌های مبتنی بر Event

در زیر فهرستی از رابط‌هایی که مبتنی بر رابط اصلی `Event` هستند، همراه با پیوند به مستندات مربوطه در مرجع API MDN آورده شده است. توجه داشته باشید که همهٔ رابط‌های رویداد نام‌هایی دارند که به «Event» ختم می‌شوند.

- {{domxref("AnimationEvent")}}
- {{domxref("AudioProcessingEvent")}} {{Deprecated_Inline}}
- {{domxref("BeforeUnloadEvent")}}
- {{domxref("BlobEvent")}}
- {{domxref("ClipboardChangeEvent")}}
- {{domxref("ClipboardEvent")}}
- {{domxref("CloseEvent")}}
- {{domxref("CompositionEvent")}}
- {{domxref("CustomEvent")}}
- {{domxref("DeviceMotionEvent")}}
- {{domxref("DeviceOrientationEvent")}}
- {{domxref("DragEvent")}}
- {{domxref("ErrorEvent")}}
- {{domxref("FetchEvent")}}
- {{domxref("FocusEvent")}}
- {{domxref("FontFaceSetLoadEvent")}}
- {{domxref("FormDataEvent")}}
- {{domxref("GamepadEvent")}}
- {{domxref("HashChangeEvent")}}
- {{domxref("HIDInputReportEvent")}}
- {{domxref("IDBVersionChangeEvent")}}
- {{domxref("InputEvent")}}
- {{domxref("KeyboardEvent")}}
- {{domxref("MediaStreamEvent")}} {{Deprecated_Inline}}
- {{domxref("MessageEvent")}}
- {{domxref("MouseEvent")}}
- {{domxref("MutationEvent")}} {{Deprecated_Inline}}
- {{domxref("OfflineAudioCompletionEvent")}}
- {{domxref("PageTransitionEvent")}}
- {{domxref("PaymentRequestUpdateEvent")}}
- {{domxref("PointerEvent")}}
- {{domxref("PopStateEvent")}}
- {{domxref("ProgressEvent")}}
- {{domxref("RTCDataChannelEvent")}}
- {{domxref("RTCPeerConnectionIceEvent")}}
- {{domxref("StorageEvent")}}
- {{domxref("SubmitEvent")}}
- {{domxref("TimeEvent")}}
- {{domxref("TouchEvent")}}
- {{domxref("TrackEvent")}}
- {{domxref("TransitionEvent")}}
- {{domxref("UIEvent")}}
- {{domxref("WebGLContextEvent")}}
- {{domxref("WheelEvent")}}

## سازنده (Constructor)

- {{domxref("Event.Event", "Event()")}}
  - : یک شیء `Event` ایجاد کرده و آن را به فراخواننده بازمی‌گرداند.

## ویژگی‌های نمونه (Instance properties)

- {{domxref("Event.bubbles")}} {{ReadOnlyInline}}
  - : یک مقدار بولی (boolean) که نشان می‌دهد آیا رویداد در DOM به بالا حباب می‌زند (bubbles) یا خیر.
- {{domxref("Event.cancelable")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد آیا رویداد قابل لغو (cancelable) است یا خیر.
- {{domxref("Event.composed")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد آیا رویداد می‌تواند از مرز بین DOM سایه (shadow DOM) و DOM معمولی عبور کند یا خیر.
- {{domxref("Event.currentTarget")}} {{ReadOnlyInline}}
  - : ارجاعی به هدف ثبت‌شدهٔ فعلی برای رویداد. این همان شیءای است که رویداد قرار است به آن ارسال شود. ممکن است این مقدار در طول مسیر از طریق _retargeting_ تغییر کرده باشد.
- {{domxref("Event.defaultPrevented")}} {{ReadOnlyInline}}
  - : نشان می‌دهد که آیا فراخوانی {{domxref("event.preventDefault()")}} رویداد را لغو کرده است یا خیر.
- {{domxref("Event.eventPhase")}} {{ReadOnlyInline}}
  - : نشان می‌دهد کدام مرحله از جریان رویداد در حال پردازش است. یکی از اعداد زیر است: `NONE`، `CAPTURING_PHASE`، `AT_TARGET`، `BUBBLING_PHASE`.
- {{domxref("Event.isTrusted")}} {{ReadOnlyInline}}
  - : نشان می‌دهد که آیا رویداد توسط مرورگر (مثلاً پس از کلیک کاربر) یا توسط یک اسکریپت (با استفاده از یک روش ایجاد رویداد) آغاز شده است.
- {{domxref("Event.srcElement")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : یک نام مستعار برای ویژگی {{domxref("Event.target")}}. به جای آن از {{domxref("Event.target")}} استفاده کنید.
- {{domxref("Event.target")}} {{ReadOnlyInline}}
  - : ارجاعی به شیءای که رویداد در ابتدا به آن ارسال شده است.
- {{domxref("Event.timeStamp")}} {{ReadOnlyInline}}
  - : زمانی که رویداد ایجاد شده است (به میلی‌ثانیه). طبق مشخصات، این مقدار زمان از مبدأ (epoch) است—اما در عمل، تعریف مرورگرها متفاوت است. همچنین کارهایی برای تغییر این مقدار به {{domxref("DOMHighResTimeStamp")}} در حال انجام است.
- {{domxref("Event.type")}} {{ReadOnlyInline}}
  - : نامی که نوع رویداد را مشخص می‌کند.

### ویژگی‌های قدیمی (legacy) و غیراستاندارد

- {{domxref("Event.cancelBubble")}} {{deprecated_inline}}
  - : یک نام مستعار قدیمی برای {{domxref("Event.stopPropagation()")}} که باید به جای آن استفاده شود. تنظیم مقدار آن به `true` قبل از بازگشت از یک مدیریت‌کننده رویداد، از انتشار رویداد جلوگیری می‌کند.
- {{domxref("Event.explicitOriginalTarget")}} {{non-standard_inline}} {{ReadOnlyInline}}
  - : هدف اصلی صریح رویداد.
- {{domxref("Event.originalTarget")}} {{non-standard_inline}} {{ReadOnlyInline}}
  - : هدف اصلی رویداد، قبل از هر گونه retargeting.
- {{domxref("Event.returnValue")}} {{deprecated_inline}}
  - : یک ویژگی قدیمی که همچنان برای اطمینان از کارکرد سایت‌های موجود پشتیبانی می‌شود. به جای آن از {{domxref("Event.preventDefault()")}} و {{domxref("Event.defaultPrevented")}} استفاده کنید.
- {{domxref("Event.composed", "Event.scoped")}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا رویداد داده شده از طریق ریشه سایه (shadow root) به DOM استاندارد حباب می‌زند یا خیر. به جای آن از {{domxref("Event.composed", "composed")}} استفاده کنید.

## روش‌های نمونه (Instance methods)

- {{domxref("Event.composedPath()")}}
  - : مسیر رویداد (آرایه‌ای از اشیاء که شنوندگان (listeners) روی آن‌ها فراخوانی خواهند شد) را بازمی‌گرداند. این شامل گره‌های درختان سایه (shadow trees) نمی‌شود اگر ریشه سایه با {{domxref("ShadowRoot.mode")}} بسته (closed) ایجاد شده باشد.
- {{domxref("Event.preventDefault()")}}
  - : رویداد را لغو می‌کند (اگر قابل لغو باشد).
- {{domxref("Event.stopImmediatePropagation()")}}
  - : برای این رویداد خاص، از فراخوانی همهٔ شنوندگان دیگر جلوگیری می‌کند. این شامل شنوندگانی است که به همان عنصر متصل شده‌اند و همچنین آن‌هایی که به عناصری که بعداً پیمایش خواهند شد (مثلاً در مرحلهٔ capture) متصل شده‌اند.
- {{domxref("Event.stopPropagation()")}}
  - : انتشار رویداد را در DOM متوقف می‌کند.

### روش‌های منسوخ (Deprecated methods)

- {{domxref("Event.initEvent()")}} {{deprecated_inline}}
  - : مقدار یک Event ایجاد شده را مقداردهی اولیه می‌کند. اگر رویداد قبلاً ارسال شده باشد، این روش کاری انجام نمی‌دهد. به جای آن از سازنده ({{domxref("Event.Event", "Event()")}} استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [فهرست رویدادها](/en-US/docs/Web/API/Document_Object_Model/Events#event_index)
- [یادگیری: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- [یادگیری: حباب زدن رویداد (Event bubbling)](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling)
- [ایجاد و ارسال رویدادهای سفارشی](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events)