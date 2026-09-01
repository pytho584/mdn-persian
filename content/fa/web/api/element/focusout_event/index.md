---
title: "Element: focusout event"
---

---
title: "Element: focusout event"
short-title: focusout
slug: Web/API/Element/focusout_event
page-type: web-api-event
browser-compat: api.Element.focusout_event
---

{{APIRef("UI Events")}}

رویداد **`focusout`** زمانی رخ می‌دهد که یک عنصر، تمرکز خود را از دست داده است؛ این رویداد پس از رویداد {{domxref("Element/blur_event", "blur")}} رخ می‌دهد. تفاوت این دو رویداد در این است که `focusout` حباب می‌زند، در حالی که `blur` حباب نمی‌زند.

رویداد مقابل «focusout»، رویداد {{domxref("Element/focusin_event", "focusin")}} است که زمانی رخ می‌دهد که عنصر، تمرکز را دریافت کرده است.

رویداد `focusout` قابل‌لغو نیست.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("focusout", (event) => { })

onfocusout = (event) => { }
```

## نوع رویداد

یک {{domxref("FocusEvent")}} که از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("FocusEvent")}}

## نمونه‌ها

### مثال زنده

#### HTML

```html
<form id="form">
  <label>
    Some text:
    <input type="text" placeholder="text input" />
  </label>
  <label>
    Password:
    <input type="password" placeholder="password" />
  </label>
</form>
```

#### JavaScript

```js
const form = document.getElementById("form");

form.addEventListener("focusin", (event) => {
  event.target.style.background = "pink";
});

form.addEventListener("focusout", (event) => {
  event.target.style.background = "";
});
```

#### نتیجه

{{EmbedLiveSample("Live_example", '100%', '50px')}}

## مشخصات

{{Specifications}}

> [!NOTE]
> مشخصات _UI Events_ یک [ترتیب رویدادهای تمرکز](/en-US/docs/Web/API/FocusEvent#order_of_events) را توصیف می‌کند که با آنچه مرورگرهای فعلی پیاده‌سازی می‌کنند متفاوت است.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: {{domxref("Element/blur_event", "blur")}}، {{domxref("Element/focus_event", "focus")}}، {{domxref("Element/focusin_event", "focusin")}}
- [Focusing: focus/blur](https://javascript.info/focus-blur)