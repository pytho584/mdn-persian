---
title: "DataTransfer: getData() method"
---

---
title: "DataTransfer: getData() method"
short-title: getData()
slug: Web/API/DataTransfer/getData
page-type: web-api-instance-method
browser-compat: api.DataTransfer.getData
---

{{APIRef("HTML DOM")}}

متد **`DataTransfer.getData()`** دادهٔ کشیدن (drag data) را برای نوع مشخص‌شده به‌صورت یک رشته بازیابی می‌کند. اگر عملیات کشیدن داده‌ای نداشته باشد، این متد یک رشتهٔ خالی برمی‌گرداند.

نمونه‌هایی از انواع داده عبارت‌اند از `text/plain` و `text/uri-list`.

## سینتکس

```js-nolint
getData(format)
```

### پارامترها

- `format`
  - : رشته‌ای که نوع دادهٔ مورد نظر برای بازیابی را مشخص می‌کند.

### مقدار بازگشتی

یک رشته که دادهٔ کشیدن را برای `format` مشخص‌شده نشان می‌دهد. اگر عملیات کشیدن داده‌ای نداشته باشد یا برای `format` مشخص‌شده داده‌ای موجود نباشد، این متد یک رشتهٔ خالی برمی‌گرداند.

توجه داشته باشید که ممکن است `DataTransfer.getData()` مقدار مورد انتظار را برنگرداند؛ زیرا این متد فقط برای رویدادهای مشخصی امکان خواندن و نوشتن داده را فراهم می‌کند. در طول رویدادهای `dragstart` و `drop`، دسترسی به داده امن است. برای همهٔ رویدادهای دیگر، باید داده را در دسترس نبودن تلقی کرد. با وجود این، همچنان می‌توان آیتم‌ها و قالب‌های آن‌ها را برشمرد.

## مثال‌ها

این مثال کاربرد متدهای `getData()` و {{domxref("DataTransfer.setData()","setData()")}} از شیء {{domxref("DataTransfer")}} را نشان می‌دهد.

### HTML

```html
<div id="div1">
  <span id="drag" draggable="true">drag me to the other box</span>
</div>
<div id="div2"></div>
```

### CSS

```css
#div1,
#div2 {
  width: 100px;
  height: 50px;
  padding: 10px;
  border: 1px solid #aaaaaa;
}
```

### JavaScript

```js
const div1 = document.getElementById("div1");
const div2 = document.getElementById("div2");
const dragElement = document.getElementById("drag");

dragElement.addEventListener("dragstart", drag);
div1.addEventListener("dragover", allowDrop);
div2.addEventListener("dragover", allowDrop);
div1.addEventListener("drop", drop);
div2.addEventListener("drop", drop);

function allowDrop(allowDropEvent) {
  allowDropEvent.target.style.color = "blue";
  allowDropEvent.preventDefault();
}

function drag(dragEvent) {
  dragEvent.dataTransfer.setData("text", dragEvent.target.id);
  dragEvent.target.style.color = "green";
}

function drop(dropEvent) {
  dropEvent.preventDefault();
  const data = dropEvent.dataTransfer.getData("text");
  dropEvent.target.appendChild(document.getElementById(data));
  dragElement.style.color = "black";
}
```

### نتیجه

{{EmbedLiveSample('Examples', 600) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [کشیدن و رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با ذخیره‌گاه دادهٔ کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)