---
title: "HTMLMediaElement: networkState property"
short-title: networkState
slug: Web/API/HTMLMediaElement/networkState
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.networkState
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.networkState`** وضعیت فعلی دریافت رسانه از طریق شبکه را نشان می‌دهد.

## مقدار

یک `unsigned short`. مقادیر ممکن به صورت زیر هستند:

| Constant            | Value | Description                                                                           |
| ------------------- | ----- | ------------------------------------------------------------------------------------- |
| `NETWORK_EMPTY`     | 0     | هنوز داده‌ای وجود ندارد. همچنین `readyState` برابر با `HAVE_NOTHING` است.             |
| `NETWORK_IDLE`      | 1     | `HTMLMediaElement` فعال است و یک منبع انتخاب کرده است، اما از شبکه استفاده نمی‌کند. |
| `NETWORK_LOADING`   | 2     | مرورگر در حال دانلود داده‌های `HTMLMediaElement` است.                                 |
| `NETWORK_NO_SOURCE` | 3     | هیچ `src` برای `HTMLMediaElement` یافت نشد.                                           |

## مثال

این مثال به عنصر صوتی گوش می‌دهد تا پخش شروع شود و سپس بررسی می‌کند که آیا هنوز در حال بارگذاری داده است یا خیر.

```html
<audio id="example" preload="auto">
  <source src="sound.ogg" type="audio/ogg" />
</audio>
```

```js
const obj = document.getElementById("example");

obj.addEventListener("playing", () => {
  if (obj.networkState === 2) {
    // Still loading…
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement")}}: رابطی که ویژگی `HTMLMediaElement.networkState` را تعریف می‌کند.