---
title: "MediaList: item() method"
short-title: item()
slug: Web/API/MediaList/item
page-type: web-api-instance-method
browser-compat: api.MediaList.item
---

{{ APIRef("CSSOM") }}

متد **`item()`** از رابط {{domxref("MediaList")}}، رسانه‌ی (media query) موجود در اندیس مشخص‌شده را برمی‌گرداند، یا اگر اندیس موردنظر وجود نداشته باشد، `null` برمی‌گرداند.

## Syntax

```js-nolint
item(index)
[index]
```

> [!NOTE]
> می‌توان به‌جای سینتکس `item()` از سینتکس براکت (`[]`) نیز استفاده کرد.

### Parameters

- `index`
  - : یک عدد صحیح.

### Return value

اگر از سینتکس براکت (`[]`) استفاده شود و ورودی‌ای برای اندیس داده‌شده وجود نداشته باشد، `undefined` برگردانده می‌شود.

## Examples

در مثال زیر، هر رسانه‌ی (media query) ذخیره‌شده در `MediaList` مرتبط با اولین stylesheet اعمال‌شده به سند فعلی، در کنسول ثبت (log) می‌شود.

```js
const stylesheet = document.styleSheets[0];
console.log(stylesheet.media.length);
console.log(stylesheet.media.item(0)); // Returns a string like "print"
console.log(stylesheet.media.item(5)); // Returns null if there is no 5th entry
console.log(stylesheet.media[1]); // Returns a string like "print"
console.log(stylesheet.media[5]); // Returns undefined if there is no 5th entry
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}