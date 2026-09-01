---
title: "FormDataEvent: FormDataEvent() constructor"
short-title: FormDataEvent()
slug: Web/API/FormDataEvent/FormDataEvent
page-type: web-api-constructor
browser-compat: api.FormDataEvent.FormDataEvent
---

{{APIRef("DOM")}}

سازنده‌ی **`FormDataEvent()`** یک شیء جدید از نوع {{domxref("FormDataEvent")}} می‌سازد.

## سینتکس

```js-nolint
new FormDataEvent(type, formEventInit)
```

### پارامترها

- `type`
  - : یک رشته (String) شامل نام رویداد است.
    مقدار آن به بزرگی و کوچکی حروف حساس است و مرورگرها همیشه آن را روی `formdata` تنظیم می‌کنند.
- `options`
  - : یک شیء است که، _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی زیر را نیز داشته باشد:
    - `formData`
      - : یک شیء {{domxref("FormData")}} برای پر کردن اولیه‌ی {{domxref("FormDataEvent")}}.
        این شیء سپس از طریق ویژگی {{domxref("FormDataEvent.formData")}} قابل دسترسی خواهد بود.

### مقدار بازگشتی

یک شیء جدید از نوع {{domxref("FormDataEvent")}}.

## مثال‌ها

```js
const fd = new FormData();
fd.append("test", "test");

const fdEv = new FormDataEvent("formdata", { formData: fd });

for (const value of fdEv.formData.values()) {
  console.log(value);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("FormDataEvent")}}