---
title: "PictureInPictureEvent: PictureInPictureEvent() constructor"
short-title: PictureInPictureEvent()
slug: Web/API/PictureInPictureEvent/PictureInPictureEvent
page-type: web-api-constructor
browser-compat: api.PictureInPictureEvent.PictureInPictureEvent
---

{{APIRef("Picture-in-Picture API")}}

سازندهٔ **`PictureInPictureEvent()`** یک شیء جدید از نوع {{domxref("PictureInPictureEvent")}} برمی‌گرداند.

## نحو

```js-nolint
new PictureInPictureEvent(type, options)
```

### پارامترها

- `type`
  - : رشته‌ای است که نام رویداد را نشان می‌دهد. این مقدار به بزرگی/کوچکی حروف حساس است و مرورگرها آن را روی `enterpictureinpicture`، `leavepictureinpicture` یا `resize` تنظیم می‌کنند.
- `options`
  - : شیءای که، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `pictureInPictureWindow`
      - : یک {{domxref("PictureInPictureWindow")}}.

### مقدار برگشتی

یک شیء جدید از نوع {{domxref("PictureInPictureEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("PictureInPictureEvent")}} که این سازنده به آن تعلق دارد.