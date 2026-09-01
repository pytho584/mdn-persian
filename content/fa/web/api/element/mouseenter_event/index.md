---
title: "Element: mouseenter event"
short-title: mouseenter
slug: Web/API/Element/mouseenter_event
page-type: web-api-event
browser-compat: api.Element.mouseenter_event
---

{{APIRef("UI Events")}}

رویداد **`mouseenter`** زمانی روی یک {{domxref("Element")}} شلیک می‌شود که یک دستگاه اشاره‌گر (معمولاً ماوس) ابتدا طوری حرکت داده شود که نقطه‌ی داغ (hotspot) آن داخل عنصری قرار گیرد که رویداد روی آن شلیک شده است.

توجه داشته باشید که «حرکت به داخل یک عنصر» به موقعیت عنصر در درخت DOM اشاره دارد، نه به موقعیت بصری آن. برای مثال، اگر یک عنصر فرزند به‌گونه‌ای قرار گیرد که خارج از والد خود باشد، حرکت به داخل عنصر فرزند، رویداد `mouseenter` را روی عنصر والد شلیک می‌کند، حتی اگر نشانگر همچنان خارج از محدوده‌ی والد باشد.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده‌ی رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("mouseenter", (event) => { })

onmouseenter = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث برده است.

{{InheritanceDiagram("MouseEvent")}}

## نکات استفاده

اگرچه شبیه به {{domxref("Element/mouseover_event", "mouseover")}} است، اما `mouseenter` از این جهت متفاوت است که [حباب (bubble) نمی‌کند](/en-US/docs/Web/API/Event/bubbles) و وقتی نشانگر از فضای فیزیکی یکی از نوادگان به فضای فیزیکی خود عنصر حرکت می‌کند، به هیچ‌یک از نوادگان ارسال نمی‌شود. جدا از این، رویدادهای enter و over برای همان وضعیت، در صورت لزوم، همزمان شلیک می‌شوند.

### رفتار رویدادهای `mouseenter`

این توضیح، رویدادهای mouseenter دریافت‌شده توسط هر یک از چهار div هم‌مرکز را بدون padding یا margin توصیف می‌کند، بنابراین همه‌ی رویدادها در یک زمان رخ می‌دهند:
![نمودار رفتار mouseenter](mouseenter.png)
هنگام ورود به هر عنصر از سلسله‌مراتب، یک رویداد `mouseenter` به آن ارسال می‌شود. در اینجا وقتی نشانگر به متن می‌رسد، ۴ رویداد به چهار عنصر سلسله‌مراتب ارسال می‌شود.

### رفتار رویدادهای `mouseover`

![نمودار رفتار mouseover](mouseover.png)
یک رویداد `mouseover` به عمیق‌ترین عنصر درخت DOM ارسال می‌شود و سپس در سلسله‌مراتب به سمت بالا حباب می‌کند تا زمانی که توسط یک کنترل‌کننده لغو شود یا به ریشه برسد.

با سلسله‌مراتب عمیق، تعداد رویدادهای `mouseenter` ارسال‌شده می‌تواند بسیار زیاد شود و مشکلات عملکردی قابل‌توجهی ایجاد کند. در چنین مواردی، بهتر است به رویدادهای `mouseover` گوش دهید.

ترکیب با رویداد متناظر `mouseleave` (که وقتی ماوس از ناحیه‌ی محتوایی عنصر خارج می‌شود، روی عنصر شلیک می‌شود)، رویداد `mouseenter` رفتاری بسیار مشابه با شبه‌کلاس CSS {{cssxref(':hover')}} دارد.

## مثال‌ها

مستندات [`mouseover`](/en-US/docs/Web/API/Element/mouseover_event#examples) مثالی دارد که تفاوت بین `mouseover` و `mouseenter` را نشان می‌دهد.

### mouseenter

مثال ساده‌ی زیر از رویداد `mouseenter` برای تغییر حاشیه‌ی `div` هنگام ورود ماوس به فضای اختصاص‌داده‌شده به آن استفاده می‌کند. سپس آیتمی با شماره‌ی رویداد `mouseenter` یا `mouseleave` به فهرست اضافه می‌کند.

#### HTML

```html
<div id="mouseTarget">
  <ul id="unorderedList">
    <li>No events yet!</li>
  </ul>
</div>
```

#### CSS

استایل‌دهی به `div` برای اینکه بیشتر قابل‌مشاهده باشد.

```css
#mouseTarget {
  box-sizing: border-box;
  width: 15rem;
  border: 1px solid #333333;
}
```

#### JavaScript

```js
let enterEventCount = 0;
let leaveEventCount = 0;
const mouseTarget = document.getElementById("mouseTarget");
const unorderedList = document.getElementById("unorderedList");

mouseTarget.addEventListener("mouseenter", (e) => {
  mouseTarget.style.border = "5px dotted orange";
  enterEventCount++;
  addListItem(`This is mouseenter event ${enterEventCount}.`);
});

mouseTarget.addEventListener("mouseleave", (e) => {
  mouseTarget.style.border = "1px solid #333333";
  leaveEventCount++;
  addListItem(`This is mouseleave event ${leaveEventCount}.`);
});

function addListItem(text) {
  // Create a new text node using the supplied text
  const newTextNode = document.createTextNode(text);

  // Create a new li element
  const newListItem = document.createElement("li");

  // Add the text node to the li element
  newListItem.appendChild(newTextNode);

  // Add the newly created list item to list
  unorderedList.appendChild(newListItem);
}
```

### نتیجه

{{EmbedLiveSample('mouseenter')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/mousemove_event", "mousemove")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mouseover_event", "mouseover")}}
- {{domxref("Element/mouseout_event", "mouseout")}}
- {{domxref("Element/mouseleave_event", "mouseleave")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/pointerenter_event", "pointerenter")}}