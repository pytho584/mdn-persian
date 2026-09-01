---
title: "Element: focusin event"
short-title: focusin
slug: Web/API/Element/focusin_event
page-type: web-api-event
browser-compat: api.Element.focusin_event
---

{{APIRef("UI Events")}}

رویداد **`focusin`** هنگامی رخ میدهد که یک عنصر تمرکز (focus) را دریافت کرده باشد؛ این رویداد پس از رویداد {{domxref("Element/focus_event", "focus")}} رخ میدهد. تفاوت این دو رویداد در این است که `focusin` حباب میزند (bubbles)، در حالی که `focus` این کار را نمیکند.

رویداد متقابل `focusin` رویداد {{domxref("Element/focusout_event", "focusout")}} است که هنگامی رخ میدهد عنصر تمرکز خود را از دست بدهد.

رویداد `focusin` قابل لغو (cancelable) نیست.

## نحو (Syntax)

برای استفاده، نام رویداد را در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی مدیریتکننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("focusin", (event) => { })

onfocusin = (event) => { }
```

## نوع رویداد

یک {{domxref("FocusEvent")}} که از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث برده شده است.

{{InheritanceDiagram("FocusEvent")}}

## مثالها

### مثال زنده

#### HTML

```html
<form id="form">
  <label>
    متنی:
    <input type="text" placeholder="ورودی متن" />
  </label>
  <label>
    رمز عبور:
    <input type="password" placeholder="رمز عبور" />
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
> در مشخصات _UI Events_، [ترتیبی برای رویدادهای تمرکز](/en-US/docs/Web/API/FocusEvent#order_of_events) توصیف شده است که با آنچه مرورگرهای فعلی پیادهسازی میکنند متفاوت است.

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: {{domxref("Element/blur_event", "blur")}}، {{domxref("Element/focus_event", "focus")}}، {{domxref("Element/focusout_event", "focusout")}}
- [تمرکز: focus/blur](https://javascript.info/focus-blur)