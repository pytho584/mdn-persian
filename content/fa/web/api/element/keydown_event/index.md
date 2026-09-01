---
title: "Element: keydown event"
short-title: keydown
slug: Web/API/Element/keydown_event
page-type: web-api-event
browser-compat: api.Element.keydown_event
---

{{APIRef("UI Events")}}

رویداد **`keydown`** زمانی که یک کلید فشرده میشود، فعال میشود.

برخلاف رویداد منسوخ {{domxref("Element/keypress_event", "keypress")}}، رویداد `keydown` برای همه کلیدها، صرفنظر از اینکه مقدار کاراکتری تولید کنند یا نه، فعال میشود.

رویدادهای `keydown` و [`keyup`](/en-US/docs/Web/API/Element/keyup_event) کدی را ارائه میدهند که نشان میدهد کدام کلید فشرده شده است، در حالی که `keypress` نشان میدهد کدام کاراکتر وارد شده است. برای مثال، حرف کوچک «a» توسط `keydown` و `keyup` بهصورت ۶۵ گزارش میشود، اما توسط `keypress` بهصورت ۹۷. حرف بزرگ «A» توسط همه رویدادها بهصورت ۶۵ گزارش میشود.

هدف رویداد (event target) یک رویداد کلید، عنصری است که در حال حاضر فوکوس دارد و فعالیت صفحهکلید را پردازش میکند. این شامل {{HTMLElement("input")}}، {{HTMLElement("textarea")}}، هر چیزی که [`contentEditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) باشد، و هر چیز دیگری که میتوان با صفحهکلید با آن تعامل کرد، مانند {{HTMLElement("a")}}، {{HTMLElement("button")}} و {{HTMLElement("summary")}} میشود. اگر هیچ عنصر مناسبی در فوکوس نباشد، هدف رویداد {{HTMLElement("body")}} یا ریشه خواهد بود. رویداد [حبابگونه](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) است و میتواند به {{domxref("Document")}} و {{domxref("Window")}} برسد.

هدف رویداد ممکن است بین رویدادهای مختلف کلید تغییر کند. برای مثال، هدف `keydown` برای فشردن کلید <kbd>Tab</kbd> با هدف `keyup` متفاوت خواهد بود، زیرا فوکوس تغییر کرده است.

## نحو

از نام رویداد در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با تنظیم یک ویژگی کنترلکننده رویداد استفاده کنید.

```js-nolint
addEventListener("keydown", (event) => { })

onkeydown = (event) => { }
```

## نوع رویداد

یک {{domxref("KeyboardEvent")}}. ارث بردن از {{domxref("UIEvent")}} و {{domxref("Event")}}.

{{InheritanceDiagram("KeyboardEvent")}}

## مثالها

### مثال addEventListener با keydown

این مثال مقدار {{domxref("KeyboardEvent.code")}} را هر بار که کلیدی را در داخل عنصر {{HtmlElement("input")}} فشار دهید، ثبت میکند.

```html
<input placeholder="اینجا کلیک کنید، سپس یک کلید را فشار دهید." size="40" />
<p id="log"></p>
```

```js
const input = document.querySelector("input");
const log = document.getElementById("log");

input.addEventListener("keydown", logKey);

function logKey(e) {
  log.textContent += ` ${e.code}`;
}
```

{{EmbedLiveSample("addEventListener_keydown_example")}}

### رویدادهای keydown با IME

از Firefox ۶۵ به بعد، رویدادهای `keydown` و [`keyup`](/en-US/docs/Web/API/Element/keyup_event) اکنون در طول ترکیب در {{glossary("Input method editor")}} فعال میشوند تا سازگاری بین مرورگرها برای کاربران CJKT بهبود یابد ([بحث ۳۵۴۳۵۸ در Bugzilla](https://bugzil.la/354358)). برای نادیده گرفتن همه رویدادهای `keydown` که بخشی از ترکیب هستند، کاری شبیه به این انجام دهید (۲۲۹ یک مقدار ویژه برای `keyCode` است که مربوط به رویدادی است که توسط IME پردازش شده است):

```js
eventTarget.addEventListener("keydown", (event) => {
  if (event.isComposing || event.keyCode === 229) {
    return;
  }
  // انجام کار
});
```

> [!NOTE]
> `compositionstart` ممکن است _پس از_ `keydown` فعال شود، زمانی که اولین نویسه را تایپ میکنید که IME را باز میکند، و `compositionend` ممکن است _قبل از_ `keydown` فعال شود، زمانی که آخرین نویسه را تایپ میکنید که IME را میبندد. در این موارد، `isComposing` حتی زمانی که رویداد بخشی از ترکیب است، `false` است. با این حال، {{domxref("KeyboardEvent.keyCode")}} در این موارد همچنان `229` است، بنابراین همچنان توصیه میشود که `keyCode` را نیز بررسی کنید، اگرچه منسوخ شده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [`input`](/en-US/docs/Web/API/Element/input_event)
- [`keypress`](/en-US/docs/Web/API/Element/keypress_event)
- [`keyup`](/en-US/docs/Web/API/Element/keyup_event)