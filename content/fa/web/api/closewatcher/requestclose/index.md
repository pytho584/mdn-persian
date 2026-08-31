---
title: "CloseWatcher: requestClose() method"
short-title: requestClose()
slug: Web/API/CloseWatcher/requestClose
page-type: web-api-instance-method
browser-compat: api.CloseWatcher.requestClose
---

{{APIRef("HTML DOM")}}

متد **`requestClose()`** از رابط {{domxref("CloseWatcher")}} یک رویداد `cancel` را فعال می‌کند و اگر آن رویداد با {{domxref("Event.preventDefault()")}} لغو نشود، به فعال‌سازی رویداد `close` ادامه می‌دهد و سپس ناظر بستن (close watcher) را به همان شکلی که اگر `destroy()` فراخوانی شده بود، غیرفعال می‌کند.

## نحو

```js-nolint
requestClose()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده از متد `requestClose()`

در این مثال، شما یک کامپوننت رابط کاربری مخصوص خود (یک انتخاب‌گر یا picker) دارید و می‌خواهید هم از روش بستن پیش‌فرض پلتفرم (مثلاً کلید <kbd>Esc</kbd>) و هم از روش بستن سفارشی خود (دکمه بستن) پشتیبانی کنید.

مدیر رویداد `onclick` کامپوننت رابط کاربری شما می‌تواند `requestClose` را برای درخواست بستن فراخوانی کند و درخواست بستن شما را از طریق همان مدیر رویداد `onclose` که روش بستن پلتفرم استفاده می‌کند، هدایت کند.

```js
const watcher = new CloseWatcher();
const picker = setUpAndShowPickerDOMElement();
let chosenValue = null;

watcher.onclose = () => {
  chosenValue = picker.querySelector("input").value;
  picker.remove();
};

picker.querySelector(".close-button").onclick = () => {
  watcher.requestClose();
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}