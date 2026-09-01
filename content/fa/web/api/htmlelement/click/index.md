---
title: "HTMLElement: click() method"
short-title: click()
slug: Web/API/HTMLElement/click
page-type: web-api-instance-method
browser-compat: api.HTMLElement.click
---

{{ APIRef("HTML DOM") }}

متد **`HTMLElement.click()`** یک کلیک ماوس بر روی یک عنصر را شبیه‌سازی می‌کند. هنگامی که روی یک عنصر فراخوانی شود، رویداد {{domxref("Element/click_event", "click")}} آن عنصر (مگر اینکه ویژگی [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled) آن تنظیم شده باشد) فعال می‌شود.

## Syntax

```js-nolint
click()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچکدام ({{jsxref("undefined")}}).

## مثال‌ها

شبیه‌سازی کلیک ماوس هنگام حرکت نشانگر ماوس بر روی یک چک‌باکس:

### HTML

```html
<form>
  <input type="checkbox" id="myCheck" />
</form>
```

### JavaScript

```js
const checkbox = document.getElementById("myCheck");

// On mouse-over, execute myFunction
checkbox.addEventListener("mouseover", () => {
  // Simulate a mouse click
  checkbox.click();
});

checkbox.addEventListener("click", () => {
  console.log("click event occurred");
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- مدیریت‌کننده‌های رویداد مرتبط
  - {{domxref("Element.click_event", "Element.onclick")}}
  - {{domxref("Element.dblclick_event", "Element.ondblclick")}}
  - {{domxref("Element.auxclick_event", "Element.onauxclick")}}