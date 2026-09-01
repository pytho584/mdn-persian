---
title: "Event: eventPhase property"
short-title: eventPhase
slug: Web/API/Event/eventPhase
page-type: web-api-instance-property
browser-compat: api.Event.eventPhase
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

خاصیت فقط خواندنی **`eventPhase`** از رابط {{domxref("Event")}} نشان می‌دهد که در حال حاضر کدام فاز از جریان رویداد در حال ارزیابی است.

## مقدار

یک مقدار عدد صحیح برمی‌گرداند که فاز ارزیابی فعلی جریان رویداد را مشخص می‌کند. مقادیر ممکن عبارتند از:

- `Event.NONE` (0)
  - : رویداد در این لحظه در حال پردازش نیست.
- `Event.CAPTURING_PHASE` (1)
  - : رویداد در حال انتشار از طریق اشیاء ancestor (اجداد) هدف است. این فرآیند با {{domxref("Window")}} شروع می‌شود، سپس {{domxref("Document")}}، سپس {{domxref("HTMLHtmlElement")}}، و به همین ترتیب از طریق عناصر ادامه می‌یابد تا به والد هدف برسد. {{domxref("EventTarget/addEventListener", "شنوندگان رویداد", "", 1)}} که برای حالت capture (گرفتن) هنگام فراخوانی {{domxref("EventTarget.addEventListener()")}} ثبت شده‌اند، در این فاز فراخوانی می‌شوند.
- `Event.AT_TARGET` (2)
  - : رویداد به {{domxref("EventTarget", "هدف رویداد", "", 1)}} رسیده است. شنوندگان رویداد ثبت‌شده برای این فاز در این زمان فراخوانی می‌شوند. اگر {{domxref("Event.bubbles")}} `false` باشد، پس از اتمام این فاز، پردازش رویداد به پایان می‌رسد.
- `Event.BUBBLING_PHASE` (3)
  - : رویداد در حال انتشار به سمت بالا از طریق ancestors (اجداد) هدف به ترتیب معکوس است، از والد شروع می‌شود و در نهایت به {{domxref("Window")}} محتوی می‌رسد. این به عنوان _bubbling_ (حباب‌زنی) شناخته می‌شود و تنها زمانی رخ می‌دهد که {{domxref("Event.bubbles")}} `true` باشد. {{domxref("EventTarget/addEventListener", "شنوندگان رویداد", "", 1)}} ثبت‌شده برای این فاز در طول این فرآیند فراخوانی می‌شوند.

## مثال

### HTML

```html
<h4>Event Propagation Chain</h4>
<ul>
  <li>Click 'd1'</li>
  <li>Analyze event propagation chain</li>
  <li>Click next div and repeat the experience</li>
  <li>Change Capturing mode</li>
  <li>Repeat the experience</li>
</ul>
<input type="checkbox" id="chCapture" />
<label for="chCapture">Use Capturing</label>
<div id="d1">
  d1
  <div id="d2">
    d2
    <div id="d3">
      d3
      <div id="d4">d4</div>
    </div>
  </div>
</div>
<div id="divInfo"></div>
```

### CSS

```css
div {
  margin: 20px;
  padding: 4px;
  border: thin black solid;
}

#divInfo {
  margin: 18px;
  padding: 8px;
  background-color: white;
  font-size: 80%;
}
```

### JavaScript

```js
let clear = false;
const divInfo = document.getElementById("divInfo");
const divs = document.getElementsByTagName("div");
const chCapture = document.getElementById("chCapture");

chCapture.addEventListener("click", () => {
  removeListeners();
  addListeners();
  clearDivs();
});
clearDivs();
addListeners();

function removeListeners() {
  for (const div of divs) {
    if (div.id !== "divInfo") {
      div.removeEventListener("click", onDivClick, true);
      div.removeEventListener("click", onDivClick, false);
    }
  }
}

function addListeners() {
  for (const div of divs) {
    if (div.id !== "divInfo") {
      if (chCapture.checked) {
        div.addEventListener("click", onDivClick, true);
      } else {
        div.addEventListener("click", onDivClick, false);
        div.onmousemove = () => {
          clear = true;
        };
      }
    }
  }
}

function onDivClick(e) {
  if (clear) {
    clearDivs();
    clear = false;
  }
  if (e.eventPhase === 2) {
    e.currentTarget.style.backgroundColor = "red";
  }
  const level =
    ["none", "capturing", "target", "bubbling"][e.eventPhase] ?? "error";
  const para = document.createElement("p");
  para.textContent = `${e.currentTarget.id}; eventPhase: ${level}`;
  divInfo.appendChild(para);
}

function clearDivs() {
  for (let i = 0; i < divs.length; i++) {
    if (divs[i].id !== "divInfo") {
      divs[i].style.backgroundColor = i % 2 !== 0 ? "#f6eedb" : "#cceeff";
    }
  }
  divInfo.textContent = "";
}
```

### نتیجه

{{ EmbedLiveSample('Example', '', '700') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}