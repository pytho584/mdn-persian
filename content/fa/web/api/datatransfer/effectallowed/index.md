---
title: "DataTransfer: effectAllowed property"
short-title: effectAllowed
slug: Web/API/DataTransfer/effectAllowed
page-type: web-api-instance-property
browser-compat: api.DataTransfer.effectAllowed
---

{{APIRef("HTML Drag and Drop API")}}

ویژگی **`DataTransfer.effectAllowed`** اثری را که برای عملیات کشیدن (drag) مجاز است مشخص می‌کند. عملیات _copy_ برای نشان دادن این استفاده می‌شود که داده‌های در حال کشیده شدن از مکان فعلی خود به مکان رها شدن کپی خواهند شد. عملیات _move_ برای نشان دادن جابه‌جایی داده‌های در حال کشیده شدن به کار می‌رود، و عملیات _link_ برای نشان دادن ایجاد نوعی رابطه یا ارتباط بین مبدأ و مکان رها شدن استفاده می‌شود.

این ویژگی باید در رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} تنظیم شود تا اثر کشیدن مورد نظر برای مبدأ کشیدن تعیین گردد. درون دست‌کننده‌های رویداد {{domxref("HTMLElement/dragenter_event", "dragenter")}} و {{domxref("HTMLElement/dragover_event", "dragover")}}، این ویژگی به هر مقداری که در طول رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} اختصاص داده شده است، تنظیم می‌شود؛ بنابراین `effectAllowed` می‌تواند برای تعیین اینکه کدام اثر مجاز است استفاده شود.

اختصاص مقدار به `effectAllowed` در رویدادهایی غیر از {{domxref("HTMLElement/dragstart_event", "dragstart")}} هیچ تأثیری ندارد.

## مقدار

یک رشته که عملیات کشیدن مجاز را نشان می‌دهد. مقادیر ممکن عبارتند از:

- `none`
  - : مورد قابل رها شدن نیست.
- `copy`
  - : یک کپی از مورد مبدأ در مکان جدید ایجاد می‌شود.
- `copyLink`
  - : عملیات کپی یا پیوند مجاز است.
- `copyMove`
  - : عملیات کپی یا جابه‌جایی مجاز است.
- `link`
  - : یک پیوند به مبدأ در مکان جدید برقرار می‌شود.
- `linkMove`
  - : عملیات پیوند یا جابه‌جایی مجاز است.
- `move`
  - : یک مورد ممکن است به مکان جدید منتقل شود.
- `all`
  - : همه عملیات مجاز هستند.
- `uninitialized`
  - : مقدار پیش‌فرض زمانی که اثری تنظیم نشده است، معادل `all`.

اختصاص هر مقدار دیگری به `effectAllowed` تأثیری ندارد و مقدار قبلی حفظ می‌شود.

## مثال‌ها

### تنظیم effectAllowed

در این مثال، `effectAllowed` را در دست‌کننده `dragstart` به `"move"` تنظیم می‌کنیم.

#### HTML

```html
<div>
  <p id="source" draggable="true">
    Select this element, drag it to the Drop Zone and then release the selection
    to move the element.
  </p>
</div>
<div id="target">Drop Zone</div>
<pre id="output"></pre>
<button id="reset">Reset</button>
```

#### CSS

```css
div {
  margin: 0em;
  padding: 2em;
}

#source {
  color: blue;
  border: 1px solid black;
}

#target {
  border: 1px solid black;
}

#output {
  height: 100px;
  overflow: scroll;
}
```

#### جاوااسکریپت

```js
function dragstartHandler(ev) {
  log(`dragstart: effectAllowed = ${ev.dataTransfer.effectAllowed}`);

  // Add this element's id to the drag payload so the drop handler will
  // know which element to add to its tree
  ev.dataTransfer.setData("text", ev.target.id);
  ev.dataTransfer.effectAllowed = "move";
}

function dropHandler(ev) {
  log(`drop: effectAllowed = ${ev.dataTransfer.effectAllowed}`);

  ev.preventDefault();
  // Get the id of the target and add the element to the target's DOM
  const data = ev.dataTransfer.getData("text");
  ev.target.appendChild(document.getElementById(data));
}

function dragoverHandler(ev) {
  log(`dragover: effectAllowed = ${ev.dataTransfer.effectAllowed}`);
  ev.preventDefault();
}

const source = document.querySelector("#source");
const target = document.querySelector("#target");

source.addEventListener("dragstart", dragstartHandler);
target.addEventListener("dragover", dragoverHandler);
target.addEventListener("drop", dropHandler);

function log(message) {
  const output = document.querySelector("#output");
  output.textContent = `${output.textContent}\n${message}`;
  output.scrollTop = output.scrollHeight;
}

const reset = document.querySelector("#reset");
reset.addEventListener("click", () => document.location.reload());
```

#### نتیجه

{{EmbedLiveSample("Setting effectAllowed", 0, 400)}}

## مشخصات‌ها

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [کشیدن و رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با فروشگاه داده کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)