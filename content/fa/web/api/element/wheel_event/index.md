---
title: "Element: wheel event"
---

---
title: "Element: wheel event"
short-title: wheel
slug: Web/API/Element/wheel_event
page-type: web-api-event
browser-compat: api.Element.wheel_event
---

{{APIRef("UI Events")}}

رویداد **`wheel`** زمانی رخ می‌دهد که کاربر چرخ دکمه‌ی یک دستگاه اشاره‌گر (معمولاً ماوس) را می‌چرخاند. این رویداد همچنین برای دستگاه‌های مرتبطی که عملکرد چرخ را شبیه‌سازی می‌کنند، مانند ترک‌پدها و گوی‌های ماوس، ارسال می‌شود.

این رویداد جایگزین رویداد غیراستاندارد و منسوخ‌شدهٔ {{domxref("Element/mousewheel_event", "mousewheel")}} می‌شود.

رویداد `wheel` را با رویداد {{domxref("Element/scroll_event", "scroll")}} اشتباه نگیرید:

- یک رویداد `wheel` لزوماً یک رویداد `scroll` ارسال نمی‌کند. به‌عنوان مثال، ممکن است عنصر اصلاً قابل پیمایش نباشد. عمل‌های بزرگ‌نمایی با استفاده از چرخ یا ترک‌پد نیز رویدادهای `wheel` را فعال می‌کنند (با {{domxref("MouseEvent/ctrlKey", "ctrlKey")}} برابر با true).
- یک رویداد `scroll` لزوماً توسط یک رویداد `wheel` ایجاد نمی‌شود. عناصر همچنین می‌توانند با استفاده از صفحه‌کلید، کشیدن نوار پیمایش (scrollbar) یا استفاده از جاوااسکریپت پیمایش شوند.
- حتی زمانی که رویداد `wheel` پیمایش را فعال می‌کند، مقادیر `delta*` در رویداد `wheel` لزوماً جهت پیمایش محتوا را منعکس نمی‌کنند.

بنابراین، برای به دست آوردن جهت پیمایش به ویژگی‌های `delta*` رویداد `wheel` تکیه نکنید. در عوض، تغییرات مقادیر {{domxref("Element.scrollLeft", "scrollLeft")}} و {{domxref("Element.scrollTop", "scrollTop")}} عنصر هدف را در رویداد `scroll` شناسایی کنید.

رویداد `wheel` قابل لغو (cancelable) است. در برخی مرورگرها، تنها اولین رویداد `wheel` در یک دنباله قابل لغو است و رویدادهای بعدی غیرقابل‌لغو هستند. اگر رویداد لغو شود، هیچ پیمایش یا بزرگ‌نمایی انجام نمی‌شود. این ممکن است مشکلات عملکردی ایجاد کند، زیرا مرورگر باید قبل از پیمایش واقعی محتوا، منتظر پردازش هر رویداد `wheel` بماند. می‌توانید با تنظیم `passive: true` هنگام فراخوانی {{domxref("EventTarget.addEventListener", "addEventListener()")}} از این مشکل جلوگیری کنید؛ این کار ممکن است باعث شود مرورگر رویدادهای `wheel` غیرقابل‌لغو تولید کند.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("wheel", (event) => { })

onwheel = (event) => { }
```

## Event type

یک {{domxref("WheelEvent")}}. از {{domxref("MouseEvent")}}، {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("WheelEvent")}}

## Examples

### Scaling an element via the wheel

این مثال نشان می‌دهد که چگونه می‌توان یک عنصر را با استفاده از چرخ ماوس (یا سایر دستگاه‌های اشاره‌گر) مقیاس‌بندی (scale) کرد.

```html
<div>Scale me with your mouse wheel.</div>
```

```css
body {
  min-height: 100vh;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

div {
  width: 105px;
  height: 105px;
  background: #ccddff;
  padding: 5px;
}
```

```js
let scale = 1;
const el = document.querySelector("div");

function zoom(event) {
  event.preventDefault();

  scale += event.deltaY * -0.01;

  // Restrict scale
  scale = Math.min(Math.max(0.125, scale), 4);

  // Apply scale transform
  el.style.transform = `scale(${scale})`;
}

el.onwheel = zoom;
```

{{EmbedLiveSample("Scaling_an_element_via_the_wheel", 700, 300)}}

### addEventListener equivalent

مدیر رویداد را می‌توان با استفاده از روش {{domxref("EventTarget/addEventListener", "addEventListener()")}} نیز تنظیم کرد:

```js
el.addEventListener("wheel", zoom, { passive: false });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("WheelEvent")}}