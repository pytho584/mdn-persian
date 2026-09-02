---
title: "MouseEvent: relatedTarget property"
short-title: relatedTarget
slug: Web/API/MouseEvent/relatedTarget
page-type: web-api-instance-property
browser-compat: api.MouseEvent.relatedTarget
---

{{APIRef("Pointer Events")}}

ویژگی فقط‑خواندنی **`MouseEvent.relatedTarget`**، هدف ثانویه برای رویداد ماوس است، در صورت وجود.

به عبارت دیگر:

<table class="no-markdown">
  <thead>
    <tr>
      <th>نام رویداد</th>
      <th><code>target</code></th>
      <th><code>relatedTarget</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>{{domxref("Element/mouseenter_event", "mouseenter")}}</td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر وارد آن شده است
      </td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر از آن خارج شده است
      </td>
    </tr>
    <tr>
      <td>{{domxref("Element/mouseleave_event", "mouseleave")}}</td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر از آن خارج شده است
      </td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر وارد آن شده است
      </td>
    </tr>
    <tr>
      <td>{{domxref("Element/mouseout_event", "mouseout")}}</td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر از آن خارج شده است
      </td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر وارد آن شده است
      </td>
    </tr>
    <tr>
      <td>{{domxref("Element/mouseover_event", "mouseover")}}</td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر وارد آن شده است
      </td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر از آن خارج شده است
      </td>
    </tr>
    <tr>
      <td>{{domxref("HTMLElement/dragenter_event", "dragenter")}}</td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر وارد آن شده است
      </td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر از آن خارج شده است
      </td>
    </tr>
    <tr>
      <td>{{domxref("HTMLElement/dragleave_event", "dragleave")}}</td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر از آن خارج شده است
      </td>
      <td>
        {{domxref("EventTarget")}}ای که اشاره‌گر وارد آن شده است
      </td>
    </tr>
  </tbody>
</table>

برای رویدادهایی که هدف ثانویه ندارند، `relatedTarget` مقدار `null` را برمی‌گرداند.

{{domxref("FocusEvent.relatedTarget")}} ویژگی مشابهی برای رویدادهای فوکوس است.

## مقدار

یک شیء {{domxref("EventTarget")}} یا `null`.

## مثال‌ها

نشانگر ماوس خود را به داخل و خارج جعبه‌های قرمز و آبی حرکت دهید.

### HTML

```html
<body id="body">
  <div id="outer">
    <div id="red"></div>
    <div id="blue"></div>
  </div>
  <p id="log"></p>
</body>
```

### CSS

```css
#outer {
  width: 250px;
  height: 125px;
  display: flex;
}

#red {
  flex-grow: 1;
  background: red;
}

#blue {
  flex-grow: 1;
  background: blue;
}

#log {
  max-height: 120px;
  overflow-y: scroll;
}
```

### JavaScript

```js
const mouseoutLog = document.getElementById("log"),
  red = document.getElementById("red"),
  blue = document.getElementById("blue");

red.addEventListener("mouseover", overListener);
red.addEventListener("mouseout", outListener);
blue.addEventListener("mouseover", overListener);
blue.addEventListener("mouseout", outListener);

function outListener(event) {
  let related = event.relatedTarget ? event.relatedTarget.id : "unknown";

  mouseoutLog.innerText = `\nاز ${event.target.id} به ${related} ${mouseoutLog.innerText}`;
}

function overListener(event) {
  let related = event.relatedTarget ? event.relatedTarget.id : "unknown";

  mouseoutLog.innerText = `\nبه ${event.target.id} از ${related} ${mouseoutLog.innerText}`;
}
```

### نتیجه

{{EmbedLiveSample("Examples", 700, 280)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseEvent") }}