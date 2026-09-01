---
title: "Element: mouseleave event"
short-title: mouseleave
slug: Web/API/Element/mouseleave_event
page-type: web-api-event
browser-compat: api.Element.mouseleave_event
---

{{APIRef("UI Events")}}

رویداد **`mouseleave`** زمانی روی یک {{domxref("Element")}} رخ می‌دهد که مکان‌نمای یک دستگاه اشاره‌گر (معمولاً ماوس) از آن عنصر خارج شود.

رویدادهای `mouseleave` و {{domxref("Element/mouseout_event", "mouseout")}} مشابه هستند اما تفاوت آن‌ها در این است که `mouseleave` حباب نمی‌شود (bubble نمی‌کند) اما `mouseout` حباب می‌شود. این بدان معناست که `mouseleave` زمانی رخ می‌دهد که اشاره‌گر از عنصر _و_ همهٔ فرزندان آن خارج شده باشد، در حالی که `mouseout` زمانی رخ می‌دهد که اشاره‌گر از عنصر _یا_ یکی از فرزندان آن خارج شود، به دلیل حباب‌شدن (حتی اگر اشاره‌گر همچنان داخل خود عنصر باشد). به‌جز این، در صورت اقتضا، رویدادهای خروج (leave و out) برای موقعیت یکسان، هم‌زمان ارسال می‌شوند.

رویدادهای `mouseleave` و `mouseout` وقتی عنصر جایگزین یا از DOM حذف شود، فعال نخواهند شد.

توجه داشته باشید که «خروج از یک عنصر» به جایگاه عنصر در درخت DOM اشاره دارد، نه به جایگاه بصری آن. برای مثال، اگر دو عنصر خواهر به‌گونه‌ای چیدمان شوند که یکی داخل دیگری قرار بگیرد، حرکت از عنصر بیرونی به عنصر داخلی باعث فعال‌شدن رویداد `mouseleave` روی عنصر بیرونی می‌شود، حتی اگر اشاره‌گر همچنان در محدودهٔ عنصر بیرونی باشد.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم ویژگیِ handler رویداد، به‌کار ببرید.

```js-nolint
addEventListener("mouseleave", (event) => { })

onmouseleave = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("MouseEvent")}}

## توضیحات

### رفتار رویدادهای `mouseleave`

![نمودار رفتار mouseleave](mouseleave.png)

هنگام خروج از عناصر، یک رویداد `mouseleave` به هر عنصر از سلسله‌مراتب ارسال می‌شود. در این‌جا وقتی اشاره‌گر از متن به ناحیه‌ای خارج از بیرونی‌ترین div نشان‌داده‌شده حرکت کند، چهار رویداد به چهار عنصر سلسله‌مراتب ارسال می‌شود.

### رفتار رویدادهای `mouseout`

![نمودار رفتار mouseout](mouseout.png)

یک رویداد `mouseout` به عمیق‌ترین عنصر درخت DOM ارسال می‌شود و سپس در سلسله‌مراتب به سمت بالا حباب می‌شود تا زمانی که توسط یک handler لغو شود یا به ریشه برسد.

## مثال‌ها

مستندات [`mouseout`](/en-US/docs/Web/API/Element/mouseout_event#examples) نمونه‌ای دارد که تفاوت بین `mouseout` و `mouseleave` را نشان می‌دهد.

### mouseleave

مثال سادهٔ زیر از رویداد `mouseenter` برای تغییر حاشیهٔ `<div>` هنگام ورود ماوس به فضای اختصاص‌داده‌شده به آن استفاده می‌کند. سپس آیتمی به فهرست اضافه می‌کند که شامل شمارهٔ رویداد `mouseenter` یا `mouseleave` است.

#### HTML

```html
<div id="mouseTarget">
  <ul id="unorderedList">
    <li>No events yet!</li>
  </ul>
</div>
```

#### CSS

استایل‌دهی به `<div>` برای اینکه بیشتر دیده شود.

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

#### نتیجه

{{EmbedLiveSample('mouseleave')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: آشنایی با رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/mousemove_event", "mousemove")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mouseover_event", "mouseover")}}
- {{domxref("Element/mouseout_event", "mouseout")}}
- {{domxref("Element/mouseenter_event", "mouseenter")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/pointerleave_event", "pointerleave")}}