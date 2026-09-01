---
title: "Document: createTouch() method"
short-title: createTouch()
slug: Web/API/Document/createTouch
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Document.createTouch
---

{{APIRef("DOM")}}{{Deprecated_Header}}{{Non-standard_header}}

متد **`Document.createTouch()`** یک شیء جدید {{DOMxRef("Touch")}} را ایجاد و بازمی‌گرداند.

> [!NOTE]
> از سازنده {{domxref("TouchEvent.TouchEvent", "TouchEvent()")}} استفاده کنید.

## نحو (Syntax)

```js-nolint
createTouch(view, target, identifier, pageX, pageY, screenX, screenY)
```

### پارامترها

> [!NOTE]
> همه پارامترها اختیاری هستند.

- `view`
  - : {{DOMxRef("window")}} که رویداد لمس در آن رخ داده است.
- `target`
  - : {{DOMxRef("EventTarget")}} مربوط به لمس.
- `identifier`
  - : مقدار برای {{DOMxRef("Touch.identifier")}}.
- `pageX`
  - : مقدار برای {{DOMxRef("Touch.pageX")}}.
- `pageY`
  - : مقدار برای {{DOMxRef("Touch.pageY")}}.
- `screenX`
  - : مقدار برای {{DOMxRef("Touch.screenX")}}.
- `screenY`
  - : مقدار برای {{DOMxRef("Touch.screenY")}}.

> [!NOTE]
> نسخه‌های قبلی این متد شامل پارامترهای اضافی زیر بودند، اما این پارامترها در هیچ‌کدام از استانداردهای ذکر شده در زیر گنجانده نشده‌اند. بنابراین، این پارامترها باید منسوخ (deprecated) در نظر گرفته شوند و نباید استفاده شوند.

- `clientX`
  - : مقدار برای {{DOMxRef("Touch.clientX")}}.
- `clientY`
  - : مقدار برای {{DOMxRef("Touch.clientY")}}.
- `radiusX`
  - : مقدار برای {{DOMxRef("Touch.radiusX")}}.
- `radiusY`
  - : مقدار برای {{DOMxRef("Touch.radiusY")}}.
- `rotationAngle`
  - : مقدار برای {{DOMxRef("Touch.rotationAngle")}}.
- `force`
  - : مقدار برای {{DOMxRef("Touch.force")}}.

### مقدار بازگشتی

یک {{DOMxRef("Touch")}} که مطابق با پارامترهای ورودی پیکربندی شده است.

## مثال‌ها

این مثال نحوه استفاده از متد `Document.createTouch()` را برای ایجاد اشیاء {{DOMxRef("Touch")}} نشان می‌دهد.

در قطعه کد زیر، دو شیء {{DOMxRef("Touch")}} برای عنصر `target` ایجاد می‌شود.

```js
const target = document.getElementById("target");

const touch1 = document.createTouch(window, target, 1, 15, 20, 35, 40);
const touch2 = document.createTouch(window, target, 2, 25, 30, 45, 50);
```

## مشخصات

این ویژگی بخشی از هیچ مشخصات فعلی نیست. دیگر در مسیر تبدیل شدن به استاندارد قرار ندارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رویدادهای لمس](/en-US/docs/Web/API/Touch_events)
- {{DOMxRef("TouchList")}}
- {{DOMxRef("Touch")}}
- {{DOMxRef("Document.createTouchList()")}}