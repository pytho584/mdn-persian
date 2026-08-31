---
title: "BlobEvent: BlobEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BlobEvent/BlobEvent"
translated_by: "n8n + AI"
---

---
title: "BlobEvent: BlobEvent() constructor"
short-title: BlobEvent()
slug: Web/API/BlobEvent/BlobEvent
page-type: web-api-constructor
browser-compat: api.BlobEvent.BlobEvent
---

{{APIRef("MediaStream Recording")}}

سازندهٔ **`BlobEvent()`** یک شیء تازه‌ساخته {{domxref("BlobEvent")}} را با یک {{domxref("Blob")}} مرتبط برمی‌گرداند.

## نحو

```js-nolint
new BlobEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته که نام رویداد است. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را روی `dataavailable` قرار می‌دهند.
- `options`
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `data`
      - : {{domxref("Blob")}} مرتبط با رویداد.
    - `timecode` {{optional_inline}}
      - : یک {{domxref("DOMHighResTimeStamp")}} برای استفاده در مقداردهی اولیه رویداد blob.

### مقدار بازگشتی

یک شیء جدید {{domxref("BlobEvent")}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("BlobEvent")}} که این رویداد به آن تعلق دارد.