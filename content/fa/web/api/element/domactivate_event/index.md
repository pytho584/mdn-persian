---
title: "Element: DOMActivate event"
short-title: DOMActivate
slug: Web/API/Element/DOMActivate_event
page-type: web-api-event
status:
  - deprecated
browser-compat: api.Element.DOMActivate_event
---

{{APIRef}}{{Deprecated_Header}}

رویداد **`DOMActivate`** روی یک عنصر هنگامی که فعال می‌شود - مانند زمانی که با ماوس کلیک می‌شود یا با کلید فشرده به آن پیمایش می‌شود - فعال می‌گردد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید.

```js-nolint
addEventListener("DOMActivate", (event) => { })
```

> [!NOTE]
> برای این رویداد، ویژگی رویدادگردان `onDOMActivate` وجود ندارد.

## نوع رویداد

یک {{domxref("UIEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("UIEvent")}}

## مثال‌ها

این مثال به رویداد `DOMActivate` روی یک عنصر {{HtmlElement("button")}} گوش می‌دهد و {{domxref("UIEvent/detail", "detail")}} آن را نمایش می‌دهد.

### HTML

```html
<button>Click</button>
```

### JavaScript

```js
const button = document.querySelector("button");

button.addEventListener("DOMActivate", (event) => {
  button.textContent = `Click count: ${event.detail}`;
});
```

### نتیجه

توجه داشته باشید که `detail` رویداد `DOMActivate` ممکن است رفتار خاص مرورگر داشته باشد. ممکن است همیشه `0` باشد یا رفتاری مشابه `detail` رویداد {{domxref("Element/click_event", "click")}} داشته باشد (یعنی نشان‌دهنده تعداد کلیک‌های متوالی).

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("UIEvent")}}
- {{domxref("Element/click_event", "click")}}