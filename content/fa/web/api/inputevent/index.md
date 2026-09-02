---
title: "InputEvent"
---

---
title: InputEvent
slug: Web/API/InputEvent
page-type: web-api-interface
browser-compat: api.InputEvent
---

{{APIRef("UI Events")}}

رابط (interface) **`InputEvent`** نشان‌دهنده رویدادی است که کاربر را از تغییرات محتوای قابل ویرایش آگاه می‌کند.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{DOMxRef("InputEvent.InputEvent", "InputEvent()")}}
  - : یک شیء `InputEvent` ایجاد می‌کند.

## ویژگی‌های نمونه (Instance properties)

_این رابط ویژگی‌هایی را از والدین خود، {{DOMxRef("UIEvent")}} و {{DOMxRef("Event")}}، به ارث می‌برد._

- {{DOMxRef("InputEvent.data")}} {{ReadOnlyInline}}
  - : یک رشته شامل کاراکترهای درج‌شده را برمی‌گرداند. اگر تغییر متنی را درج نکند (مثلاً هنگام حذف کاراکترها)، ممکن است یک رشته خالی باشد.
- {{DOMxRef("InputEvent.dataTransfer")}} {{ReadOnlyInline}}
  - : یک شیء {{DOMxRef("DataTransfer")}} شامل اطلاعاتی درباره داده‌های متن غنی (richtext) یا متن ساده (plaintext) که به محتوای قابل ویرایش اضافه یا از آن حذف می‌شوند، برمی‌گرداند.
- {{DOMxRef("InputEvent.inputType")}} {{ReadOnlyInline}}
  - : نوع تغییر برای محتوای قابل ویرایش را برمی‌گرداند، مانند درج (inserting)، حذف (deleting) یا قالب‌بندی (formatting) متن.
- {{DOMxRef("InputEvent.isComposing")}} {{ReadOnlyInline}}
  - : یک مقدار {{JSxRef("Boolean")}} را برمی‌گرداند که نشان می‌دهد آیا رویداد پس از {{domxref("Element/compositionstart_event", "compositionstart")}} و قبل از {{domxref("Element/compositionend_event", "compositionend")}} شلیک شده است.

## روش‌های نمونه (Instance methods)

_این رابط روش‌هایی را از والدین خود، {{DOMxRef("UIEvent")}} و {{DOMxRef("Event")}}، به ارث می‌برد._

- {{DOMxRef('InputEvent.getTargetRanges()')}}
  - : یک آرایه از اشیاء {{domxref("StaticRange")}} را برمی‌گرداند که در صورت عدم لغو رویداد ورودی (input event)، تحت تأثیر تغییر در DOM قرار خواهند گرفت.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- [`beforeinput` event](/en-US/docs/Web/API/Element/beforeinput_event)
- [`input` event](/en-US/docs/Web/API/Element/input_event)